---
playbook: audit-account
title: "Повний аудит рекламного кабінету Meta → дієвий звіт (post-Andromeda)"
type: analysis
status: active
era: post-andromeda
last_reviewed: 2026-06-03
output_format: "[[playbooks/report-template]]"
reads_knowledge:
  - "[[00-philosophy/andromeda-era]]"
  - "[[01-structure/campaign-structure]]"
  - "[[03-targeting/value-rules]]"
  - "[[04-budget-scaling/big-spend-scaling]]"
  - "[[04-budget-scaling/small-budget]]"
  - "[[05-optimization/learning-phase]]"
  - "[[06-creatives/why-ads-fail]]"
  - "[[09-retargeting/retargeting-post-andromeda]]"
  - "[[12-testing/post-andromeda-testing]]"
mcp: meta-ads (read-only для цього playbook)
---

# Playbook: Повний аудит рекламного кабінету Meta

> **Що це.** Покрокова процедура (SOP) глибинного аудиту акаунта Meta Ads на актуальній (post-Andromeda) методології. Вхід — `act_XXX` + бриф (target_CPL / target_ROAS / денний бюджет). Вихід — **дієвий звіт** за форматом [[playbooks/report-template]], який відповідає на **4 кути**: що працює · що ні · чому погіршення · план масштабу.
>
> **Бар якості (з META-PROMPT §10).** Користувач може сьогодні поставити в роботу ≥3 конкретні дії (не «покращити креативи», а «паузити `ad_id=X`, дублювати концепт `ad_id=Y` з бюджетом Z»). Кожна цифра має джерело `⟦метрика · object_id · період⟧`. Кожен висновок фальсифікований (вказано як перевірити).
>
> **Цей playbook — READ-ONLY.** Аудит лише читає кабінет і видає рекомендації. Будь-яка мутація (зміна бюджету / пауза / дублювання) — окремий крок через `/ads-optimizer` з підтвердженням користувача (META-PROMPT §9.3). Аудит **готує** дії, не виконує їх.

---

## 0. Залізні правила перед стартом (guardrails — META-PROMPT §9)

Прочитати й тримати в голові ввесь час:

1. **Read-before-write / read-before-claim.** Жодного числа про кабінет, якого ти не прочитав із Marketing API **цієї сесії**. Не пам'ятати числа з минулих сесій як факт.
2. **KNOWLEDGE ≠ DATA.** «Принцип з [[00-philosophy/andromeda-era]] каже X» (база знань) і «акаунт `act_XXX` показує Y» (Marketing API) — **ніколи не змішувати** й не видавати принцип за спостереження. У звіті це два різні типи речень.
3. **Поріг значущості (safety_rules).** НЕ судити об'єкт на **<1000 показів** / **<3 конверсій** / **<2 днів** даних. Мало даних → у звіт іде «**недостатньо даних — потрібна вибірка `breakdowns=...` / довший період**», а не вигаданий висновок.
4. **Цитуй джерело кожної цифри:** метрика + object_id + період + (за потреби) поріг правила. Приклад формату: `CPL $48 ⟦ad_id=123 · last_7d⟧ > 3× target $15 → правило ad-eater CRITICAL`.
5. **«Не знаю» дозволено.** Нема в даних або в KB — сказати прямо + які breakdown/період додати. Не вигадувати бенчмарки галузі.
6. **Freshness guard.** Будь-яка тактика, яку ти радиш, має бути post-Andromeda. Якщо тягне на pre-Andromeda (дублювання адсетів, розділення cold/warm, класичне A/B схожих оголошень) — позначити й звірити з [[00-philosophy/andromeda-era]] · [[01-structure/campaign-structure]] · [[12-testing/post-andromeda-testing]].
7. **Self-check обов'язковий.** Перед фінальним звітом — секція з ≥5 пунктів «це може бути хибним, якщо…».

---

## 1. Підготовка: бриф, цільові метрики, класифікація акаунта

### 1.1 Зчитати цільові метрики (з брифу — змінні, не хардкод)

Аудит керується **target-метриками з брифу**, не «галузевими нормами»:

