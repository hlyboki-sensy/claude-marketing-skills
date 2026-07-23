---
topic: "Optimization & delivery-контроль: frequency control (target vs cap), ad sequencing, site links"
category: optimization
subcategory: optimization-events
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: 3qpLGAuvDAA, date: 2025-06-03, era: post-andromeda }
  - { id: pJfYdXzSG_M, date: 2025-06-03, era: post-andromeda }
  - { id: 5QlJLlhltxw, date: 2025-11-03, era: post-andromeda }
  - { id: FOC1SJCbQbw, date: 2023-06-03, era: pre-andromeda }
  - { id: 6iZZzwtTDDY, date: 2024-06-03, era: pre-andromeda }
---

# Optimization & delivery-контроль (frequency / sequencing / site links)

## TL;DR
Три delivery-фічі, що дають рекламодавцю більше контролю над тим, **скільки разів**, **у якому порядку** і **куди саме** Meta веде покази. (1) **Frequency control** — нова логіка частоти з вибором **target vs cap**: target цілиться в *середню* частоту (дозволяє показати «гарячим» трохи більше), у більшості випадків кращий за жорсткий cap. Перенесена з reservation у **auction**, спершу в awareness, тестується на engagement, очікувано піде на sales/leads (це і буде game-changer). Потребує **lifetime budgets** + кампанію довшу за 7 днів. (2) **Ad sequencing** — доставка оголошень у заданому порядку (storytelling/customer journey); теж переноситься з reservation в auction для **awareness/engagement**, потребує adset budgets + frequency controls + **lifetime budgets**. Найкращий юзкейс — omnipresent content. (3) **Site links** — додаткові посилання під оголошенням (як у Google Ads); піднімають CTR (рання data Ben) і ймовірно CVR; об'єктиви traffic/engagement/leads/sales, лише Facebook feed, для sales треба вимкнути catalog. ⟦3qpLGAuvDAA @2025-06-03⟧ ⟦5QlJLlhltxw @2025-11-03⟧ ⟦pJfYdXzSG_M @2025-06-03⟧ Наскрізна гігієна (evergreen, підтверджена pre-Andromeda): кожен **auto-enabled delivery/optimization-дефолт** Meta треба оцінити «на користь тобі чи Meta?» і за потреби повернути контроль — як з pre-Andromeda **«optimize text per person»** (auto-on, вимикач схований за standard enhancements), так і з нинішнім frequency-дефолтом (cap замість оптимальнішого target). ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧

