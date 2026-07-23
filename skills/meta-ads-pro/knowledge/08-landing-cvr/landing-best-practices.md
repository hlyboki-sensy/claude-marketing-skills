---
topic: "Landing/CVR-поверхня лід-кампаній: instant forms (lead forms) — будова, якість лідів, лід-магніт, тонкощі конверсії"
category: landing-cvr
subcategory: landing-best-practices
status: active
era: mixed
last_reviewed: 2026-06-03
confidence: medium
sources:
  - { id: pzcU1pAhmug, date: 2023-06-03, era: pre-andromeda }
  - { id: iQ9rRnKtrxY, date: 2023-06-03, era: pre-andromeda }
  - { id: l7Jr57qS5uo, date: 2023-06-03, era: pre-andromeda }
  - { id: 2L7MdGJAFV8, date: 2023-06-03, era: pre-andromeda }
  - { id: cdX-jtSwQoI, date: 2024-06-03, era: pre-andromeda }
  - { id: yKIe6JiDooI, date: 2024-06-03, era: pre-andromeda }
---

# Landing/CVR-поверхня лід-кампаній: instant forms

## TL;DR
«Landing» у Meta-лід-кампаніях — це не лише зовнішня сторінка, а й **instant form (lead form)** — нативна in-app поверхня конверсії, куди людина потрапляє після кліку. Ці 6 джерел (2023–24, **era: pre-andromeda**) детально описують саме **instant-form CVR**: як зробити форму, що дає багато дешевих лідів і не вбиває їх якість. Ключове, що тут **evergreen** (винесено в [P]): instant form ≠ просто форма — це **друга точка продажу** (треба переконати людину дати контакт і потім відповісти на дзвінок); проси **тільки необхідне** + **обов'язково phone number**; **privacy-policy URL обов'язковий**; congruent-зображення з оголошення; кожне покращення «продажу» в формі піднімає і кількість, і якість, і response rate. Pre-Andromeda **тактики/UI** (form types More volume vs Higher intent, build-your-story у Rich creative, lead filtering tool, View file для лід-магніту, sharing open) лежать у блоці «Як було раніше».

⚠️ **Era-застереження.** **Post-Andromeda ІСТИНА про conversion location та instant forms (2025-фічі: SMS-верифікація, autofill off, follow-up chat, additional actions, «не вибирати website vs instant form») живе у [[02-objectives/leads-vs-sales-vs-traffic]]** — не дублюю її тут. Цей файл — глибина на pre-Andromeda механіку форми. **Класичні website-landing-page CVR-практики (швидкість, above-the-fold, форма на сторінці) у цих 6 джерелах майже не розкриті** — «недостатньо даних», лише згадка, що сильний власний сайт може допомагати конверсії, а слабкий — навпаки. ⟦pzcU1pAhmug @2023-06-03⟧ ⟦l7Jr57qS5uo @2023-06-03⟧ ⟦cdX-jtSwQoI @2024-06-03⟧ ⟦2L7MdGJAFV8 @2023-06-03⟧

## Принципи [P]

