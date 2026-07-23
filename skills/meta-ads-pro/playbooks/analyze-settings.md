---
playbook: analyze-settings
title: "Аудит НАЛАШТУВАНЬ кампанії/адсета vs актуальний best-practice (post-Andromeda)"
type: analysis
status: active
era: post-andromeda
last_reviewed: 2026-06-03
output_format: "[[playbooks/report-template]]"
reads_knowledge:
  - "[[00-philosophy/andromeda-era]]"
  - "[[01-structure/campaign-structure]]"
  - "[[02-objectives/choosing-objective]]"
  - "[[03-targeting/value-rules]]"
  - "[[03-targeting/advantage-plus-audience]]"
  - "[[05-optimization/learning-phase]]"
  - "[[06-creatives/creative-enhancements]]"
  - "[[09-retargeting/retargeting-post-andromeda]]"
  - "[[12-testing/post-andromeda-testing]]"
mcp: meta-ads (read-only для цього playbook)
---

# Playbook: Аудит налаштувань кампанії/адсета

> **Що це.** Покрокова процедура (SOP) аудиту **конфігурації** акаунта Meta Ads — НЕ перформансу, а **самих налаштувань** vs актуальний (post-Andromeda) best-practice. Вхід — `act_XXX` + бриф (target_CPL / target_ROAS / business model / scale_goal). Вихід — **дієвий звіт** за форматом [[playbooks/report-template]], де по кожному параметру стоїть: **поточне → рекомендація → джерело правила `[[...]]`**.
>
> **Чим відрізняється від [[playbooks/audit-account]].** Audit-account питає «що працює / що ні / чому просадка / план скейлу» (перформанс). Цей playbook питає «**чи правильно зібрано кампанію**»: objective, optimization event, бюджет vs learning phase, структура (консолідація vs фрагментація), broad / Advantage+ / value rules, placements, exclusions / auction overlap, bid strategy, частота змін (helicopter-parenting). Часто запускається **до** перформанс-аудиту: немає сенсу оптимізувати бюджети на неправильно зібраному адсеті.
>
> **Бар якості (META-PROMPT §10).** Кожен пункт = конкретний об'єкт (`campaign_id` / `adset_id` / `ad_id`) + поточне значення з Marketing API + поріг правила + конкретна дія. НЕ «структура застаріла», а «`campaign_id=A` (cold) і `campaign_id=B` (warm) б'ють той самий сегмент тим самим оффером → злити в один hybrid-адсет ⟦[[09-retargeting/retargeting-post-andromeda]]⟧».
>
> **READ-ONLY.** Цей playbook лише читає конфіг і рекомендує. Будь-яка мутація (зміна objective/бюджету/таргетингу, пауза, консолідація) — окремий крок через `/ads-optimizer` чи `/campaign-manager` з підтвердженням користувача (META-PROMPT §9.3, safety_rules). Аудит **готує** дії, не виконує.

---

## 0. Залізні правила перед стартом (guardrails — META-PROMPT §9)

Тримати в голові ввесь час:

1. **Read-before-claim.** Жодного твердження про налаштування акаунта, якого ти не прочитав із Marketing API **цієї сесії** (`get_campaigns`/`get_adsets`/`get_ads`/`get_ad_creatives`/`get_custom_audiences`). Не пам'ятати конфіг із минулих сесій як факт.
2. **KNOWLEDGE ≠ DATA.** «Принцип з [[01-structure/campaign-structure]] каже консолідувати» (база знань) і «акаунт `act_XXX` має 5 cold-адсетів» (Marketing API) — **ніколи не змішувати**. Перше — посилання `[[...]]`, друге — маркер `⟦object_id · поле=значення⟧`.
3. **Налаштування читаються прямо, перформанс — за порогом значущості.** Сам факт конфігурації (objective=TRAFFIC, 1 ad у адсеті, окрема warm-кампанія) видно **детерміновано** з API — тут поріг значущості не потрібен. АЛЕ якщо рекомендація спирається на **метрику** (напр. «цей optimization event не набирає 50/тиждень», «ця демографія дешевша → value rule»), діє поріг **<1000 показів / <3 конверсій / <2 днів** → інакше «недостатньо даних».
4. **Цитуй джерело кожної цифри/факту:** `⟦adset_id=120XXX · optimization_goal=LINK_CLICKS⟧`, `⟦adset_id=120XXX · results/week=12 · last_7d⟧`. Заборонено факт без маркера.
5. **«Не знаю» дозволено.** Якщо Marketing API не віддає певне поле (напр. `learning_status`, `bid_strategy`, exclusions) — сказати прямо «це поле треба звірити в Ads Manager вручну», а не вигадувати значення.
6. **Freshness guard.** Кожна рекомендація має бути post-Andromeda. Якщо ловиш себе на pre-Andromeda пораді (дублювати адсети, розділити cold/warm, класичне A/B схожих оголошень, «один CTA на креатив») — це **anti-pattern**, звірити з [[00-philosophy/andromeda-era]] · [[01-structure/campaign-structure]] · [[12-testing/post-andromeda-testing]].
7. **Дефолт post-Andromeda ≠ догма.** «1 кампанія + 1 адсет» — дефолт, але відхилення буває **свідомо правильним** (мульти-гео, різні продукти, omnipresent для high-ticket, retargeting-only під особливий оффер). Перш ніж ставити прапор «фрагментація», перевір, чи це не одне з валідних виключень ⟦[[01-structure/campaign-structure]]⟧.
8. **Self-check обов'язковий.** Перед фінальним звітом — секція з ≥5 «це може бути хибним, якщо…».

---

## 1. Підготовка: бриф і що взагалі «правильно» для цього акаунта

«Правильне» налаштування залежить від бізнес-моделі й цілей із брифу — не від абстрактної норми.

### 1.1 Зчитати з брифу (змінні, не хардкод)