## Принципи [P]
- [P] **Frequency = середня к-сть показів одній людині.** Високий frequency корисний для **великих/складних рішень** (треба багато переконувати, додавати proof/testimonials); для **імпульсних/безкоштовних/дешевих** оферів краще «розмазати» покази тонше по більшій аудиторії, бо повторні покази тим, хто вже сказав «ні», — злив бюджету. ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Платиш за impressions (за очі).** Ті самі покази можна сконцентрувати на малій к-сті людей (вони бачать рекламу знову й знову) або розподілити тонше на більшу к-сть — це стратегічний вибір під тип оферу. ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Поширена скарга: Meta надто швидко нарощує frequency** — бере меншу частку аудиторії і б'є по ній повторно, замість рівномірного розподілу impressions. Frequency-контроль — спосіб це стримати. ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Target краще за cap у більшості випадків.** Cap — жорстка стеля («не більше N разів»). Target — ціль по *середньому*: дозволяє Meta показати трохи більше тим, хто активно залучається/клікає/майже конвертнув, і вирівняти решту → зазвичай кращий результат. ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Frequency-контроль у awareness — корисно, але НЕ game-changer.** Справжній прорив — коли його додадуть до **sales/leads** (об'єктиви, де живе більшість рекламодавців): тоді можна стримувати ре-таргет Advantage+ продуктів і змусити Meta виходити на холодні аудиторії. ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Frequency-cap у sales/leads вирішує ключову проблему Advantage+** — що він надто агресивно ре-таргетить і ллє забагато бюджету в warm-аудиторії. Cap/target змушує Meta, вичерпавши ліміт на warm-людях, переходити на cold → фокус на **new customer acquisition**. ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Ad sequencing = контроль над customer journey.** Замість «довірити Meta показати щось випадково» рекламодавець веде проспекта по етапах: value → demonstration → testimonial → call-to-action. Природно лягає на storytelling. ⟦5QlJLlhltxw @2025-11-03⟧
- [P] **Перенесення фічі з reservation у auction = велика подія.** Reservation buying type Ben радить лише дуже великим бізнесам (порівняння з HR-департаментом: малому бізнесу — спосіб злити багато грошей); тож фічі, доступні *тільки* там, не мали значення. Auction — де живе переважна більшість рекламодавців і їхній бюджет. ⟦5QlJLlhltxw @2025-11-03⟧ ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Omnipresent content працює В ЧАСІ і вимагає терпіння/віри, не data.** На старті ще немає цифр — треба вірити, що спрацює за 6+ міс; «нерді-маркетологи» з цим борються найбільше. Підходить бізнесам, де треба багато переконувати: експертні послуги (coaching/consulting/info) і будь-що дорожче ~$1000, де прямий продаж важкий. ⟦5QlJLlhltxw @2025-11-03⟧
- [P] **Site links дають більше контролю над тим, КУДИ клікають.** Людина може піти не на головний destination, а на релевантний підрозділ (case studies / done-for-you / testimonials / who-we-work-with). Більше опцій + точніший збіг із наміром → більше кліків і вища ймовірність конверсії. ⟦pJfYdXzSG_M @2025-06-03⟧
- [P] **Meta часто додає фічі, що вже працюють у Google Ads.** Site links у Google існують давно і доведено працюють (більше кліків + конверсій) — те, що Meta їх копіює, добрий сигнал. ⟦pJfYdXzSG_M @2025-06-03⟧
- [P] **Лінкуй туди, де в тебе competitor advantage / зняття заперечення.** Веди site link на те, що *переконує перед дією*: гарна гарантія/warranty, refund policy (якщо вона — selling point), reviews, portfolio, «з ким працюємо». Думай про інфо, яку проспект хоче *до* покупки. ⟦pJfYdXzSG_M @2025-06-03⟧
- [P] **Рання наявність фічі (ще не в усіх акаунтах) = competitive advantage.** Meta роллаутить нове частинами; хто отримав site links / frequency control / ad sequencing раніше — має перевагу при «limited downside». ⟦pJfYdXzSG_M @2025-06-03⟧ ⟦5QlJLlhltxw @2025-11-03⟧
- [P] **Кожну delivery/optimization-фічу, яку Meta вмикає за замовчуванням, треба оцінити: вона служить тобі чи Meta?** Наскрізна теза, підтверджена pre-Andromeda: коли Meta «дуже хоче», щоб ти щось зробив (хитрий дефолт, friction проти ручного контролю), став питання — це бо ти отримаєш кращий результат і лишишся на платформі (тоді Meta теж заробляє → добра рекомендація), чи бо це вигідно Meta у короткому горизонті? Інколи перше, інколи друге. Цей самий фільтр Ben застосовував і до post-Andromeda frequency-дефолту (cap замість target), і до pre-Andromeda «optimize text per person». ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧ ⟦3qpLGAuvDAA @2025-06-03⟧
- [P] **Meta дедалі автоматизує/забирає контроль на користь новачків — просунутий рекламодавець має вертати контроль там, де це важливо.** Платформа «катує до beginners»: прибирає кастомізацію/специфіку, бо новачок із багатьма ручними налаштуваннями частіше зробить усе неправильно. Для будь-кого, хто вийшов за стадію повного початківця (тобто більшості), частину цих авто-фіч треба свідомо вимикати. **Наскрізна теза, підтверджена і pre-, і post-Andromeda** (детальні драйвери — у [[00-philosophy/andromeda-era]]). ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧
- [P] **Якщо вся гнучкість зрізана — «усі отримують однаковий результат» і вигравати ніде.** Meta-реклама — конкурентний marketplace: щоб бачити добрі результати, треба робити краще за інших рекламодавців. Коли інструменти забирають кастомізацію, ринок гомогенізується; перевагу зберігає той, хто знає, як зайти й повернути контроль (вимкнути зайве, зробити оголошення так, як хоче). ⟦FOC1SJCbQbw @2023-06-03⟧
- [P] **«Optimize text per person» (= text improvements) переставляє твої primary text / headline / description місцями на рівні індивіда.** Для повного новачка прийнятно (він просто вписав хороше про продукт — нехай Meta тасує); для просунутого — небезпечно: headline у слоті primary text (і навпаки), а description (часто call-to-action типу «click here to claim your free offer») у headline до того, як людина щось знає про оголошення, — ламає сенс і flow. ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧
- [P] **Кілька варіантів primary text / headline / description (до 5) ≠ optimize text per person.** Завести по кілька опцій і дати Meta тестувати їх — корисно (тест різних хедлайнів/текстів без купи окремих оголошень). Шкідливе саме **автоматичне перекидання написаного між слотами**. Не плутати ці дві речі. ⟦FOC1SJCbQbw @2023-06-03⟧

