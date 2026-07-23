---
topic: "Структура кампанії post-Andromeda — рівні Advantage+, консолідація cold+warm, controls vs suggestions"
category: structure
subcategory: campaign-structure
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: 13s-G9Uj51A, date: 2026-03-03, era: post-andromeda }
  - { id: 6avwp4gBZsQ, date: 2025-06-03, era: post-andromeda }
  - { id: 1Or1B4L_bdY, date: 2025-12-03, era: post-andromeda }
  - { id: FiZ9IEQteMU, date: 2026-03-03, era: post-andromeda }
  - { id: cqNsMJPoM7c, date: 2024-06-03, era: pre-andromeda }
  - { id: _TkJrNLeNwM, date: 2024-06-03, era: pre-andromeda }
  - { id: X6TjkMH_r2I, date: 2023-06-03, era: pre-andromeda }
---

# Структура кампанії post-Andromeda

## TL;DR
Advantage+ кампанії **переінженерили**: ASC (Advantage Plus Shopping) перейменовано на **Advantage Plus Sales**, повернулися **три рівні** (campaign / adset / ad) замість злитих двох, а діапазон Advantage+ розширили на **leads** (та інші objectives). Нова дефолтна структура — **консолідація** до мінімуму: часто **одна кампанія + один адсет**, у який складено **20+ різнопланових оголошень**. Cold і warm більше **НЕ розділяємо** (custom audiences тепер у *suggest an audience*, тож Meta усе одно змішує). Воронку Meta **секвенсує сама** в межах одного адсета. Розділяємо лише за **локацією** (hard boundary в *controls*) і **за продуктом/послугою** (різна оптимізація). Усередині адсета з'явились ключові важелі: **controls vs suggest-an-audience**, **further limit reach → manual**, **campaign score**, **audience segment reporting**, **ad scheduling** (тільки через lifetime budget), **placement controls**, **value rules**, **performance goal**, **automated rules**. ⟦13s-G9Uj51A @2026-03-03⟧ ⟦6avwp4gBZsQ @2025-06-03⟧

