---
playbook: report-template
purpose: "Універсальний ФОРМАТ звіту для всіх аналітичних playbooks meta-ads-pro (audit-account, analyze-landing, analyze-creative, analyze-video-ad, analyze-settings)"
status: active
era: post-andromeda
last_reviewed: 2026-06-03
applies_to:
  - playbooks/audit-account.md
  - playbooks/analyze-landing.md
  - playbooks/analyze-creative.md
  - playbooks/analyze-video-ad.md
  - playbooks/analyze-settings.md
mcp: meta-ads (read-only для аналізу)
---

# Report Template — спільний формат дієвого звіту

> **Що це.** Не окремий аналіз, а **скелет вихідного документа**, який інші playbooks наповнюють своїми даними. Будь-який playbook (`audit-account`, `analyze-settings`, `analyze-creative`, …) збирає дані через API, проганяє свою логіку, а потім **викладає висновки САМЕ в цю структуру**. Так усі звіти `meta-ads-pro` мають однаковий кістяк, однакову строгість і однаковий self-check.
>
> **Еталон якості** — `materials/traffic/fb-deep-audit-meta-prompt.md`. Анти-галюцинаційні правила — `META-PROMPT.md §9` + `guardrails/` + `safety_rules.md`.
>
> **Головний бар** (з META-PROMPT §10): користувач може **сьогодні** поставити в роботу ≥3 конкретні дії; кожна цифра має джерело (object_id · дата · метрика); кожен висновок **фальсифікований** (вказано, як перевірити). Інакше звіт відхиляється.

---

## 0. Як цим користуватись (для playbook-агента)

1. **Спочатку дані, потім висновки.** Жодного рядка звіту не пишеться, поки не прочитано сирі дані з Marketing API цієї сесії (`get_insights`, `get_campaigns`, `get_adsets`, `get_ads`, `get_ad_creatives`, `get_custom_audiences`). Read-before-write — `guardrails` / META-PROMPT §9.1.
2. **Розділяй два джерела фактів.** `KNOWLEDGE` (принцип бази, через `[[category/subcategory]]`) і `DATA` (число твого акаунту з Marketing API) — **ніколи не змішуй**. «База каже консолідувати» ≠ «у твоєму акаунті 5 cold-адсетів б'ють той самий сегмент». Перше — посилання `[[...]]`, друге — `⟦object_id @date⟧`. META-PROMPT §9.2.
3. **Поріг значущості.** Не виносити вирок об'єкту на `<1000 показів` АБО `<3 конверсії` АБО `<2 дні` даних (`safety_rules.md` → «Мінімум даних»). Менше — пиши «**недостатньо даних** — потрібна вибірка `breakdowns=...` / довший період», а не вигадуй.
4. **Кожна цифра — з джерела.** Формат маркера даних усюди в звіті: `⟦<object_id> · <metric>=<value> · <period>⟧`. Якщо число — заява Meta з UI (напр. «AI image +11% CTR»), позначай `Meta-claim`, не як вимір акаунту.
5. **Заповнюй ВСІ 9 секцій по порядку** (нижче). Секцію без даних не викидати — лишити заголовок і всередині написати «недостатньо даних: потрібно `<що саме запитати>`».
6. **Дієвість — закон.** Кожна рекомендація = конкретний об'єкт (`campaign_id` / `adset_id` / `ad_id`) + метрика + поріг + дія + очікуваний ефект з арифметикою. НЕ «покращити креативи», а «паузити `ad_id=X` (CPL 3× target), дублювати `ad_id=Y` з +30% бюджету».
7. **Формат виводу — за запитом:** Markdown (швидкий чат-звіт) АБО HTML (повний звіт під збереження в `materials/`). Обидва шаблони — у цьому файлі (§A markdown, §B HTML).
8. **Self-check — обов'язковий** (секція 9): ≥5 тверджень «це хибно, якщо…» + таблиця факт→джерело→як перевірити. Без неї звіт не фінальний (META-PROMPT §9.8).

> **Жодних змін** в акаунті в межах звіту: всі playbooks-аналітики **read-only**. Звіт лише **рекомендує** дії; виконання — окремо через `/ads-optimizer` чи `/campaign-manager` з підтвердженням (`safety_rules.md` → «Dangerous операції»).

---

## 1. Структура звіту (9 секцій, фіксований порядок)