| Змінна | Звідки | Навіщо в аудиті налаштувань |
|---|---|---|
| `business_model` | бриф | leads vs sales → який objective/optimization event правильний ⟦[[02-objectives/choosing-objective]]⟧ |
| `target_CPL` / `target_ROAS` | бриф | поріг для оцінки optimization event і bid strategy |
| `daily_budget_plan` | бриф | чи бюджет реалістичний для виходу з learning (50 результатів/тиждень) ⟦[[05-optimization/learning-phase]]⟧ |
| `scale_goal` | бриф | впливає на рекомендацію по bid strategy і структурі під масштаб |
| `geo` | бриф | мульти-гео → валідне розділення за локацією ⟦[[01-structure/campaign-structure]]⟧ |
| `product_range` | бриф | різні продукти/послуги → валідне розділення кампаній ⟦[[01-structure/campaign-structure]]⟧ |
| `is_high_ticket` / `involved_purchase` | бриф | дозволяє omnipresent-структуру і зміну optimization event на вищий у воронці ⟦[[05-optimization/learning-phase]]⟧ |
| `ltv_by_segment` | бриф / CRM | основа для value rules — без реальних цифр % береться «зі стелі» ⟦[[03-targeting/value-rules]]⟧ |

> Якщо брифу немає або `business_model`/`target` не задані — **частковий СТОП**: за [[04-budget-scaling/big-spend-scaling]] «знати свої цифри — основа». Без них не можна сказати, чи objective правильний і де ставити пороги. У звіт: «бриф неповний — рекомендації по objective/optimization умовні; запитати business model + target_CPL/ROAS з урахуванням маржі».

### 1.2 Класифікувати акаунт за бюджетом (міняє «правильну» структуру)

За [[04-budget-scaling/small-budget]]:

| Клас | Поріг (KB) | Що це міняє в аудиті налаштувань |
|---|---|---|
| **tiny** | ≤ ~$20/день | гіпер-консолідація обов'язкова (1 кампанія/1 адсет/1 оффер); awareness/traffic objective = червоний прапор; крок правок ще довший |
| **small** | < ~$100/день | консолідація; крок правок 7–14 днів; багато адсетів = прапор фрагментації |
| **mid / big** | вище | дефолтні post-Andromeda правила; для $300M-масштабу — [[04-budget-scaling/big-spend-scaling]] |

На малому бюджеті розпорошена структура небезпечніша (конверсій і так мало — learning не виходить), тому пороги фрагментації жорсткіші.

### 1.3 Прочитати історію змін (для аудиту частоти правок — helicopter-parenting)

За safety_rules прочитати `history/` за останні **7–14 днів** (для цього playbook — за весь доступний період). Звідси будується **частота значних змін на адсет** (питання I нижче): скільки разів за тиждень міняли бюджет/таргетинг/креативи. Якщо `history/` немає — спертися на Activity Log із Marketing API (2.6), а якщо й його немає — чесно зафіксувати, що частоту змін оцінити неможливо.

---

## 2. Збір налаштувань через API (read-only)

> Усі виклики — read-only інструменти `meta-ads`. Незалежні виклики — **паралельно** (один блок). Плейсхолдер акаунта — `act_XXX`.

### 2.1 Дерево об'єктів і їхні налаштування (ядро цього playbook)

```
get_campaigns(object_id="act_XXX", status_filter="ACTIVE")   # objective, bid_strategy, budget(CBO?), buying_type, special_ad_categories
get_adsets(object_id="act_XXX")                              # optimization_goal, billing_event, budget(ABO?), bid_strategy, bid_amount,
                                                            #   targeting(geo/age/gender/interests/custom_audiences/advantage_audience),
                                                            #   promoted_object, learning_status, attribution_spec, schedule/dayparting, placements
get_ads(object_id="act_XXX")                                # к-сть активних оголошень у кожному адсеті, статус, creative_id
get_ad_creatives(object_id="act_XXX")                       # формат, object_story, degrees_of_freedom (creative enhancements), CTA, asset_feed_spec (variations)
get_custom_audiences(object_id="act_XXX")                   # custom audiences + їх вікна/розмір (для retargeting/segments аудиту)
```

Збудувати дерево `campaign → adset → ad → creative` і **поряд із кожним вузлом виписати його налаштування** (саме вони — предмет цього аудиту). Ключові поля, які треба дістати:

| Рівень | Поля-налаштування | Якщо Marketing API не віддає |
|---|---|---|
| campaign | `objective`, `bid_strategy` (LOWEST_COST / COST_CAP / BID_CAP / ROAS), `daily_budget` (= CBO якщо на кампанії), `buying_type`, `special_ad_categories` | звірити в Ads Manager вручну, позначити в data-gaps |
| adset | `optimization_goal`, `billing_event`, `daily_budget` (= ABO), `bid_strategy`/`bid_amount`, `promoted_object` (pixel/event), `targeting` (geo, age, gender, `flexible_spec`/interests, `custom_audiences`, `advantage_audience`/`targeting_automation`), `attribution_spec`, `adset_schedule` (dayparting), `targeting[publisher_platforms/facebook_positions/instagram_positions]` | те саме |
| ad | к-сть **активних** ads/адсет, `creative_id` | — |
| creative | `degrees_of_freedom_spec` (creative enhancements ON/OFF), `asset_feed_spec` (скільки primary text / headline / description variations), `call_to_action_type` | звірити вручну |

> ⚠️ Назви полів залежать від версії Graph API / реалізації Marketing API. Якщо поле відсутнє — **не вигадувати** значення (guardrail §0.5): у звіт «поле `bid_strategy` не повернулось Marketing API — звірити в Ads Manager → Campaign → Bid strategy».

### 2.2 Insights-мінімум (тільки там, де налаштування треба підкріпити метрикою)

Цей playbook **не** робить повний 5-періодний збір (це робота [[playbooks/audit-account]]). Але деякі рекомендації по налаштуваннях вимагають метрики:

```
# для перевірки «чи optimization event набирає 50 результатів/тиждень»
get_insights(object_id="act_XXX", time_range="last_7d", level="adset")     # results = actions[цільовий_івент]

# для «чи bid strategy тримає target_CPL/ROAS»
get_insights(object_id="act_XXX", time_range="last_30d", level="adset")
```

Дістати на рівні адсета: `spend, impressions, actions[цільовий_івент], frequency`. `results/week = actions / (дні_періоду) × 7`. Цей показник звіряється з порогом learning **50/тиждень** ⟦[[05-optimization/learning-phase]]⟧.

