---
topic: "Вибір campaign objective у Meta Ads — який і коли"
category: objectives
subcategory: choosing-objective
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: -6okjIwMmmU, date: 2025-06-03, era: post-andromeda }
  - { id: ZiidV7nzUbs, date: 2024-06-03, era: pre-andromeda }
  - { id: ppM54Wti08I, date: 2023-06-03, era: pre-andromeda }
---

# Вибір campaign objective у Meta Ads — який і коли

## TL;DR
Campaign objective визначає, **під що Meta оптимізує** кампанію, і змінює дефолти на всіх наступних кроках — помилка тут майже гарантовано вбиває кампанію. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧ За замовчуванням бери **Sales** або **Leads** — у ~85% випадків саме вони дають найкращий результат. ⟦-6okjIwMmmU @2025-06-03⟧ Правило вибору між ними: **оптимізуй під дію, що найдалі по воронці і яку можеш ТОЧНО трекати** (з урахуванням attribution window ≤7 днів). Traffic / Engagement / Awareness / App promotion — нішеві, вживаються рідко. Не «переграй систему» псевдо-objective + не зіпсуй усе неправильним **performance goal**. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧

## Принципи [P]
- [P] **Objective = як Meta оптимізує кампанію.** Він диктує оптимізацію доставки і змінює купу дефолтів/пресетів на наступних кроках створення — тому впливає на результат величезно. Помилився з objective → кампанія майже точно не злетить. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [P] **Будь прямим: оптимізуй під те, що реально хочеш.** Хочеш продажі — бери Sales; хочеш ліди — бери Leads. Не йди манівцями через «дешевший» трафік/енгейджмент в надії, що люди «дойдуть» до конверсії самі. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [P] **Трекай дію, що найдалі по воронці і яку можеш точно виміряти.** Можеш надійно трекати продаж → Sales; не можеш → Leads. Lead — цілком ОК, якщо продаж не трекається. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [P] **Враховуй attribution window (макс 7 днів після кліку).** Якщо шлях lead→sale довгий (дзвінок, пропозиція, оплата за тижні) — продаж випадає з вікна атрибуції і важко звʼязати клік з конверсією через офлайн-проміжні кроки. Тому для довгих B2B/сервісних циклів оптимізуй під Leads, не Sales. ⟦-6okjIwMmmU @2025-06-03⟧
- [P] **Не «грай проти системи».** Стара школа «оберу Traffic замість Sales, бо Meta не дасть мені продажі» — застаріла; на сучасній платформі це майже завжди гірший результат. Meta фінансово зацікавлена дати тобі ліди/продажі — бо тоді ти спендиш більше (рекламодавець — клієнт Meta, не юзер). Споріднено: [[00-philosophy/andromeda-era]]. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [P] **Performance goal може звести нанівець правильний objective.** Якщо під Leads/Sales обрати goal типу *maximize landing page views / link clicks* — кампанія поведеться як Traffic; *maximize daily unique reach / impressions* — як Awareness. Тобто правильний objective + неправильний goal = зіпсований результат. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧ ⟦ppM54Wti08I @2023-06-03⟧
- [P] **Objective лише ЗВУЖУЄ список того, під що можна оптимізувати; реально оптимізує — performance goal (optimization for ad delivery).** Дві кампанії з різними objective (Sales vs Traffic), але однаковим performance goal (напр. landing page views) Meta оптимізує **ідентично** і дають однаковий результат. Objective + conversion location лише формують **перелік** доступних goals; машинне навчання Meta керується саме обраним goal. Тому «я кручу Sales/conversions кампанію» нічого не значить, якщо goal стоїть landing page views — це фактично Traffic-кампанія. ⟦ppM54Wti08I @2023-06-03⟧
- [P] **Conversion location теж змінює перелік доступних performance goals.** Зміна destination (website → Messenger) відкриває інші goals (напр. *conversations* замість *conversions*). Тобто перелік goals = функція (objective × conversion location). ⟦ppM54Wti08I @2023-06-03⟧

## Тактики зараз [T]