| # | Секція | Що містить | Мін. вимога |
|---|--------|-----------|-------------|
| H | Header + KPI-strip | Заголовок, ціль (`target_CPL`/`target_ROAS` з брифу), 4–5 топ-метрик із WoW-дельтами | Кожна метрика — `⟦джерело⟧`, дельта зі знаком |
| 1 | 🩺 Діагноз | 3–5 речень підсумку + severity-таблиця (симптом→тяжкість→причина→швидкий фікс) | ≥1 рядок таблиці; «причина» прив'язана до DATA, не до здогаду |
| 2 | ✅ Що працює | Картки: object_id · метрики · **причина** успіху · як скейлити | ≥1 картка або «недостатньо даних» |
| 3 | ❌ Що не працює | Картки: object_id · втрачений бюджет · корінь · дія | ≥1 картка або «недостатньо даних» |
| 4 | 🔥 Кардинальні (top-3) | 3 дії, кожна 30–50% impact, повна 7-полів картка | Рівно ≤3, кожна з expected_impact в цифрах |
| 5 | 🔧 Інкрементальні (5–10) | Малі дії 3–10% кожна, сумарно 30–50% | 5–10 шт., кожна з полями effort/impact |
| 6 | 🚀 Roadmap | Тижневий план + **арифметична** проєкція до цілі | Розрахунок «якщо X,Y,Z → результат N» |
| 7 | 🔍 Data-gaps | Які breakdowns/метрики/періоди потрібні наступного разу | ≥2 конкретні запити (`breakdowns=...`) |
| 8 | 🧐 Self-check | ≥5 «хибно, якщо…» + facts-table (факт→джерело→як перевірити) | ≥5 пунктів фальсифікації |

> Секції 2 і 3 («що працює / що не працює») у деяких playbooks зливаються в одну (напр. `analyze-creative` для одного креативу) — тоді залиш одну секцію з обома полюсами. Решта 7 — завжди присутні.

---

## 2. Контракти полів (єдині для всіх playbooks)

### 2.1 Маркер даних (data marker)
Будь-яке число про акаунт супроводжується:
```
⟦<object_id> · <metric>=<value> · <period>⟧
```
Приклади:
- `⟦adset_id=120XXX · CPL=$3.61 · 30.04–06.05⟧`
- `⟦ad_id=120YYY · CTR=2.2% · last_7d⟧`
- `⟦act_XXX · spend=$1943 · last_7d⟧`

Заборонено число без маркера. Якщо джерело — заява Meta з інтерфейсу: `(Meta-claim, UI)`.

### 2.2 Посилання на знання (knowledge link)
Принцип/тактика бази — через `[[category/subcategory]]`, **без** конкретних чисел акаунту:
- «консолідувати адсети» → [[05-optimization/learning-phase]], [[01-structure/campaign-structure]]
- «масштабувати наявну кампанію, не дублювати» → [[04-budget-scaling/big-spend-scaling]]
- «один angle на оголошення» → [[06-creatives/why-ads-fail]]
- «hybrid warm+cold, не окрема warm-кампанія» → [[09-retargeting/retargeting-post-andromeda]]
- «малий бюджет: ніша + не helicopter-parent» → [[04-budget-scaling/small-budget]]

### 2.3 Картка рекомендації (7 полів — для §4 кардинальних і §5 інкрементальних)
```yaml
title:           <короткий заголовок дії>
target_object:   <campaign_id | adset_id | ad_id>          # конкретний об'єкт!
trigger:         <метрика + поріг, що запускає дію>         # ⟦data marker⟧
what:            <що саме зробити: pause / +30% budget / duplicate / новий тест>
why:             <корінь + посилання [[knowledge]]>
expected_impact: <у цифрах, з арифметикою — див. §2.4>
effort:          <S | M | L  +  ~к-сть днів роботи>
risk:            <low | mid | high  +  одне речення чому>
success_metric:  <яка метрика і до якого порога за який строк підтвердить успіх>
```
Для §5 (інкрементальних) поля ті самі, але `expected_impact` дрібніший (3–10%) і опис коротший.

### 2.4 Правило `expected_impact` (анти-галюцинація прогнозів)
Прогноз БЕЗ арифметики — заборонений (META-PROMPT §10 anti-goals).
- ❌ «підніме ROAS у 3 рази», «CTR зросте на 20%».
- ✅ ланцюжок із чисел акаунту:
  > «Top-3 креативи дають CTR 2.6% ⟦ad_id=A,B,C · last_7d⟧ проти 2.2% по акаунту ⟦act_XXX · last_7d⟧. Якщо паузнути 4 ad-eaters (CPL >2× target ⟦…⟧) і їхній бюджет $X/день перелити в Top-3 → за тиждень re-learning очікувано середній CTR ≈2.5% → CPC ≈$0.42 → CPL ≈$2.40 проти поточного $3.61. **Гіпотеза**, перевірити по `last_7d` після зміни.»

Кожен прогноз позначай як **гіпотезу** + умову перевірки. Числа беруться з ФАКТИЧНИХ топ/медіан акаунту, не зі стелі.

### 2.5 Рейтинг-pills (єдина легенда для всіх звітів)
| Pill | Значення | Поріг (приклад; калібрується брифом) |
|------|----------|--------------------------------------|
| 🔥 TOP | сильно краще цілі — кандидат на скейл | метрика ≤0.7× target (CPL) АБО ≥1.3× target (ROAS) |
| ✅ GOOD | в нормі / трохи краще | у коридорі ±10% target |
| ⚠️ AVG | межовий, під наглядом | гірше target на 10–50% |
| ❌ BAD | провальний — лікувати/паузити | гірше target ≥50%, або spend без конверсій ≥2× target |