## Тактики зараз [T]

### Frequency control (target vs cap)
- [T] **Де:** awareness-кампанія → рівень adset → блок **Frequency control** (раніше називався Frequency cap). За замовч. Meta ставить cap «2 times every 7 days». ⟦3qpLGAuvDAA @2025-06-03⟧
- [T] **Увімкнути target (а не cap):** опція target сіра, поки не переключиш daily → **lifetime budgets** і кампанію довшу за **7 днів** (Meta дефолтить на місяць). Тоді обираєш target → к-сть impressions (1/2/3…) за період. ⟦3qpLGAuvDAA @2025-06-03⟧
- [T] **Підбір частоти — під офер, без універсального числа.** Sale на 3–7 днів → розмазати тонко (напр. **1 impression / 7 днів** або **1 / 3 дні** для 3-денного sale), щоб охопити максимум warm-аудиторії. Складніший офер → вища частота (більше переконувати). ⟦3qpLGAuvDAA @2025-06-03⟧
- [T] **Юзкейси, де frequency-cap у sales/leads замінить awareness:** flash-sales (3–7 днів), limited-time offers, анонс нового продукту — раніше для frequency-cap доводилось крутити awareness; коли cap дійде в sales/leads, ці кампанії краще робити одразу на sales/leads. ⟦3qpLGAuvDAA @2025-06-03⟧
- [T] **Бути вибірковим:** cap/target ставити лише там, де треба «розмазати» (limited-time offers, новий продукт); для звичайних evergreen-кампаній frequency-контроль не обов'язковий. ⟦3qpLGAuvDAA @2025-06-03⟧