| Змінна | Звідки | Як використовується |
|---|---|---|
| `target_CPL` | бриф | головний поріг для CPL Gap, ad-eater, severity |
| `target_ROAS` | бриф (sale-based бізнес) | поріг scaling/decrease правил, scaling ceiling |
| `daily_budget_plan` | бриф | коридор бюджету акаунта / напрямів |
| `scale_goal` | бриф | цільовий денний бюджет для секції «план масштабу» |
| `attribution_window` | бриф / Ads Manager | max 7-day click (інколи 1-day) — межа того, що Meta «бачить» ⟦[[03-targeting/value-rules]]⟧ |

> Якщо брифу нема або target не заданий — **СТОП**: за [[04-budget-scaling/big-spend-scaling]] «знати свої цифри — основа». Без `target_CPL/ROAS` (з урахуванням маржі) неможливо коректно поставити пороги scaling/decrease. У звіт: «target не заданий — рекомендації по масштабу умовні; запитати цільовий CPL/ROAS з урахуванням gross margin».

### 1.2 Класифікувати акаунт за бюджетом (визначає, які правила застосовувати)

За [[04-budget-scaling/small-budget]] поведінка кардинально різна:

| Клас | Поріг (з KB) | Який режим аудиту |
|---|---|---|
| **tiny** | ≤ ~$20/день (~$600/міс) | гіпер-консолідація; темп правок ще довший; awareness/traffic = червоний прапор |
| **small** | < ~$100/день (< $3,000/міс) | консолідація; крок між правками 7–14 днів; провал ймовірніший у креативах, не таргетингу |
| **mid / big** | вище | дефолтні post-Andromeda правила; для $300M-масштабу — [[04-budget-scaling/big-spend-scaling]] |

Зафіксувати клас на старті — він міняє інтерпретацію «learning limited» і «scaling ceiling».

### 1.3 Прочитати історію дій (для кута «чому погіршення»)

За safety_rules — прочитати `history/` за останні **3–7 днів** (а для кута «чому погіршення» — за весь аналізований період). Це джерело для кореляції «дія спеціаліста → зміна метрики» (питання E нижче). Якщо `history/` нема — кут «чому погіршення» спирається тільки на Activity Log з кабінету (див. 2.7).

---

## 2. Збір даних через API (read-only)

> Усі виклики — read-only інструменти `meta-ads`. Незалежні виклики запускати **паралельно** (в одному блоці). Плейсхолдер акаунта — `act_XXX`.

### 2.1 Структура акаунта (карта об'єктів)

```
get_campaigns(object_id="act_XXX", status_filter="ACTIVE")     # активні кампанії + їх budget/objective/bid_strategy
get_adsets(object_id="act_XXX")                                 # адсети: budget, optimization_goal, targeting, learning_status
get_ads(object_id="act_XXX")                                    # оголошення: статус, прив'язка до адсета
get_ad_creatives(object_id="act_XXX")                           # креативи: body, video_id, thumbnail, object_story
get_custom_audiences(object_id="act_XXX")                       # custom audiences (для audience-segments / retargeting аудиту)
```

Збудувати дерево: `campaign → adset → ad → creative`. Запам'ятати `optimization_goal` кожного адсета (визначає, яка метрика = «результат»; див. [[05-optimization/learning-phase]]: поріг 50/тиждень рахується саме від цього івента).

### 2.2 Insights за 5 періодів × 4 рівні (ядро аудиту)

**Часові вікна** (як у `/ads-reporter`): `today` · `yesterday` · `last_3d` · `last_7d` · `last_30d`.
**Рівні:** `account` · `campaign` · `adset` · `ad`.

Мінімальний обов'язковий набір (паралельно):

```
# account-level (заголовок звіту, KPI-strip, WoW)
get_insights(object_id="act_XXX", time_range="last_30d", level="account")
get_insights(object_id="act_XXX", time_range="last_7d",  level="account")
get_insights(object_id="act_XXX", time_range="last_3d",  level="account")
get_insights(object_id="act_XXX", time_range="yesterday",level="account")
get_insights(object_id="act_XXX", time_range="today",    level="account")

# campaign-level (структура витрат, consolidation/fragmentation)
get_insights(object_id="act_XXX", time_range="last_30d", level="campaign")
get_insights(object_id="act_XXX", time_range="last_7d",  level="campaign")

# adset-level (Health Score, learning, fatigue, scaling)
get_insights(object_id="act_XXX", time_range="last_30d", level="adset")
get_insights(object_id="act_XXX", time_range="last_7d",  level="adset")
get_insights(object_id="act_XXX", time_range="last_3d",  level="adset")
get_insights(object_id="act_XXX", time_range="yesterday",level="adset")
get_insights(object_id="act_XXX", time_range="today",    level="adset")

# ad-level (ad-eaters, creative concentration)
get_insights(object_id="act_XXX", time_range="last_7d",  level="ad")
get_insights(object_id="act_XXX", time_range="yesterday",level="ad")
```