### Дефолтний вибір
- [T] **За замовчуванням — Sales або Leads.** Це objectives, які вживаються частіше за всі інші «by far». ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Sales** — коли можеш точно трекати продаж: e-commerce; деякі сервісні бізнеси, де весь шлях lead→sale швидкий і повністю онлайн в один захід; продаж квитків на івент (якщо трекаєш purchase). ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Leads** — коли продаж трекати важко або цикл довгий (напр. реклама агенції/сервісу: лід → дзвінок → пропозиція/візит/quote → оплата за тижні поза онлайн-кліком). Ліди можна збирати **на сайті** або **в інстант-формах** просто в Facebook/Instagram (без переходу на сайт) — інстант-форми часто дають **дешевші ліди**. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Для Leads/Sales обовʼязково встанови Meta pixel** — без трекінгу цих дій objective не спрацює як треба. ⟦ZiidV7nzUbs @2024-06-03⟧

### Performance goal
- [T] **Лишай дефолтний performance goal** — у більшості випадків усе буде ОК. Для Leads/Sales дефолт = *maximize number of conversions* — саме те, що треба. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Maximize value of conversions** — якщо налаштований трекінг цінності (різні ліди/продажі коштують по-різному і ця інфа віддається в акаунт через pixel): Meta дасть не лише максимум конверсій, а й дорожчі для бізнесу. Працює і для Sales, і для Leads. ⟦-6okjIwMmmU @2025-06-03⟧
- [T] **Не чіпай решту goals** (*landing page views / link clicks / daily unique reach / impressions*) — вони перетворюють Leads/Sales на Traffic/Awareness. Винятки «extremely rare». ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ppM54Wti08I @2023-06-03⟧

### Нішеві objectives (вживай рідко, лише у конкретних сценаріях)
- [T] **Traffic** — лише коли: (а) женеш на блог-пост і потрібно тільки споживання контенту без подальшої дії; (б) на Instagram-профіль (нарощування підписників або «Instagram profile method» — профіль як квазі-лендінг із pinned posts і story highlights); (в) на **сторонній сайт без власного контролю**, де неможливо поставити Meta pixel / трекати дію. Не використовувати для продажів/лідів. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Engagement** — лише коли: будуєш Facebook-аудиторію (Facebook page як destination для підписників), будуєш Facebook-групу (доступно не у всіх акаунтах), поглиблюєш стосунки з наявними фоловерами, або fringe-кейс конкурсного оголошення, де ціль — багато «шуму»/активності. Прийом «спершу набити followers/social proof на сторінці, щоб виглядати credible, а потім рекламувати» — допустимий швидкий розгін перед основними кампаніями. Інакше — занадто непрямий шлях. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Awareness** — для дуже великих брендів з великими бюджетами без потреби в коротко/середньостроковому ROAS (top-of-mind: авто, soft drinks типу Coca-Cola). Малому бізнесу — уникати. Виняток: **omnipresent content strategy** для high-ticket продуктів/послуг (працює завдяки **frequency capping**; типово на warm-аудиторію місяцями). ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **App promotion** — якщо є застосунок: дає app installs, а також **app events** (напр. in-app purchases — таргетувати наявних юзерів, щоб довести до premium). ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧

### Conversion location (Leads)
- [T] **При Leads дефолтний conversion location — instant forms** (лід лишається в FB/IG, заповнює форму). Доступні також: website / landing page, Messenger, чат в Instagram. Це не «лише сайт», як думають новачки. ⟦ZiidV7nzUbs @2024-06-03⟧ Глибше про вибір instant form vs website → [[02-objectives/leads-vs-sales-vs-traffic]].

### Експлуатаційні правила
- [T] **Objective існуючої кампанії змінити НЕ можна** — лише перестворити кампанію з новим objective. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- [T] **Не дублюй кампанію, щоб змінити objective перед запуском** — дублікат тягне налаштування під старий objective, а нові дефолти (на рівні адсету/оголошення) можуть «поламатись» і завадити коректному показу. Краще перестворити з нуля. ⟦ZiidV7nzUbs @2024-06-03⟧