### Ad sequencing (порядок показів)
- [T] **Де (auction):** кампанія з об'єктивом **awareness або engagement** → рівень adset → блок **Ad sequencing** («Deliver your ads in a specific order…»). У reservation був давно; news — перенесення в auction. ⟦5QlJLlhltxw @2025-11-03⟧
- [T] **Критерії доступності ad sequencing (auction):** (1) об'єктив awareness/engagement (НЕ sales/leads — поки); (2) **adset budgets** (не campaign budgets); (3) увімкнені **frequency controls** (напр. 1 impression / 7 днів); (4) **lifetime budgets** (головна зміна від дефолтів). ⟦5QlJLlhltxw @2025-11-03⟧
- [T] **Класична послідовність:** value → demonstration → testimonial → call-to-action (4 «відра» оголошень). Дати Meta секвенсувати їх по customer journey, не розділяючи вручну. ⟦5QlJLlhltxw @2025-11-03⟧
- [T] **Lifetime-бюджет під ad-refresh цикл:** оскільки sequencing вимагає lifetime budgets (фіксована довжина кампанії), зроби тривалість кампанії під цикл оновлення оголошень (кожні **3–6 міс**) — функціонально буде як попередній OC-сетап. ⟦5QlJLlhltxw @2025-11-03⟧
- [T] **Очікувана консолідація OC-структури:** замість 10–14 окремих adset'ів (по 1 оголошенню) — з ad sequencing можна звести в **менше adset'ів** (чи навіть один), бо порядок тепер задає фіча, а не ручне розділення на кампанії. (Ben обіцяв окреме відео з фінальною рекомендацією — наразі недостатньо даних для точної нової структури.) ⟦5QlJLlhltxw @2025-11-03⟧
- [T] **Інші юзкейси sequencing:** countdown до івента / поетапне розкриття спікерів/артистів (продаж квитків); sales з дедлайнами; **laddered discounts** у ре-таргеті (10% → 15% → 20% → 25%): найгарячіші куплять одразу на 10% (більше маржі), хто вагається — отримає глибші знижки далі. ⟦5QlJLlhltxw @2025-11-03⟧

### Site links (ad sources)
- [T] **Передумова:** на рівні adset змінити conversion location з **instant forms на website** (клік веде на сайт/лендинг). ⟦pJfYdXzSG_M @2025-06-03⟧
- [T] **Де:** рівень оголошення → блок **Ad sources** → поле **website URL** (Meta спробує згенерувати site links авто; якщо ні — додати руками). ⟦pJfYdXzSG_M @2025-06-03⟧
- [T] **Мінімум 3 site links**, щоб вони показались. Кожен = URL + **label** (короткий зрозумілий текст: «Contact», «Portfolio», «Case studies», «Who we work with»). Старт із homepage у website URL — «не помилишся», далі можна звузити до category/product-сторінки. ⟦pJfYdXzSG_M @2025-06-03⟧
- [T] **Об'єктиви, що вмикають site links:** traffic / engagement / leads / sales. НЕ працює з app promotion. Для **sales** треба **вимкнути «use a catalog»** на рівні кампанії. ⟦pJfYdXzSG_M @2025-06-03⟧
- [T] **Обмеження плейсменту:** наразі site links доставляються **лише у Facebook feed** (інші плейсменти — ймовірно згодом). Показуються під headline як ряд клікабельних кнопок поряд із основним CTA. ⟦pJfYdXzSG_M @2025-06-03⟧
- [T] **Трекінг site links:** Ads Manager → **Breakdown → By website URL** (бачиш кліки/конверсії по кожному лінку); можна крос-розбити (напр. + age). Якщо якийсь site link дає кращий ROAS/CVR — розглянь зміну головного destination оголошення на нього. ⟦pJfYdXzSG_M @2025-06-03⟧

## Числа / бенчмарки
| Параметр | Значення | Джерело |
|---|---|---|
| Frequency control: дефолтний cap | 2 times every 7 days | ⟦3qpLGAuvDAA⟧ |
| Frequency target: передумова | lifetime budgets + кампанія > 7 днів | ⟦3qpLGAuvDAA⟧ |
| Приклад частоти під 3–7-денний sale | 1 impression / 7 днів (або 1 / 3 дні для 3-денного) | ⟦3qpLGAuvDAA⟧ |
| Frequency control: статус роллауту | awareness/auction — частково; engagement — у тесті; sales/leads — очікувано згодом | ⟦3qpLGAuvDAA⟧ |
| Ad sequencing: передумови (auction) | awareness/engagement + adset budgets + frequency controls + lifetime budgets | ⟦5QlJLlhltxw⟧ |
| OC-структура (до фічі) | 10–14 adset'ів, по 1 оголошенню кожен | ⟦5QlJLlhltxw⟧ |
| OC frequency cap (приклад) | 1 impression / 7 днів × 14 adset'ів ≈ 2 різні оголошення/день/людину | ⟦5QlJLlhltxw⟧ |
| OC: цикл оновлення оголошень | кожні 3–6 міс | ⟦5QlJLlhltxw⟧ |
| OC: поріг «дорогого» оферу для direct-sell | ~$1000+ (важко продавати в лоб) | ⟦5QlJLlhltxw⟧ |
| Приклад high-ticket для OC | $10 000 / $50 000 (треба довго будувати довіру) | ⟦5QlJLlhltxw⟧ |
| Laddered discounts (приклад) | 10% → 15% → 20% → 25% | ⟦5QlJLlhltxw⟧ |
| Site links: мінімум для показу | 3 | ⟦pJfYdXzSG_M⟧ |
| Site links: плейсмент | лише Facebook feed (наразі) | ⟦pJfYdXzSG_M⟧ |
| Site links: ефект | покращення CTR (рання data клієнтів Ben); ймовірно й CVR | ⟦pJfYdXzSG_M⟧ |
| Site links: об'єктиви | traffic / engagement / leads / sales (не app promotion) | ⟦pJfYdXzSG_M⟧ |