**Поля, які треба витягти на кожному рівні:** `spend, impressions, clicks, ctr, cpc, cpm, frequency, reach, actions[*]` (де `actions` містить цільовий конверсійний івент — `complete_registration` / `lead` / `purchase` залежно від `optimization_goal`), `date_start`/`date_stop`. Похідні рахуються тобою (2.8), а не беруться «на віру».

### 2.3 Тренд по днях (для fatigue і «чому погіршення»)

Для трендів CTR/CPC/CPL по днях за останні 14 днів:

```
get_insights(object_id="act_XXX", time_range={"since":"YYYY-MM-DD","until":"YYYY-MM-DD"},
             level="adset", time_increment=1)
```

`time_increment=1` дає по-денну розбивку → можна побудувати тренд кожного адсета (питання B).

### 2.4 Breakdown: audience segments (new / engaged / existing) — КРИТИЧНО post-Andromeda

За [[09-retargeting/retargeting-post-andromeda]] навіть «cold» адсет Meta частково ллє на warm (у прикладі KB ~40% бюджету). Тому аудит **обов'язково** перевіряє цей спліт:

```
# Якщо Marketing API підтримує breakdown audience segments:
get_insights(object_id="act_XXX", time_range="last_30d", level="adset",
             breakdowns="user_segment_keys")   # або еквівалент audience_segments у даному Marketing API
```

> ⚠️ Назва breakdown залежить від реалізації Marketing API. Якщо такого breakdown **немає в інструменті** — це не привід вигадувати спліт. У звіт: «розбивку new/engaged/existing треба знімати в Ads Manager → Breakdown → **Audience segments**; якщо там `all unknown` — не налаштовані audience segments (Advertising settings → визначити engaged / existing customers) ⟦[[09-retargeting/retargeting-post-andromeda]]⟧». Це сама по собі знахідка аудиту.

### 2.5 Breakdown: демографія і площадки (для якості трафіку і value rules)

```
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="age")
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="gender")
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="country")
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="publisher_platform")
```

Призначення:
- **age/gender** → чи є демографія з явно кращим CPL → кандидат на **value rule** (а не на окремий адсет!) ⟦[[03-targeting/value-rules]]⟧.
- **country** → для мульти-гео; нагадати, що локація — це hard control, тут розділення валідне ⟦[[01-structure/campaign-structure]]⟧.
- **publisher_platform** → де FB/IG/Audience Network дають дешевший/дорожчий результат.

> ⚠️ Не давати висновок по сегменту з <1000 показів / <3 конверсій (guardrail §0.3). Breakdown дробить вибірку — частина клітинок буде нерепрезентативна; такі позначати «недостатньо даних».

### 2.6 Custom audiences та їх вікна (для retargeting-аудиту)

З `get_custom_audiences` зафіксувати кожну аудиторію + її **вікно** (retention). Орієнтири вікон з [[09-retargeting/retargeting-post-andromeda]]:

| Джерело | Вікно |
|---|---|
| lead form | 90 днів |
| website visitors | 180 днів |
| FB/IG page engagement | 365 днів |

Якщо є ліди/клієнти **старші за вікно** → прапор «завантажити зовнішній список» (особливо для нового акаунта, якого Meta ще не знає).

### 2.7 Activity Log (для кута «чому погіршення» — питання E)

Якщо Marketing API надає Activity Log — витягти всі `pause/resume/create/update/budget_change` events за аналізований період: `timestamp · actor · object_id · extra_data (old→new)`. Якщо Marketing API **не** надає Activity Log — кут «чому погіршення» спирається на `history/` (1.3) + на по-денний тренд (2.3). У звіт чесно: «Activity Log недоступний через API — кореляція дій будується з локальної history/».

### 2.8 Похідні метрики (рахуєш ти, фіксуєш формули)

