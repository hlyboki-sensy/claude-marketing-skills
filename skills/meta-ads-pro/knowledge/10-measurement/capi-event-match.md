---
topic: "Conversions API + Pixel + event match quality — як налаштувати точний трекінг (фундамент даних для AI)"
category: measurement
subcategory: capi-event-match
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
note: "НОВИЙ файл. Ядро теми — Pixel + CAPI + first-party cookies + event match quality — це наскрізна, підтверджена post-Andromeda ІСТИНА (data quality = паливо для AI; див. [[00-philosophy/andromeda-era]] → «правильно встановити CAPI, тримати high event match quality»). Усі 5 джерел тут — PRE-Andromeda (черв. 2024), але описують саме цей evergreen фундамент SETUP-у. Конкретні 2024-факти, що ВЖЕ застаріли (ретайр AEM, скасування обов'язкової верифікації домену) винесені у блок «Як було раніше». Tier B-відео (Apple 30% charge) підтверджує лише принцип «не бустити з застосунку»."
sources:
  - { id: 7DzaSOj7o4c, date: 2024-06-03, era: pre-andromeda }
  - { id: WazafPAYdOo, date: 2024-06-03, era: pre-andromeda }
  - { id: 9upmOIFQHRY, date: 2024-06-03, era: pre-andromeda }
  - { id: sifeq5bURzM, date: 2024-06-03, era: pre-andromeda }
  - { id: 9nzhm1nXtDo, date: 2024-06-03, era: pre-andromeda }
---

# Conversions API + Pixel + event match quality — точний трекінг як фундамент даних

## TL;DR
Точність трекінгу — фундамент усього: без неї і рекламодавець не бачить, що масштабувати/вимикати, і **machine learning Meta недоотримує паливо** для оптимізації. Базовий стек (evergreen, підтверджений post-Andromeda — див. [[00-philosophy/andromeda-era]], [[10-measurement/diagnostics]]): **(1) правильно встановити Pixel** + сконфігурувати **conversion events** (event setup tool / partner integration / плагін); **(2) увімкнути automatic Advanced Matching** (email/phone → кращий метч до людей у FB); **(3) увімкнути Conversions API** (другий канал даних, не залежний від браузера/iOS); **(4) тримати first-party cookies on** (бо third-party cookies відмирають). Перевіряти все через **Meta Pixel Helper** (Chrome) + звірку з бек-ендом/GA. ⚠️ Дві речі з цих відео 2024 ВЖЕ змінились: **aggregated event measurement (AEM) ретайрнуто**, **верифікація домену більше не обов'язкова** — Meta перенесла це «за лаштунки». Окремо (Tier B): **не бусти пост із застосунку FB на iOS** — Apple бере +30% service charge. ⟦WazafPAYdOo @2024-06-03⟧ ⟦7DzaSOj7o4c @2024-06-03⟧ ⟦9upmOIFQHRY @2024-06-03⟧ ⟦sifeq5bURzM @2024-06-03⟧ ⟦9nzhm1nXtDo @2024-06-03⟧

## Принципи [P]