## Принципи [P]
- [P] **Три рівні повернулись.** В Advantage+ Sales знову є campaign / adset / ad level. ASC раніше зливала campaign+adset у два рівні з дуже обмеженим таргетингом; тепер «традиційна» структура з трьома рівнями, хоч елементи переставлені. ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **Manual ще існує, але дефолт — Advantage+.** Manual sales campaign і «manual sales з Advantage+ audience» раніше були РІЗНИМИ речами (рекламодавці плутали); тепер вони фактично злиті в одне, плюс лишилась окрема manual-опція. Manual важче в користуванні й потребує **дуже вагомої причини** — не дефолтитись на нього. ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **Controls = hard boundaries, suggest-an-audience = м'які підказки.** Локація/age/gender/custom audiences у *controls* — Meta здебільшого НЕ виходить за межі; ті ж параметри в *suggest an audience* — лише підказка, Meta робить своє. Тому чесне A/B можливе лише за параметрами з *controls*. ⟦13s-G9Uj51A @2026-03-03⟧ ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **Suggestions майже не мають мінусів.** Додавання suggestions (інтереси, age, custom/lookalike) не звужує аудиторію — Meta може їх проігнорувати (тоді ти там само, де ASC без таргет-інпутів) або «навести алгоритм» у потрібний бік. Особливо корисні **off-Meta custom audiences** (напр. email-список покупців за 3 роки) — їх Meta сама не знайде, якщо людина не заходила на сайт і немає піксель-сигналу. Тому campaign score від suggestions не падає. ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **Не розділяй cold і warm за замовчуванням.** Custom audiences (warm) живуть у *suggest an audience*, тож Meta однаково таргетить і cold, і warm — окремі адсети/кампанії під них дають великий overlap. Поки не зайдеш у *further limit the reach* і не знімеш suggestion з custom audience, твій «retargeting adset» насправді — «both adset» (cold+warm). ⟦13s-G9Uj51A @2026-03-03⟧ ⟦1Or1B4L_bdY @2025-12-03⟧
- [P] **Консолідуй дані в якомога меншу к-сть елементів.** Більше конверсій в одному адсеті → Meta повноцінно виходить з learning phase і краще оптимізує (час доби, частота показів, кому й який креатив показати). *Evergreen — той самий аргумент вже звучав pre-Andromeda: $100/день на 4 адсети = ~$25/адсет «вчиться» повільно; той самий бюджет в одному адсеті вчиться набагато швидше й дає кращий перформанс.* ⟦13s-G9Uj51A @2026-03-03⟧ ⟦cqNsMJPoM7c @2024-06-03⟧
- [P] **Auction overlap ≠ audience overlap.** Проблема не в тому, що «бідиш сам проти себе» (міф — тисячі рекламодавців і так конкурують за тих людей), а в тому, що розкидані по адсетах покази заважають Meta спланувати оптимальну **частоту на юзера** (напр. 4–5 показів за 24–48 год). *Evergreen — pre-Andromeda це формулювалось так: коли кілька адсетів того самого рекламодавця заходять в один аукціон, доставка одного/обох страждає (ростуть CPM або адсет не докручує бюджет, бо Meta «плутається»).* ⟦13s-G9Uj51A @2026-03-03⟧ ⟦cqNsMJPoM7c @2024-06-03⟧
- [P] Логіка воронки **top/mid/bottom funnel лишається валідною з маркетингового боку** (познайомити з ідеєю → прогріти доказами → CTA-оголошення й відгуки) — змінилося лише ТЕ, що тепер це робиться в межах ОДНОГО адсета, а не в окремих кампаніях. Meta достатньо «розумна», щоб секвенсувати сама. *Pre-Andromeda та сама воронкова логіка реалізовувалась РУЧНОЮ структурою: lead-magnet кампанія → окрема retargeting-кампанія; omnipresent content — десятки «content»-оголошень на ту саму людину для прогріву.* ⟦13s-G9Uj51A @2026-03-03⟧ ⟦X6TjkMH_r2I @2023-06-03⟧
- [P] **Performance goal не менш важливий за campaign objective.** Objective лише звужує опції; саме performance goal диктує, як Meta оптимізує. Розрив у розумінні: про важливість objective знають, про важливість performance goal — є лаг. ⟦FiZ9IEQteMU @2026-03-03⟧
- [P] **Campaign score (=opportunity score на рівні кампанії)** — підказка Meta «налаштуй ось так». 100 = усі рекомендовані налаштування. Кореляція з результатом НЕ повна: бувають успішні кампанії з нижчим score і слабші з вищим. Але в середньому: низький score + поганий результат → підняття score зазвичай покращує результат. ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **Один кампейн на продукт/послугу-рейндж** (evergreen, не змінилось pre→post). Дробити споріднені продукти/варіації по різних кампаніях шкідливо: вони таргетять тих самих людей зі схожим офером → конкуренція кампаній між собою + ad fatigue. Розводити в різні кампанії варто лише **по-справжньому різні** рейнджі (shoes vs hats — окремо; пари різних shoes — разом). ⟦X6TjkMH_r2I @2023-06-03⟧ ⟦cqNsMJPoM7c @2024-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧
- [P] **Warm-аудиторії малі й швидко «вигорають».** Warm-сегмент майже завжди значно менший за cold; на нього легко **перевитратити** бюджет (спершу дає чудові результати) і випалити. Pre-Andromeda це вирішували, кладучи warm-адсет у CBO-кампанію разом з cold (Meta авто-балансувала бюджет; warm авто-ростив із розширенням бази); post-Andromeda warm живе в *suggest an audience* того ж адсета. Сам факт «warm маленький і вигорає» — evergreen. ⟦X6TjkMH_r2I @2023-06-03⟧
- [P] **Не перевантажуй систему навчання Meta.** Забагато змінних одночасно (десятки оголошень × десятки адсетів × багато опцій) → під час learning Meta тестує «не те з тим», результати просідають. Завжди — баланс «достатньо тестувати, але не топити алгоритм». *Pre-Andromeda стелі були нижчі (≤5–6 оголошень/адсет; не 20 адсетів/кампанію); post-Andromeda стеля піднялась (20+ оголошень), але сам принцип балансу лишається.* ⟦X6TjkMH_r2I @2023-06-03⟧ ⟦cqNsMJPoM7c @2024-06-03⟧ ⟦_TkJrNLeNwM @2024-06-03⟧

## Тактики зараз [T]

