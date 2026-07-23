---
topic: "Value Rules та важелі контролю над оптимізацією Meta (value-side)"
category: targeting
subcategory: value-rules
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: bv8AsY0xkIk, date: 2026-05-06, era: post-andromeda }
  - { id: OWYL-Mw-874, date: 2025-08-03, era: post-andromeda }
  - { id: WRyAUXjBlJM, date: 2025-06-03, era: post-andromeda }
  - { id: j0HHLor-nmw, date: 2025-06-03, era: post-andromeda }
  - { id: 2D2ObSdXhdc, date: 2025-07-03, era: post-andromeda }
  - { id: IYesh3616M0, date: 2025-06-03, era: post-andromeda }
  - { id: TOII24BtKAo, date: 2025-06-03, era: post-andromeda }
  - { id: QUfjpZOlH28, date: 2023-06-03, era: pre-andromeda }
  - { id: 8IzbiiWnfLY, date: 2023-06-03, era: pre-andromeda }
---

# Value Rules та важелі контролю над оптимізацією Meta

## TL;DR
В пост-Andromeda таргетинг здебільшого віддано Meta (broad/open), тож головна робота рекламодавця — **донести Meta правильну бізнес-логіку про цінність** і обрати налаштування, що **впливають на її оптимізацію**. Ядро теми — **Value Rules**: лишаєш broad-таргетинг (Advantage+), але кажеш Meta **бідити більше/менше** за демографії, які ти ЗНАЄШ що цінніші (LTV, refund rate, lead→client CR) — те, чого Meta не бачить через атрибуційне вікно. ⟦bv8AsY0xkIk @2026-05-06⟧ Поруч стоїть «suite» нових важелів контролю: **incremental attribution** (Meta оптимізує під конверсії, що НЕ сталися б без реклами; +46% інкрементальних конверсій у тестах) ⟦OWYL-Mw-874 @2025-08-03⟧, **maximize value of conversions** (бідити під сумарну цінність, а не кількість) ⟦WRyAUXjBlJM @2025-06-03⟧, **industry setting** (донести Meta, що це за бізнес → +32% sales у кейсі) ⟦j0HHLor-nmw @2025-06-03⟧, **combine social proof** (злити лайки/реакції схожих оголошень) ⟦2D2ObSdXhdc @2025-07-03⟧ та свідомий контроль **placements** (Advantage+ ≠ завжди добре) ⟦IYesh3616M0 @2025-06-03⟧. Спільний принцип: рекламодавець виграє там, де **доносить Meta дані/контекст**, яких та сама не має. У основі всього лежить evergreen-механіка **аукціону**: ціна = попит рекламодавців проти фіксованої пропозиції показів, тож «дешевша аудиторія/плейсмент» = менша конкуренція за неї (pre-Andromeda це робили вручну через Inspect tool / вибір платформи; зараз цей пошук більше бере на себе сама Meta). ⟦QUfjpZOlH28 @2023-06-03⟧ ⟦8IzbiiWnfLY @2023-06-03⟧