## Числа / бенчмарки
| Параметр | Значення | Джерело |
|---|---|---|
| Частка, коли Sales/Leads дають кращий результат (опитування аудиторії Ben Heath на YouTube) | ~80–85% ⟦-6okjIwMmmU⟧ / «80–90%» в раніших матеріалах ⟦ZiidV7nzUbs⟧ | ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧ |
| Максимальне attribution window | 7 днів після кліку | ⟦-6okjIwMmmU @2025-06-03⟧ Meta-claim |
| Дефолтний performance goal для Leads/Sales | maximize number of conversions | ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧ |
| К-сть «робочих» objectives на практиці (Sales+Leads) | 2 (з 6 доступних) | ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧ |
| Приріст конверсій: conversions-goal vs traffic-goal (той самий бюджет) | +74% конверсій | ⟦ppM54Wti08I @2023-06-03⟧ Meta-stat, ODAX-епоха |

> ⚠️ 7-денне attribution window — параметр платформи Meta (Meta-claim), не незалежний замір.
> ⚠️ ~80–85% (і «80–90%» у раніших відео) — це самоопитування підписаної аудиторії одного каналу, не репрезентативна вибірка ринку.
> ⚠️ +74% конверсій (conversions vs traffic, той самий бюджет) — «official stat», який Ben отримав від Meta в ODAX-епоху (2023). Це Meta-claim до Andromeda, не сучасний незалежний замір; ілюструє масштаб впливу правильного performance goal, а не точне число на сьогодні.

## Як було раніше і що змінилось
- ❌ Раніше (стара школа): обирати Traffic/Engagement замість Sales/Leads, щоб «обхитрити» Meta й здешевити трафік, очікуючи, що користувачі самі дойдуть до конверсії. Ben був скептичний до цього і раніше, але багато рекламодавців так робили. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧ (era: pre-andromeda — те саме застереження звучало вже у 2024)
- ✅ Зараз: платформа Meta набагато краще оптимізує під реальну ціль — обирай objective, що прямо відповідає бажаній дії (Sales/Leads), і довіряй оптимізації. Псевдо-objective майже завжди дає гірший результат. ⟦-6okjIwMmmU @2025-06-03⟧
- ℹ️ Логіка «спершу Awareness, потім Sales далі по воронці» інтуїтивно приваблива, але на практиці для малого/середнього бізнесу не працює — веде до objective без короткострокового ROAS. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- ⚠️ **Pre-Andromeda теза «campaign objectives don't matter anymore — важить лише optimization for ad delivery setting»** ⟦ppM54Wti08I @2023-06-03⟧ — це ODAX-епоха (2023), коли акцент змістили на performance goal. Evergreen-ядро тези справедливе й досі (objective без правильного goal нічого не дає → див. [P] вище). Але **формулювання «objective байдужий» застаріло** для сучасної платформи: post-Andromeda objective задає не лише перелік goals, а й цілий каскад дефолтів/пресетів на адсет- та ad-рівні (таргетинг, плейсменти, формати), тож впливає «величезно». ⟦superseded by -6okjIwMmmU @2025-06-03⟧ Практичний висновок незмінний: завжди звіряй **і** objective, **і** performance goal.
- ⚠️ Ще pre-Andromeda (2023) фіксувалося, що **Meta-репи й сама платформа підштовхують ставити landing page views** (особливо новим акаунтам без conversion-даних), бо це наповнює колонку «results» гарними числами й переконує рекламодавця, що він «щось отримав» → спендити більше. Це досі anti-pattern: ти думаєш, що крутиш conversions-кампанію, а фактично — traffic. ⟦ppM54Wti08I @2023-06-03⟧ ⟦-6okjIwMmmU @2025-06-03⟧