### Базова структура
- [T] **Дефолт структури:** одна кампанія + один адсет + багато оголошень всередині. Розгортати ширше лише за чіткою причиною (нижче). ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **20+ оголошень в адсеті** — тепер не лише допустимо, а й рекомендовано: Meta хоче креативного різноманіття (image+video, UGC, founder, demonstration, customer testimonial), щоб тестувати й **персоналізувати доставку** під людину. Верхньої межі автор не ставить — обмежує лише к-сть якісних оголошень. ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **Воронку складай в один адсет:** частину оголошень як top-funnel (founder/story), частину mid (product demo), частину bottom (testimonial / CTA) — Meta сама вибудує послідовність (одні крутить першими, інші в ретаргет-ролі). ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **Тестуй копірайт через variations, НЕ через окремі оголошення:** до **5 варіантів** primary text, **5** headline, **5** description в межах ОДНОГО оголошення (рівень ad → блок копірайту → клік у поле → «1 of 5»). Окремі оголошення лишай для різного КРЕАТИВУ. ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **Розділяй за локацією** (часто): різні країни/локації (US vs UK vs Australia; міста франшизи) — в окремих адсетах/кампаніях, бо локація в *controls* = hard boundary і дає чесний спліт. Якщо бізнес обслуговує одну країну й готовий лити на всю — не морочитися. ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **Одна кампанія на продукт/послугу-рейндж** (не на варіацію): hats vs shoes — окремо; red hats vs blue hats — разом. ⟦13s-G9Uj51A @2026-03-03⟧ ⟦X6TjkMH_r2I @2023-06-03⟧
- [T] **Виняток — dynamic catalog campaign:** загальну каталожну кампанію з відносно малим бюджетом можна тримати business-wide, бо Meta витратить більшість бюджету на ретаргет. ⟦13s-G9Uj51A @2026-03-03⟧