```
CTR  = clicks / impressions * 100
CPC  = spend / clicks
CPM  = spend / impressions * 1000
CPL/CPA = spend / результат                # результат = actions[цільовий_івент]
Freq = impressions / reach                  # або беремо frequency з API
spend_share(ad)    = ad.spend / adset.spend
spend_share(top3)  = Σ(top-3 ads by spend).spend / total_spend
results/week(adset)= результати адсета, нормовані на 7 днів   # для порога learning 50/тиждень
```

Кожне похідне число у звіті несе джерело `⟦метрика · object_id · період⟧`.

---

## 3. Health Score (узгоджено з `/ads-optimizer`)

Health Score рахується на рівні **адсета** (як у `/ads-optimizer` Шаг 5). HS ∈ [-100; +100].

```
HS = round( (CPL_Gap + Trends + Diagnostics + Today_Adj) × Volume_Factor )
```

| Компонент | Діапазон | Логіка (стисло) |
|---|---|---|
| **CPL Gap** до `target_CPL` | −45…+45 | дешевше ≥30% → +45; ±10% → ±10; дорожче ≥30% → −45 |
| **Trends** (3d vs 7d) | −15…+15 | покращення → +; погіршення → − |
| **Diagnostics** | до −30 | CTR<1% → −8; CPM > медіани×1.3 → −12; Freq(7d)>2 → −10 |
| **Today_Adj** | 0…+30 | сьогодні значно дешевше за вчора (показів ≥300) → компенсація |
| **Volume_Factor** | ×0.6…×1.0 | <1000 показів ближче до 0.6; >5000 ближче до 1.0 |

**Класи:** `very_good ≥+25` · `good +5…+24` · `neutral −5…+4` · `slightly_bad −25…−6` · `bad ≤−25`.

> **Зв'язок HS ↔ post-Andromeda:** Diagnostics-штрафи (CTR/CPM/Freq) — це симптоми, але **корінь** часто креативний, не таргетинговий ⟦[[04-budget-scaling/small-budget]] · [[06-creatives/why-ads-fail]]⟧. HS дає пріоритет, а **дія** (що саме лагодити) — з відповідного knowledge-файлу. Низький HS на адсеті з нормальним CTR і високим CPL = ймовірно офер/лендинг, а не «вимкнути адсет».

Volume_Factor — це і є вшитий **поріг значущості** (§0.3): на «сирих» адсетах HS automatically придушений до ×0.6, тому ти не зробиш гучний висновок на 200 показах.

---

## 4. Скелет аналізу (питання A–H)

> Це той самий каркас, що в еталоні `fb-deep-audit-meta-prompt.md`. Кожна відповідь = **число з джерелом + дія з object_id + поріг**. Де даних бракує — «недостатньо даних, потрібна вибірка `...`».

### A. Creative concentration (single point of failure)

**Питання:** який % бюджету йде на TOP-3 оголошення? на TOP-1?
**Розрахунок:** `spend_share(top3)`, `spend_share(top1)` на `level="ad", last_7d` (і `last_30d`).
**Поріг / дія:**
- TOP-1 > 50% бюджету → **single point of failure**: якщо це оголошення вигорить, акаунт просяде різко. Дія: «нарощувати креативне різноманіття в адсеті до 8–10+ різнопланових концептів ⟦[[01-structure/campaign-structure]] · [[00-philosophy/andromeda-era]]⟧», вказати конкретні `ad_id`, що тримають концентрацію.
- **АЛЕ:** перш ніж радити «вимкнути дороге оголошення без конверсій» — перевірити, чи це не **top-funnel у послідовності Meta**: в одному адсеті Meta сама секвенсує top→mid→bottom; оголошення з великим spend і малими прямими конверсіями може «прогрівати» інші ⟦[[01-structure/campaign-structure]]⟧. Не радити паузу такого оголошення наосліп.

### B. Frequency / fatigue (вигорання)

**Питання:** чи стабільна frequency в активних адсетах? Куди йде CTR за 14 днів?
**Розрахунок:** `frequency` (7d/30d) + тренд CTR по днях (`time_increment=1`, 2.3).
**Поріг / дія:**
- `Freq(7d) > 2` → штраф у HS; `Freq > 4` увага, `> 7` критично (з `/ads-reporter`).
- CTR адсета впав **>20% за тиждень** → кандидат на **оновлення креативу** (не на дублювання адсета — дублювання це pre-Andromeda anti-pattern ⟦[[04-budget-scaling/big-spend-scaling]]⟧).
- Fatigue лікується **новими різноплановими креативами батчем** (≤1 партія/7 днів, щоб не рестартити learning) ⟦[[05-optimization/learning-phase]]⟧, а не зміною аудиторії.