## Помилки / anti-patterns
- ❌ **Старт із Traffic «бо легко»** (не треба pixel, просто встав лінк). Поширений старт новачків, але рідко доречний — Meta поставить оголошення перед тими, хто радше **клікне**, а не купить/залишить лід. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- ❌ **Старт із Engagement «бо хочу багато лайків/переглядів»**. Meta нагенерує енгейджменту, але не наступного кроку (продаж/лід). Енгейджмент звучить добре, та для більшості рекламодавців — хибна ціль. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- ❌ **Малий бізнес на Awareness** в надії на близький ROAS — це формат великих брендів, не для прямих лідів/продажів. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- ❌ **Зіпсувати performance goal** після правильного objective: обрати landing page views / link clicks (→ поводиться як Traffic) або daily unique reach / impressions (→ як Awareness). ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ppM54Wti08I @2023-06-03⟧
- ❌ **Думати, що крутиш «conversions/sales-кампанію», коли performance goal = landing page views.** Назва objective не значить нічого без правильного goal — це фактично Traffic-кампанія, хоч і називається Sales. ⟦ppM54Wti08I @2023-06-03⟧
- ❌ **Слухати Meta-репа, який радить landing page views** для нового акаунта «бо мало conversion-даних» — наповнює results-колонку, але не дає реальних конверсій. ⟦ppM54Wti08I @2023-06-03⟧
- ❌ **«Гейміти» систему** псевдо-objective (Traffic заради лінк-кліків в надії на конверсії) — застарілий підхід, майже завжди гірший результат. ⟦-6okjIwMmmU @2025-06-03⟧ ⟦ZiidV7nzUbs @2024-06-03⟧
- ❌ **Оптимізувати під Sales за довгого офлайн-циклу**, де продаж випадає з 7-денного вікна атрибуції і не звʼязується з кліком → краще Leads. ⟦-6okjIwMmmU @2025-06-03⟧
- ❌ **Дублювати кампанію й міняти objective на льоту** — ламає налаштування під старий objective; перестворюй з нуля. ⟦ZiidV7nzUbs @2024-06-03⟧

## Застосування в аналізі/оптимізації
- **Аудит кампанії:** першим ділом звірити objective з бізнес-ціллю. Traffic/Engagement/Awareness під кампанію, де ціль — продажі/ліди → червоний прапор, рекомендувати перестворення на Sales/Leads (objective не міняється на льоту).
- **Звірка performance goal (часто головна знахідка):** під Leads/Sales має стояти *maximize number of conversions* (або *value*, якщо є value-трекінг). Якщо стоїть link clicks / landing page views / reach / impressions → прапор «objective знівельовано performance goal» — кампанія де-факто Traffic/Awareness, попри назву. ⟦ppM54Wti08I⟧
- **Sales vs Leads під клієнта:** перевірити довжину циклу і якість трекінгу проти 7-денного attribution window; довгий B2B/сервісний цикл → Leads; швидкий онлайн-чекаут/e-commerce → Sales.
- **Інстант-форми vs сайт для лідів:** якщо ціна ліда висока і трекінг конверсії на сайті слабкий — тест інстант-форм (часто дешевші ліди). Деталі вибору → [[02-objectives/leads-vs-sales-vs-traffic]].
- **Звʼязок:** [[00-philosophy/andromeda-era]] · [[00-philosophy/how-delivery-works]] · [[01-structure/campaign-structure]] · [[02-objectives/leads-vs-sales-vs-traffic]] · [[05-optimization/optimization-events]] · [[05-optimization/learning-phase]] · [[09-retargeting/omnipresent-content]] · [[04-budget-scaling/big-spend-scaling]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "If you get this wrong your campaigns are highly unlikely to succeed." — Ben Heath ⟦-6okjIwMmmU @2025-06-03⟧
> "Track the action that is furthest along your sales funnel that you can accurately track." — Ben Heath ⟦-6okjIwMmmU @2025-06-03⟧
> "Please don't try and be extra clever and game the system." — Ben Heath ⟦-6okjIwMmmU @2025-06-03⟧
> "You can undo a lot of the good work… by selecting the wrong performance goal." — Ben Heath ⟦-6okjIwMmmU @2025-06-03⟧
> "If you want leads go for leads, if you want sales go for sales." — Ben Heath ⟦ZiidV7nzUbs @2024-06-03⟧
> "It is the optimization for ad delivery setting that dictates how your campaign is going to be optimized." — Ben Heath ⟦ppM54Wti08I @2023-06-03⟧
> "Don't let anyone tell you… you are running a conversions campaign… if you're optimizing for landing page views — you are not." — Ben Heath ⟦ppM54Wti08I @2023-06-03⟧
> "The official stat… is 74% more [conversions], same budget." — Ben Heath ⟦ppM54Wti08I @2023-06-03⟧