### Навіщо трекінг (фундамент)
- [P] **Без Pixel кампанії «гарантовано проваляться».** Pixel — код на сайті/лендінгу, що трекає дії після кліку (purchase / lead). Він потрібен ДВІЧІ: (1) рекламодавцю — оцінити ROI, рішення scale/stop, порівняти ad A vs ad B на гранулярному рівні; (2) **Meta для оптимізації** — без Pixel вона «не знає, як виглядає purchase/lead», тож не може приносити більше таких. **Наскрізна теза, підтверджена post-Andromeda:** точні дані = паливо для AI-оптимізації (див. [[00-philosophy/andromeda-era]] «data helps AI perform better»). ⟦WazafPAYdOo @2024-06-03⟧
- [P] **Meta використовує безліч data points для оптимізації**, не лише факт конверсії: скільки показів знадобилось людині до покупки, о котрій годині купила, вік (42 / 38 / 26) тощо. Що повніші дані з Pixel/CAPI — то краще працює machine learning. ⟦WazafPAYdOo @2024-06-03⟧
- [P] **iOS 14.5 (~2021) обмежив трекінг дій на iOS-пристроях** після кліку → впала точність даних. Подвійний удар: (1) рекламодавцю важче оптимізувати (не видно, який ad дає які конверсії й ROAS); (2) **machine learning Meta теж недоотримує дані** для оптимізації навколо них. Саме звідси з'явились CAPI і (тимчасово) AEM. ⟦7DzaSOj7o4c @2024-06-03⟧ ⟦9upmOIFQHRY @2024-06-03⟧
- [P] **Privacy-обмеження лише наростатимуть** (EU-правила тощо) → роль CAPI лише зростатиме з часом. Це той самий «battle with regulators», через який data quality лишається сталою віссю переваги (див. [[00-philosophy/andromeda-era]]). ⟦7DzaSOj7o4c @2024-06-03⟧ ⟦sifeq5bURzM @2024-06-03⟧
- [P] **Точність не мусить бути ідеальною — має бути «схожою».** Дані в Events Manager не зобов'язані збігатися з Google Analytics точь-в-точь; достатньо, щоб вони були **близькими** — тоді знаєш, що сетап коректний. ⟦WazafPAYdOo @2024-06-03⟧

### Conversions API
- [P] **CAPI — «ще одна тятива до лука» (another string to your bow):** додатковий канал, що повертає важливі дані в акаунт, **не покладаючись лише на Pixel**, який на iOS ненадійний. Це не заміна Pixel, а **доповнення** до нього (Pixel усе одно потрібен). ⟦7DzaSOj7o4c @2024-06-03⟧ ⟦sifeq5bURzM @2024-06-03⟧
- [P] **CAPI треба налаштувати ВСІМ рекламодавцям Meta** — і дані йдуть на користь і рекламодавцю (точніші рішення), і Meta (краща AI-оптимізація, найкращі результати). **Наскрізна теза, підтверджена post-Andromeda:** правильно встановлений CAPI + high event match quality — «easy win», який навіть великі агенції часто не роблять (див. [[00-philosophy/andromeda-era]]). ⟦7DzaSOj7o4c @2024-06-03⟧
- [P] **CAPI зараз НАБАГАТО легше поставити, ніж раніше:** для більшості платформ це фактично **галочка** (checkbox) після встановлення Pixel — не обов'язково «технічно й складно». Складно стає лише на рівні ручного коду. ⟦7DzaSOj7o4c @2024-06-03⟧