### Рівень адсета: audience controls vs suggestions
- [T] **Верхній перемикач audience:** *Find prospective customers even if they haven't interacted* (дефолт, для більшості) vs *Retarget ads to people who interacted*. Для більшості бізнесів — перша опція (ретаргет усе одно частково буде). ⟦6avwp4gBZsQ @2025-06-03⟧
- [T] **Секція Controls (hard boundaries):** location (радіус/штат/країна/міжнар.); *show more controls* → minimum age (до 25, для age-restricted продуктів), exclude custom audiences, languages, **exclude catalog interactions**. ⟦6avwp4gBZsQ @2025-06-03⟧
- [T] **Секція Suggest an audience (м'які):** custom/lookalike audiences, age range, gender, detailed targeting — як підказки. Додавати охоче, особливо off-Meta custom audiences. ⟦6avwp4gBZsQ @2025-06-03⟧
- [T] **Перехід у manual:** *further limit the reach of your ads* → *switch setup*. Тоді з'являються чекбокси **use as suggestion** біля age/gender/custom audience — зніми галочку, щоб зробити параметр hard boundary. **Detailed targeting** — єдиний, де suggestion **зняти НЕ можна** (detailed targeting expansion завжди ON). ⟦6avwp4gBZsQ @2025-06-03⟧ ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Справжній retargeting-only адсет:** зайди в *further limit the reach* → додай custom audience → зніми *use as suggestion* → тоді ads ідуть ЛИШЕ цій warm-аудиторії (напр. website visitors 180 днів, або email-список тих, хто завантажив lead magnet, для upsell). ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Більше підстав для таргет-інпутів у LEADS, ніж у Sales:** у sales Meta оптимізує на purchase value — «дай мені більше таких»; у leads є питання **якості** — можеш свідомо платити більше за лід, генерувати менший обсяг, але з кращою конверсією. Можна додати suggestions або поекспериментувати з manual; для кращих даних — conversion leads. ⟦6avwp4gBZsQ @2025-06-03⟧

### Performance goal (важіль оптимізації на рівні адсета)
- [T] **Maximize value of conversions** замість *maximize number of conversions*: щоб з'явилось — спершу зміни conversion location з *website and calls* (multiple) на **single → website**. Тоді Meta фаворить тих, хто не лише купить, а й **витратить більше** — менше продажів, але вищий загальний value/ROAS. ⟦FiZ9IEQteMU @2026-03-03⟧
- [T] **Для e-commerce — no-brainer:** value кожної покупки вже передається з Shopify назад у Meta. Особливо важливо за **сильно різних чеків** ($20 vs $200; $100 vs $2000). Якщо все продається за одну ціну й купують раз — сенсу мало (тоді перший workон — додати upsell). ⟦FiZ9IEQteMU @2026-03-03⟧
- [T] **Для leads — складніше:** треба оцінити вартість ліда на момент його створення й передати назад. (а) Різні послуги → різні landing/thank-you pages → різні conversion events з різними values (напр. roof replacement $20k×конв.1/5=$4k/лід vs repair $2k×50%=$1k/лід). (б) Одна послуга → форма з drop-down по бюджету: низький бюджет → одна thank-you page, високий → інша, кожній — свій conversion value. Потрібні **Meta Pixel + Conversions API**. ⟦FiZ9IEQteMU @2026-03-03⟧
- [T] **Чотири нижні опції performance goal НЕ для leads/sales:** landing page views / link clicks = по суті traffic; unique reach / impressions = по суті awareness. ⟦FiZ9IEQteMU @2026-03-03⟧

### Інші структурні налаштування адсета/кампанії
- [T] **Audience segment reporting** (рівень кампанії): визнач *engaged audiences* (хто дивився відео/взаємодіяв) та *existing customers* (попередні покупки) — НЕ змінює таргетинг, лише дає у звітах розбивку бюджету на cold / warm / retargeting. ⟦6avwp4gBZsQ @2025-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **Ad scheduling** — тільки через **lifetime budget**: campaign level → змінити daily на lifetime → *show more settings* → ad set scheduling → *deliver ads at all times* змінити на *set a schedule*; потім adset level → budget&schedule → show more settings → *run ads on a schedule* → намалювати сітку годин/днів. Класичний кейс — B2B leads 9:00–17:00 Пн–Пт (speed to lead). Для sales сенсу менше (покупка о 2:00 в суботу так само цінна); для leads — так (лід уночі ≠ лід вдень). ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Placement controls** (тепер сховані): adset → *show more settings* → *placement controls*. Можна прибрати цілі платформи (лишити лише Instagram) або окремі placements (feeds/stories/reels). **Дефолт лишати** (Advantage+ placements) для conversion-based (sales/leads); **обов'язково лізти й чистити** для traffic/awareness — насамперед вимкнути **audience network** (найдешевший і найнижчоякісніший трафік). ⟦1Or1B4L_bdY @2025-12-03⟧ ⟦6avwp4gBZsQ @2025-06-03⟧
- [T] **Combine social proof:** All tools → Advertising settings → Social information → *Combine likes and reactions for similar ads* — переконатись, що ON. Лайки/реакції зі схожих оголошень складаються в одне число (важливо, бо тестуєш багато схожих варіацій, і «2 лайки тут, 4 там» виглядає гірше за об'єднані 300). Майже завжди тільки плюс. ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Optimize text per person** (рівень ad): з'являється, коли увімкнено standard enhancements. Meta тасує primary text / headline / description і добирає **комбінацію під КОЖНУ людину** (не «найкраще в середньому»). Дай до **5 primary + 5 headline + опис** — більше опцій = краща персоналізація. Обережно у **зарегульованих індустріях** (перестановка тексту може порушити вимоги регулятора). ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Automated rules** (рівень кампанії/адсета/оголошення): … → More → Automated rules → Create new rule. Apply to: all active campaigns / ads / adsets (або конкретні). Дії: turn off/on, increase/decrease daily|lifetime budget, send notification. Допомагає, коли (а) кампаній забагато для ручного контролю; (б) рекламодавець не може стриматись «тинкерити» (аналогія з index-fund інвестуванням). Деталі scaling-сетапу → [[04-budget-scaling/big-spend-scaling]]. ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Value rules** (рівень адсета): зважити бід на цінніші сегменти (age/gender/location/device/placement/conversion location). Деталі й приклади → [[03-targeting/value-rules]]. ⟦1Or1B4L_bdY @2025-12-03⟧
- [T] **Apply-кнопки campaign score:** коли score падає через ручні зміни (напр. вибрані конкретні placements), Meta показує кнопку *Apply* — один клік повертає рекомендоване, без ручного лазіння. ⟦6avwp4gBZsQ @2025-06-03⟧
- [T] **Розмічай аудиторні сегменти** для звітів: All tools → Advertising settings → Audience segments → визнач engaged / existing (підвʼязавши custom audiences) → у звітах видно new / engaged / existing. ⟦13s-G9Uj51A @2026-03-03⟧
- [T] **Свідомо ігноруй warnings Meta**, коли відходиш від дефолту за конкретною стратегією — але саме свідомо. Warnings зроблені «для маси» / в середньому. ⟦13s-G9Uj51A @2026-03-03⟧

## Числа / бенчмарки
| Параметр | Значення | Джерело |
|---|---|---|
| Рівні в Advantage+ Sales | 3 (campaign / adset / ad) — повернулись | ⟦6avwp4gBZsQ @2025-06-03⟧ |
| Дефолтний campaign score (порожній сетап) | 88 (з прикладу) | ⟦6avwp4gBZsQ @2025-06-03⟧ |
| Приріст score за доданий catalog (приклад) | +12 пунктів | ⟦6avwp4gBZsQ @2025-06-03⟧ |
| «Штраф» за відхід від Advantage+ audience (Meta-claim) | ~33% вищий cost per result у середньому | ⟦6avwp4gBZsQ @2025-06-03⟧ |
| «Штраф» manual targeting (Meta-claim, інший приклад) | 7.2% вищий CPR | ⟦1Or1B4L_bdY @2025-12-03⟧ |
| «Штраф» за прибирання suggestions / retargeting-only (Meta-claim) | 42% вищий CPR у середньому | ⟦1Or1B4L_bdY @2025-12-03⟧ |
| Minimum age у controls | до 25 (для age-restricted продуктів) | ⟦6avwp4gBZsQ @2025-06-03⟧ |
| Варіантів primary text для optimize-text-per-person | до 5 | ⟦1Or1B4L_bdY @2025-12-03⟧ |
| Рекоменд. к-сть оголошень в адсеті | 20+ (верхньої межі автор не ставить) | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Стара рекомендація Meta по оголошеннях | не тримати 5–6 live в адсеті (застаріло) | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Варіацій тексту в одному оголошенні | до 5 primary / 5 headline / 5 description | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Оптимальна частота на юзера (приклад) | 4–5 показів за 24–48 год | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Дефолт кампаній/адсетів | часто 1 кампанія + 1 адсет | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Поріг «involved purchase» для omnipresent | high-ticket $10k–$20k послуга | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Приклад розбивки конверсій (1 адсет) | 93 = 20 new + 9 engaged + 59 existing + решта unknown | ⟦13s-G9Uj51A @2026-03-03⟧ |
| Приклад розрахунку lead value (roof) | replacement $20k×1/5=$4k/лід; repair $2k×50%=$1k/лід | ⟦FiZ9IEQteMU @2026-03-03⟧ |
| Роллаут нової структури Advantage+ | стейджено ~6 міс (з ~черв. 2025) | ⟦6avwp4gBZsQ @2025-06-03⟧ |
| _pre-A_ Direct-offer: адсети | 5 = 1 warm + 4 cold (2 interest + 2 lookalike) | ⟦X6TjkMH_r2I @2023-06-03⟧ |
| _pre-A_ Оголошень/адсет (звичайні ads) | 3–4 типово, ≤5 live одночасно | ⟦X6TjkMH_r2I @2023-06-03⟧ ⟦cqNsMJPoM7c @2024-06-03⟧ |
| _pre-A_ Креатив-опцій у Dynamic Creative | до 10 (+ варіанти headline/primary text), 1 ad/адсет | ⟦cqNsMJPoM7c @2024-06-03⟧ ⟦_TkJrNLeNwM @2024-06-03⟧ |
| _pre-A_ Оновлена Meta-рекомендація ads/адсет | 6 або менше (бюджет-залежно: на $10–20/день брати 2–3) | ⟦cqNsMJPoM7c @2024-06-03⟧ |
| _pre-A_ Omnipresent: адсети | 9–10 (та сама аудиторія, різне оголошення в кожному) | ⟦X6TjkMH_r2I @2023-06-03⟧ |
| _pre-A_ Omnipresent: розмір аудиторії | ідеально 20–50k, точно <100k | ⟦X6TjkMH_r2I @2023-06-03⟧ |
| _pre-A_ Omnipresent: frequency cap / бюджет | ~1 показ/5 днів × 10 ads ⇒ ~2 ads/день; ~$1/день/адсет старт | ⟦X6TjkMH_r2I @2023-06-03⟧ |
| _pre-A_ Dynamic-creative структура | CBO OFF (бюджет на адсеті), 2 адсети, 1 ad/адсет, retargeting окремо | ⟦_TkJrNLeNwM @2024-06-03⟧ |
| _pre-A_ Частка акаунтів під direct/DC-структуру | ~80–90% (решта — omnipresent тощо) | ⟦_TkJrNLeNwM @2024-06-03⟧ |

> ⚠️ Рядки «Meta-claim» (33% / 7.2% / 42%) — це попередження-оцінки самої Meta «в середньому по всіх рекламодавцях», а не незалежний замір. У конкретному акаунті може бути інакше. ⟦6avwp4gBZsQ⟧ ⟦1Or1B4L_bdY⟧

## Як було раніше і що змінилось
- ❌ Раніше (структура аудиторій): **окремі кампанії/адсети під cold vs warm** з різним бюджетом і месиджингом; **окремі кампанії під етапи воронки** (top/mid/bottom) з ручним проведенням; **багато адсетів** під різні інтереси / lookalike / open; **ліміт ~5–6 оголошень**/адсет; **окремі оголошення під різні headline/primary text**. ⟦superseded by 13s-G9Uj51A @2026-03-03⟧

### Класичні pre-Andromeda структури (era: pre-andromeda — історія, НЕ застосовувати як дефолт)
Нижче — детально три «канонічні» структури Ben Heath 2023–24 для ~80–90% акаунтів. Усі **superseded** консолідованим post-Andromeda дефолтом (1 кампанія + 1 адсет, cold+warm разом, Meta секвенсує воронку сама).

- ❌ **Direct-offer (2023, CBO-епоха):** **1 кампанія на продукт-рейндж** → **5 адсетів = 1 warm + 4 cold** → **3–4 оголошення/адсет** (≤5 live). **Campaign Budget Optimization (Advantage Campaign Budget) ON**, бюджет на рівні кампанії. Ключові правила: (а) **по одному cold-таргету на адсет** (2 interest + 2 lookalike), щоб бачити чистий cost-per-result і відсівати слабші, додаючи нові раунди; (б) warm-адсет тримали **всередині** CBO-кампанії разом з cold — Meta авто-розраховувала «правильний» бюджет на warm (малий і вигорає) і авто-нарощувала його з ростом warm-бази; (в) **ті самі оголошення в усіх cold-адсетах**, щоб різниця в результатах читалась як таргетинг, а не креатив; warm — ті самі ads як «нагадування» (лишали можливість окремих retargeting-меседжів типу −10%). ⟦X6TjkMH_r2I @2023-06-03⟧ ⟦superseded by 13s-G9Uj51A @2026-03-03⟧
- ❌ **Lead-magnet (2023):** **дві** кампанії. (1) Lead-magnet кампанія (objective leads / instant form або сайт) — структура як у direct-offer (1 warm + 4 cold адсети), але warm-адсет **виключає** тих, хто вже opt-in. (2) Окрема **Retargeting** кампанія (1 адсет) — таргет «lead-magnet opt-ins» **мінус** «next-steppers» (хто вже зробив наступний крок), щоб ловити «середину». **Два шари retargeting** (часта плутанина): шар-1 — догнати тих, хто ще не opt-in (website/video/IG-engagers → opt-in); шар-2 — догнати тих, хто opt-in, але не зробив наступний крок. ⟦X6TjkMH_r2I @2023-06-03⟧ ⟦superseded by 13s-G9Uj51A @2026-03-03⟧
- ❌ **Omnipresent content (2023, для expertise-based / high-AOV послуг):** objective **awareness/reach**, **CBO OFF (ABO)**. **9–10 адсетів = та сама аудиторія** в кожному, але **різне content-оголошення** в кожному (how-to, testimonial, case study). Інверсія direct-offer: не «однакові ads на різні аудиторії», а «різні ads на одну аудиторію». **CBO навмисно вимкнено**, інакше Meta зллє бюджет в один адсет → люди бачать лише одне оголошення (провал ідеї omnipresence). Бюджет — **однаковий малий на кожен адсет** (~$1/день/адсет старт). Аудиторія: ідеально **20–50k**, точно **<100k**; **frequency cap** напр. 1 показ/5 днів × 10 ads ⇒ ~2 різні оголошення/день. Це **НЕ тестова** структура — фіксований набір, новий контент раз на 3–6 міс. Детальніше → [[09-retargeting/omnipresent-content]]. ⟦X6TjkMH_r2I @2023-06-03⟧
- ❌ **Dynamic-creative перехід (2024, проміжна еволюція):** при Dynamic Creative Ben радив **інвертувати** попереднє: **CBO OFF → бюджет на рівні адсета** (DC додає купу змінних на ad-рівні, тож систему «розвантажують» деінде; плюс ABO лікувало «весь бюджет в один адсет»); **скоротити адсети** (4→2, напр. 1 interest + 1 open), решту таргетів тестувати **послідовно**, не одночасно; **retargeting винести в окрему кампанію** (warm інакше реагує, потрібна окрема оптимізація частоти); **1 оголошення/адсет** (DC це форсує) — все одно більше змінних, ніж 4 звичайні ads. DC: до **10 креатив-опцій** + кілька варіантів headline/primary text у ОДНОМУ ad. Для новачків DC **не радили** (важко зрозуміти, що саме перформить) — починати з традиційних ads. ⟦_TkJrNLeNwM @2024-06-03⟧ ⟦superseded by 13s-G9Uj51A @2026-03-03⟧
- ❌ **Консолідаційний поворот (2024, міст до post-Andromeda):** Ben **змінив** рекомендацію на **1 адсет** у direct-offer кампанії — бо (а) з open / Advantage+ audience окремі таргети дають **тотальний audience overlap** (особливо коли не можна вимкнути detailed targeting expansion), тож сенс окремих адсетів зник; (б) консолідація бюджету = швидший вихід з learning phase; (в) уникнення **auction overlap**. Оголошень — **6 або менше** (оновлена рекомендація Meta), при цьому **бюджет-залежно**: на $10–20/день брати **2–3 (навіть 1)**, шість — лише на великих бюджетах; решту з 20 ідей тестувати **раундами**, не разом. Виключення з «6 max»: **dynamic creative** (до 10 опцій, але 1 ad/адсет) та **Advantage+ Shopping** (більше комбінацій через великий каталог). **Multiple text optimization** (кілька headline/primary text в одному ad) — для дрібних варіацій тексту; **окремі ads** — лише для значущо різного оферу/стилю. ⟦cqNsMJPoM7c @2024-06-03⟧ ⟦superseded by 13s-G9Uj51A @2026-03-03⟧

- ❌ Раніше (Advantage+): при виборі sales objective питали «ASC чи manual sales»; ASC зливала campaign+adset у **два рівні** з мінімальним таргетингом; «manual sales» і «manual sales з Advantage+ audience» були РІЗНИМИ й плутали людей; leads мали «manual» або «tailored» (tailored ≈ ASC). ⟦superseded by 6avwp4gBZsQ @2025-06-03⟧
- ❌ Раніше (placements): явний вибір *automatic vs manual placements* на видноті. Тепер сховано за *show more settings → placement controls*. ⟦superseded by 1Or1B4L_bdY @2025-12-03⟧
- ❌ Раніше (текст оголошення): Meta добирала **одну найкращу комбінацію в середньому** для всіх. Тепер optimize-text-per-person добирає **під кожну людину окремо**. ⟦superseded by 1Or1B4L_bdY @2025-12-03⟧
- ❌ Раніше (pre-2022 таргетинг): введені критерії = жорсткі межі, «не виходь за них». Тепер дефолт — *suggest an audience* (підказки), а жорсткі межі треба свідомо вмикати через *further limit reach → switch setup* (зняти *use as suggestion*). ⟦superseded by 6avwp4gBZsQ @2025-06-03⟧
- ✅ Зараз: **Advantage Plus Sales** (з трьома рівнями) + **Advantage Plus Leads** (схожі між собою, легше перемикатись між клієнтами); **одна кампанія + один адсет** за замовчуванням; cold+warm **разом**; воронку Meta **секвенсує сама**; **20+ різнопланових оголошень**; копірайт — через **variations**; розділення лише за **локацією** і **продуктом/послугою**; performance goal **maximize value** там, де чеки різняться.

## Помилки / anti-patterns
- ❌ **Дефолтитись на manual targeting** без вагомої причини: втрачаєш Meta AI, звужуєш аудиторію, score падає. Manual — лише свідомо й рідко. ⟦6avwp4gBZsQ @2025-06-03⟧
- ❌ Тримати **окремі кампанії/адсети під cold і warm** — Meta усе одно змішає (overlap), а ти втрачаєш консолідацію даних. ⟦13s-G9Uj51A @2026-03-03⟧
- ❌ Вважати, що додавання warm custom audience у *suggest an audience* робить адсет «retargeting» — насправді це **«both» адсет** (cold+warm), поки не зайдеш у *further limit reach* і не знімеш suggestion. ⟦1Or1B4L_bdY @2025-12-03⟧
- ❌ Тестувати різні інтереси / lookalike / open у різних адсетах — вони в *suggest an audience*, Meta ігнорує; чесного спліту немає. ⟦13s-G9Uj51A @2026-03-03⟧
- ❌ Плодити окремі оголошення під кожен headline/primary text — роби через variations. ⟦13s-G9Uj51A @2026-03-03⟧
- ❌ **Вимкнути top-funnel оголошення**, яке «жере бюджет без конверсій»: воно працює у top-funnel ролі, без нього перформанс конверсійних оголошень різко погіршиться. ⟦13s-G9Uj51A @2026-03-03⟧
- ❌ Сліпо тримати дефолт «1 кампанія + 1 адсет», коли стратегія цього не передбачає (omnipresent content вимагає кількох адсетів) або акаунт не може протестувати новий креатив у єдиному адсеті. ⟦13s-G9Uj51A @2026-03-03⟧
- ❌ Відходити від дефолту «бо так казали 3 роки тому» — відхилення має бути за конкретною зрозумілою стратегією. ⟦13s-G9Uj51A @2026-03-03⟧
- ❌ Лишати **maximize number of conversions** за сильно різних чеків — Meta жене дешеві низькоцінні конверсії (алгоритм буквальний: «як отримати максимум конверсій → ці дешеві й швидкі»). Треба **maximize value**. ⟦FiZ9IEQteMU @2026-03-03⟧
- ❌ Лишати **audience network** увімкненим у traffic/awareness кампаніях — Meta зллє туди багато дешевого низькоякісного трафіку/охоплення, який не конвертить далі. ⟦1Or1B4L_bdY @2025-12-03⟧
- ❌ **Ad scheduling шукати без lifetime budget** — на daily budget опції просто немає (вона сильно прихована). ⟦1Or1B4L_bdY @2025-12-03⟧
- ❌ Гнатись за campaign score = 100 як самоціль: кореляція з результатом неповна, бувають успішні кампанії з нижчим score. ⟦6avwp4gBZsQ @2025-06-03⟧
- ❌ Лишати **combine social proof** вимкненим, коли тестуєш багато схожих оголошень — розпорошені лайки виглядають слабше. ⟦1Or1B4L_bdY @2025-12-03⟧
- ❌ Використовувати **optimize text per person** у зарегульованій ніші без перевірки — перестановка тексту може порушити вимоги регулятора. ⟦1Or1B4L_bdY @2025-12-03⟧

## Застосування в аналізі/оптимізації
- **Аудит структури:** окремі cold/warm кампанії або вручну розбита воронка (top/mid/bottom як окремі кампанії) → прапор, рекомендувати консолідацію в один адсет.
- **Перевір тип кампанії:** якщо акаунт ще на старій ASC/manual-розвилці — нагадати, що йде роллаут Advantage+ Sales/Leads (3 рівні), і що manual тепер потребує свідомої причини.
- **Performance goal — перша річ для перевірки** в sales/leads з різними чеками: maximize number → перемкнути на maximize value (за наявності value-сигналу: Shopify для sales, або налаштованих lead-values + Pixel/CAPI для leads). Якщо value-сигналу немає — спершу його поставити.
- **Adset з великими витратами й майже без конверсій** при хорошому CPL/CPA інших — НЕ радити вимикати: ймовірно це автоматичний top-funnel у послідовності Meta (частіше в акаунтах з дорогим офером).
- **Перевір «retargeting» адсети:** чи реально це retargeting-only (suggestion знято у *further limit reach*) чи фактично both (cold+warm). «retargeting-heavy» спліт (як 59 з 93 — existing) сам по собі не аномалія.
- **Перевір placements:** у traffic/awareness має бути вимкнений audience network; у conversion-based — лишати Advantage+ placements.
- **Швидкі win-перевірки сетапу:** combine social proof = ON; optimize text per person = ON (поза зарегульованими нішами); audience segments розмічені для звітів.
- **B2B leads** з повільним фолоу-апом → запропонувати ad scheduling (lifetime budget) під робочі години.
- Якщо в єдиному адсеті **не вдається розгойдати новий креатив** → сигнал відійти від дефолту й застосувати окрему структуру тестування → [[12-testing/post-andromeda-testing]].
- **Звʼязок:** [[00-philosophy/andromeda-era]] · [[03-targeting/value-rules]] · [[04-budget-scaling/big-spend-scaling]] · [[12-testing/post-andromeda-testing]] · [[06-creatives/creative-enhancements]] · [[06-creatives/creative-strategy-volume]] · [[09-retargeting/omnipresent-content]] · [[01-structure/asc-vs-manual]] · [[10-measurement/significance-thresholds]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "You no longer need to choose a campaign setup." — Meta UI / Ben Heath ⟦6avwp4gBZsQ @2025-06-03⟧
> "Advantage plus shopping campaigns are now called advantage plus sales campaigns." — Ben Heath ⟦6avwp4gBZsQ @2025-06-03⟧
> "If you want to do manual targeting now, you need a really good reason for doing that." — Ben Heath ⟦6avwp4gBZsQ @2025-06-03⟧
> "By default, we're absolutely going to combine both cold and warm audiences into the same campaign and the same adset." — Ben Heath ⟦13s-G9Uj51A @2026-03-03⟧
> "Often just using the one campaign and the one adset." — Ben Heath ⟦13s-G9Uj51A @2026-03-03⟧
> "You don't want to make the mistake of turning off the ad that is being used in a topfunnel capacity." — Ben Heath ⟦13s-G9Uj51A @2026-03-03⟧
> "Meta is now sophisticated enough to work that out. So they will add sequence for you automatically." — Ben Heath ⟦13s-G9Uj51A @2026-03-03⟧
> "It's the performance goal that dictates how your meta ad campaign is going to be optimized." — Ben Heath ⟦FiZ9IEQteMU @2026-03-03⟧
> "Meta's algorithm is very literal." — Ben Heath ⟦FiZ9IEQteMU @2026-03-03⟧
> "Unless you come into this part… Meta's going to put your ads in front of warm audiences. They're also going to put your ads in front of cold audiences." — Ben Heath ⟦1Or1B4L_bdY @2025-12-03⟧
> _(pre-A)_ "I have now changed my recommended Facebook ad campaign structure… I'd now recommend that most advertisers have one ad set." — Ben Heath ⟦cqNsMJPoM7c @2024-06-03⟧
> _(pre-A)_ "We don't want the campaigns to compete with each other… one campaign not per product, per product range." — Ben Heath ⟦X6TjkMH_r2I @2023-06-03⟧
> _(pre-A)_ "Keep the ads consistent across ad sets, at least initially, until you've worked out your targeting options." — Ben Heath ⟦X6TjkMH_r2I @2023-06-03⟧