### C. Audience overlap / auction overlap (конкуренція з самим собою)

**Питання:** чи є адсети/кампанії зі схожим таргетингом, що б'ються в аукціоні?
**Сигнал у даних:** зростання CPC/CPM при **стабільному** обсязі показів у групі схожих адсетів; кілька майже ідентичних кампаній поруч (з 2.1).
**Поріг / дія:**
- За post-Andromeda справжня проблема — **auction overlap** (не «bidding up проти себе»): розкидані по адсетах покази заважають Meta спланувати частоту на юзера ⟦[[01-structure/campaign-structure]] · [[04-budget-scaling/big-spend-scaling]]⟧.
- Дві кампанії «нібито cold і warm» на тих самих людей з тим самим оффером → **консолідувати в один hybrid-адсет** ⟦[[09-retargeting/retargeting-post-andromeda]]⟧. Вказати конкретні `campaign_id`.
- ⚠️ Точний % overlap API-інсайти напряму не дають → «перевірити в Ads Manager (Audience overlap tool); якщо >30% — об'єднати», а не вигадувати число.

### D. Learning phase / Learning Limited audit

**Питання:** скільки адсетів у `Learning` / `Learning Limited`? Чи порушено правило «50 результатів/тиждень»?
**Дані:** `learning_status` з `get_adsets` (2.1) + `results/week(adset)` (2.8).
**Поріг / дія** (з [[05-optimization/learning-phase]]):
- `results/week < ~40` під свій `optimization_goal` + багато паралельних адсетів → прапор **«consolidation needed»**, НЕ «raise budget». Дія: «злити адсети X,Y,Z в один, щоб прогнати конверсії через нього (приклад KB: 5×15 → 1×75/тиждень)».
- Learning limited **сам по собі не катастрофа** — адсет може бути прибутковим. Не радити «закидати бюджетом» неприбутковий адсет (0.6× ROAS бюджетом не лікують).
- Зміна івента оптимізації (purchase → ATC) — **тільки** якщо 50 purchases/тиждень нереальні (high-ticket / малий бізнес). Якщо ~20 і близько до масштабу — лишити кінцеву ціль.
- Перевірити **частоту змін**: якщо спеціаліст міняє адсети щодня (drip-feed креативів по одному) → прапор «постійний re-entry в learning», рекомендувати adjustment schedule ≤1/7 днів.

### E. Specialist actions ↔ KPI correlation («чому останні дні гірше»)

**Питання:** які конкретні дії (pause/resume/create/edit/budget) корелюють з падінням CTR/CPC/CPL?
**Дані:** Activity Log (2.7) або `history/` (1.3) + по-денний тренд метрик (2.3).
**Метод (time-shift):** для кожної дії з timestamp подивитись метрики наступних **24–72 год** того ж об'єкта. Побудувати timeline `дата → дія → Δметрика`.
**Поріг / дія:**
- Стрибок бюджету **10× за раз** (напр. $20→$200) → майже завжди різке погіршення CPA, бо «системі Meta дуже важко» ⟦[[04-budget-scaling/big-spend-scaling]]⟧. Якщо знайдено в логу — це і є причина просадки.
- Часті зміни (нові оголошення/налаштування щодня) → постійний re-learning ⟦[[05-optimization/learning-phase]]⟧.
- ⚠️ Кореляція ≠ причинність: завжди звіряти з **сезонністю** (Q4 CPM росте) і датою останньої зміни структури, перш ніж винуватити конкретну дію або Andromeda ⟦[[00-philosophy/andromeda-era]]⟧. Якщо просадка збіглася з Q4/святами — це гіпотеза-конкурент, винести в self-check.

### F. Funnel-level / структура (consolidation vs fragmentation)