Пороги беруться з `target_CPL`/`target_ROAS` брифу. Узгоджено з класами Health Score `/ads-optimizer` (very_good/good/neutral/slightly_bad/bad) і з ad-eater-рівнями `safety_rules.md`.

---

## 3. Health Score у звіті (узгодження з `/ads-optimizer` і `/ads-reporter`)

Якщо playbook оцінює адсети, він використовує той самий **5-компонентний Health Score**, що й `/ads-optimizer` — звіт не вигадує свою шкалу.

- **Формула:** `HS = round((CPL_Gap + Trends + Diagnostics + Today_Adj) × Volume_Factor)`, HS ∈ [−100; +100].
- **Компоненти:** CPL Gap (±45) · Trends 3d↔7d (±15) · Diagnostics (CTR<1% −8 / CPM>median×1.3 −12 / Freq>2 −10) · Today-компенсація (0..+30) · Volume Factor (×0.6..1.0).
- **Класи → pills:** very_good(≥+25)=🔥 · good(+5..+24)=✅ · neutral(−5..+4)=⚠️ · slightly_bad(−25..−6)=⚠️ · bad(≤−25)=❌.
- **Дія за класом** (з `/ads-optimizer` Шаг 7): very_good→скейл +10..+30% · good→тримати · neutral→нагляд · slightly_bad→−20..−40% · bad→−50% або пауза.
- **Ad-eater** = **оголошення** (ad), не адсет: CRITICAL CPL>3×target → пауза; HIGH zero-leads при spend≥2×target → пауза. Деталі — `safety_rules.md`.

> Якщо даних на адсет `<1000` показів — Volume Factor тягне HS до 0; у звіті явно: «HS низької довіри — мало показів, рішення відкласти».

---

## 4. API-збір даних під цей формат (read-only)

Мінімальний набір викликів, щоб заповнити всі 9 секцій (точний перелік — у конкретному playbook):

```text
# Структура
get_campaigns(object_id="act_XXX", status_filter="ACTIVE")
get_adsets(object_id="act_XXX")
get_ads(object_id="act_XXX")
get_ad_creatives(ad_id="...")            # для секцій про креатив
get_custom_audiences(object_id="act_XXX")# для секцій про ретаргетинг/сегменти

# Метрики (5 періодів — як у /ads-reporter)
get_insights(object_id="act_XXX", time_range="today",     level="adset")
get_insights(object_id="act_XXX", time_range="yesterday", level="adset")
get_insights(object_id="act_XXX", time_range="last_3d",   level="adset")
get_insights(object_id="act_XXX", time_range="last_7d",   level="adset")
get_insights(object_id="act_XXX", time_range="last_30d",  level="adset")
get_insights(object_id="act_XXX", time_range="last_7d",   level="ad")     # ad-eater detection

# Breakdowns (для секції "що працює/не працює" і для закриття data-gaps)
get_insights(object_id="act_XXX", time_range="last_30d", breakdowns="age")
get_insights(object_id="act_XXX", time_range="last_30d", breakdowns="gender")
get_insights(object_id="act_XXX", time_range="last_30d", breakdowns="country")
get_insights(object_id="act_XXX", time_range="last_30d", breakdowns="publisher_platform")
```

**Правило data-gap:** якщо для висновку треба зріз, якого ще не зробив — НЕ вигадуй («Stories гірше Feed»), а в секцію 7 запиши: «потрібен `breakdowns=publisher_platform`, період `last_14d`».

---

# §A. MARKDOWN-ШАБЛОН ЗВІТУ

> Копіюй цей блок у вихід і заповнюй. `{{...}}` — підставити з DATA; `[[...]]` — посилання на базу знань; усі числа — з `⟦маркером⟧`.