### Cookies / Advanced Matching
- [P] **Відмирають лише third-party cookies — і це НЕ велика проблема для Meta-реклами.** Google прибирає 3rd-party cookies у Chrome (Chrome ≈60% search-користувачів); Safari (≈12%) зробив це роками раніше — і Meta-реклама працювала прибутково. Рішення: **Pixel на first-party cookies** збирає потрібні дані (purchase/lead), Meta все одно отримує їх для оптимізації. ⟦sifeq5bURzM @2024-06-03⟧
- [P] **Cookies корисні й для самих користувачів** (логін «запам'ятав мене», кошик зберігається), не лише для трекінгу — тому повністю вони не зникають; зникає саме *third-party* трекінг через пристрої/час. First-party лишаються. ⟦sifeq5bURzM @2024-06-03⟧
- [P] **Automatic Advanced Matching підвищує точність даних:** використовує дані, які клієнт сам надав бізнесу (email, phone), щоб точніше зматчити веб-події з людьми у FB. Рекомендується вмикати завжди. (Це прямий предок метрики **event match quality** post-Andromeda.) ⟦WazafPAYdOo @2024-06-03⟧ ⟦7DzaSOj7o4c @2024-06-03⟧
- [P] **Meta «вміє котитися з ударами» (roll with the punches).** Після iOS 14.5 вона перебудувала стек і тепер значно краще готова до privacy-змін. Якщо новий апдейт (як смерть 3rd-party cookies) виявиться болючішим, ніж очікувалось, — Meta, найімовірніше, вирішить це автоматично з часом, як уже було з AEM. (Той самий тон, що й pre-Andromeda прогноз в [[00-philosophy/andromeda-era]]: «iOS 14.5-масштабного удару більше не буде».) ⟦sifeq5bURzM @2024-06-03⟧

## Тактики зараз [T]

### Встановити Pixel (WordPress і не тільки)
- [T] **Знайти / створити Pixel:** Ads Manager → all tools → **Events Manager** → Data sources. ID видно в *data set ID* і під назвою Pixel зліва — скопіювати. Немає Pixel → зелена кнопка **Create**, далі Meta питає базову інфо про бізнес → отримуєш Pixel + ID. ⟦WazafPAYdOo @2024-06-03⟧
- [T] **WordPress:** plugins → add new → пошук «meta» → **Meta Pixel for WordPress** → install → activate → settings → Get started → залогінитись у FB-профіль → надати дозволи → перевірити business manager / FB page / (опц.) Instagram / **ad account** / **Pixel ID** → увімкнути **automatic Advanced Matching** → next. Це ставить **base code** Pixel (page views, custom audiences для ретаргету). ⟦WazafPAYdOo @2024-06-03⟧ ⟦7DzaSOj7o4c @2024-06-03⟧
- [T] **Налаштувати conversion events** (base code це ще не робить): Events Manager → **Add events** → Meta Pixel → **Event setup tool** → Open Event setup tool → ввести URL (напр. thank-you / confirmation page) → Open website → **Track a URL** (зазвичай надійніше за «track a button») → вибрати event (Lead / Purchase / …) → (опц.) value → Confirm. Тепер кожен, хто потрапляє на цей URL, тригерить подію. ⟦WazafPAYdOo @2024-06-03⟧
- [T] **Інші платформи (Shopify, WooCommerce, Kajabi …):** Events Manager → Add events → Add new integration → Meta Pixel → **Use partner integration** → обрати свою платформу → залогінитись/дати інфо. На Shopify conversion events (add to cart / purchase) часто **створюються автоматично** — все одно перевір, що вони на місці. ⟦WazafPAYdOo @2024-06-03⟧
- [T] **Немає твоєї платформи в інтеграціях / Pixel вшитий вручну в код:** якщо ти не технар — **найми когось** (Fiverr/Upwork) поставити правильно (недорого, зекономить головний біль). Самостійний ручний код Ben не радить чіпати нетехнічним людям. ⟦WazafPAYdOo @2024-06-03⟧ ⟦7DzaSOj7o4c @2024-06-03⟧

### Увімкнути Conversions API
- [T] **Через плагін/інтеграцію (WordPress «Meta for WordPress»):** після конекту проскролити до **Meta advanced configuration** → знайти **«Send website events to Meta using Conversions API»** → переконатися, що **галочка стоїть**. Інколи ввімкнено за замовчуванням, часто — ні; **завжди перевіряй вручну** і вмикай, інакше CAPI не працює. ⟦7DzaSOj7o4c @2024-06-03⟧
- [T] **На більшості платформ CAPI — це теж просто checkbox** (Shopify тощо) після того, як Pixel встановлено: «там десь буде галочка — знайди й увімкни». ⟦7DzaSOj7o4c @2024-06-03⟧
- [T] **Pixel вшито вручну кодом → CAPI хай ставить технар/розробник** (той, хто вшивав Pixel) або фрилансер — це over the head для нетехнічного рекламодавця. ⟦7DzaSOj7o4c @2024-06-03⟧
- [T] **Плагін буває buggy:** якщо конект не проходить — спробувати ще раз / інший браузер; плагін не foolproof, але коли працює — робить усе дуже просто. ⟦7DzaSOj7o4c @2024-06-03⟧

### First-party cookies + перевірка
- [T] **Увімкнути first-party cookies:** Events Manager → Data sources → обрати правильний Pixel → **Settings** (вгорі) → проскролити до **Website settings and cookie usage** → переконатися, що **first-party cookies = ON** (Edit, якщо ні). Більшість акаунтів мають це on за замовчуванням, але **бачили й вимкнені** — займає ~30 секунд, перевір. ⟦sifeq5bURzM @2024-06-03⟧
- [T] **Перевірити сетап через Meta Pixel Helper (Chrome extension):** Google → «meta pixel helper» → install (потрібен Chrome) → відкрити сторінку сайту → подивитись, чи є **base code** (page view) і чи тригеряться **conversion events**; **зелені галочки** = дані йдуть. Працює і для **шпигування за конкурентами** (чи стоїть у них Pixel / які events). → [[10-measurement/spying-competitors]]. ⟦WazafPAYdOo @2024-06-03⟧
- [T] **Звірити з бек-ендом за ~добу:** після сетапу зайти за день у Events Manager і перевірити, що дані схожі на інше джерело (Google Analytics тощо) — не точь-в-точь, але близько. ⟦WazafPAYdOo @2024-06-03⟧

### Не «зливати» 30% Apple
- [T] **НЕ бусти пост із застосунку Facebook на iOS** — з лют. 2024 Apple трактує це як in-app purchase і бере **+30% service charge** (Meta перекладає його на рекламодавця). Ти не отримуєш за ці 30% нічого (ні impressions, ні reach, ні лідів) — гроші йдуть Apple. ⟦9nzhm1nXtDo @2024-06-03⟧
- [T] **Як уникнути 30%:** запускати рекламу з **комп'ютера через Ads Manager** (рекомендовано — повна функціональність) або бустити з **браузера** (facebook.com / Meta Business Suite), не з iOS-застосунку. Charge виникає лише при оплаті *всередині* iOS-апа. ⟦9nzhm1nXtDo @2024-06-03⟧
- [T] **Якщо все-таки бустиш з апа** — **prepay** в акаунт через браузер (телефон/комп): тоді буст з iOS-застосунку йде з вже внесених коштів і не трактується як in-app purchase → без +30%. Все одно не основний рекомендований метод. ⟦9nzhm1nXtDo @2024-06-03⟧

## Числа / бенчмарки
| Факт | Значення | Джерело |
|---|---|---|
| iOS 14.5 (початок privacy-удару по трекінгу) | ~2021 (≈2.5–3 роки до відео 2024) | ⟦7DzaSOj7o4c⟧ ⟦9upmOIFQHRY⟧ |
| Apple service charge на буст із FB iOS-апа | +30% (з лют. 2024) | ⟦9nzhm1nXtDo⟧ |
| Chrome — частка search-користувачів | ~60% | ⟦sifeq5bURzM⟧ |
| Safari — частка search-користувачів (прибрав 3rd-party cookies роками раніше) | ~12% | ⟦sifeq5bURzM⟧ |
| Очікуване повне прибирання 3rd-party cookies у Chrome | Q3–Q4 2024 (прогноз) | ⟦sifeq5bURzM⟧ |
| AEM: ліміт web-подій (стара модель, тепер знято) | було 8 подій у priority order | ⟦9upmOIFQHRY⟧ |
| Звірка Events Manager vs GA | не точь-в-точь, має бути «схоже» | ⟦WazafPAYdOo⟧ |

> ⚠️ Числа часток браузерів і таймлайн прибирання cookies — **оцінки/прогнози Ben станом на черв. 2024**, не поточні заміри. «8 подій AEM» — параметр уже **ретайрнутої** моделі (нижче). Apple +30% — фактична політика з лют. 2024 (актуальна, поки Apple її тримає).

## Як було раніше і що змінилось

### Pre-Andromeda факти, що ВЖЕ застаріли (era: pre-andromeda)
> Контекст: відео 9upmOIFQHRY і WazafPAYdOo (черв. 2024, **до анонсу Andromeda груд. 2024**) фіксують момент, коли Meta **прибирала** пост-iOS-14.5 «милиці» трекінгу. Ці конкретні кроки сетапу **вже не потрібні** — Meta перенесла їхню функцію «за лаштунки» (узгоджується з post-Andromeda станом у [[00-philosophy/andromeda-era]]).
- ❌ Раніше (post-iOS-14.5, era: pre-andromeda): треба було вручну налаштувати **aggregated event measurement (AEM)** — список **8 conversion events у priority order**; на iOS-пристрої трекалась лише **найвища за пріоритетом** подія (зробив view→IC→add-to-cart→purchase, а бачиш тільки purchase). ⟦9upmOIFQHRY @2024-06-03⟧ ⟦superseded by 9upmOIFQHRY @2024-06-03⟧ — сам AEM ретайрнуто в цьому ж відео.
- ✅ Зараз: **AEM прибрано** з акаунтів («it's gone»); пріоритезувати web-події вручну й вибирати домен для iOS 14.5+ **більше не треба** — нічого робити. Ben прогнозував, що функцію AEM Meta **робитиме автоматично за лаштунками** (напр. подія, під яку оптимізуєш кампанію, сама стає top-priority), і що якість даних або не зміниться, або **покращиться** (особливо якщо динамічно). ⟦9upmOIFQHRY @2024-06-03⟧
- ❌ Раніше (era: pre-andromeda): обов'язкова **верифікація домену** (proof of ownership) — передумова, щоб конфігурувати conversion events і priority list. ⟦9upmOIFQHRY @2024-06-03⟧ ⟦WazafPAYdOo @2024-06-03⟧ ⟦superseded by 9upmOIFQHRY @2024-06-03⟧
- ✅ Зараз: верифікація домену **не обов'язкова** (Ben усе ще *рекомендує* зробити з інших причин, але як передумова трекінгу — вже ні). Це **game-changer для конверсій через third-party домени** (вебінар-софт, Amazon тощо), де домен тобі не належить: тепер їх можна трекати без верифікації. ⟦9upmOIFQHRY @2024-06-03⟧ ⟦WazafPAYdOo @2024-06-03⟧
- ✅ Незмінне ядро (corroboration, evergreen): **Pixel + conversion events лишаються обов'язковими**; CAPI потрібен усім; Advanced Matching і first-party cookies — вмикати. Це той самий фундамент data quality, що його post-Andromeda матеріали називають сталою віссю переваги. ⟦WazafPAYdOo @2024-06-03⟧ ⟦7DzaSOj7o4c @2024-06-03⟧ ⟦sifeq5bURzM @2024-06-03⟧ → [[00-philosophy/andromeda-era]] · [[10-measurement/diagnostics]]
- ⚠️ Загальний вектор: post-iOS-14.5 «милиці» (AEM, ручна верифікація домену, ручний priority list) Meta **знімає й автоматизує** — той самий рух «забрати ручне керування за лаштунки», що його Andromeda довела до персоналізації доставки на рівні індивіда. Тому сьогодні фокус зміщено з «налаштувати AEM/домен» на **якість сигналу** (CAPI, event match quality, повнота конверсійних даних) і **ширші атрибуційні вікна** (engage-through, view-through 1d) → [[00-philosophy/andromeda-era]]. ⟦9upmOIFQHRY @2024-06-03⟧

## Помилки / anti-patterns
- ❌ **Запускати трафік без Pixel / без conversion events** — кампанії «гарантовано провалюються»: ні рекламодавець, ні Meta не бачать, що таке конверсія. ⟦WazafPAYdOo @2024-06-03⟧
- ❌ **Покладатися лише на Pixel без CAPI** — на iOS Pixel-дані ненадійні; CAPI — другий канал, що повертає дані; ставити треба всім. ⟦7DzaSOj7o4c @2024-06-03⟧
- ❌ **Вважати галочку CAPI ввімкненою «за замовчуванням»** і не перевірити — часто вона ВИМКНЕНА; без неї CAPI не працює. Завжди перевіряти вручну (Meta advanced configuration). ⟦7DzaSOj7o4c @2024-06-03⟧
- ❌ **Не перевірити first-party cookies** — бачили акаунти, де вимкнено; з відмиранням 3rd-party cookies це ламає збір даних. 30 секунд на перевірку. ⟦sifeq5bURzM @2024-06-03⟧
- ❌ **Не увімкнути automatic Advanced Matching** — втрачаєш точність метчу веб-подій до людей у FB (предок event match quality). ⟦WazafPAYdOo @2024-06-03⟧
- ❌ **Панікувати через «смерть cookies»** — стосується лише third-party; first-party cookies + CAPI закривають потребу, Meta-реклама працює (Safari прибрав їх давно — і нічого). ⟦sifeq5bURzM @2024-06-03⟧
- ❌ **Бустити пост із застосунку FB на iOS** — Apple бере +30% ні за що; запускай з комп'ютера/браузера (або prepay). ⟦9nzhm1nXtDo @2024-06-03⟧
- ❌ **Нетехнічному рекламодавцю лізти в ручний код Pixel/CAPI** — краще плагін/partner integration або найняти фрилансера, ніж зламати сетап. ⟦WazafPAYdOo @2024-06-03⟧ ⟦7DzaSOj7o4c @2024-06-03⟧
- ❌ **Очікувати ідеального збігу Events Manager з GA** — має бути «схоже», не точь-в-точь; вимога точної рівності веде в нікуди. ⟦WazafPAYdOo @2024-06-03⟧

## Застосування в аналізі/оптимізації
- **Аудит трекінгу (перший крок будь-якого аудиту даних):** перевірити через Pixel Helper, що (1) base Pixel стоїть, (2) conversion events тригеряться зеленим, (3) CAPI-галочка ввімкнена, (4) first-party cookies on, (5) Advanced Matching on. Брак будь-чого — пріоритетна рекомендація, бо без точних даних усі подальші висновки ненадійні. → [[10-measurement/diagnostics]].
- **«0 конверсій / дивні цифри»:** перш ніж винуватити креатив/офер — звірити, чи коректно надходять події (Pixel Helper + звірка з бек-ендом/GA «схоже, не точно»). Engagement-bait, що не продає, — це не «вина трекінгу», а брак конгруентності ad↔лендінг → [[10-measurement/diagnostics]] · [[08-landing-cvr/landing-best-practices]].
- **Конверсії на third-party домені** (вебінар-софт, маркетплейс): нагадати, що верифікація домену **більше не потрібна** — їх можна трекати; головне — Pixel/CAPI-сигнал. ⟦9upmOIFQHRY⟧
- **Перед масштабуванням / на великих бюджетах:** точний трекінг — передумова; на мульти-канальних бізнесах Meta переоцінює/недооцінює свою роль → додатково сторонній трекінг (Hyros-клас). → [[04-budget-scaling/big-spend-scaling]].
- **Недозвіт через «безклікові» покупки / довгий цикл:** CAPI + event match quality + ширші атрибуційні вікна (view-through 1d) — щоб дати Meta більше повних конверсійних даних (паливо для AI). → [[00-philosophy/andromeda-era]].
- **Якщо клієнт бустить з телефону** — перевести на Ads Manager з комп'ютера (і функціональність, і економія 30% Apple).
- Зв'язок: [[00-philosophy/andromeda-era]] · [[10-measurement/diagnostics]] · [[10-measurement/spying-competitors]] · [[00-philosophy/industry-news]] · [[04-budget-scaling/big-spend-scaling]] · [[08-landing-cvr/landing-best-practices]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "Without it your campaigns are guaranteed to fail." — Ben Heath (про Pixel) ⟦WazafPAYdOo @2024-06-03⟧ (pre-andromeda)
> "The conversions API… gives you another string to your bow." — Ben Heath ⟦7DzaSOj7o4c @2024-06-03⟧ (pre-andromeda)
> "It's a lot easier to set up now than it used to be." — Ben Heath (про CAPI) ⟦7DzaSOj7o4c @2024-06-03⟧ (pre-andromeda)
> "Aggregated event measurement is being retired. It's gone." — Ben Heath ⟦9upmOIFQHRY @2024-06-03⟧ (pre-andromeda)
> "This basically takes us back to where we were pre-iOS 14.5." — Ben Heath ⟦9upmOIFQHRY @2024-06-03⟧ (pre-andromeda)
> "You don't need to use third party cookies… make sure your meta pixel is set up to use first party cookies." — Ben Heath ⟦sifeq5bURzM @2024-06-03⟧ (pre-andromeda)
> "Meta is much better at dealing with changes… they roll with the punches." — Ben Heath ⟦sifeq5bURzM @2024-06-03⟧ (pre-andromeda)
> "Avoid the Apple service charge… don't boost in the Facebook iOS app." — Ben Heath ⟦9nzhm1nXtDo @2024-06-03⟧ (pre-andromeda)