**Питання:** чи розбита воронка вручну на багато кампаній? Чи розділені cold/warm? Чи один напрям майже вимкнено — це стратегія чи помилка?
**Дані:** дерево з 2.1 + spend по кампаніях (2.2).
**Поріг / дія** (з [[01-structure/campaign-structure]]):
- Окремі кампанії під top/mid/bottom funnel або під cold/warm → **прапор**, рекомендувати консолідацію в одну кампанію + один адсет (Meta секвенсує сама).
- Розділення валідне **тільки** за **локацією** (hard control) і за **продуктом/послугою** (різна оптимізація). Якщо розділено за інтересами/lookalike — невалідно post-Andromeda.
- Якщо напрям майже без бюджету — спитати: є хоч 1 його креатив з CPL < target? Якщо ні — можливо, свідоме рішення; якщо так — втрачена можливість.

### G. Tariff / revenue connection (якщо є дані продажів)

**Питання:** які креативи дали найбільший **revenue** (а не просто найбільше лідів)?
**Дані:** insights (ліди по `ad_id`) + зовнішні дані продажів (CRM/customers), якщо передані в бриф.
**Поріг / дія:**
- Зв'язати `ad_id → ліди → продажі/виручка` по даті. Топ за revenue ≠ топ за к-стю реєстрацій. Масштабувати треба те, що дає **гроші**, не «дешеві ліди».
- ⚠️ **Attribution gap:** Meta часто не бачить subsequent payments (recurring) → реальна цінність кампанії може бути вища за звіт Meta ⟦[[09-retargeting/retargeting-post-andromeda]]⟧. Для LTV/recurring-бізнесу — звіряти з зовнішнім трекером, інакше приймеш рішення по заниженій картині.
- Якщо даних продажів **нема** в брифі → «недостатньо даних для revenue-аналізу; cross-match по `ad_id` × дата потребує файлу customers/CRM».

### H. Time-of-day / day-of-week (якщо є дані)

**Питання:** коли найдешевша конверсія? Чи крутиться адсет 24/7, коли треба тільки в peak?
**Дані:**
```
get_insights(object_id="act_XXX", time_range="last_30d", level="adset",
             breakdowns="hourly_stats_aggregated_by_advertiser_time_zone")
```
**Поріг / дія:** якщо є виражені дешеві/дорогі години → розглянути dayparting.
> ⚠️ Якщо breakdown недоступний у Marketing API або обсяг малий — «потрібна вибірка `breakdowns=hourly_stats_...` + `time_increment=1`», не вигадувати «вечір дорожчий».
> ⚠️ Обережно post-Andromeda: Meta сама планує **ad impression delivery plan** (коли показати юзеру) ⟦[[05-optimization/learning-phase]]⟧ — жорсткий dayparting може заважати цьому плану. Радити обережно, як гіпотезу до тесту.

---

## 5. Формування звіту (формат [[playbooks/report-template]])

> Структура нижче дзеркалить gold-standard `fb-deep-audit-meta-prompt.md` і §8 META-PROMPT. Звіт відповідає на 4 кути; кожна секція — дієва.

### 5.1 Header + KPI-strip
- Період аудиту, акаунт (`act_XXX`), `target_CPL`/`target_ROAS`, клас бюджету (з 1.2).
- 4–5 топ-метрик акаунта з **WoW-дельтами** (last_7d vs попередні 7 днів): Spend, Results, CPL/CPA, CTR, (ROAS).

### 5.2 🩺 Діагноз (3–5 речень + severity-таблиця)
Один абзац — головні висновки. Потім таблиця:

| Симптом | Тяжкість | Корінева причина | Швидке лікування |
|---|---|---|---|
| напр. CPL +80% за 4 тижні | 🔴 | fatigue top-1 креативу (Freq 4.2) | новий батч концептів |

### 5.3 ✅ Що класно спрацювало (кут 1)
3–7 карток. Кожна: `object_id` (ad/adset) · дати · метрики · **причина** (яка комбінація креатив+аудиторія+timing дала результат, не просто «спрацювало») · **як скейлити** (з [[04-budget-scaling/big-spend-scaling]]).

### 5.4 ❌ Що погано спрацювало (кут 2)
3–7 карток. Кожна: `object_id` · дати · витрачений бюджет · **корінева причина** (audience fatigue / creative burnout / wrong placement / learning reset / поганий креатив — діагноз з [[06-creatives/why-ads-fail]]) · **рекомендована дія** (конкретна).

### 5.5 📉 Чому останні дні гірше (кут 3)
- Timeline `дата → дія → Δметрика` (з питання E).
- Кореляційна матриця: дії спеціаліста ↔ зміни KPI.
- Вердикт (1 абзац) + **обов'язкова згадка конкурентних пояснень** (сезонність/Q4, re-learning wobble) — щоб не списати все на одну причину.