```markdown
# {{Тип аналізу}} · {{об'єкт: act_XXX / campaign / лендинг / креатив}} · {{період}}
🎯 Ціль: {{target_CPL}} / {{target_ROAS}} (з брифу) · поточно: {{факт CPL/ROAS}} ⟦джерело⟧

**KPI-strip** (WoW):
| Метрика | Зараз | Δ vs попередній період | Джерело |
|---------|------:|:----------------------:|---------|
| Spend | {{$X}} | {{+/−Y%}} | ⟦act_XXX · spend · {{period}}⟧ |
| CPL / CPA | {{$X}} | {{+/−Y%}} | ⟦…⟧ |
| CTR | {{X%}} | {{+/−Ypp}} | ⟦…⟧ |
| {{Конверсії}} | {{N}} | {{+/−Y%}} | ⟦…⟧ |
| {{ROAS / Leads}} | {{X}} | {{+/−Y%}} | ⟦…⟧ |

## 🩺 Діагноз
{{3–5 речень: головний висновок одним абзацом. Що болить, наскільки серйозно, корінь. Без води, кожна теза — з ⟦DATA⟧.}}

| Симптом | Тяжкість | Причина (корінь) | Швидкий фікс |
|---------|:--------:|------------------|--------------|
| {{CPL +80% за 4 тижні ⟦…⟧}} | ❌ | {{creative burnout: top-1 жере 55% бюджету ⟦ad_id=… · spend_share⟧}} | {{паузити ad_id=…, перелити в ad_id=…}} |
| {{CTR 2.7→2.2% ⟦…⟧}} | ⚠️ | {{frequency 4.1 ⟦adset_id=… · freq · last_7d⟧}} [[06-creatives/why-ads-fail]] | {{новий angle, Creative Testing tool}} [[12-testing/post-andromeda-testing]] |

## ✅ Що працює
{{За кожним: object_id, метрики, ПРИЧИНА (яка комбінація креатив+аудиторія+timing дала результат), як скейлити.}}

**🔥 {{Назва/ad_id}}** — {{CPL $X, CTR Y%}} ⟦ad_id=… · last_7d⟧
- Причина: {{конкретна комбінація, не "спрацювало"}}
- Як скейлити: {{+30% бюджету / дублювати angle / value rule}} [[04-budget-scaling/big-spend-scaling]]

## ❌ Що не працює
{{За кожним: object_id, втрачений бюджет ($ за період), корінева причина, дія.}}

**❌ {{Назва/ad_id}}** — {{CPL $X (Z× target), spend $W без N конв.}} ⟦ad_id=… · last_7d⟧
- Корінь: {{audience fatigue / wrong placement / message overload / learning reset}}
- Дія: {{pause ad_id=… / −40% / замінити angle}}

## 🔥 Кардинальні зміни (top-3)
{{Рівно ≤3. Кожна — 30–50% impact. Картка з §2.3. ROI-пріоритет.}}

### 1. {{title}}
- **Об'єкт:** {{adset_id/ad_id}}
- **Тригер:** {{метрика+поріг}} ⟦…⟧
- **Що:** {{дія}}
- **Чому:** {{корінь}} [[knowledge]]
- **Очікуваний ефект:** {{арифметика з §2.4 — гіпотеза}}
- **Effort:** {{S/M/L · ~Nдн}} · **Risk:** {{low/mid/high · чому}}
- **Success metric:** {{метрика→поріг→строк}}

### 2. … ### 3. …

## 🔧 Інкрементальні зміни (5–10, сумарно 30–50%)
| # | Об'єкт | Що | Чому | Impact | Effort | Risk | Success |
|---|--------|----|------|:------:|:------:|:----:|---------|
| 1 | {{adset_id}} | {{−30% бюджет}} | {{HS −22, CPL +30% ⟦…⟧}} | ~5% | S | low | {{CPL≤target за 7д}} |
| … | | | | | | | |

## 🚀 Roadmap до {{цілі}}
**Тиждень 1:** {{кроки + budget ramp}} · **Т2:** … · **Т3:** … · **Т4:** …

**Проєкція (арифметика):**
> Якщо CTR {{X%}}, CPC {{$Y}}, CPL {{$Z}} (з топ-кейсів ⟦…⟧) → бюджет {{$N/день}} дасть {{M}} конв./день @ {{$K}}/конв. Це **гіпотеза**, перевірити по {{period}} після кроку 1.

## 🔍 Чого бракує в даних
- {{потрібен `breakdowns=publisher_platform` — щоб судити про плейсменти}}
- {{потрібен `breakdowns=hourly_stats` + `time_increment=1` — для time-of-day}}
- {{потрібен CRM-крос (paid_full vs реєстрації) — для revenue-attribution}}

## 🧐 Self-check цього звіту
**Факти → джерело → як перевірити:**
| Факт | Джерело | Як фальсифікувати |
|------|---------|-------------------|
| {{CPL виріс +80%}} | ⟦act_XXX · 4 тижні⟧ | {{перерахувати spend/leads по тижнях}} |

**Це хибно, якщо:**
1. {{<1000 показів на ключовому адсеті → вибірка нерепрезентативна}}
2. {{конверсії з затримкою атрибуції ще «доїдуть» → CPL насправді нижчий}}
3. {{причина деградації — Q4-сезонність CPM, а не сетап}} [[00-philosophy/andromeda-era]]
4. {{ad-eater насправді top-funnel у послідовності Meta}} [[01-structure/campaign-structure]]
5. {{warm-аудиторія вичерпалась — справа в офері/креативі, не в бюджеті}} [[04-budget-scaling/big-spend-scaling]]
```

---

# §B. HTML-ШАБЛОН ЗВІТУ (темна тема, рейтинг-pills)