> ⚠️ «Покращення CTR» від site links — рання спостережувана data з акаунтів клієнтів Ben, не контрольований замір. Числа OC (14 adset'ів, $10k/$50k, 10→25%) і приклади частоти — ілюстративні з відео, не виміряні бенчмарки твого акаунту. Статуси роллауту (frequency у sales/leads, site links поза FB feed) — прогнози Ben, ще не факт станом на дати джерел.

## Як було раніше і що змінилось
- ❌ Раніше: лише **frequency CAP** (жорстка стеля «не більше N разів»), і тільки в **awareness** об'єктиві (auction). ⟦superseded by 3qpLGAuvDAA @2025-06-03⟧
- ✅ Зараз: блок **Frequency control** з вибором **target vs cap** (target цілиться в середнє → зазвичай кращий). Доступний у awareness/auction (роллаут триває), тестується на engagement, очікувано піде на sales/leads — і це буде game-changer. ⟦3qpLGAuvDAA @2025-06-03⟧
- ❌ Раніше **target-frequency був тільки в reservation buying type** — Ben його не згадував, бо reservation не радить нікому, крім дуже великих бізнесів. ⟦superseded by 3qpLGAuvDAA @2025-06-03⟧ ⟦superseded by 5QlJLlhltxw @2025-11-03⟧
- ✅ Зараз target-frequency приходить у **auction** (де живе бюджет більшості). ⟦3qpLGAuvDAA @2025-06-03⟧
- ❌ Раніше **ad sequencing існував лише в reservation** → для більшості нерелевантний; в OC-стратегії порядок показів не контролювався — «довірся Meta» або вручну ставити value-adset'и live на кілька днів раніше за решту (працювало лише в перший тиждень). ⟦superseded by 5QlJLlhltxw @2025-11-03⟧
- ✅ Зараз ad sequencing переноситься в **auction** (awareness/engagement) → справжній контроль над customer journey; OC-структуру можна **консолідувати** в менше adset'ів. ⟦5QlJLlhltxw @2025-11-03⟧
- ❌ Раніше з OC-стратегією за замовч. — **daily budgets**; контролю порядку не було. ⟦superseded by 5QlJLlhltxw @2025-11-03⟧
- ✅ Зараз для ad sequencing потрібні **lifetime budgets** (Ben загалом не фанат lifetime через гнучкість daily, але тут — виправдано; підлаштувати тривалість кампанії під ad-refresh цикл 3–6 міс). ⟦5QlJLlhltxw @2025-11-03⟧
  - ⚠️ Конфлікт із дефолтом «daily > lifetime майже завжди» з [[04-budget-scaling/big-spend-scaling]]: lifetime тут — свідомий виняток заради доступу до sequencing/target-frequency, а не загальна рекомендація.
- ❌ Раніше **site links у Meta не існували** (були лише в Google Ads); рекламодавець вів увесь трафік на один головний destination. ⟦superseded by pJfYdXzSG_M @2025-06-03⟧
- ✅ Зараз з'явився блок **Ad sources / site links** (≥3 лінки під оголошенням, лише FB feed) → більше кліків і ймовірно конверсій; трекінг через breakdown by website URL. ⟦pJfYdXzSG_M @2025-06-03⟧
- ⚠️ Куди йде далі (прогнози Ben, ще не факт): frequency control → sales/leads; ad sequencing → можливо sales/leads колись («maybe one day, not yet»); site links → інші плейсменти поза FB feed; auto-генерація site links самою Meta. ⟦3qpLGAuvDAA @2025-06-03⟧ ⟦5QlJLlhltxw @2025-11-03⟧ ⟦pJfYdXzSG_M @2025-06-03⟧

### Передісторія: «optimize text per person» — auto-фіча, яку треба було вимикати (era: pre-andromeda)
> Контекст: відео FOC1SJCbQbw (2023) і 6iZZzwtTDDY (2024) — **до анонсу Andromeda (груд. 2024)**. Описують той самий патерн, що й post-Andromeda frequency-дефолт: Meta вмикає delivery/optimization-фічу за замовчуванням, ховає вимикач, і просунутому рекламодавцю треба її свідомо контролювати. Принципи звідси (оцінювати кожен авто-дефолт; повертати контроль; не плутати з мульти-варіантами тексту) винесені вище як evergreen [P]; нижче — pre-Andromeda специфіка/механіка.
- ❌ Раніше (era: pre-andromeda) Meta зробила **«optimize text per person»** (раніша назва «text improvements») **auto-enabled by default** на нових кампаніях/оголошеннях — фіча тасувала твій primary text / headline / description по слотах на рівні індивіда. Доступна вже ~6 міс до того, як її зробили дефолтом. Просунутому рекламодавцю — вимикати. ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧
- ❌ Раніше (era: pre-andromeda) **вимикач був прихований**: на рівні оголошення під add-creative секцією «optimized text per person» показувалось просто як **Enabled без тоглу**. Щоб з'явився перемикач, треба було спершу зняти **standard enhancements** (вище, під ad format) — і лише тоді toggle «optimize text per person» ставав доступним (за замовч. усе ще On → треба окремо вимкнути). ⟦FOC1SJCbQbw @2023-06-03⟧
  - ⚠️ «Standard enhancements» (= пізніше **Advantage+ creative**) сам по собі має корисні елементи (яскравість/контраст/кольори) — але якщо ціною був примусовий «optimize text per person», Ben радив радше зняти весь блок. Сьогодні набір цих enhancement-опцій ширший і керується по-окремо → див. [[06-creatives/creative-enhancements]]. ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧
- ⚠️ Що змінилось / лишилось: сама **логіка «Meta вмикає delivery-фічу за замовчуванням, а ти оцінюєш і за потреби вимикаєш»** — evergreen і прямо повторюється в post-Andromeda frequency-дефолті (cap замість оптимальнішого target). Конкретний UI-шлях (standard enhancements → toggle) — pre-Andromeda, ймовірно застарів, бо Advantage+ creative тепер інакше згрупований. ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦3qpLGAuvDAA @2025-06-03⟧

## Помилки / anti-patterns
- ❌ **Лишати cap там, де доречний target.** Жорстка стеля не дає Meta показати трохи більше «гарячим»; у більшості випадків target дає кращий результат. ⟦3qpLGAuvDAA @2025-06-03⟧
- ❌ **Високий frequency на імпульсний/безкоштовний офер.** Повторні покази тим, хто вже відмовився, — злив бюджету; такі офери треба «розмазувати» тонко. ⟦3qpLGAuvDAA @2025-06-03⟧
- ❌ **Крутити awareness заради frequency-cap для flash-sale**, коли вже можна (або скоро можна) поставити cap прямо в sales/leads — це дасть кращі результати. ⟦3qpLGAuvDAA @2025-06-03⟧
- ❌ **Користуватися reservation buying type не будучи дуже великим бізнесом** заради фіч типу sequencing — спосіб злити багато грошей; ці фічі вже приходять в auction. ⟦5QlJLlhltxw @2025-11-03⟧ ⟦3qpLGAuvDAA @2025-06-03⟧
- ❌ **Братися за omnipresent content із «Tik-Tok brain».** Стратегія вимагає часу/зусиль на сетап і терпіння (6+ міс) — без цього не варто й починати. ⟦5QlJLlhltxw @2025-11-03⟧
- ❌ **Один і той самий ad показувати 14 разів/тиждень** — людина миттєво вигорає й перестає реагувати; саме тому OC = 14 РІЗНИХ оголошень (зв'язок з creative diversity, [[00-philosophy/andromeda-era]]). ⟦5QlJLlhltxw @2025-11-03⟧
- ❌ **Менше за 3 site links** — не покажуться взагалі. ⟦pJfYdXzSG_M @2025-06-03⟧
- ❌ **Незрозумілі labels site links** — людина має одразу розуміти, куди веде кнопка (Contact/Portfolio/Case studies), інакше не клікне. ⟦pJfYdXzSG_M @2025-06-03⟧
- ❌ **Намагатися ввімкнути site links не на тому об'єктиві / з catalog у sales** і дивуватись, чому блок не показується: треба traffic/engagement/leads/sales і вимкнений catalog (для sales). ⟦pJfYdXzSG_M @2025-06-03⟧
- ❌ **«Не бачу фічу → я щось зробив не так».** Site links / frequency control / ad sequencing роллаутяться частинами; можливо, акаунт її просто ще не отримав (або не виставлені правильні передумови, бо блок з'являється лише після них). ⟦pJfYdXzSG_M @2025-06-03⟧ ⟦3qpLGAuvDAA @2025-06-03⟧ ⟦5QlJLlhltxw @2025-11-03⟧
- ❌ **Лишати «optimize text per person» увімкненим, не будучи повним новачком** (era: pre-andromeda). Авто-перекидання тексту по слотах ламає продуманий headline/primary text/flow; на просунутому рівні майже завжди вимикати. ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧
- ❌ **Здатися перед «Enabled без тоглу» і вирішити, що фічу не вимкнути** (era: pre-andromeda). Вона вимикається — просто треба спершу зняти standard enhancements, потім окремо тоглнути «optimize text per person». ⟦FOC1SJCbQbw @2023-06-03⟧
- ❌ **Плутати корисне (кілька варіантів primary text/headline/description для тесту) зі шкідливим (auto-перекидання написаного між слотами)** і вимикати не те. ⟦FOC1SJCbQbw @2023-06-03⟧
- ❌ **Сліпо приймати будь-який auto-enabled дефолт Meta** (text improvements тоді, frequency-cap зараз), не оцінивши, він на користь твого результату чи Meta. ⟦FOC1SJCbQbw @2023-06-03⟧ ⟦6iZZzwtTDDY @2024-06-03⟧ ⟦3qpLGAuvDAA @2025-06-03⟧

## Застосування в аналізі/оптимізації
- **Frequency-аудит:** якщо у звіті висока frequency на малій аудиторії при імпульсному/дешевому офері → прапор «frequency build-up», рекомендувати target (або cap) і «тонший» розподіл. Для high-ticket/складного оферу — навпаки, вища частота доречна. → [[00-philosophy/how-delivery-works]].
- **Advantage+ ллє в warm:** якщо A+ кампанія занадто ре-таргетить і не йде на cold → коли frequency-control дійде в sales/leads, поставити cap/target, щоб виштовхнути Meta на new customer acquisition. → [[03-targeting/advantage-plus-audience]].
- **Limited-time offer / flash sale:** перевірити, чи не крутиться awareness лише заради cap — мігрувати на sales/leads з frequency-контролем, щойно доступно. → [[02-objectives/leads-vs-sales-vs-traffic]].
- **OC / omnipresent content:** для експертних послуг / оферів $1000+ з довгим циклом → пропонувати ad sequencing (auction, awareness/engagement, lifetime, adset budgets, freq-cap), консолідувати стару 10–14-adset структуру; нагадати про 3–6-міс refresh і потребу в терпінні. → [[00-philosophy/andromeda-era]] · [[06-creatives/creative-enhancements]].
- **lifetime vs daily конфлікт:** якщо рекомендуєш sequencing/target-frequency (вимагають lifetime) — явно зазначити, що це виняток із дефолту «daily майже завжди» і прив'язати тривалість до refresh-циклу. → [[04-budget-scaling/big-spend-scaling]].
- **Site links як easy win:** для website-конверсій з кількома сильними підрозділами (case studies / reviews / refund / warranty / who-we-work-with) → додати ≥3 site links, особливо там, де вони знімають заперечення; виміряти приріст CTR/CVR. → [[08-landing-cvr/landing-best-practices]] · [[06-creatives/creative-enhancements]].
- **Трекінг site links:** breakdown by website URL → якщо один лінк дає помітно кращий ROAS/CVR, тестувати зміну головного destination оголошення на нього.
- **«Фічі немає» в аудиті:** перш ніж робити висновок, що щось зламано, перевірити роллаут і правильність передумов (conversion location = website для site links; lifetime + >7 днів для target-frequency; усі 4 критерії для sequencing).
- **Аудит auto-enabled дефолтів (delivery/optimization-гігієна):** для кожної фічі, яку Meta ввімкнула за замовчуванням, питати «це на користь результату чи Meta?». Конкретно: на оголошеннях не-новачка перевірити **«optimize text per person» / text improvements** — якщо ввімкнено й текст продуманий, рекомендувати вимкнути (через зняття standard enhancements → toggle); НЕ чіпати корисні мульти-варіанти тексту. Той самий принцип — до frequency-дефолту (target замість cap, де доречно). → [[06-creatives/creative-enhancements]].
- **Звʼязок:** [[05-optimization/learning-phase]] · [[00-philosophy/andromeda-era]] · [[00-philosophy/how-delivery-works]] · [[03-targeting/advantage-plus-audience]] · [[02-objectives/choosing-objective]] · [[04-budget-scaling/big-spend-scaling]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "Target is better than cap in most cases… across most advertising." — Ben Heath ⟦3qpLGAuvDAA @2025-06-03⟧
> "What is a game changer about this feature is it being added to other campaign objectives." — Ben Heath ⟦3qpLGAuvDAA @2025-06-03⟧
> "This ad sequencing feature has been brought over to the auction buying type, and that is a really big deal." — Ben Heath ⟦5QlJLlhltxw @2025-11-03⟧
> "Only give this a go if you don't have full Tik Tok brain. It requires time and effort." — Ben Heath ⟦5QlJLlhltxw @2025-11-03⟧
> "Connect ad sources to include more information in your ad that can help inspire action." — Meta UI via ⟦pJfYdXzSG_M @2025-06-03⟧
> "There's limited downside in doing so… we are seeing an improvement in CTR." — Ben Heath ⟦pJfYdXzSG_M @2025-06-03⟧
> "Is that because it benefits us as advertisers… or is it something that meta wants us to do because it's going to help them make more money over the short run?" — Ben Heath ⟦6iZZzwtTDDY @2024-06-03⟧ (pre-andromeda)
> "It's still turned on as default even when you deselect standard enhancements." — Ben Heath ⟦FOC1SJCbQbw @2023-06-03⟧ (pre-andromeda)
> "If a lot of the flexibility is taken away… everyone gets the same results, it all becomes very homogenized and you can't win at this game as easily." — Ben Heath ⟦FOC1SJCbQbw @2023-06-03⟧ (pre-andromeda)
> "You have to take more control… particularly be careful these don't ruin the way your ad creative looks." — Ben Heath ⟦6iZZzwtTDDY @2024-06-03⟧ (pre-andromeda)