### 5.6 🔥 Кардинальні зміни (top-3, кожна 30–50% impact)
Кожна картка: `{ title, what (з object_id), why (цифри-джерело), expected_impact (з арифметикою), effort_days, risk, success_metric, deadline }`.
**expected_impact обов'язково з розрахунком**, не «зросте на 20%». Приклад формату:
> «Дублювати **концепт** (не адсет!) top-3 переможців як нові оголошення в межах наявного адсета ⟦[[01-structure/campaign-structure]]⟧ → ціль: підняти креативне різноманіття з N до N+3, знизити концентрацію top-1 з 62% ⟦ad_id=X · last_7d⟧ до <40%. Якщо нові концепти дадуть CTR на рівні медіани топ-кейсів (Z%) → очікуваний CPC ≈ $A → CPL ≈ $B».

### 5.7 🔧 Інкрементальні зміни (5–10, сумарно 30–50%)
Малі дії, ті ж поля. Напр.: паузити конкретний ad-eater `ad_id=...` (CPL Nx target), налаштувати audience segments, додати value rule на демографію з кращим CPL, завести adjustment schedule ≤1/7 днів.

### 5.8 🚀 Roadmap до `scale_goal` (з арифметикою)
- Тижневий план (Тиждень 1/2/3/4) з конкретними кроками і **budget ramps за вибраним способом**:
  - **Option 1 (automated rules)** — +3%/день, парне decrease-правило з буфером (CPL < X scale / CPL > Y decrease) ⟦[[04-budget-scaling/big-spend-scaling]]⟧.
  - **Option 2 (manual)** — спадний % (на $50/день +100%, на $800/день +20%), крок ≥5 днів.
  - Вибір способу — за типом особистості клієнта (з брифу), не за бізнес-моделлю.
- **Scaling ceiling**: показати покрокову проєкцію (де ROAS/CPL ще тримає target) — стеля видна тільки stepped-підходом, не стрибком.
- **Projection з розрахунком:** «якщо CTR=x, CPC=y, CPL=z (медіана топ-кейсів) → бюджет `scale_goal`/день дасть ≈ N результатів @ $z».

### 5.9 🔍 Data-gaps (чого бракує для наступного аудиту)
Перелік breakdown/метрик/періодів, яких бракувало: напр. `breakdowns=publisher_platform не знято`, `audience segments = all unknown`, `немає файлу продажів для revenue-аналізу`, `Activity Log недоступний через API`.

### 5.10 🧐 Self-check (≥5 пунктів — обов'язково)
Таблиця ключових фактів + джерел + «як перевірити/фальсифікувати» (див. секцію SELF-CHECK нижче).

---

## 6. Передача в оптимізацію (межа READ-ONLY)

Аудит **готує**, але не виконує. Усі дієві рекомендації зі звіту (паузи, бюджети, дублювання, value rules, консолідація) виконуються окремо через `/ads-optimizer`, який:
- ще раз прочитає `history/` за 3 дні (правила коливань/повторів);
- покаже точну зміну `object_id · old→new` з обґрунтуванням і ризиком;
- дочекається явного «так» (META-PROMPT §9.3, safety_rules);
- залогує виконане в `history/`.

У звіті позначити кожну дію тегом готовності: `[ready-for-/ads-optimizer]`.

---

## 7. Anti-goals цього аудиту (з META-PROMPT §10 — чого НЕ робити)

- ❌ Загальні поради без цифр («тестуй більше креативів», «роби ретаргетинг»).
- ❌ Цитати/принципи Бена без прив'язки до конкретного `object_id` і цифри акаунта (KNOWLEDGE видане за DATA).
- ❌ Прогноз без арифметики («підніме ROAS у 3 рази»).
- ❌ Pre-Andromeda тактика як актуальна: **дублювання адсетів** для скейлу, **розділення cold/warm**, **класичне A/B схожих оголошень**, «вимкнути top-funnel оголошення, бо жере бюджет». Усе це — anti-patterns ⟦[[01-structure/campaign-structure]] · [[04-budget-scaling/big-spend-scaling]] · [[12-testing/post-andromeda-testing]]⟧.
- ❌ Висновок на <1000 показів / <3 конверсій (поріг значущості).
- ❌ Вигадані бенчмарки («CPM у вашій ніші має бути $5») — тільки цифри з Marketing API цієї сесії або позначені як принцип з KB.
- ❌ Числа без `⟦метрика · object_id · період⟧`.
- ❌ Beauty без substance: 50 секцій там, де 5 інсайтів.