### Instant form як точка конверсії (evergreen)
- [P] **Клік ≠ лід: форму ще треба «продати».** Те, що людина клікнула по оголошенню, не означає, що вона заповнить форму — особливо якщо просиш багато інфо. Instant form — окремий крок конверсії, де треба переконати людину дати контакт. Тому greeting/опис, що **підтверджують дію** і **пояснюють, що буде далі**, реально підіймають і conversion rate форми, і якість лідів. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Чим більше людина розуміє процес — тим охочіше робить наступний крок.** Наскрізна теза digital-маркетингу: невизначеність («а що далі?») — некомфортна, вона гальмує. Пояснити кроки (хто/коли зв'яжеться, що буде на дзвінку) у greeting і completion — знижує тертя і на рівні форми, і на рівні відповіді на наступний контакт. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧ ⟦cdX-jtSwQoI @2024-06-03⟧
- [P] **Проси тільки те, що реально потрібно (≈90% кейсів: name + email + phone).** Кожне зайве поле = більше тертя й менше лідів (людина на телефоні, відволіклась, не повернулась). Решту (адреса, вік об'єкта, деталі) збереш **на дзвінку** після того, як людина вже стала лідом. Виняток — коли треба фільтрувати великий потік. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Phone number — майже обов'язкове поле для сервісних офферів.** По самому email contact rate дуже низький (легко ігнорувати; листи летять у спам; людина не пам'ятає бренд). Телефон + швидкий дзвінок різко піднімає і дозвон, і конверсію в наступний крок. Бонус: **email у Facebook-профілі часто застарілий** (акаунт реєстрували 10+ років тому), а телефон люди міняють набагато рідше → ще одна причина брати phone. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Швидкість follow-up — частина CVR.** Часта прихована причина «погана якість лідів» — повільний дотиск (наприклад, обдзвін «двічі на тиждень»): лід від вівторка чекає до п'ятниці й вистигає. Дзвони якнайшвидше (sales-команда — 15–30 хв; як мінімум кілька батчів на день), поки інтерес свіжий. Це не про форму, а про систему обробки — але прямо б'є по конверсії ліда в клієнта. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Congruence «оголошення → форма» тримає людину.** Використовуй зображення з оголошення як фон форми: візуальна тяглість каже «ти в правильному місці». Якщо картинка/відчуття форми різко інші — частина людей (особливо хто не звик до instant forms / старша аудиторія) думає «я не туди клікнув» і виходить. Той самий принцип конгруентності діє і для зовнішніх landing-сторінок. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Privacy policy — non-optional для будь-якої лід-форми.** Рекламу без сайту запустити можна, а **лід-кампанію, що збирає контакти, без privacy-policy — ні**. Посилання має вести на **живу сторінку** (не PDF/jpeg/download). Сайт не обов'язковий — досить одної публічної сторінки з політикою. Special ad categories (фінанси/житло/страхування) потребують **custom disclaimer**. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Більше «продажу» в формі = вища і кількість, і якість, і response rate одночасно.** Раніше lead form був «надто базовим» — не давав по-справжньому продати наступний крок. Додавання benefits / how-it-works / соц-доказів / офера в форму дає більше причин і **дати контакт**, і **відповісти на дзвінок** (класична претензія «лід не бере слухавку» частково лікується саме тут). Та сама логіка, чому reviews всюди на Amazon і продажниках — вони працюють. ⟦cdX-jtSwQoI @2024-06-03⟧
- [P] **Якість лідів коштує кількості — це усвідомлений компроміс.** Будь-який крок «підняти якість» (review screen, lead filtering, зайве питання-кваліфікатор, більше тертя в формі) **зменшує обсяг і підіймає CPL** — часто вдвічі. Для бізнесу з sales-командою, що марнує час на «порожні» ліди, це виправдано; рішення приймається свідомо, дивлячись на economіку дзвінків, а не на сам CPL. ⟦2L7MdGJAFV8 @2023-06-03⟧ ⟦iQ9rRnKtrxY @2023-06-03⟧
- [P] **Якісніші ліди → можна вкласти більше ресурсу в їх конверсію → конверсія росте кратно.** Фільтруючи «таймвейстерів», команда вивільняє час на нурчинг тих, хто реально може купити; це не лише економія, а й важіль на сам conversion rate (бачили кратне зростання у клієнтів). ⟦2L7MdGJAFV8 @2023-06-03⟧
- [P] **Тримати конверсію in-app = точніші дані = краща оптимізація (post-iOS-14 логіка).** Коли людина не йде на зовнішній сайт, Meta «бачить» подію конверсії майже зі 100% точністю (на відміну від ~30%+ втрати на iOS при переході на сайт). Точніші дані в акаунті → Meta краще оптимізує доставку, і ти сам приймаєш кращі рішення (що вимкнути, який таргетинг). Накопичено в часі це відчутно покращує результат. Це pre-Andromeda обґрунтування, чому Meta штовхає instant forms. ⟦l7Jr57qS5uo @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [P] **Лід-магніт «прямо в формі» різко піднімає consumption rate.** Якщо віддавати файл (гайд/чек-лист/шаблон) одразу в instant form, а не листом, набагато більший % людей реально його отримає й перегляне (немає спам-фільтрів, deliverability, «зайду пізніше в пошту»). Ben очікував **подвоєння+ consumption rate** проти email. А чим більше людей справді спожили лід-магніт — тим більше їх готові до наступного кроку (логіка lead-magnet-стратегії). ⟦l7Jr57qS5uo @2023-06-03⟧
- [P] **Зворотний бік лід-магніту в формі: не будуєш email-list і «не тренуєш» відкриття листів.** Email-list — цінний актив, але його цінність **впала** через privacy-правила (не можна слати офери без згоди). Також: не віддаючи лід-магніт першим листом, ти не «привчаєш» людину відкривати твої листи (deliverability-розігрів). І ти **не ведеш людину на свій сайт** — мінус, якщо сайт добре продає; плюс, якщо сайт слабкий. Це pre-Andromeda компроміс. ⟦l7Jr57qS5uo @2023-06-03⟧
- [P] **«Share: open» перетворює оголошення на джерело органічних лідів.** Якщо оголошення шерять (бо воно цінне/вірусне, або людина знає того, кому продукт треба), людина, що побачила репост, теж має могти стати лідом. Хороший маркетинг провокує шери (приклад Dollar Shave Club) — глушити їх дефолтним «restricted» означає викидати безкоштовні ліди. ⟦yKIe6JiDooI @2024-06-03⟧

## Тактики зараз [T]
> ⚠️ Pre-Andromeda конкретика форми (form types, build-your-story, lead filtering, View file, sharing) — нижче у «**Як було раніше і що змінилось**», бо UI/підхід частково оновлені post-Andromeda. **Актуальні post-Andromeda налаштування instant forms (2025) і вибір conversion location** бери з [[02-objectives/leads-vs-sales-vs-traffic]].
- [T] **Базовий «скелет» форми, що тримається в часі (evergreen):** name + email + **phone** · greeting, що підтверджує дію + пояснює наступний крок · description у questions, що повторює дію · **privacy-URL (жива сторінка, не PDF)** · completion-екран «ми зв'яжемось протягом X, тримай телефон під рукою». ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [T] **Виставити систему швидкого обдзвону** (sales-команда 15–30 хв або кілька батчів/день) як частину CVR-плану ліда → клієнт. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [T] **Спліт-тестувати форми** (різні офери / копія / фон): для різних оферів — різні оголошення + різні форми; навіть копію в формі можна тестувати кількома версіями одночасно. → дет. тестування [[12-testing/post-andromeda-testing]]. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- [T] **На лід-кампанії — conversion-style налаштування доставки:** optimize **for leads** (не landing page views / traffic — Meta дасть саме те, що просиш: клікнуть-і-підуть); placements — **Advantage+** (бо оптимізація під конверсію сама відсіє погані плейсменти). ⟦pzcU1pAhmug @2023-06-03⟧ → [[03-targeting/placements]] · [[05-optimization/optimization-events]].
- [T] **Тестувати instant form проти website** як conversion location — обидва варто перевірити (post-iOS-14 Ben схиляється до instant form через трекінг). АЛЕ актуальний хід — **новий свіч «оптимізувати під будь-який з двох»** → бери з [[02-objectives/leads-vs-sales-vs-traffic]]. ⟦pzcU1pAhmug @2023-06-03⟧

## Числа / бенчмарки
| Факт | Значення | Джерело |
|---|---|---|
| Типове поле-сетап форми | name + email + phone (~90% кейсів) | ⟦iQ9rRnKtrxY⟧ ⟦pzcU1pAhmug⟧ |
| Приклад CPL сервісного ліда (instant form) | часто < $10 (іноді значно менше) | ⟦pzcU1pAhmug⟧ |
| Ефект ввімкнення lead filtering / review screen на CPL | може **подвоїти** CPL (коштом обсягу) | ⟦2L7MdGJAFV8⟧ ⟦iQ9rRnKtrxY⟧ |
| Очікуваний приріст consumption rate лід-магніту (форма vs email) | ~×2 і більше (рання оцінка Ben) | ⟦l7Jr57qS5uo⟧ |
| Втрата трекінгу при переході на сайт (iOS) | ~30%+ подій неточні/втрачені | ⟦l7Jr57qS5uo⟧ ⟦pzcU1pAhmug⟧ |
| Privacy-policy посилання | обов'язкове; жива сторінка, НЕ PDF/jpeg/download | ⟦iQ9rRnKtrxY⟧ ⟦pzcU1pAhmug⟧ |
| Рекоменд. к-сть live адсетів / ads на адсет (lead-кампанія) | ≤5 адсетів; 3–4 ads на адсет | ⟦pzcU1pAhmug⟧ |
| Benefits у Rich creative (overview / per-card) | 2–3 унікальні бенефіти | ⟦cdX-jtSwQoI⟧ |
| Рекоменд. фон форми (aspect) | 1200×628 px (або картинка з оголошення) | ⟦iQ9rRnKtrxY⟧ ⟦pzcU1pAhmug⟧ |
| Done-for-you мін. бюджет Ben (контекст епохи) | $3K/міс | ⟦l7Jr57qS5uo⟧ ⟦iQ9rRnKtrxY⟧ |

> ⚠️ Числа — pre-Andromeda приклади/оцінки Ben (CPL < $10, ×2 consumption, ~30% iOS-втрата, «подвоєння CPL» від фільтра), **ілюстративні, не універсальні бенчмарки**. Налаштування доставки epoch-2023 (Advantage campaign budget on, manual placements тільки для traffic) частково застаріли — звіряти з post-Andromeda структурою [[01-structure/campaign-structure]].

## Як було раніше і що змінилось
> Контекст: усі 6 джерел — **pre-Andromeda (2023–24)**. Post-Andromeda стан instant forms (2025-фічі) і вибір conversion location — у [[02-objectives/leads-vs-sales-vs-traffic]]; нижче — pre-Andromeda **специфіка форми**, з якої воно виросло.

- ❌ Раніше (era: pre-andromeda): **form type More volume vs Higher intent** як головний важіль якості. *Higher intent* додавав **review screen** («ви впевнені?») — менше лідів, але якісніших; *More volume* (дефолт) — навпаки. Рекомендація: старт із **More volume**, перемикатись на Higher intent лише якщо sales-команда не дозвонюється/ліди не конвертять. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧ → ✅ post-Andromeda якість лідів адресують **SMS-верифікацією + autofill off** (новіші важелі) → [[02-objectives/leads-vs-sales-vs-traffic]]. ⟦superseded by leads-vs-sales 2025-фічі⟧
- ❌ Раніше (era: pre-andromeda): **Lead filtering tool** — multiple-choice питання (класика: «бюджет»: <$1k / $1k–5k / $5k+) з тогглом lead filtering: відповіді нижче порогу → людина **не стає лідом**, бачить окремий «не підходимо» thank-you екран. Свідомий розмін якості на кількість (CPL міг подвоїтись). ⟦2L7MdGJAFV8 @2023-06-03⟧ → ⚠️ Концептуально лишається валідним способом кваліфікації; перевір наявність/оновлення інструмента в поточному UI.
- ❌ Раніше (era: pre-andromeda): **Rich creative form type** (2024) — у форму можна було додати **benefits** (2–3), **build-your-story** (how it works / get started / more about us / how we're different / highlights), **product/service cards** (карусель-стиль), **social proof** (reviews / accredited by / in the news), **incentive** (= offer + «good until» дата + disclaimer). Сильно «продавало» наступний крок; Ben бачив у ранніх тестах покращення якості лідів. Компроміс: трохи вищий CPL (більше читати). АЛЕ: Rich creative **прибирав review screen** → з Higher intent несумісний; радив спліт-тест Rich creative vs Higher intent. ⟦cdX-jtSwQoI @2024-06-03⟧ → ✅ post-Andromeda підтверджено спліт-тестами, що form type / image / Rich creative помітно рухають обсяг, CPL і якість → [[02-objectives/leads-vs-sales-vs-traffic]].
- ❌ Раніше (era: pre-andromeda): **лід-магніт через email** з landing-сторінкою + CRM. ✅ Новіше (з 2023): **View file** CTA у completion → віддати PDF/PNG/JPEG **прямо в формі**, без сайту/CRM. Плюси: вищий consumption, менше саппорту («не прийшов файл» = спам), не треба landing-сторінки/девелопера, точніші дані. Мінуси: не будуєш email-list, не «тренуєш» відкриття листів, не ведеш на сайт. → ✅ post-Andromeda View file лишається серед **additional actions** після сабміту → [[02-objectives/leads-vs-sales-vs-traffic]]. ⟦l7Jr57qS5uo @2023-06-03⟧
- ❌ Раніше (era: pre-andromeda) **сховане налаштування `sharing: restricted` за замовчуванням** у формі (вкладка Settings, не Content): тільки той, кому Meta показала оголошення напряму, міг сабмітнути форму — репости «вмирали». Виправлення: **перемкнути на `open`** → люди, що побачили оголошення через шер, теж стають лідами (часто органічні/безкоштовні). Нюанс звітності: ліди в Ads Manager **не зміняться** (рахуються тільки прямі з реклами), але в експорті файлу / CRM з'явиться колонка ads vs organic і більше лідів. Fringe-виняток для `restricted` — офер «тільки для нових клієнтів». ⟦yKIe6JiDooI @2024-06-03⟧ → ⚠️ У post-Andromeda матеріалах база **не згадує** це налаштування — лишаю як pre-Andromeda нюанс, що варто перевіряти в актуальному UI.
- ⚠️ Раніше (era: pre-andromeda) типові **delivery-дефолти лід-кампанії**: Advantage campaign budget **on**, daily budget (не lifetime — Meta «з'їдає» останні ~15% lifetime-бюджету), optimize **for leads**, Advantage+ placements. Daily-vs-lifetime лишилось evergreen (див. [[04-budget-scaling/big-spend-scaling]]), решта структури — звіряти з post-Andromeda [[01-structure/campaign-structure]]. ⟦pzcU1pAhmug @2023-06-03⟧

## Помилки / anti-patterns
- ❌ **Лишати `sharing: restricted`** (дефолт) у формі — вбиваєш органічні ліди від шерів. Майже завжди треба `open`. ⟦yKIe6JiDooI @2024-06-03⟧
- ❌ **Forма без поля phone** для сервісного офера — по email майже не дозвонишся/не достукаєшся. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- ❌ **Напхати зайвих питань** (адреса, вік об'єкта, демографія) у форму — тертя, менше лідів; збери це на дзвінку. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- ❌ **Повільний follow-up** (обдзвін «двічі на тиждень») і потім скарга «ліди погані» — лід вистигає; дзвони якнайшвидше. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- ❌ **Запускати лід-кампанію без privacy-policy URL** (або вести лінк на PDF) — форма не запуститься. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- ❌ **Різке/непов'язане зображення форми** vs оголошення — людина думає «не туди клікнув» і виходить. ⟦iQ9rRnKtrxY @2023-06-03⟧ ⟦pzcU1pAhmug @2023-06-03⟧
- ❌ **Оптимізувати лід-кампанію під landing page views / traffic** (як радять деякі Meta-репи) — Meta приведе тих, хто клікне й піде; оптимізуй **for leads**. ⟦pzcU1pAhmug @2023-06-03⟧
- ❌ **Лишати форму «базовою»**, коли є Rich creative — не використовуєш безкоштовний важіль «продати» наступний крок (benefits/соц-доказ/офер). ⟦cdX-jtSwQoI @2024-06-03⟧
- ❌ **Вмикати фільтри якості (Higher intent / lead filtering), не дивлячись на economіку** — отримаєш менше лідів і вищий CPL; виправдано лише коли sales-час дорогий. ⟦2L7MdGJAFV8 @2023-06-03⟧ ⟦iQ9rRnKtrxY @2023-06-03⟧
- ❌ **Чекати на «leads generated» в Ads Manager** після ввімкнення sharing=open і дивуватись, що число те саме — органічні ліди видно в **експорті/CRM**, не в Ads Manager. ⟦yKIe6JiDooI @2024-06-03⟧

## Застосування в аналізі/оптимізації
- **Аудит instant form:** є phone? form type/«fрикція» адекватні меті (More volume на старті, фільтри — лише якщо дорогий sales-час)? privacy-URL живий (не PDF)? фон конгруентний оголошенню? не напхано зайвих питань? completion готує до дзвінка? `sharing = open`? Якщо «тестують» дрібні правки форми — нагадати: форму не редагують, а **дублюють** нову версію. → [[02-objectives/leads-vs-sales-vs-traffic]].
- **«Ліди погані» — діагностика по порядку:** (1) швидкість follow-up (часто головне); (2) form type/фільтри (чи не на More volume без жодної кваліфікації при дорогому продукті); (3) офер/копія форми (чи продає наступний крок); (4) congruence оголошення→форма. → [[10-measurement/diagnostics]] · [[06-creatives/why-ads-fail]].
- **Лід-магніт-кампанія:** розглянути **View file** прямо в формі (вищий consumption, менше саппорту) проти класичного email-list (актив, але менш цінний post-privacy) — вибір за тим, наскільки цінний список і чи сильний сайт. → [[09-retargeting/retargeting-post-andromeda]] (ретаргет тих, хто відкрив, але не сабмітнув).
- **Conversion location (instant form vs website):** не вирішувати наперед — порадити **post-Andromeda свіч «оптимізувати під будь-який»** і тестувати; класичний website-landing CVR (швидкість/above-the-fold/форма на сторінці) ці джерела не покривають — «недостатньо даних». → [[02-objectives/leads-vs-sales-vs-traffic]].
- **Звʼязок:** [[02-objectives/leads-vs-sales-vs-traffic]] · [[02-objectives/choosing-objective]] · [[06-creatives/local-business]] · [[06-creatives/why-ads-fail]] · [[10-measurement/diagnostics]] · [[09-retargeting/retargeting-post-andromeda]] · [[12-testing/post-andromeda-testing]] · [[01-structure/campaign-structure]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "You haven't yet sold the lead. You need to convince someone to go on and take those next steps." — Ben Heath ⟦iQ9rRnKtrxY @2023-06-03⟧ (pre-andromeda)
> "The more people understand the process, the more willing they are to take the next step." — Ben Heath ⟦iQ9rRnKtrxY @2023-06-03⟧ (pre-andromeda)
> "I absolutely recommend you put in your phone number… you want to call them and you want to call them as quickly as possible." — Ben Heath ⟦iQ9rRnKtrxY @2023-06-03⟧ (pre-andromeda)
> "You can run Facebook ads without a website… but you cannot run ads designed to generate leads without a privacy policy." — Ben Heath ⟦iQ9rRnKtrxY @2023-06-03⟧ (pre-andromeda)
> "I always felt the lead form was a little bit basic… with Rich creative we absolutely can [sell]." — Ben Heath ⟦cdX-jtSwQoI @2024-06-03⟧ (pre-andromeda)
> "I wouldn't be surprised if it doubles or more the actual consumption rate of your lead magnet." — Ben Heath ⟦l7Jr57qS5uo @2023-06-03⟧ (pre-andromeda)
> "Whenever I'm running an ad campaign I don't want anything to do with it to be restricted… the vast majority want to go with open." — Ben Heath ⟦yKIe6JiDooI @2024-06-03⟧ (pre-andromeda)
> "Whenever you're trying to improve lead quality there's always going to be a cost… in this case it's going to be lead quantity." — Ben Heath ⟦2L7MdGJAFV8 @2023-06-03⟧ (pre-andromeda)
> "You get what you ask for. If you want leads, optimize for leads." — Ben Heath ⟦pzcU1pAhmug @2023-06-03⟧ (pre-andromeda)
</content>
</invoke>