> Поріг значущості (§0.3) діє: якщо адсет має <1000 показів / <3 конверсій — не робити метрикових висновків, тільки конфігураційні (об'єктивно видимі з API).

### 2.3 Breakdown: audience segments (new / engaged / existing) — для аудиту retargeting-структури

За [[09-retargeting/retargeting-post-andromeda]] навіть «cold» адсет Meta частково ллє на warm. Це **прямо стосується налаштувань**: якщо значна частка spend «cold» адсета йде на engaged/existing — окрема warm-кампанія в конфізі **зайва**.

```
get_insights(object_id="act_XXX", time_range="last_30d", level="adset",
             breakdowns="user_segment_keys")   # або еквівалент audience_segments у даному Marketing API
```

> ⚠️ Якщо breakdown недоступний у Marketing API — це не привід вигадувати спліт. У звіт: «розбивку new/engaged/existing зняти в Ads Manager → Breakdown → **Audience segments**; якщо там `all unknown` — **audience segments не налаштовані** (Advertising settings → визначити engaged / existing customers) ⟦[[09-retargeting/retargeting-post-andromeda]]⟧». Відсутність налаштованих audience segments — сама по собі знахідка цього аудиту.

### 2.4 Breakdown: демографія і площадки (для value rules і placements)

```
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="age")
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="gender")
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="country")
get_insights(object_id="act_XXX", time_range="last_30d", level="adset", breakdowns="publisher_platform")
```

- **age/gender** → чи є демографія з явно кращим CPL/ROAS → кандидат на **value rule** (бід +%, broad лишається), а НЕ на окремий вузький адсет ⟦[[03-targeting/value-rules]]⟧.
- **country** → для мульти-гео; локація — hard control, тут розділення на адсети **валідне** ⟦[[01-structure/campaign-structure]]⟧.
- **publisher_platform** → інформативно (де FB/IG/AN дають який результат), АЛЕ ручне відключення площадок — не дефолт post-Andromeda (див. питання G).

> ⚠️ Не давати висновок по сегменту з <1000 показів / <3 конверсій (§0.3). Breakdown дробить вибірку → частина клітинок нерепрезентативна, такі позначати «недостатньо даних».

### 2.5 Custom audiences та їх вікна

З `get_custom_audiences` зафіксувати кожну аудиторію + **вікно** (retention) + чи вона стоїть у таргетингу як `custom_audiences` і чи знято `use as suggestion`. Орієнтири вікон ⟦[[09-retargeting/retargeting-post-andromeda]]⟧:

| Джерело | Вікно |
|---|---|
| lead form | 90 днів |
| website visitors | 180 днів |
| FB/IG page engagement | 365 днів |

Це треба для питань F (retargeting-структура) і F-bis (exclusions): чи custom audiences взагалі заведені (Pixel + списки — досі обов'язкові), і чи коректно вони використані.

### 2.6 Activity Log (для аудиту частоти змін — питання I)

Якщо Marketing API надає Activity Log — витягти `create/update/pause/resume/budget_change/targeting_change` events за період: `timestamp · actor · object_id · extra_data(old→new)`. Це джерело для метрики «значних змін на адсет за тиждень». Якщо Marketing API **не** надає Activity Log — спертися на `history/` (1.3). Якщо немає й її — у звіт «частоту змін оцінити неможливо: ні Activity Log (Marketing API), ні локальна history/».

---

## 3. Скелет аудиту налаштувань (питання A–I)

> **Це ядро playbook.** Кожен пункт у форматі **Поточне → Best-practice → Рекомендація → Джерело `[[...]]`**, прив'язаний до конкретного `campaign_id`/`adset_id`. Де потрібна метрика, а її бракує — «недостатньо даних, потрібна вибірка `...`».

### A. Objective (ціль кампанії: leads / sales — правильна?)

**Поточне:** `objective` кожної активної кампанії (з 2.1) + `business_model` із брифу.
**Best-practice:** objective = той бізнес-результат, який реально треба. Meta доставляє **буквально під ціль**: скажеш traffic — знайде «клікерів», що не конвертять; скажеш leads/sales — тягне відповідний результат ⟦[[02-objectives/choosing-objective]] · [[04-budget-scaling/small-budget]]⟧.
**Прапори / дія:**
- `objective ∈ {AWARENESS, TRAFFIC, ENGAGEMENT, VIDEO_VIEWS, REACH}` при `business_model = leads/sales` → **червоний прапор**. Особливо на tiny/small бюджеті: awareness/traffic тут прямо протипоказані ⟦[[04-budget-scaling/small-budget]]⟧. Дія: «перевести `campaign_id=A` з TRAFFIC на LEADS/SALES (Outcome leads / sales), оптимізація під конверсійний івент».
- **Виняток:** omnipresent content campaign для дуже «involved» покупок (high-ticket / consulting / expertise) — там верхня частина воронки виправдана, але навіть тоді для малого бізнесу Ben радить не фокусуватись на ній ⟦[[04-budget-scaling/small-budget]] · [[01-structure/campaign-structure]]⟧. Якщо `is_high_ticket=true` — не ставити прапор автоматично.
- `objective = SALES`, але бізнес генерує **ліди** (не прямі онлайн-покупки) → невідповідність objective ↔ модель; звірити з `promoted_object`/подією.

### B. Optimization event (під що оптимізується адсет)

**Поточне:** `optimization_goal` + `promoted_object` (pixel/event) кожного адсета (з 2.1) + `results/week` (з 2.2).
**Best-practice:** оптимізувати під **кінцеву** бізнес-ціль (purchase / lead / complete_registration), а не під проксі (link clicks, landing page views, post engagement), **якщо** реально набираються ~50 результатів/тиждень ⟦[[05-optimization/learning-phase]]⟧.
**Прапори / дія:**
- `optimization_goal = LINK_CLICKS / LANDING_PAGE_VIEWS / POST_ENGAGEMENT` при цілі продажів/лідів → **прапор**: Meta оптимізує під клікерів, не під покупців. Дія: «змінити optimization event `adset_id=X` на `OFFSITE_CONVERSIONS`/lead/purchase ⟦[[02-objectives/choosing-objective]] · [[05-optimization/learning-phase]]⟧».
- `optimization_goal = purchase`, але `results/week < ~40–50` під цей івент **і** бізнес high-ticket (5–10 продажів/тиждень — стеля) → **тільки тоді** розглянути зсув на вищий у воронці івент (purchase → add to cart / lead). Це **test-and-see**, не гарантія ⟦[[05-optimization/learning-phase]]⟧. Дія з порогом: `⟦adset_id=X · results/week=7 · last_7d⟧ < 50 + high_ticket → кандидат purchase→ATC`.
- ❌ **НЕ** міняти івент, якщо ~20 purchases/тиждень і близько до масштабу/покращення кампанії — оптимізуй під кінцеву ціль (Meta дуже буквальна: частина ATC не дійде до покупки) ⟦[[05-optimization/learning-phase]]⟧.
- Якщо `results/week` неможливо порахувати (мало даних / немає conversion tracking) → «недостатньо даних; перевірити, чи стоїть Pixel + conversion event у `promoted_object`».

### C. Бюджет vs learning phase (чи реалістично вийти з навчання)

**Поточне:** `daily_budget` (CBO на кампанії або ABO на адсеті) + `optimization_goal` + `results/week`.
**Best-practice:** бюджету має вистачати, щоб набрати ~**50 результатів/тиждень** того івента, під який оптимізуєш — інакше адсет осідає в **Learning Limited**. АЛЕ «learning limited ≠ катастрофа»: можна бути прибутковим; фікс — **не закидати бюджетом наосліп**, а консолідувати + покращити оффер/креатив ⟦[[05-optimization/learning-phase]]⟧.
**Прапори / дія:**
- Багато дрібних адсетів, кожен ~10–20 результатів/тиждень → майже всі впадуть у learning limited. Дія: **консолідувати** в один адсет (приклад KB: 5×15 → 1×75/тиждень), а НЕ піднімати бюджет на кожному ⟦[[05-optimization/learning-phase]]⟧. Вказати конкретні `adset_id`, що зливаються.
- `learning_status = LEARNING_LIMITED` на адсеті з прийнятним CPA/ROAS → **не чіпати агресивно**; у звіт «learning limited, але прибутковий — консолідація піднесе результат, бюджетом не лікувати».
- Адсет неприбутковий (напр. ROAS значно нижче target) → **НЕ** «raise budget щоб добити 50 конверсій»; рекомендувати менший бюджет + покращення оферу/креативу ⟦[[05-optimization/learning-phase]] · [[06-creatives/why-ads-fail]]⟧.
- ⚠️ «50/тиждень» — поріг, який декларує Meta; на практиці вихід буває й за ~20–40. Не подавати «50» як жорстку істину ⟦[[05-optimization/learning-phase]]⟧.

### D. Структура (консолідація 1 камп + 1 адсет? розділені cold/warm — прапор)

**Поточне:** к-сть активних кампаній / адсетів / оголошень на адсет (з 2.1) + як вони названі/таргетовані.
**Best-practice (дефолт post-Andromeda):** **одна кампанія + один адсет + 20+ різнопланових оголошень** усередині; cold і warm **не розділяти** (Meta змішує однаково — custom audiences у *suggested audience*); воронку (top/mid/bottom) Meta секвенсує сама в межах одного адсета ⟦[[01-structure/campaign-structure]] · [[00-philosophy/andromeda-era]]⟧.
**Прапори / дія:**
- Окремі кампанії/адсети під **cold vs warm** → **прапор фрагментації**: «`campaign_id=A`(cold)+`campaign_id=B`(warm) → консолідувати в один hybrid-адсет ⟦[[01-structure/campaign-structure]] · [[09-retargeting/retargeting-post-andromeda]]⟧».
- Окремі кампанії під **етапи воронки** (top/mid/bottom funnel вручну) → прапор: Meta секвенсує сама; скласти оголошення різних етапів в один адсет.
- Багато адсетів під **різні інтереси / lookalike / open** → прапор: вони в *suggested audience*, чесного спліту немає, Meta робить своє. Консолідувати ⟦[[01-structure/campaign-structure]] · [[12-testing/post-andromeda-testing]]⟧.
- **<8–10 різнопланових оголошень** в адсеті (тим паче 1–3) → прапор «creative diversity gap»: Andromeda хоче 20+ різних кутів/форматів ⟦[[00-philosophy/andromeda-era]]⟧. Дія: «нарощувати концепти в `adset_id=X` до 8–10+ (UGC / founder / demo / testimonial)».
- **Валідні виключення (НЕ прапор):** розділення за **локацією** (hard control) ⟦[[01-structure/campaign-structure]]⟧; за **продуктом/послугою** з різною оптимізацією (hats vs shoes — окремо; red vs blue hats — разом); **omnipresent** для high-ticket; **dynamic catalog** business-wide; **retargeting-only** під особливий оффер. Перш ніж радити консолідацію — звірити з брифом (`geo`, `product_range`, `is_high_ticket`).
- ❌ **Не радити** «вимкнути дороге оголошення без прямих конверсій»: в одному адсеті це може бути **top-funnel** у послідовності Meta — пауза погіршить конверсійні оголошення ⟦[[01-structure/campaign-structure]]⟧.

### E. Broad / Advantage+ / Value Rules (таргетинг-філософія)

**Поточне:** `targeting` адсета — чи увімкнено `advantage_audience` / `targeting_automation`, чи стоять вузькі `interests`/`flexible_spec`/lookalikes як **hard** обмеження, чи заведені **value rules** (Advertising settings → Value rules; через API можуть не повертатись — звірити вручну).
**Best-practice:** еволюція таргетингу — від вузьких інтересів у багатьох адсетах → до **broad/open (Advantage+)** → до **гібриду broad + value rules** (broad лишається, але бід коригується під відому LTV-різницю демографій) ⟦[[03-targeting/value-rules]] · [[03-targeting/advantage-plus-audience]]⟧.
**Прапори / дія:**
- Вузький ручний таргетинг (детальні інтереси / lookalike як hard-обмеження) у багатьох адсетах → **прапор**: повернення до pre-Andromeda. Дія: «перейти на broad/Advantage+ audience у `adset_id=X`; інтереси лишити лише як *suggestion*, не hard» ⟦[[03-targeting/value-rules]]⟧.
- Broad стоїть, **value rules відсутні**, але в брифі/CRM є чітка LTV-різниця по демографії (з 2.4 + `ltv_by_segment`) → дія: «додати value rule на `adset_id=X` з **розрахованим** % (напр. women +80%, бо LTV ≈ ×2.4), а не довільним ⟦[[03-targeting/value-rules]]⟧». До 10 правил на набір; критерії: age/gender/location/conversion location/device/OS/placement.
- ❌ Вмикати value rules **без** реальних цифр (бід «зі стелі») → прапор: спершу звести CRM+ad account+трекер (≈90 хв) ⟦[[03-targeting/value-rules]]⟧.
- ⚠️ Value rules можуть підняти **загальний CPA** (Meta прямо попереджає) — ок, лише якщо LTV-виграш більший. Подати як свідомий трейд-оф, не як «безкоштовне покращення».
- Якщо `advantage_audience`/value rules не читаються через API → «звірити в Ads Manager; через API ці поля не повернулись» (data-gap).

### F. Exclusions / overlap (auction overlap, custom audiences, suggestions)

**Поточне:** custom audiences у таргетингу (з 2.5), наявність **exclusions** (виключених аудиторій), кілька майже ідентичних адсетів/кампаній (з 2.1), спліт audience segments (з 2.3).
**Best-practice:** дефолт — **hybrid-адсет** (warm+cold разом), Meta сама перерозподіляє бюджет на ретаргет; окрема warm-кампанія **зайва й шкідлива** (фрагментація + auction overlap). Custom audiences, Pixel і tracking — **досі обов'язкові** (для audience segments і покриття аудиторій поза вікном Meta) ⟦[[09-retargeting/retargeting-post-andromeda]]⟧.
**Прапори / дія:**
- Дві кампанії/адсети «нібито cold і warm» на **тих самих людей з тим самим оффером** → **auction overlap** (не «bidding up», а збій delivery-плану частоти) ⟦[[01-structure/campaign-structure]] · [[09-retargeting/retargeting-post-andromeda]] · [[04-budget-scaling/big-spend-scaling]]⟧. Дія: «злити `campaign_id=A`+`B` в один hybrid-адсет».
- **Custom audiences не заведені взагалі** (порожній `get_custom_audiences` / не використані) → прапор: «Meta й так ретаргетить» — це **bad advice**; завести Pixel-audiences + завантажити списки клієнтів/лідів (особливо для нового акаунта) ⟦[[09-retargeting/retargeting-post-andromeda]]⟧.
- **Audience segments = `all unknown`** (з 2.3) → engaged/existing не визначені; поставити в Advertising settings, інакше немає чесної картини new vs retargeting ⟦[[09-retargeting/retargeting-post-andromeda]]⟧.
- **Retargeting-only адсет, але не знято `use as suggestion`** → він фактично працює як звичайний hybrid і **не** обмежує доставку лише на warm. Дія: «further limit the reach → switch setup → зняти *use as suggestion*» — **тільки** якщо retargeting-only справді потрібен (особливий оффер для warm / ascension) ⟦[[09-retargeting/retargeting-post-andromeda]]⟧.
- ⚠️ Точний **% audience overlap** API-інсайти напряму не дають → «перевірити в Ads Manager (Audience Overlap tool); якщо >30% — об'єднати», а не вигадувати число.
- Ліди/візитери **старші за вікно** custom audience (>90 / >180 / >365 днів) → завантажити зовнішній список ⟦[[09-retargeting/retargeting-post-andromeda]]⟧.

### G. Placements (плейсменти: Advantage+ placements чи ручні?)

**Поточне:** `targeting.publisher_platforms` / `facebook_positions` / `instagram_positions` адсета (з 2.1) — увімкнено Advantage+ placements (усі) чи **вручну обмежено** площадки/позиції.
**Best-practice:** post-Andromeda Meta персоналізує доставку на рівні людини й сама вирішує, де показати; дефолт — **Advantage+ placements** (усі). Ручне вирізання плейсментів зменшує простір оптимізації. Creative enhancements (visual touch-ups / flex media) самі підставляють формати між плейсментами ⟦[[06-creatives/creative-enhancements]] · [[00-philosophy/andromeda-era]]⟧.
**Прапори / дія:**
- **Manual placements** з вимкненими площадками (напр. вимкнено Audience Network / Reels / Stories) **без сильної причини** → прапор: повернути Advantage+ placements, нехай Meta оптимізує ⟦[[00-philosophy/andromeda-era]]⟧. Якщо причина в даних (площадка стабільно дорожча на достатній вибірці з 2.4) — подати як гіпотезу до тесту, не як факт.
- ⚠️ **Не** рекомендувати ручне відключення площадки на підставі одного breakdown-зрізу з малою вибіркою (<1000 показів / <3 конв.) — це частий помилковий хід.
- Перевірити, що креатив **спроєктований під кроп** (важлива інфо/субтитри по центру, не скраю), бо Meta кропить під 4:5 та інші формати між плейсментами ⟦[[06-creatives/creative-enhancements]]⟧.

### G-bis. Creative enhancements (Advantage+ creative — фільтр, не «все ON/все OFF»)

**Поточне:** `degrees_of_freedom_spec` / creative enhancements кожного оголошення (з 2.1) + чи є `asset_feed_spec` variations.
**Best-practice:** рекламодавець — **фільтр**: вмикати ті enhancements, що пасують конкретному креативу, вимикати ті, що спотворюють меседж. Набір різний для image/video ⟦[[06-creatives/creative-enhancements]]⟧.
**Прапори / дія:**
- На креативах із **критичним текстом** усередині (тестимоніали, точний оффер) увімкнено `enhanced media text` / `add overlays` / `animation` → прапор «зруйнований меседж»: вимкнути для цих оголошень ⟦[[06-creatives/creative-enhancements]]⟧.
- **Продуктове фото без тексту**, але `add overlays` / `animation` вимкнено → втрачений важіль: увімкнути (оверлеї відчутно піднімають перформанс).
- Копірайт тестується **окремими оголошеннями** замість variations → дія: звести в `asset_feed_spec` (до 5 primary / 5 headline / 5 description в одному оголошенні), окремі оголошення лишити під різний **креатив** ⟦[[01-structure/campaign-structure]] · [[12-testing/post-andromeda-testing]]⟧.
- **Завжди ON** як дефолт-рекомендація: visual touch-ups, flex media, text improvements. **Завжди перевіряти руками:** music, AI image variations.

### H. Bid strategy (стратегія ставок)

**Поточне:** `bid_strategy` кампанії/адсета (з 2.1): LOWEST_COST (highest volume) / COST_CAP / BID_CAP / ROAS-goal + `bid_amount` + `daily_budget` vs `lifetime_budget`.
**Best-practice:** для більшості — **LOWEST_COST** (Meta вичавлює максимум обсягу в межах бюджету); caps (cost cap / bid cap / ROAS goal) — лише коли є тверді юніт-економічні межі й достатньо конверсійних даних. **Daily budgets > lifetime budgets** майже завжди (гнучкіші, легше масштабувати) ⟦[[04-budget-scaling/big-spend-scaling]]⟧.
**Прапори / дія:**
- `bid_strategy = BID_CAP / COST_CAP` із занадто низьким `bid_amount` на адсеті з малим обсягом → ризик «not spending» / недонавчання (Meta не знаходить конверсій під жорсткою стелею). Дія: «перевірити, чи cap реалістичний vs фактичний CPL `⟦adset_id=X · CPL · last_30d⟧`; якщо адсет не витрачає бюджет — послабити cap або перейти на LOWEST_COST» ⟦[[05-optimization/learning-phase]]⟧.
- `lifetime_budget` без явної причини (немає фіксованого вікна промо) → рекомендувати **daily budget** (гнучкість для масштабу) ⟦[[04-budget-scaling/big-spend-scaling]]⟧.
- ROAS-goal стратегія на бізнесі з recurring/LTV → ⚠️ Meta не бачить subsequent payments, ROAS-ціль може бути заниженою → звіряти з зовнішнім трекером ⟦[[09-retargeting/retargeting-post-andromeda]]⟧.
- Якщо `bid_strategy` не повертається Marketing API → «звірити в Ads Manager → Bid strategy» (data-gap).

### I. Частота змін (helicopter-parenting)

**Поточне:** к-сть значних змін на адсет за тиждень (з `history/` 1.3 / Activity Log 2.6): зміни бюджету, таргетингу, додавання оголошень по одному, зміни налаштувань адсета.
**Best-practice:** **не смикати** кампанію — графік змін **≤1 раз / 7 днів** (на малому бюджеті — довше: 10–14 днів, бо менше конверсій → довше набирається сигнал). Креативи заливати **батчем** (5 за раз у кінці тижня), а не drip-feed по одному щодня. Кожна значна зміна **рестартить learning phase** і ламає ad impression delivery plan ⟦[[05-optimization/learning-phase]] · [[04-budget-scaling/small-budget]]⟧.
**Прапори / дія:**
- >1 значна зміна на адсет за 7 днів (тим паче щоденні правки / drip-feed креативів по одному) → **прапор «helicopter-parenting»**: «завести adjustment schedule на `adset_id=X` — ≤1 партія змін/7 днів (на tiny/small — 10–14 днів); креативи батчем» ⟦[[05-optimization/learning-phase]]⟧.
- Часті зміни **бюджету** (стрибки туди-сюди) → постійний re-learning; на малому бюджеті крок між правками прив'язувати до **conversion volume**, не до календаря ⟦[[04-budget-scaling/small-budget]]⟧. Для перевірки реального кроку — significance calculator (ціль ~90%).
- Стрибок бюджету **10× за раз** в логу (напр. $20→$200) → окремий прапор (це й scaling-помилка, і learning-reset) ⟦[[04-budget-scaling/big-spend-scaling]]⟧.
- Якщо ні `history/`, ні Activity Log → «частоту змін оцінити неможливо — увімкнути логування дій / надати Activity Log» (data-gap).

---

## 4. Зведена матриця аудиту (вихідна таблиця playbook)

> Це **головний робочий артефакт** цього playbook — таблиця «параметр → поточне → best-practice → рекомендація → джерело». Вона лягає в секцію «що не працює» / severity-таблицю звіту [[playbooks/report-template]]. Кожен рядок прив'язаний до `object_id` і несе посилання `[[...]]`.

| # | Параметр | Об'єкт | Поточне (DATA `⟦...⟧`) | Best-practice (KNOWLEDGE) | Прапор | Рекомендація (дія) | Джерело |
|---|---|---|---|---|:--:|---|---|
| A | Objective | `campaign_id=…` | напр. `objective=TRAFFIC` | leads/sales під результат | 🔴 | перевести на LEADS/SALES | [[02-objectives/choosing-objective]] |
| B | Optimization event | `adset_id=…` | напр. `optimization_goal=LINK_CLICKS` | кінцевий конверсійний івент | 🟠 | змінити на OFFSITE_CONVERSIONS | [[05-optimization/learning-phase]] |
| C | Бюджет vs learning | `adset_id=…` | напр. `results/week=12` | ~50/тиждень або консолідація | 🟠 | консолідувати, не «raise budget» | [[05-optimization/learning-phase]] |
| D | Структура (cold/warm) | `campaign_id=…` | напр. окремі cold+warm | 1 камп + 1 адсет (hybrid) | 🟠 | злити в один адсет | [[01-structure/campaign-structure]] |
| D | Creative diversity | `adset_id=…` | напр. `ads=2` | 20+ різних концептів | 🟡 | нарощувати до 8–10+ | [[00-philosophy/andromeda-era]] |
| E | Targeting (broad/VR) | `adset_id=…` | напр. вузькі інтереси hard | broad + value rules | 🟠 | перейти на broad/Advantage+ | [[03-targeting/value-rules]] |
| F | Exclusions / overlap | `campaign_id=…` | напр. дублі cold+warm | hybrid, без auction overlap | 🟠 | консолідувати + audience segments | [[09-retargeting/retargeting-post-andromeda]] |
| F | Custom audiences | `act_XXX` | напр. не заведені | Pixel+списки обов'язкові | 🟠 | завести CA + завантажити списки | [[09-retargeting/retargeting-post-andromeda]] |
| G | Placements | `adset_id=…` | напр. manual, AN off | Advantage+ placements | 🟡 | повернути Advantage+ placements | [[00-philosophy/andromeda-era]] |
| G-bis | Creative enhancements | `ad_id=…` | напр. overlays ON на тестимоніалі | фільтр per-креатив | 🟡 | вимкнути на критичному тексті | [[06-creatives/creative-enhancements]] |
| H | Bid strategy | `adset_id=…` | напр. BID_CAP низький / lifetime | LOWEST_COST + daily | 🟡 | перевірити cap / → daily budget | [[04-budget-scaling/big-spend-scaling]] |
| I | Частота змін | `adset_id=…` | напр. 5 змін/тиждень | ≤1/7 днів, батчі | 🟠 | adjustment schedule | [[05-optimization/learning-phase]] |

> Severity-легенда (як у [[playbooks/report-template]]): 🔴 критично (ламає доставку/економіку) · 🟠 суттєво (фрагментація, неправильний event/таргетинг) · 🟡 покращення (diversity, enhancements, placements). Кожна 🔴/🟠 має потрапити в «Кардинальні» або «Інкрементальні» зміни звіту.

---

## 5. Формування звіту (формат [[playbooks/report-template]])

Звіт — за спільним шаблоном (9 секцій). Особливості наповнення для **settings-аудиту**:

### 5.1 Header + KPI-strip
Період, акаунт (`act_XXX`), `target_CPL`/`target_ROAS`, клас бюджету (1.2), `business_model`. KPI-strip тут — не стільки перформанс, скільки **конфіг-зведення**: к-сть кампаній / адсетів / середня к-сть оголошень на адсет / objective-розподіл / % адсетів у Learning Limited.

### 5.2 🩺 Діагноз (3–5 речень + severity-таблиця)
Один абзац: головні структурні проблеми конфігу. Severity-таблиця = верх **матриці §4** (тільки 🔴/🟠 рядки): `Параметр → Тяжкість → Поточне → Best-practice фікс`.

### 5.3 ✅ Що налаштовано правильно
Картки по параметрах, де конфіг **відповідає** best-practice (напр. «objective=SALES коректний», «broad+value rules вже стоять», «1 адсет з 18 концептами»). Це не «вода» — показує, що НЕ чіпати, і калібрує довіру до решти.

### 5.4 ❌ Що налаштовано неправильно
Картки = 🔴/🟠 рядки матриці §4. Кожна: `object_id` · поточне `⟦...⟧` · best-practice · корінь · **конкретна дія** · джерело `[[...]]`.

### 5.5 🔥 Кардинальні зміни (top-3 — налаштування з найбільшим impact)
3 дії, кожна 30–50% impact. Для settings-аудиту типові кардинальні:
- **Виправити objective/optimization event** (якщо TRAFFIC/LINK_CLICKS на продажах) — найбільший важіль: Meta почне тягнути правильний результат.
- **Консолідація структури** (cold+warm / багато адсетів → 1 hybrid-адсет) — виводить із learning limited, прибирає auction overlap.
- **Broad + value rules** замість вузького ручного таргетингу.
Кожна картка: `{ title, what (object_id), why (поточне значення `⟦...⟧` + правило `[[...]]`), expected_impact (з арифметикою/логікою), effort_days, risk, success_metric, deadline }`.
> expected_impact обґрунтовувати **механізмом + цифрою**, не «зросте на 20%». Приклад: «Консолідувати `adset_id=X,Y,Z` (зараз 12+15+11 results/week ⟦last_7d⟧) в один → ~38/тиждень в одному адсеті → ближче до порога 50, ймовірний вихід із Learning Limited ⟦[[05-optimization/learning-phase]]⟧; auction overlap між ними зникає».

### 5.6 🔧 Інкрементальні зміни (5–10)
Дрібніші конфіг-фікси: налаштувати audience segments, увімкнути/вимкнути конкретні creative enhancements (`ad_id`), повернути Advantage+ placements, перевести lifetime→daily budget, завести adjustment schedule ≤1/7 днів, додати value rule на демографію з кращим CPL.

### 5.7 🚀 Roadmap (порядок впровадження змін налаштувань)
Послідовність важлива, бо зміни **рестартять learning**: спершу структурні (objective/optimization/консолідація) **однією партією**, потім дати 7 днів re-learning, потім таргетинг/value rules, потім creative enhancements. Не міняти все одночасно щодня (це і є helicopter-parenting). Якщо паралельно планується скейл — вказати спосіб (Option 1/2) з [[04-budget-scaling/big-spend-scaling]].

### 5.8 🔍 Data-gaps
Перелік полів, яких Marketing API не віддав і які треба звірити вручну: напр. `bid_strategy не повернувся`, `creative enhancements (degrees_of_freedom) недоступні`, `value rules через API не читаються`, `audience segments = all unknown`, `Activity Log недоступний — частоту змін не оцінити`.

### 5.9 🧐 Self-check (≥5 — обов'язково)
Таблиця факт→джерело→як перевірити + ≥5 «хибно, якщо…» (див. SELF-CHECK нижче), наповнені реальними значеннями акаунта.

---

## 6. Передача в оптимізацію (межа READ-ONLY)

Аудит **готує**, але не виконує. Усі дієві рекомендації (зміна objective/optimization event, консолідація, broad/value rules, placements, bid strategy, adjustment schedule) виконуються окремо через `/ads-optimizer` чи `/campaign-manager`, який:
- ще раз прочитає `history/` за 3 дні (правила коливань/повторів);
- покаже точну зміну `object_id · old→new` з обґрунтуванням і ризиком;
- дочекається явного «так» (META-PROMPT §9.3, safety_rules);
- залогує виконане в `history/`.

> ⚠️ Особливість settings-змін: зміна objective / optimization event / таргетингу **скидає learning phase**. У переданих діях це має бути зазначено явно («ця зміна рестартить learning — згрупувати з іншими структурними і не чіпати 7 днів»), щоб `/ads-optimizer` не розбивав їх на щоденні правки.

У звіті позначити кожну дію тегом готовності: `[ready-for-/ads-optimizer]`.

---

## 7. Anti-goals цього аудиту (META-PROMPT §10 — чого НЕ робити)

- ❌ Загальні поради без об'єкта/значення («структура застаріла», «налаштуй краще таргетинг»).
- ❌ Принцип Бена виданий за стан акаунта (KNOWLEDGE як DATA): «база каже консолідувати» ≠ «у тебе 5 cold-адсетів `⟦...⟧`».
- ❌ Pre-Andromeda рекомендація як актуальна: **розділити cold/warm**, **дублювати адсети** для скейлу, **вузький ручний таргетинг** замість broad, **класичне A/B схожих оголошень** замість Creative Testing tool / variations, **«один CTA на креатив»**, «**вимкнути top-funnel оголошення**, бо жере бюджет». Усе — anti-patterns ⟦[[00-philosophy/andromeda-era]] · [[01-structure/campaign-structure]] · [[12-testing/post-andromeda-testing]]⟧.
- ❌ Прапор «фрагментація» без перевірки **валідних виключень** (локація / продукт / omnipresent / retargeting-only).
- ❌ Рекомендація по optimization event / value rule / placement на основі метрики з вибіркою <1000 показів / <3 конверсій.
- ❌ Вигадане значення поля, якого Marketing API не віддав (bid_strategy, learning_status, enhancements) — замість цього data-gap «звірити вручну».
- ❌ Факт без маркера `⟦object_id · поле=значення⟧`.
- ❌ Beauty без substance: розписувати 11 параметрів там, де реально проблемні 3.

---

## SELF-CHECK (як перевірити / фальсифікувати цей аудит налаштувань)

> Цю секцію playbook **повторює в самому звіті** (5.9), наповнюючи реальними значеннями акаунта. Тут — каркас.

**Чек-лист цілісності (перед видачею звіту):**
- [ ] Кожне налаштування прочитане з Marketing API **цієї сесії** і несе `⟦object_id · поле=значення⟧`; поля, яких Marketing API не дав, винесені в data-gaps (а не вгадані).
- [ ] Жодне речення не змішує KNOWLEDGE (принцип `[[...]]`) і DATA (конфіг акаунта).
- [ ] Кожен прапор «фрагментація» звірений із валідними виключеннями (локація / продукт / omnipresent / retargeting-only / dynamic catalog).
- [ ] Будь-яка рекомендація, що спирається на **метрику**, має достатню вибірку (≥1000 показів / ≥3 конв. / ≥2 дні); інакше «недостатньо даних».
- [ ] ≥3 дії дієві: кожна = `object_id` + поточне значення + поріг/правило + конкретна дія + джерело `[[...]]`.
- [ ] Кожна кардинальна зміна має `expected_impact` з механізмом і цифрою.
- [ ] Жодна рекомендована тактика не є pre-Andromeda без явної мітки (звірено з §7).
- [ ] У переданих діях зазначено, які **рестартять learning phase** (objective/optimization/таргетинг), щоб згрупувати їх.
- [ ] Усі дієві пункти позначені `[ready-for-/ads-optimizer]` (аудит нічого не змутував сам).

**Фальсифікаційні твердження (≥5 — «цей висновок хибний, якщо…»):**
1. «Структура `act_XXX` фрагментована (окремі cold/warm) — консолідувати» — **хибне, якщо** розділення зроблено за **локацією** (hard control) або за **різними продуктами** з різною оптимізацією; тоді це валідно ⟦[[01-structure/campaign-structure]]⟧. Перевірити: чим саме відрізняються кампанії (geo/продукт vs аудиторія).
2. «Окрема warm-кампанія `campaign_id=B` зайва» — **хибне, якщо** це свідомий **retargeting-only** під особливий оффер для warm (ascension / кастомний меседж) зі знятим *use as suggestion*; тоді вона виправдана ⟦[[09-retargeting/retargeting-post-andromeda]]⟧. Перевірити: чи однаковий оффер у cold і warm.
3. «Objective=TRAFFIC треба змінити на LEADS» — **хибне, якщо** кампанія — навмисний **omnipresent content** для high-ticket/involved покупки (`is_high_ticket=true`); тоді верх воронки виправданий ⟦[[01-structure/campaign-structure]] · [[04-budget-scaling/small-budget]]⟧. Перевірити бриф.
4. «Optimization event purchase треба зсунути на ATC (бо learning limited)» — **хибне, якщо** адсет робить ~20 purchases/тиждень і близький до масштабу: Meta дуже буквальна, частина ATC не дійде до покупки — краще лишити кінцеву ціль ⟦[[05-optimization/learning-phase]]⟧.
5. «Адсет `adset_id=X` у Learning Limited → проблема» — **хибне, якщо** він **прибутковий** (CPA/ROAS у target): learning limited не катастрофа, бюджетом не лікувати, консолідація піднесе результат без «raise budget» ⟦[[05-optimization/learning-phase]]⟧.
6. «Демографію A додати у value rule (дешевша)» — **хибне, якщо** вибірка A <1000 показів / <3 конв. (breakdown дробить дані) **або** немає реальної LTV-різниці в CRM — тоді % береться «зі стелі» ⟦[[03-targeting/value-rules]]⟧. Перевірити: розмір вибірки A + `ltv_by_segment`.
7. «Manual placements (AN off) — повернути Advantage+» — **хибне, якщо** відключення спирається на **достатню** вибірку, де площадка стабільно дорожча; тоді це обґрунтоване рішення, а не помилка. Перевірити обсяг даних у breakdown publisher_platform.
8. «`bid_strategy=COST_CAP` шкодить (адсет недовитрачає)» — **хибне, якщо** cap навмисний для жорсткої юніт-економіки і адсет **витрачає** бюджет у target; тоді cap працює як треба. Перевірити: фактичний spend vs daily_budget і CPL vs cap.
9. «Багато змін на адсет = helicopter-parenting» — **хибне, якщо** це були **критичні** втручання (CPL 5× target, ad-eater) або одна батч-партія креативів, а не щоденний drip-feed; історія могла злити їх у логу. Перевірити timestamps у `history/`/Activity Log.

**Якщо хоч один пункт не можеш закрити даними — у звіт іде data-gap (5.8), а не здогад.**