---

## SELF-CHECK (як перевірити / фальсифікувати цей аудит)

> Цю секцію аудит **повторює в самому звіті** (5.10), наповнюючи реальними цифрами акаунта. Тут — каркас і питання, на які треба відповісти чесно.

**Чек-лист цілісності (перед видачею звіту):**
- [ ] Кожне число про акаунт прочитане з Marketing API **цієї сесії** і несе `⟦метрика · object_id · період⟧`.
- [ ] Жодне речення не змішує KNOWLEDGE (принцип з [[...]]) і DATA (метрика акаунта).
- [ ] Жоден висновок не зроблено на <1000 показів / <3 конверсій / <2 днів — інакше там стоїть «недостатньо даних, потрібна вибірка …».
- [ ] ≥3 дії дієві: кожна = `object_id` + метрика + поріг + конкретна дія (не «покращити креативи»).
- [ ] Кожна кардинальна зміна має `expected_impact` з арифметикою.
- [ ] Roadmap до `scale_goal` має покроковий розрахунок і вибраний спосіб (Option 1/2) під клієнта.
- [ ] Жодна рекомендована тактика не є pre-Andromeda без явної мітки (звірено з §7).
- [ ] Усі дієві пункти позначені `[ready-for-/ads-optimizer]` (аудит нічого не змутував сам).

**Фальсифікаційні твердження (≥5 — «цей висновок хибний, якщо…»):**
1. «Падіння CPL спричинене fatigue креативу X» — **хибне, якщо** просадка збігається з Q4/сезонним зростанням CPM по всьому акаунту (перевірити: CPM-тренд `level="account", time_increment=1` за період) ⟦[[00-philosophy/andromeda-era]]⟧.
2. «Адсет Y треба консолідувати, бо learning limited» — **хибне, якщо** його `optimization_goal` рідкісний (high-ticket purchase) і ~20 результатів/тиждень — це стеля бізнесу; тоді learning limited прийнятний, консолідація може не допомогти ⟦[[05-optimization/learning-phase]]⟧.
3. «Оголошення Z — ad-eater (дороге, без прямих конверсій), паузити» — **хибне, якщо** Meta використовує його як **top-funnel** у послідовності одного адсета; пауза погіршить конверсійні оголошення ⟦[[01-structure/campaign-structure]]⟧. Перевірити: чи в адсеті є конверсійні оголошення, чий CPL зростає при паузі Z (тест, не припущення).
4. «Скейлити переможця W» — **хибне, якщо** W конвертить переважно **warm-аудиторію** (engaged+existing), а не cold; на скейлі warm швидко вичерпується і CPL злетить ⟦[[04-budget-scaling/big-spend-scaling]] · [[09-retargeting/retargeting-post-andromeda]]⟧. Перевірити: Breakdown → Audience segments по W.
5. «Дія спеціаліста D (timestamp) спричинила падіння» — **хибне, якщо** падіння почалося ДО дії (звірити по-денний тренд 2.3) або є інша зміна в той же день (кореляція ≠ причинність).
6. «CPL акаунта вищий за target, бо погана аудиторія» — **хибне, якщо** корінь у **креативах** (на малих бюджетах провал частіше тут, не в таргетингу) ⟦[[04-budget-scaling/small-budget]] · [[06-creatives/why-ads-fail]]⟧; перевірити CTR: низький CTR при норм. CPM = креатив/оффер, не аудиторія.
7. «Revenue від кампанії = X (зі звіту Meta)» — **хибне, якщо** бізнес recurring/LTV: Meta не бачить subsequent payments, реальна цінність вища ⟦[[09-retargeting/retargeting-post-andromeda]]⟧; звірити з зовнішнім трекером/CRM.
8. «Сегмент демографії A дешевший — додати value rule» — **хибне, якщо** вибірка A <1000 показів / <3 конверсій (breakdom дробить дані); число CPL по A статистично шумне.

**Якщо хоч один пункт не можеш закрити даними — у звіт іде data-gap (5.9), а не здогад.**