> Для повного звіту під збереження в `<your-output-folder>/report.html` (у дистрибутиві — нейтральний шлях). Темна тема (#0f172a фон, #1e293b cards, #fde047 accent), sticky toolbar, pills 🔥/✅/⚠️/❌, color-coded WoW-дельти. Розмір орієнтовно 100–300 KB, час читання 15–25 хв (як еталон).
>
> Заповнюй вузли `data-fill="..."`; усі числа лишай із `⟦маркером⟧` у видимому тексті або в `title=`-тултіпі.

```html
<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>{{Тип аналізу}} · {{об'єкт}} · {{період}}</title>
<style>
  :root{
    --bg:#0f172a; --card:#1e293b; --card2:#243044; --line:#334155;
    --txt:#e2e8f0; --muted:#94a3b8; --accent:#fde047;
    --top:#22c55e; --good:#84cc16; --avg:#f59e0b; --bad:#ef4444; --info:#38bdf8;
  }
  *{box-sizing:border-box}
  body{margin:0;background:var(--bg);color:var(--txt);
       font:15px/1.6 -apple-system,Segoe UI,Roboto,Inter,sans-serif}
  a{color:var(--accent)}
  .wrap{max-width:1080px;margin:0 auto;padding:0 20px 80px}
  .toolbar{position:sticky;top:0;z-index:20;background:rgba(15,23,42,.92);
           backdrop-filter:blur(8px);border-bottom:1px solid var(--line);
           display:flex;gap:14px;flex-wrap:wrap;align-items:center;
           padding:12px 20px;margin-bottom:8px}
  .toolbar a{color:var(--muted);text-decoration:none;font-size:13px;white-space:nowrap}
  .toolbar a:hover{color:var(--accent)}
  header{padding:26px 0 8px}
  h1{font-size:26px;margin:0 0 4px}
  .sub{color:var(--muted);font-size:14px}
  .kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px;margin:18px 0}
  .kpi{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:12px 14px}
  .kpi .lbl{color:var(--muted);font-size:12px;text-transform:uppercase;letter-spacing:.04em}
  .kpi .val{font-size:22px;font-weight:700;margin-top:2px}
  .delta-up{color:var(--top)} .delta-down{color:var(--bad)} .delta-flat{color:var(--muted)}
  section{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:20px 22px;margin:16px 0}
  h2{font-size:20px;margin:0 0 12px;border-left:4px solid var(--accent);padding-left:10px}
  .lead{color:var(--txt);font-size:15px;margin:0 0 14px}
  table{width:100%;border-collapse:collapse;margin:10px 0;font-size:14px}
  th,td{border:1px solid var(--line);padding:8px 10px;text-align:left;vertical-align:top}
  th{background:var(--card2);color:var(--muted);font-weight:600}
  td.num{text-align:right;font-variant-numeric:tabular-nums}
  .pill{display:inline-block;padding:2px 9px;border-radius:999px;font-size:12px;font-weight:700}
  .p-top{background:rgba(34,197,94,.15);color:var(--top);border:1px solid var(--top)}
  .p-good{background:rgba(132,204,22,.15);color:var(--good);border:1px solid var(--good)}
  .p-avg{background:rgba(245,158,11,.15);color:var(--avg);border:1px solid var(--avg)}
  .p-bad{background:rgba(239,68,68,.15);color:var(--bad);border:1px solid var(--bad)}
  .cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:14px}
  .card{background:var(--card2);border:1px solid var(--line);border-radius:12px;padding:14px 16px}
  .card.crit{border-left:4px solid var(--bad)}
  .card.win{border-left:4px solid var(--top)}
  .card h3{margin:0 0 8px;font-size:16px}
  .card dl{display:grid;grid-template-columns:120px 1fr;gap:4px 10px;margin:0;font-size:13px}
  .card dt{color:var(--muted)} .card dd{margin:0}
  .src{color:var(--info);font-size:12px;font-family:ui-monospace,monospace}
  .kb{color:var(--accent);font-size:12px}
  .gap{color:var(--avg);font-weight:600}
  .note{background:rgba(56,189,248,.08);border:1px solid var(--info);border-radius:8px;padding:10px 12px;color:var(--muted);font-size:13px;margin:10px 0}
  ul{margin:8px 0;padding-left:20px} li{margin:4px 0}
  code{background:#0b1220;border:1px solid var(--line);border-radius:5px;padding:1px 6px;font-size:13px}
</style>
</head>
<body>
<nav class="toolbar">
  <strong style="color:var(--accent)">{{короткий тип}}</strong>
  <a href="#diagnosis">🩺 Діагноз</a>
  <a href="#worked">✅ Працює</a>
  <a href="#failed">❌ Не працює</a>
  <a href="#cardinal">🔥 Кардинальні</a>
  <a href="#incremental">🔧 Інкрементальні</a>
  <a href="#roadmap">🚀 Roadmap</a>
  <a href="#gaps">🔍 Data-gaps</a>
  <a href="#selfcheck">🧐 Self-check</a>
</nav>

<div class="wrap">
  <header>
    <h1 data-fill="title">{{Тип аналізу}} · {{об'єкт}}</h1>
    <div class="sub" data-fill="subtitle">
      Ціль {{target_CPL}}/{{target_ROAS}} · поточно {{факт}} · період {{period}}
    </div>
  </header>

  <!-- KPI STRIP -->
  <div class="kpis" data-fill="kpis">
    <div class="kpi"><div class="lbl">Spend</div><div class="val">{{$X}}
      <span class="delta-down">{{+Y%}}</span></div></div>
    <div class="kpi"><div class="lbl">CPL / CPA</div><div class="val">{{$X}}
      <span class="delta-down">{{+Y%}}</span></div></div>
    <div class="kpi"><div class="lbl">CTR</div><div class="val">{{X%}}
      <span class="delta-down">{{−Ypp}}</span></div></div>
    <div class="kpi"><div class="lbl">Конверсії</div><div class="val">{{N}}
      <span class="delta-up">{{+Y%}}</span></div></div>
    <div class="kpi"><div class="lbl">ROAS / Leads</div><div class="val">{{X}}
      <span class="delta-flat">{{≈0%}}</span></div></div>
  </div>

  <!-- 1. ДІАГНОЗ -->
  <section id="diagnosis">
    <h2>🩺 Діагноз</h2>
    <p class="lead" data-fill="diagnosis-lead">
      {{3–5 речень підсумку. Кожна теза — з даними.}}
    </p>
    <table>
      <thead><tr><th>Симптом</th><th>Тяжкість</th><th>Причина (корінь)</th><th>Швидкий фікс</th></tr></thead>
      <tbody data-fill="severity-rows">
        <tr>
          <td>CPL +80% за 4 тижні <span class="src">⟦act_XXX · 4w⟧</span></td>
          <td><span class="pill p-bad">❌ critical</span></td>
          <td>creative burnout: top-1 жере 55% бюджету <span class="src">⟦ad_id=… · spend_share⟧</span></td>
          <td>паузити ad_id=…, перелити в ad_id=…</td>
        </tr>
        <tr>
          <td>CTR 2.7→2.2% <span class="src">⟦… · last_7d⟧</span></td>
          <td><span class="pill p-avg">⚠️ avg</span></td>
          <td>frequency 4.1 <span class="src">⟦adset_id=… · freq⟧</span> <span class="kb">[[06-creatives/why-ads-fail]]</span></td>
          <td>новий angle через Creative Testing tool <span class="kb">[[12-testing/post-andromeda-testing]]</span></td>
        </tr>
      </tbody>
    </table>
  </section>

  <!-- 2. ЩО ПРАЦЮЄ -->
  <section id="worked">
    <h2>✅ Що працює</h2>
    <p class="lead">За кожним: object_id, метрики, причина успіху, як скейлити.</p>
    <div class="cards" data-fill="win-cards">
      <div class="card win">
        <h3><span class="pill p-top">🔥 TOP</span> {{ad_id / назва}}</h3>
        <dl>
          <dt>Метрики</dt><dd>CPL {{$X}}, CTR {{Y%}} <span class="src">⟦ad_id=… · last_7d⟧</span></dd>
          <dt>Причина</dt><dd>{{конкретна комбінація креатив×аудиторія×timing}}</dd>
          <dt>Як скейлити</dt><dd>{{+30% / дублювати angle}} <span class="kb">[[04-budget-scaling/big-spend-scaling]]</span></dd>
        </dl>
      </div>
    </div>
  </section>

  <!-- 3. ЩО НЕ ПРАЦЮЄ -->
  <section id="failed">
    <h2>❌ Що не працює</h2>
    <p class="lead">За кожним: object_id, втрачений бюджет, корінь, дія.</p>
    <div class="cards" data-fill="fail-cards">
      <div class="card crit">
        <h3><span class="pill p-bad">❌ BAD</span> {{ad_id / назва}}</h3>
        <dl>
          <dt>Метрики</dt><dd>CPL {{$X}} ({{Z×}} target), spend {{$W}} / {{N}} конв. <span class="src">⟦ad_id=… · last_7d⟧</span></dd>
          <dt>Корінь</dt><dd>{{fatigue / wrong placement / message overload}}</dd>
          <dt>Дія</dt><dd>{{pause ad_id=… / −40%}}</dd>
        </dl>
      </div>
    </div>
  </section>

  <!-- 4. КАРДИНАЛЬНІ -->
  <section id="cardinal">
    <h2>🔥 Кардинальні зміни (top-3)</h2>
    <p class="lead">Кожна → 30–50% impact. ROI-пріоритет. Прогноз = гіпотеза з арифметикою.</p>
    <div class="cards" data-fill="cardinal-cards">
      <div class="card crit">
        <h3>1. {{title}}</h3>
        <dl>
          <dt>Об'єкт</dt><dd><code>{{adset_id/ad_id}}</code></dd>
          <dt>Тригер</dt><dd>{{метрика+поріг}} <span class="src">⟦…⟧</span></dd>
          <dt>Що</dt><dd>{{дія}}</dd>
          <dt>Чому</dt><dd>{{корінь}} <span class="kb">[[knowledge]]</span></dd>
          <dt>Ефект</dt><dd>{{арифметика-гіпотеза §2.4}}</dd>
          <dt>Effort</dt><dd>{{M · ~2дн}}</dd>
          <dt>Risk</dt><dd>{{mid · чому}}</dd>
          <dt>Success</dt><dd>{{метрика→поріг→строк}}</dd>
        </dl>
      </div>
      <!-- card 2, card 3 -->
    </div>
  </section>

  <!-- 5. ІНКРЕМЕНТАЛЬНІ -->
  <section id="incremental">
    <h2>🔧 Інкрементальні зміни (5–10, сумарно 30–50%)</h2>
    <table>
      <thead><tr><th>#</th><th>Об'єкт</th><th>Що</th><th>Чому</th><th>Impact</th><th>Effort</th><th>Risk</th><th>Success</th></tr></thead>
      <tbody data-fill="incremental-rows">
        <tr>
          <td>1</td><td><code>{{adset_id}}</code></td><td>−30% бюджет</td>
          <td>HS −22, CPL +30% <span class="src">⟦…⟧</span></td>
          <td class="num">~5%</td><td>S</td>
          <td><span class="pill p-good">low</span></td><td>CPL≤target за 7д</td>
        </tr>
      </tbody>
    </table>
  </section>

  <!-- 6. ROADMAP -->
  <section id="roadmap">
    <h2>🚀 Roadmap до {{цілі}}</h2>
    <table>
      <thead><tr><th>Тиждень</th><th>Кроки</th><th>Budget ramp</th><th>Очікувано (гіпотеза)</th></tr></thead>
      <tbody data-fill="roadmap-rows">
        <tr><td>1</td><td>{{паузи ad-eaters + перелив у TOP}}</td><td>{{$X→$X}}</td><td>{{CPL ↓ до $Z ⟦…⟧}}</td></tr>
        <tr><td>2</td><td>{{+10% наявній кампанії}} <span class="kb">[[04-budget-scaling/big-spend-scaling]]</span></td><td>{{$X→$Y}}</td><td>{{…}}</td></tr>
        <tr><td>3</td><td>{{Creative Testing tool: 2×10 хуків}} <span class="kb">[[12-testing/post-andromeda-testing]]</span></td><td>—</td><td>{{новий angle-переможець}}</td></tr>
        <tr><td>4</td><td>{{масштаб переможця}}</td><td>{{$Y→$Z}}</td><td>{{…}}</td></tr>
      </tbody>
    </table>
    <div class="note" data-fill="projection">
      <strong>Проєкція:</strong> якщо CTR {{X%}}, CPC {{$Y}}, CPL {{$Z}} (з топ-кейсів <span class="src">⟦…⟧</span>)
      → бюджет {{$N/день}} дасть {{M}} конв./день @ {{$K}}/конв.
      <em>Гіпотеза, перевірити по {{period}} після кроку 1.</em>
    </div>
  </section>

  <!-- 7. DATA-GAPS -->
  <section id="gaps">
    <h2>🔍 Чого бракує в даних</h2>
    <ul data-fill="gaps">
      <li><span class="gap">потрібен</span> <code>breakdowns=publisher_platform</code> — щоб судити про плейсменти (зараз — <span class="gap">недостатньо даних</span>)</li>
      <li><span class="gap">потрібен</span> <code>breakdowns=hourly_stats</code> + <code>time_increment=1</code> — для time-of-day</li>
      <li><span class="gap">потрібен</span> CRM-крос (paid vs реєстрації) — для revenue-attribution</li>
    </ul>
  </section>

  <!-- 8. SELF-CHECK -->
  <section id="selfcheck">
    <h2>🧐 Self-check цього звіту</h2>
    <table>
      <thead><tr><th>Факт</th><th>Джерело</th><th>Як фальсифікувати</th></tr></thead>
      <tbody data-fill="facts">
        <tr><td>CPL виріс +80%</td><td><span class="src">⟦act_XXX · 4w⟧</span></td><td>перерахувати spend/leads по тижнях</td></tr>
      </tbody>
    </table>
    <p class="lead" style="margin-top:14px"><strong>Це хибно, якщо:</strong></p>
    <ul data-fill="falsify">
      <li>на ключовому адсеті <code>&lt;1000</code> показів → вибірка нерепрезентативна</li>
      <li>конверсії з затримкою атрибуції ще «доїдуть» → реальний CPL нижчий</li>
      <li>деградація — від Q4-сезонності CPM, а не сетапу <span class="kb">[[00-philosophy/andromeda-era]]</span></li>
      <li>"ad-eater" — насправді top-funnel у послідовності Meta <span class="kb">[[01-structure/campaign-structure]]</span></li>
      <li>warm-аудиторія вичерпалась — корінь в офері/креативі, не в бюджеті <span class="kb">[[04-budget-scaling/big-spend-scaling]]</span></li>
    </ul>
  </section>
</div>
</body>
</html>
```

---

## §C. Перелік pills та кольорів (швидка довідка для верстки)

| Pill | CSS-клас | Колір | Коли |
|------|----------|-------|------|
| 🔥 TOP | `p-top` | `--top` зелений | сильно краще цілі, скейл |
| ✅ GOOD | `p-good` | `--good` лайм | в нормі |
| ⚠️ AVG | `p-avg` | `--avg` бурштин | межовий, нагляд |
| ❌ BAD | `p-bad` | `--bad` червоний | провал, лікувати/паузити |

WoW-дельти: `delta-up` (покращення, зелений), `delta-down` (погіршення, червоний), `delta-flat` (±10%, сірий).
**Увага напрямку:** для CPL/CPA/CPC/frequency «вгору» = погано (червоний); для CTR/конверсій/ROAS «вгору» = добре (зелений). Не плутати знак дельти зі знаком користі.

---

## §D. Чек-ліст готовності звіту (прогнати перед видачею)

Скопійовано/звужено з еталона + META-PROMPT §9.8 + safety_rules:

- [ ] Кожна цифра має `⟦object_id · metric · period⟧` (жодного «голого» числа).
- [ ] `KNOWLEDGE` (через `[[...]]`) і `DATA` (через `⟦...⟧`) ніде не змішані й не видані одне за одне.
- [ ] Жоден об'єкт не осуджений на `<1000` показів / `<3` конв. / `<2` дні — інакше «недостатньо даних».
- [ ] Усі 9 секцій присутні; порожні явно позначені «недостатньо даних: потрібно `...`».
- [ ] Кардинальних — **рівно ≤3**, кожна з `expected_impact` у цифрах (арифметика, не «×3»).
- [ ] Інкрементальних — **5–10**, кожна з полями effort/impact/risk/success.
- [ ] Кожна рекомендація прив'язана до конкретного `campaign_id`/`adset_id`/`ad_id` + дія + поріг.
- [ ] Roadmap має **арифметичну** проєкцію, позначену як **гіпотеза** + умова перевірки.
- [ ] Data-gaps: ≥2 конкретні `breakdowns=...` / періоди / зовнішні джерела.
- [ ] Self-check: ≥5 «хибно, якщо…» + facts-table (факт→джерело→як перевірити).
- [ ] Прогнози позначені «Meta-claim», якщо це заяви Meta з UI, а не вимір акаунту.
- [ ] HTML (якщо обрано): темна тема, sticky toolbar, pills 🔥/✅/⚠️/❌, color-coded дельти, ~100–300 KB.
- [ ] Жодних реальних ключів/ID кабінетів/Word-контексту проекту (дистрибутив = generic, `act_XXX`).
- [ ] Звіт **нічого не змінює** в акаунті; дії — лише рекомендації для `/ads-optimizer`·`/campaign-manager` з підтвердженням.

---

## §E. SELF-CHECK самого шаблону (як перевірити/фальсифікувати придатність формату)

Цей playbook — інструмент; ось як зрозуміти, що він **не** виконує свою роль (і що тоді чинити):

1. **Формат хибний, якщо** наповнений ним звіт містить рекомендацію без `object_id` (напр. «покращити креативи») — тоді §2.3 (картка з `target_object`) не змусила прив'язку; підсилити чек-ліст §D і відхилити звіт.
2. **Формат хибний, якщо** агент пише число без `⟦маркера⟧` і це проходить — означає §2.1 не блокує; додати жорсткіший gate у guardrails (read-before-write фіксує, що число взято з Marketing API цієї сесії).
3. **Формат хибний, якщо** `KNOWLEDGE` видано за `DATA` (принцип Бена як «спостереження акаунту») — тоді §0.2 / §2.2 не розвели джерела; перевірити, що `[[...]]` і `⟦...⟧` ніколи не в одному твердженні як одне ціле.
4. **Формат хибний, якщо** прогноз у §4 не має арифметики («підніме ROAS ×3») — §2.4 не спрацювало; вимагати ланцюжок чисел акаунту + слово «гіпотеза».
5. **Формат хибний, якщо** об'єкт із `<1000` показів отримав вирок 🔥/❌ — поріг значущості (§0.3, §D) проігноровано; Volume Factor мав стягнути HS до 0 і змусити «відкласти рішення».
6. **Формат хибний, якщо** він суперечить `/ads-optimizer` (інша шкала HS, інші ліміти бюджету ±30%/−50%, інші ad-eater-пороги) — §3 не синхронізовано; звірити з `ads-optimizer/SKILL.md` і `safety_rules.md` і вирівняти.
7. **Формат хибний, якщо** тактики в рекомендаціях суперечать актуальній базі (напр. радить «дублювати адсети під аудиторії» — pre-Andromeda анти-патерн) — посилання `[[...]]` ведуть на застаріле; перевірити `era: post-andromeda` цільових knowledge-файлів ([[04-budget-scaling/big-spend-scaling]], [[01-structure/campaign-structure]], [[05-optimization/learning-phase]]).
8. **Як остаточно перевірити придатність:** дати готовий звіт незалежній людині й спитати «чи можеш сьогодні поставити в роботу ≥3 дії, не ставлячи уточнень?». Якщо ні — формат не виконав головний бар META-PROMPT §10, ітерувати.