## Принципи [P]
- [P] **Еволюція таргетингу** у 3 кроки: дуже специфічні інтереси/lookalike в багатьох адсетах → broad/open (Meta сама знаходить) → **гібрид** (broad + value rules для впливу). ⟦bv8AsY0xkIk @2026-05-06⟧
- [P] Meta оптимізує лише в межах **атрибуційного вікна** (макс 7-day click, інколи 1-day), тож не «бачить» LTV, refund rate, lead→client CR. Це знання можеш довнести ти. ⟦bv8AsY0xkIk @2026-05-06⟧
- [P] **Консолідація** в один адсет — добре: більше даних конверсій → краще навчання/оптимізація. Value rules дозволяють це замість багатьох адсетів під різні демографії. Технічний бік цього самого принципу — **auction overlap**: дублі адсетів/таргетингу з одного акаунта потрапляють у той самий аукціон, і Meta прибирає менш конкурентний адсет з аукціону («to prevent you from bidding against yourself we removed the less competitive ad set») → один з адсетів не доставляється коректно. Тому одна-кілька кампаній > купа дублів. ⟦bv8AsY0xkIk @2026-05-06⟧ ⟦QUfjpZOlH28 @2023-06-03⟧
- [P] **Ціна Meta-реклами задається аукціоном: попит проти пропозиції.** Пропозиція (скільки людей на FB/IG × частота користування) майже **фіксована** і величезна; попит (конкуренція рекламодавців за ad real estate) **зростає** з масштабуванням кампаній і притоком нових рекламодавців → CPM окремих аудиторій сильно росте. Це наскрізна evergreen-теза (підтверджена і pre-, і post-Andromeda): де **менше конкурентів за ті самі слоти** — там дешевше. ⟦QUfjpZOlH28 @2023-06-03⟧ ⟦8IzbiiWnfLY @2023-06-03⟧ (та сама demand/supply механіка в [[00-philosophy/andromeda-era]])
- [P] **Скорочення опцій таргетингу саме по собі піднімає конкуренцію (й ціну).** Коли Meta прибрала тисячі таргетинг-опцій (поч. 2023), рекламодавці, що раніше сиділи на різних окремих інтересах, опинились на тих самих небагатьох → більше конкурентів на опцію → дорожчі аудиторії. Це pre-Andromeda передвісник того самого вектора, що згодом привів до broad/open. ⟦QUfjpZOlH28 @2023-06-03⟧
- [P] **CPM різний по платформах і це теж функція ПОПИТУ, а не лише результату.** FB історично бував дорожчим за IG (≈2013-15, бо всі хотіли FB), потім вирівнялись (≈2015-21), а далі IG став на ~20-40% дорожчим за FB — не тому, що IG дає кращі результати, а тому, що рекламодавці **вважають** IG «кращим/молодшим» і туди йдуть. Перцепція рекламодавців рухає ціну, навіть коли реальні результати протилежні (опитування: 76% сказали, що FB дає кращі результати). ⟦8IzbiiWnfLY @2023-06-03⟧
- [P] **Пессимізм/відтік рекламодавців з каналу = можливість для тих, хто лишається.** Якщо частина рекламодавців іде (напр. через негативну пресу про Meta/FB) при стабільній базі користувачів — конкуренція за слоти падає, CPM дешевшає → кращий ROAS у тих, хто не пішов. ⟦8IzbiiWnfLY @2023-06-03⟧ (corroborates [[00-philosophy/andromeda-era]])
- [P] **Incrementality = які конверсії НЕ сталися б без твоєї реклами.** Рекламодавці роками хотіли відділити «купив би й так» (warm-аудиторія, email-лист, інші канали) від «купив саме завдяки рекламі». Incremental attribution фільтрує перше й дає Meta орієнтуватись на друге. ⟦OWYL-Mw-874 @2025-08-03⟧
- [P] **Incremental attribution — це НЕ лише звітність, а й оптимізація.** Поширена помилка вважати, що це просто новий звіт; насправді Meta змінює, кому показувати ads (менше — тим, хто конвертне й так). ⟦OWYL-Mw-874 @2025-08-03⟧
- [P] **«Демократизація» просунутої аналітики.** Раніше incrementality / conversion-lift studies могли дозволити лише великі спендери/агенції. Incremental attribution робить цей рівень аналізу доступним малим і середнім рекламодавцям прямо в платформі. ⟦OWYL-Mw-874 @2025-08-03⟧
- [P] **Гроші на «не-інкрементальні» конверсії — НЕ обовʼязково злив.** Експозиція, нагадування, підняття average order value, довгострокова присутність бренду мають цінність. Не варто панікувати, що все поза інкрементом — викинуті гроші. ⟦OWYL-Mw-874 @2025-08-03⟧
- [P] **Поведінка змінилась: купують, не клікаючи (Gen Z ×2).** Тому міряти лише click-attribution мало — треба враховувати тих, хто побачив ad, вийшов, перевірив reviews/AI й купив без повернення до оголошення. Це обґрунтовує incremental + engaged-view. ⟦OWYL-Mw-874 @2025-08-03⟧ (перетин з [[00-philosophy/andromeda-era]])
- [P] **Performance goal — найважливіше налаштування (важливіше за objective).** Правильний objective можна повністю звести нанівець неправильним performance goal: кампанія оптимізуватиметься зовсім не так, як ти хочеш. Саме performance goal визначає, як Meta оптимізує доставку. ⟦WRyAUXjBlJM @2025-06-03⟧
- [P] **Conversion location + objective визначають, які performance goals доступні; performance goal визначає оптимізацію.** Зміна conversion location (website / messenger / instant form / Instagram profile…) змінює набір performance goals. ⟦WRyAUXjBlJM @2025-06-03⟧
- [P] **Value optimization > volume optimization, коли цінність конверсій різна.** `Maximize value of conversions` каже Meta бідити більше за людей, які не лише конвертнуть, а й куплять на більшу суму (вищий order value); `maximize number` ставить усі конверсії рівними. ⟦WRyAUXjBlJM @2025-06-03⟧
- [P] **Чим краще Meta розуміє твій бізнес, тим краще оптимізує.** Industry setting допомагає Meta зрозуміти акаунт; маючи дані інших схожих бізнесів, вона точніше оптимізує (кого таргетити, у який час, скільки показів). ⟦j0HHLor-nmw @2025-06-03⟧
- [P] **«Заплутаний» історією акаунт гірше оптимізується.** Якщо в акаунті крутилось багато різних продуктів/послуг на різні демографії, Meta «плутається» (особливо на Advantage+ Shopping, що покладається на її AI-таргетинг). Звуження фокусу + донесення контексту знімає плутанину. ⟦j0HHLor-nmw @2025-06-03⟧
- [P] **Соц-докази підвищують конверсію, особливо на cold-аудиторії.** Лайки/реакції/коменти сигналізують легітимність і «розмір» бізнесу → більше впевненості зробити наступний крок. ⟦2D2ObSdXhdc @2025-07-03⟧
- [P] **Більше тестів → соц-докази розпорошуються по багатьох оголошеннях.** Кожне окреме оголошення має по жменьці лайків; combine social proof зливає їх → суттєво сильніший сукупний сигнал. ⟦2D2ObSdXhdc @2025-07-03⟧
- [P] **Інтереси Meta й рекламодавця здебільшого збігаються, АЛЕ не завжди.** Кращі результати → рекламодавець лишається й платить більше → Meta теж виграє. Проте Meta має **ad inventory to fill** — і деякі її рекомендації вигідні насамперед їй (класичний приклад — push Advantage+ placements). ⟦IYesh3616M0 @2025-06-03⟧
- [P] **Placement — це value-важіль.** Низькоякісні плейсменти (Audience Network) дають дешеві link clicks / video views, але гірше конвертять. На conversion-кампаніях це ок (Meta оптимізує під конверсію); на traffic/engagement/awareness — дешеві «дії» ≠ бізнес-результат. ⟦IYesh3616M0 @2025-06-03⟧
- [P] **Рекомендації самої ad-платформи фільтруй на «чий це інтерес».** Більшість порад Meta — корисні (бо хоче, щоб ти лишився), але завжди є сценарії, де порада робить гроші насамперед Meta. Перевіряй на конкретиці (як з 133%-claim про placements). ⟦IYesh3616M0 @2025-06-03⟧
- [P] **«I've seen this before» filter** — кожен користувач миттєво проскролює те, що візуально вже бачив. Тому цінність переможного креативу вижимають, змінюючи **візуальну обгортку**, а не суть/хук. ⟦TOII24BtKAo @2025-06-03⟧ (ядро — у [[06-creatives/creative-strategy-volume]])
- [P] **Cost-per-result завжди має пріоритет над «проміжними» сигналами.** Auction competition / overlap / saturation — корисні **додаткові** дані, але не мусять перекривати головну метрику (cost per purchase/lead/те, під що оптимізуєш). Висока конкуренція за аудиторію з відмінним CPA — все одно ок. Той самий принцип evergreen: дешеві «дії» (кліки/в'ю на низькоякісних плейсментах) ≠ бізнес-результат. ⟦QUfjpZOlH28 @2023-06-03⟧ ⟦IYesh3616M0 @2025-06-03⟧

## Тактики зараз [T]

### Value Rules (ядро)
- [T] **Де:** Ads Manager → Advertising settings → Value rules → Create rule set. Застосовується вручну на рівні **адсета** (не авто після створення). ⟦bv8AsY0xkIk @2026-05-06⟧
- [T] **Критерії:** age, gender, location, conversion location (website vs instant form), device (desktop/mobile), mobile OS (iOS/Android), placement (напр. Feed vs Audience Network). До **10 правил** на набір; можна комбінувати 2 змінні (напр. «жінки 45+»). ⟦bv8AsY0xkIk @2026-05-06⟧
- [T] Increase/decrease bid by % — приклад із відео: women **+80%** (бо LTV ≈ ×2.4 vs чоловіки в ювелірному бізнесі). ⟦bv8AsY0xkIk @2026-05-06⟧
- [T] **ПЕРЕД** налаштуванням — порахувати по CRM реальну різницю цінності демографій (інакше % береться «зі стелі»). Сісти на 90 хв і звести CRM+ad account+трекер. ⟦bv8AsY0xkIk @2026-05-06⟧

### Incremental attribution
- [T] **Де:** рівень **адсета** → блок Conversion → show more options → **Attribution setting** → перемкнути зі *Standard attribution* на **Incremental attribution** («optimize delivery for incremental conversions»). ⟦OWYL-Mw-874 @2025-08-03⟧
- [T] **Умови доступності (поки):** conversion location = **website**; кампанія **sales**, оптимізація під **purchases** (також product-catalog кампанії). Performance goal — *maximize number of conversions* АБО *maximize value of conversions* (останнє Meta саме тестує; інкремент + цінність = просунута комбінація). ⟦OWYL-Mw-874 @2025-08-03⟧
- [T] **Очікуй, що topline-цифри впадуть** (менше «покупок», нижчий ROAS у звіті), бо рахуються лише інкрементальні конверсії. Це не обовʼязково гірший перформанс — ти отримуєш більше того, що реально цінне. Читай звіт із поправкою. ⟦OWYL-Mw-874 @2025-08-03⟧
- [T] **Читання звіту incremental attribution:** breakdown *results by attribution setting*; враховуй не лише *1-day click*, а й **engaged-view** конверсії (хтось не клікнув, але подивився відео / клікнув «see more») — з ними сумарні конверсії помітно вищі навіть на інкрементальній базі. ⟦OWYL-Mw-874 @2025-08-03⟧
- [T] **Тестуй із відкритим розумом** і дай часу: інкрементальні фічі-оптимізації зазвичай **кращають з часом** (акаунт «вчиться»), тож приріст інкрементальних конверсій імовірно зростатиме. Можна відкотитись, якщо не зайшло. ⟦OWYL-Mw-874 @2025-08-03⟧

### Performance goal та value optimization
- [T] **Sales-кампанія (найчастіша):** conversion location = **website**, performance goal = **maximize value of conversions** (а не number), коли продаєш різні товари з різними чеками. Для одного товару з єдиною ціною — maximize number (різниці нема). ⟦WRyAUXjBlJM @2025-06-03⟧
- [T] **Leads-кампанія:** default *maximize number of conversions* — ок; краще *maximize value of conversions*, якщо ліди на різні послуги мають різну цінність і це налаштовано. Якщо є CRM-інтеграція — *maximize number of conversion leads* (оптимізація під тих, хто реально стане клієнтом, а не просто лід). ⟦WRyAUXjBlJM @2025-06-03⟧
- [T] **Налаштувати value у Pixel:** щоб value optimization працювала, треба передавати цінність конверсій (e-commerce: Shopify+Pixel автоматично шле «купив на $60 / на $150» → Meta таргетить схожих на дорожчого покупця). ⟦WRyAUXjBlJM @2025-06-03⟧
- [T] **Якщо сумніваєшся — бери default performance goal** (за умови, що objective обрано правильно): зазвичай це «ок», навіть якщо не оптимально. ⟦WRyAUXjBlJM @2025-06-03⟧

### Industry setting
- [T] **Де:** Ads Manager → ☰ (три лінії) → Advertising settings → **Industry** → Add industry → save. Можна задати **до 2 індустрій** (приклад кейсу: *e-commerce* + *technology*). ⟦j0HHLor-nmw @2025-06-03⟧
- [T] **Зміни НЕ діють на активні кампанії** — лише на нові. Після save потрібно **створити нові / дублювати наявні** кампанії, щоб ефект зайшов. ⟦j0HHLor-nmw @2025-06-03⟧
- [T] Обирай **максимально точні** індустрії (опцій обмежено; не всім вистачить точних — бери ширше, але якомога ближче). ⟦j0HHLor-nmw @2025-06-03⟧

### Combine social proof
- [T] **Де:** Ads Manager → ☰ → all tools → Advertising settings → **Social information** → відкрити → поставити галку **«allow Meta to combine likes and reactions for similar ads»**. ⟦2D2ObSdXhdc @2025-07-03⟧
- [T] **Вмикай — downside немає.** Meta зливає лайки/реакції оголошень, де текст і зображення однакові/схожі (точне визначення «similar» поки невідоме — імовірно той самий headline + та сама destination). Особливо корисно, коли тестуєш багато copy/creative-варіацій. ⟦2D2ObSdXhdc @2025-07-03⟧
- [T] Фіча доступна не всім (на момент відео ~20% акаунтів автора, частина — увімкнена за замовчуванням); якщо блоку Social information нема — ще не розкотили, перевір пізніше. ⟦2D2ObSdXhdc @2025-07-03⟧

### Контроль placements (як value-важіль)
- [T] **Conversion-кампанії (sales/leads з оптимізацією під конверсію):** лишай **Advantage+ placements** — дай Meta гнучкість, де показати (включно з догрівом через Audience Network / in-stream «щоб дотиснути»). ⟦IYesh3616M0 @2025-06-03⟧
- [T] **Non-conversion кампанії (awareness/traffic/engagement):** перемикай на **manual placements** і обмеж до **найякісніших** (feeds, stories, reels) — інакше Meta дасть дешеві, але низькоякісні дії на Audience Network. ⟦IYesh3616M0 @2025-06-03⟧
- [T] **Як знайти manual placements:** Meta ховає їх глибше (треба клікнути в налаштування плейсментів і змінити). У manual sales/leads це можливо; у Advantage+ Shopping / tailored leads — **placements зафіксовані** (змінити не можна). ⟦IYesh3616M0 @2025-06-03⟧
- [T] **Платформенний CPM-чек (evergreen, працює й зараз):** Ads Manager → breakdown **by platform** → порівняти CPM **Facebook vs Instagram**. Якщо ефективність (конверсії на 1000 показів) приблизно однакова, а один із плейсментів дешевший — це безпосередній value-сигнал. На **conversion-кампанії з обома платформами** Meta сама переллє бюджет туди, де результат кращий (тому здебільшого лишай **обидві**), але знати розрив корисно. ⟦8IzbiiWnfLY @2023-06-03⟧

### Вижимання цінності з переможного креативу (суміжне; ядро — у 06-creatives)
- [T] Знайшов winner — спершу **вижми максимум**, перш ніж робити щось нове: змінюй візуальну «обгортку», щоб обійти «I've seen this before» filter (зміна фону/кольору/локації; зовнішності/одягу спікера; заміна людини в кадрі під ЦА; реордер пунктів ПІСЛЯ хука; фільтри B&W/sepia/cartoon; стиль монтажу/субтитрів/музики; темп і манера подачі). **НЕ змінюй хук** — інакше це вже нове оголошення. Дозволяє продовжити життя winner'а на місяці/роки. Деталі → [[06-creatives/creative-strategy-volume]]. ⟦TOII24BtKAo @2025-06-03⟧

## Числа / бенчмарки
| Параметр | Значення | Джерело |
|---|---|---|
| Макс правил на Value-rule набір | 10 | ⟦bv8AsY0xkIk⟧ |
| Value Rules: bid adjustment | у % (приклад +80% на women, LTV ≈ ×2.4) | ⟦bv8AsY0xkIk⟧ |
| Атрибуційне вікно (стеля оптимізації) | макс 7-day click (1-day engaged/view-through) | ⟦bv8AsY0xkIk⟧ |
| Incremental attribution: приріст інкрементальних конверсій у тестах | +46% | ⟦OWYL-Mw-874⟧ Meta-claim |
| Incremental attribution: умови | website + sales + purchases (або product catalog) | ⟦OWYL-Mw-874⟧ |
| Incremental attribution: ефект на topline | звітні конверсії/ROAS падають (рахується лише інкремент) | ⟦OWYL-Mw-874⟧ |
| Industry setting: кейс приросту продажів | +32% sales (той самий спенд) | ⟦j0HHLor-nmw⟧ |
| Industry setting: к-сть індустрій | до 2 (приклад: e-commerce + technology) | ⟦j0HHLor-nmw⟧ |
| Advantage+ placements: claim Meta про CPA | −133% CPA при 6+ placements (на average, small businesses) | ⟦IYesh3616M0⟧ Meta-claim (CPA ≠ CPC; вводить в оману) |
| Combine social proof: покриття на момент відео | ~20% акаунтів автора | ⟦2D2ObSdXhdc⟧ |
| «Winner» за визначенням | топ-5% (1 з 20 оголошень) | ⟦TOII24BtKAo⟧ |
| Auction competition: референсні точки Meta | +20 = висока конкуренція, −20 = низька (0 = середня по платформі) | ⟦QUfjpZOlH28⟧ (pre-andromeda) |
| Auction overlap: приклад «здорового» числа | 1.68 (що нижче — то краще; високе = доставка ламається) | ⟦QUfjpZOlH28⟧ (pre-andromeda) |
| Розрив CPM Facebook vs Instagram (2023) | IG на ~20-40% дорожчий за FB | ⟦8IzbiiWnfLY⟧ (pre-andromeda, датований) |
| Опитування YouTube-аудиторії: «FB дає кращі результати за IG» | 76% | ⟦8IzbiiWnfLY⟧ (pre-andromeda) |
| Масштаб автора (контекст довіри) | $50M+ ($150M+ у пізніших відео) ad spend, 2000+ бізнесів, 9 років | ⟦OWYL-Mw-874⟧ ⟦TOII24BtKAo⟧ |

> ⚠️ **Meta-claims обережно.** «+46% інкрементальних конверсій» і «−133% CPA» — це заяви/дані Meta з її матеріалів, не незалежний замір. Особливо **−133%**: це **cost per action**, а не cost per conversion — на non-conversion кампаніях (traffic/engagement) «дешеві дії» на низькоякісних плейсментах роздувають метрику й НЕ означають кращий бізнес-результат. «+32% sales» — реальний кейс акаунта Ben, але частина приросту могла бути від простого **дублювання кампаній** (а не лише industry setting). ⟦IYesh3616M0⟧ ⟦j0HHLor-nmw⟧
> ⚠️ **Pre-Andromeda числа датовані.** Розрив CPM FB vs IG (20-40%) — зріз 2023 р., не поточний бенчмарк (механіка demand/supply за ним evergreen, конкретний % — ні). Auction-overlap 1.68 і auction-competition ±20 — референсні точки Meta з Inspect tool (інструмент і досі існує, але вага його впала з переходом на broad). ⟦QUfjpZOlH28⟧ ⟦8IzbiiWnfLY⟧

## Як було раніше і що змінилось
- ❌ Раніше (таргетинг): точний ручний таргетинг (вузькі інтереси / lookalike) в багатьох адсетах. ⟦superseded by broad — bv8AsY0xkIk @2026-05-06⟧
- ⚠️ Проміжно: чистий broad без можливості впливу на якість аудиторії.
- ✅ Зараз: **broad + Value Rules** (гібрид) — лишаєш гнучкість Meta, але впливаєш на бід під свою юніт-економіку. ⟦bv8AsY0xkIk @2026-05-06⟧
- ❌ Раніше **attribution = лише time-window для звітності** (35-day click тощо), що інформувало оптимізацію, але без поділу на інкремент. ⟦superseded by OWYL-Mw-874 @2025-08-03⟧
- ✅ Зараз з'явилось **incremental attribution** як ОПЦІЯ на рівні адсета — Meta оптимізує під конверсії, що не сталися б без реклами, і менше показує тим, хто купив би й так. Очікувано стане доступним для більшої к-сті objective (ймовірно leads). ⟦OWYL-Mw-874 @2025-08-03⟧
- ❌ Раніше «найважливіше налаштування» вважали **campaign objective**. ⟦superseded by WRyAUXjBlJM @2025-06-03⟧
- ✅ Зараз найважливіше — **performance goal** (саме він визначає оптимізацію); objective + conversion location лише задають, які performance goals доступні. ⟦WRyAUXjBlJM @2025-06-03⟧
- ❌ Раніше «automatic placements» — назва, що не «продавала». ⟦superseded by IYesh3616M0 @2025-06-03⟧
- ✅ Зараз перейменовано на **Advantage+ placements** (звучить як «перевага»), зроблено default, manual-плейсменти сховано глибше, а в деяких типах кампаній (Advantage+ Shopping / tailored leads) — взагалі зафіксовано. Це частина push'у Meta заповнювати ad inventory. ⟦IYesh3616M0 @2025-06-03⟧
- ⚠️ Куди йде далі: Meta системно додає **важелі контролю над оптимізацією** (value rules, incremental attribution, combine social proof, industry) — рекламодавцям дають «більше слова» в тому, як Meta оптимізує. Очікувати ще. ⟦OWYL-Mw-874 @2025-08-03⟧ ⟦2D2ObSdXhdc @2025-07-03⟧

### Передісторія: пошук «дешевшої аудиторії» вручну (era: pre-andromeda)
> Контекст: відео QUfjpZOlH28 і 8IzbiiWnfLY (обидва черв. 2023) — **до Andromeda**. Описують, як рекламодавець pre-Andromeda сам полював на менш конкурентні (дешевші) аудиторії/плейсменти через дані Inspect tool і розрив CPM між платформами. **Принцип** (ціна = аукціон попит/пропозиція; cost-per-result > проміжних сигналів) — evergreen і винесений вище у [P]. Нижче — pre-Andromeda **тактика/механіка**, що значною мірою **передана Meta** (broad/open сама шукає дешевших людей), хоч інструменти й досі існують для діагностики.
- ❌ Раніше (era: pre-andromeda) **робоча схема пошуку дешевої аудиторії:** запустити **5+ адсетів, по ОДНІЙ таргетинг-опції в кожному** → дати покрутитись → при оцінці перформансу зайти в **Inspect tool** (рівень адсета) і подивитись **auction competition** (наскільки конкурентна аудиторія: +20 висока / −20 низька / 0 середня) поряд із cost-per-conversion → лишити/масштабувати ті, де добрий CPA І низька конкуренція. ⟦QUfjpZOlH28 @2023-06-03⟧ ⟦superseded by bv8AsY0xkIk @2026-05-06⟧ (broad + value rules) → [[03-targeting/broad-vs-detailed]] · [[03-targeting/advantage-plus-audience]]
- ⚠️ Pre-Andromeda нюанси Inspect tool (значна частина досі валідна як **діагностика**, не як стратегія таргетингу):
  - **auction competition** не можна подивитись наперед — лише по адсетах, що **вже крутились** (не прогноз). Різкий стрибок/падіння графіка часто збігається з міткою «ad set targeting updated» (зміна таргетингу). ⟦QUfjpZOlH28 @2023-06-03⟧
  - **auction overlap** — наскільки ти **сам із собою** в одному аукціоні (дублі адсетів/таргетингу з того ж акаунта); Meta прибирає менш конкурентний адсет → погана доставка. Винесено вище як технічний бік [P] консолідації. ⟦QUfjpZOlH28 @2023-06-03⟧
  - **audience saturation + frequency** — діагностика ad fatigue: росте frequency й падають результати → пора міняти аудиторію/креатив. → [[10-measurement/diagnostics]]
  - використовуй auction competition як **зовнішній сигнал**: якщо вартість стрибнула/впала **без твоїх змін** — можливо, конкуренти зайшли/вийшли з аукціону за цю аудиторію. ⟦QUfjpZOlH28 @2023-06-03⟧
- ⚠️ Раніше (era: pre-andromeda) **деякі індустрії інхерентно дорожчі** — інколи дешеву аудиторію знайти легко, інколи майже неможливо (треба тестувати багато опцій). Лишається валідним і зараз як рамка очікувань. ⟦QUfjpZOlH28 @2023-06-03⟧
- ⚠️ Раніше (era: pre-andromeda) рекомендація **тримати FB+IG обидва й експлуатувати дешевший CPM на FB** (бо рекламодавці тікали в IG за перцепцією, а не за результатом). У post-Andromeda це частково **передано автоматиці** (на conversion-objective з обома платформами Meta сама діверсифікує бюджет туди, де результат кращий — див. «Контроль placements») — лишай обидві, не вимикай FB наосліп. Конкретний розрив 20-40% — **датований 2023**, не поточний бенчмарк; механіка «перцепція рекламодавців рухає CPM» — evergreen (винесена в [P]). ⟦8IzbiiWnfLY @2023-06-03⟧ → [[03-targeting/placements]] · [[06-creatives/instagram-ads]]

## Помилки / anti-patterns
- ❌ Вмикати value rules **без знання своїх цифр** (бід «зі стелі»). ⟦bv8AsY0xkIk @2026-05-06⟧
- ❌ Повертатись до старого вузького ручного таргетингу замість гібриду. ⟦bv8AsY0xkIk @2026-05-06⟧
- ⚠️ Свідомий трейд-оф: value rules можуть підняти **загальний CPA** (Meta прямо попереджає) — ок, якщо LTV-виграш більший. ⟦bv8AsY0xkIk @2026-05-06⟧
- ❌ **Вважати incremental attribution «лише звітом».** Це й оптимізація — вона змінює доставку. ⟦OWYL-Mw-874 @2025-08-03⟧
- ❌ **Перемкнути на incremental attribution, побачити нижчі topline-цифри й вирішити «стало гірше».** Рахується лише інкремент — реальний результат може бути кращим. Читай із поправкою. ⟦OWYL-Mw-874 @2025-08-03⟧
- ❌ **Панікувати, що все поза інкрементом — злив бюджету.** Експозиція/нагадування/AOV/бренд мають довгострокову цінність. ⟦OWYL-Mw-874 @2025-08-03⟧
- ❌ **Правильний objective + неправильний performance goal.** Обрати leads/sales, а потім поставити landing page views / link clicks / reach / impressions → кампанія працює як traffic/awareness, не оптимізує під конверсію. ⟦WRyAUXjBlJM @2025-06-03⟧
- ❌ **Лишати maximize number, коли цінності конверсій різні** (особливо sales з різними чеками) — втрачаєш value optimization. ⟦WRyAUXjBlJM @2025-06-03⟧
- ❌ **Задати industry й думати, що активні кампанії одразу оптимізуються інакше.** Діє лише на нові — треба дублювати/створювати. ⟦j0HHLor-nmw @2025-06-03⟧
- ❌ **Engagement-baiting заради соц-доказів** («лайкни/прокоментуй/поший») — порушує політику Meta, ризик для акаунта. Замість цього вмикай combine social proof. ⟦2D2ObSdXhdc @2025-07-03⟧
- ❌ **Прогрівати креатив через окрему engagement-кампанію, щоб потім запустити як sales-ad.** Engagement (відео-в'ю, «see more») — не = соц-докази; до того ж заздалегідь не знаєш, який креатив зайде → ризик злити гроші на «прогрів» оголошення, що не спрацює. Краще одразу sales/leads — winner набере соц-докази органічно. ⟦2D2ObSdXhdc @2025-07-03⟧
- ❌ **Advantage+ placements на non-conversion кампаніях** (traffic/engagement/awareness). Дасть дешеві, але низькоякісні дії (Audience Network) → роздуті метрики, гірший бізнес-результат. Там потрібні manual + якісні плейсменти. ⟦IYesh3616M0 @2025-06-03⟧
- ❌ **Сліпо вірити −133%-claim Meta про placements.** Це cost per **action**, не conversion; на non-conversion кампаніях дешеві кліки/в'ю не = продажі. ⟦IYesh3616M0 @2025-06-03⟧
- ❌ **Змінювати хук, «вижимаючи» winner.** Це вже нове оголошення, а не продовження життя переможця. ⟦TOII24BtKAo @2025-06-03⟧
- ❌ (era: pre-andromeda, досі валідно) **Тримати дублі адсетів/таргетингу в одному акаунті заради «тестів/масштабу»** → auction overlap, менш конкурентний адсет вимикається з аукціону, доставка ламається. ⟦QUfjpZOlH28 @2023-06-03⟧
- ❌ (era: pre-andromeda, досі валідно) **Дозволяти auction competition / saturation перекривати головну метрику.** Висока конкуренція за аудиторію з відмінним CPA — все одно лишай; cost-per-result у пріоритеті. ⟦QUfjpZOlH28 @2023-06-03⟧
- ❌ (era: pre-andromeda) **Ігнорувати Facebook і лити лише в Instagram** «бо IG крутіший/молодший» — це перцепція, що роздуває CPM IG; на конверсійній цілі лишай обидві платформи й користай дешевший FB-CPM. ⟦8IzbiiWnfLY @2023-06-03⟧

## Застосування в аналізі/оптимізації
- **Аудит таргетингу:** якщо акаунт на broad і є чітка LTV-різниця по демографії з CRM → рекомендувати value rule з **розрахованим** %, а не довільним. Розглядати conversion location / device / placement як value-важелі, якщо є дані по якості ліда (website lead > instant form тощо). ⟦bv8AsY0xkIk @2026-05-06⟧
- **Кандидати на incremental attribution:** sales/website/purchases-акаунти, що скаржаться на «надто багато warm-аудиторії / конверсій, що сталися б і так». Перед оцінкою результату — навчити клієнта читати інкрементальний звіт (topline впаде) і дивитись engaged-view. → [[00-philosophy/andromeda-era]].
- **Performance-goal аудит:** перевірити, що leads/sales-кампанії не стоять на landing page views / link clicks / reach (інакше це прихований traffic/awareness). Для sales з різними чеками — підняти до maximize value of conversions (за наявності value у Pixel). → [[02-objectives/leads-vs-sales-vs-traffic]].
- **Industry setting як швидкий win:** для акаунтів із «заплутаною» історією або поганою оптимізацією на Advantage+ Shopping — задати 1–2 максимально точні індустрії і **передублювати** кампанії; памʼятати, що частина приросту може бути просто від дублювання. → [[01-structure/asc-vs-manual]].
- **Combine social proof:** перевірити Advertising settings → Social information; якщо є й вимкнено — увімкнути (downside немає), особливо коли клієнт тестує багато варіацій.
- **Placement-аудит:** на conversion-кампаніях лишати Advantage+; на awareness/traffic/engagement — перемкнути на manual (feeds/stories/reels). Перевірити, чи клієнт не «купився» на −133%-claim. → [[03-targeting/placements]].
- **CPM/аукціон-діагностика (evergreen, з pre-Andromeda арсеналу):** при скарзі «CPM росте» — розбити **breakdown by platform** (FB vs IG; чи не сидить клієнт лише на дорожчому IG) і за потреби заглянути в **Inspect tool → auction competition** конкретного адсета (зовнішня конкуренція vs твої зміни) + **auction overlap** (чи нема дублів-кампаній, що б'ються самі з собою). Пам'ятати: це **діагностика**, не заміна broad-таргетингу; cost-per-result лишається головним. → [[10-measurement/diagnostics]] · [[10-measurement/spying-competitors]] · [[06-creatives/instagram-ads]]. ⟦QUfjpZOlH28 @2023-06-03⟧ ⟦8IzbiiWnfLY @2023-06-03⟧
- **Звʼязок:** [[03-targeting/advantage-plus-audience]] · [[03-targeting/broad-vs-detailed]] · [[03-targeting/placements]] · [[09-retargeting/retargeting-post-andromeda]] · [[00-philosophy/andromeda-era]] · [[00-philosophy/how-delivery-works]] · [[02-objectives/leads-vs-sales-vs-traffic]] · [[06-creatives/creative-strategy-volume]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "Keep the broad open targeting… but also please factor in this other bit of information." — Ben Heath ⟦bv8AsY0xkIk @2026-05-06⟧
> "Incremental attribution is all about incrementality… which conversions would not have taken place." — Ben Heath ⟦OWYL-Mw-874 @2025-08-03⟧
> "It absolutely is going to affect how Meta runs your ad campaigns." — Ben Heath ⟦OWYL-Mw-874 @2025-08-03⟧
> "You can completely undo that by selecting the wrong performance goal." — Ben Heath ⟦WRyAUXjBlJM @2025-06-03⟧
> "It's the performance goal that determines how the campaign will be optimized." — Ben Heath ⟦WRyAUXjBlJM @2025-06-03⟧
> "We know that that understanding leads to better campaign optimization." — Ben Heath ⟦j0HHLor-nmw @2025-06-03⟧
> "I would absolutely recommend that you come in here and tick this box." — Ben Heath ⟦2D2ObSdXhdc @2025-07-03⟧
> "Notice the wording. It's cost per action, not cost per conversion. They are different things." — Ben Heath ⟦IYesh3616M0 @2025-06-03⟧
> "Meta has ad inventory to fill." — Ben Heath ⟦IYesh3616M0 @2025-06-03⟧
> "When you find a winner, get as much, squeeze as much life out of it as you possibly can." — Ben Heath ⟦TOII24BtKAo @2025-06-03⟧
> "The cost of Facebook advertising is set by an auction. You are bidding against other advertisers." — Ben Heath ⟦QUfjpZOlH28 @2023-06-03⟧ (pre-andromeda)
> "To prevent you from bidding against yourself, we removed the less competitive ad set from the auction." — Meta (Inspect tool), цит. Ben Heath ⟦QUfjpZOlH28 @2023-06-03⟧ (pre-andromeda)
> "It's not the fact that they're getting better results on Instagram, it's the fact that advertisers think they're going to get better results — they're driving up the price." — Ben Heath ⟦8IzbiiWnfLY @2023-06-03⟧ (pre-andromeda)
