---
topic: "Ретаргетинг post-Andromeda — чому Meta ретаргетить сама і навіщо тоді hybrid-адсет"
category: retargeting
subcategory: retargeting-post-andromeda
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: YZ_zNzXHOio, date: 2026-04-03, era: post-andromeda }
  - { id: raSBSNu1fYE, date: 2025-06-03, era: post-andromeda }
---

# Ретаргетинг post-Andromeda

## TL;DR
Ретаргетинг «повністю змінився»: навіть адсет, налаштований як cold/broad, Meta сама ллє частково на warm-аудиторії — у прикладі ~**40%** бюджету пішло на engaged + existing customers ⟦YZ_zNzXHOio @2026-04-03⟧. Тому окрема warm-кампанія здебільшого **зайва** і навіть шкідлива (фрагментація даних, auction overlap). Дефолт зараз — **hybrid-адсет** (warm+cold разом, Meta сама перерозподіляє бюджет). Custom audiences, Pixel і tracking **залишаються обовʼязковими**. Чистий retargeting-only — лише як виняток через «further limit the reach» + знятий «use as suggestion».

Розширення (раннє відео): є **дві базові стратегії** залежно від типу кампанії. **(1) Manual sales/leads + Advantage+ audience** → hybrid-адсет: усі custom audiences ідуть у Advantage+ audience як suggestions, решта таргетингу відкрита; Meta стартує з warm і виходить на cold. **(2) ASC (Advantage+ Shopping → перейменовується на Advantage+ Sales)** → ретаргетинг повністю автоматичний (Meta сама ділить cold / engaged / existing). Обидві мають **один компроміс** — не можна кастомізувати креатив/копію між warm і cold; рішень три: розділити на warm/cold адсети (hard constraints), або «не зважати» і ставити найкращі ads на всіх (рекомендовано для e-com), або винести прогрів у **omnipresent content campaign** (для high-ticket >$1 000). ⟦raSBSNu1fYE @2025-06-03⟧

## Принципи [P]
- [P] Custom audiences живуть у блоці **suggestion audience** (Advantage+ audience), а не в hard controls. Тому Meta вільно вирішує — таргетити твою warm-аудиторію чи проігнорувати; це не жорстка межа. ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧
- [P] **Audience controls = hard constraints; Advantage+ audience-інпути = suggestions.** Локація/мін.вік у audience controls — жорсткі (Meta не вийде за них); вік/стать/інтереси/custom audiences у Advantage+ audience — лише підказки (Meta стартує з них, але вийде за межі, якщо бачить кращий результат). Це і робить «warm-виглядаючий» адсет насправді **hybrid**. ⟦raSBSNu1fYE @2025-06-03⟧
- [P] Ретаргетинг тепер **двосторонній**: cold-адсет Meta частково ретаргетить сама, а retargeting-focused адсет Meta частково ллє на cold. Часто «cold» і «warm» кампанії в підсумку б'ють по одних людях — фактично це одна кампанія. ⟦YZ_zNzXHOio @2026-04-03⟧
- [P] Warm-аудиторії (engaged + existing customers) конвертять дешевше за нову — «that shouldn't be a surprise to anyone». Тому частка покупок із них непропорційно висока навіть за невеликого бюджету на них. ⟦YZ_zNzXHOio @2026-04-03⟧
- [P] **Консолідація > фрагментація**: один адсет на 50 конверсій/тиждень оптимізується краще, ніж два по 25, бо обсяг конверсій корисний для навчання. ⟦YZ_zNzXHOio @2026-04-03⟧
- [P] Custom audiences й Pixel НЕ стали непотрібними. Pixel і досі дає Meta видимість дій на сайті та факту візиту; custom audiences потрібні навіть якщо ти прямо не ретаргетиш. ⟦YZ_zNzXHOio @2026-04-03⟧
- [P] Meta не бачить аудиторій, старших за вікно custom audience; зовнішні списки довносять це знання — особливо критично для **нових акаунтів**, яким Meta ще не знає клієнтів. ⟦YZ_zNzXHOio @2026-04-03⟧
- [P] **Головний компроміс hybrid/ASC-ретаргетингу — не можна розрізнити креатив/копію між warm і cold.** Якщо warm і cold в одному адсеті (або в ASC), ті самі ads ідуть усім; хочеш окремий меседж/знижку для warm — мусиш розділити адсети. ⟦raSBSNu1fYE @2025-06-03⟧
- [P] **Сегментація warm/cold — все більш «old school».** За останні 5–10 років маркетинг зрозумів вагу brand-building і відмовляється від жорстких воронкових кроків; для багатьох (особливо e-com) краще «put your best foot forward» — найкращі ads на всіх — це й дає максимум конверсій. ⟦raSBSNu1fYE @2025-06-03⟧
- [P] **Цінність розрізнення warm/cold залежить від бізнесу.** Для e-com — зазвичай неважливо (продавай усім). Для high-ticket / складних послуг, де треба довго прогрівати, — важливо: різні ads протягом тривалого часу, щоб довести людину до готовності платити високу ціну. ⟦raSBSNu1fYE @2025-06-03⟧
- [P] **ASC сам вирішує спліт cold/engaged/existing і робить це добре та консистентно** (залежно від розміру warm-аудиторій). Тому для багатьох клієнтів ASC дає стабільно кращий результат — і з апдейтами стає ще потужнішим, тож Heath Media використовує його все частіше. ⟦raSBSNu1fYE @2025-06-03⟧
- [P] **Точні дані — передумова будь-якої retargeting-стратегії** (незалежно від обраної). Вони потрібні і рекламодавцю (бачити, що відбувається, оптимізувати), і Meta (кому, як часто показувати). Через privacy-регуляції точність pixel-даних впала і падатиме далі — це не можна недооцінювати. ⟦raSBSNu1fYE @2025-06-03⟧ ⟦YZ_zNzXHOio @2026-04-03⟧

## Тактики зараз [T]
- [T] **Hybrid-адсет за замовчуванням**: не ділити на «cold» і «warm» адсети/кампанії — один адсет на warm+cold. Креатив робити такий, що працює і на warm, і на cold (не лише під warm). ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧
- [T] **Стратегія 1 — manual + Advantage+ audience (hybrid).** Create → Sales (або Leads) → **Manual** campaign → adset → у блоці **Advantage+ audience** додати ВСІ custom audiences (180-day website visitors, FB/IG engagers, video viewers, instant/lead-form, email-список — і Meta-, і non-Meta-джерела), решту (вік/стать/detailed targeting) лишити **відкритою**. Виглядає як warm-адсет, але це hybrid: Meta стартує з warm і виходить на cold. ⟦raSBSNu1fYE @2025-06-03⟧
- [T] **Розділення warm/cold (коли треба різний меседж/знижка) — Стратегія 1b.** *Warm-адсет:* у блоці audience натиснути **«switch to original audience options»** → додати всі custom audiences у custom audience section → **deselect «Advantage custom audience»** (інакше Meta вийде за межі списків). Це робить таргетинг **hard constraint** — лише люди зі списків. Решту (локація/вік) лишити відкритою. *Cold-адсет:* продублювати, повернутись на **Advantage+ audience**, у **audience controls → show more options → exclude custom audiences** виключити ті самі warm-списки (виключення тут — hard constraint), і **не** додавати їх у Advantage+ audience; додати свої suggestions (вік/стать/інтереси). Так warm не бачитимуть cold-ads → можна окремий креатив/копію. ⟦raSBSNu1fYE @2025-06-03⟧
- [T] **Стратегія 2 — ASC (Advantage+ Shopping / «Advantage+ Sales»).** Create → Sales → **Advantage+ shopping**. Ретаргетинг handled автоматично: Meta сама розподіляє бюджет між cold / engaged / existing customers. Підходить, якщо різний меседж між warm/cold не критичний (часто дає консистентно кращий результат). ⟦raSBSNu1fYE @2025-06-03⟧
- [T] **Визнач engaged + existing у reporting-секції ASC** (Advantage+ audience → reporting): engaged = ті, хто споживав контент/взаємодіяв, але не купив; existing = customer list / покупці. **Ці інпути НЕ впливають на доставку — лише на звітність** (бачиш, скільки витрачено на cold vs engaged vs existing). У manual-стратегії аналог — audience segments. ⟦raSBSNu1fYE @2025-06-03⟧ ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] **Omnipresent content campaign для high-ticket (>$1 000).** Якщо продукт/послуга дорогі й вимагають прогріву — запустити окрему **awareness/engagement** кампанію виключно на прогрів warm-аудиторії, паралельно з ASC/manual sales/leads. Так зʼявляється природне розрізнення: warm бачать прогрівні ads, а пряма-продажна кампанія тисне на офер. ⟦raSBSNu1fYE @2025-06-03⟧
- [T] **Три рішення компромісу «однакові ads для warm і cold»:** (а) розділити на warm/cold адсети (Стратегія 1b); (б) **не зважати** — поставити найкращі ads на всіх (рекомендовано для e-com, дає максимум конверсій); (в) винести прогрів в **omnipresent content campaign** (для high-ticket). Вибір — за типом бізнесу. ⟦raSBSNu1fYE @2025-06-03⟧
- [T] **Перевір свій спліт**: Ads Manager → Breakdown → **Audience segments** — розбиває spend і результати на *engaged audience / existing customers / new audience*. Якщо бачиш «all unknown» — не налаштовані audience segments. ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] **Налаштувати audience segments**: Advertising settings → shortcuts → визначити **engaged audience** (напр. website visitors, FB/IG engagers, lead form, video viewers, email-список) і **existing customers** (customer list / Shopify / purchase-подія). Без цього не буде розбивки. ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] **Користуйся dynamic budget reallocation**: коли warm-аудиторії з часом ростуть, Meta в межах одного адсета сама збільшує частку бюджету на ретаргетинг → кращі загальні результати. В окремих адсетах це довелось би робити вручну (складніше, легше помилитись). ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] **Завантажуй зовнішні списки** клієнтів/лідів — щоб Meta знала тих, хто за межами вікна custom audience, і краще розуміла, хто купував і схильний купити знову. ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] **Retargeting-only — лише як виняток** (особливий оффер тільки для warm; кастомне повідомлення; ascension на high-ticket для тих, хто купив low-ticket). Як: ад-сет → audience → **further limit the reach of your ads** → **switch setup** (Meta лякатиме попередженнями) → додати custom audience → **зняти галочку «use as suggestion»**. Тоді targeting стає hard constraint. ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] Не всі акаунти мають опцію «further limit the reach» — це не дефолт і не рекомендований режим; у більшості випадків hybrid кращий. ⟦YZ_zNzXHOio @2026-04-03⟧
- [T] Підключити **tracking/attribution (у відео — Hyros)**: Meta часто не бачить subsequent payments при recurring billing / довгих циклах рішення, тож реальна цінність кампанії може бути значно вища за звіт Meta — інакше приймеш рішення по заниженій картині. Працює і для платного, і для органічного трафіку (видно, звідки прийшов лід). ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧

## Числа / бенчмарки
| Параметр | Значення | Джерело |
|---|---|---|
| Spend cold-адсета на warm (engaged+existing) | ~40% | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Загальний spend прикладу | ~$80K (з них $47–48K на new audience) | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Покупок усього / частка з warm | 942 / понад половина з engaged+existing | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Вікно custom audience: lead form | 90 днів | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Вікно custom audience: FB page engagement | 365 днів | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Вікно custom audience: website visitors | 180 днів | ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧ |
| Tracking-приклад (Hyros): згенеровано / не показано Meta | £96K / £58K не у звіті Meta | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Орієнтир консолідації | 1 адсет × 50 конв./тижд. > 2 адсети × 25 | ⟦YZ_zNzXHOio @2026-04-03⟧ |
| Макс. вікно атрибуції Meta | 7 днів | ⟦raSBSNu1fYE @2025-06-03⟧ |
| Tracking-приклад 2 (Hyros): spend / revenue / Meta бачить / Hyros бачить | £22K spend, £15K revenue, Meta ~£3K, Hyros повні £15K (£12K Meta не бачила) | ⟦raSBSNu1fYE @2025-06-03⟧ |
| Поріг high-ticket для omnipresent content | >$1 000 з клієнта | ⟦raSBSNu1fYE @2025-06-03⟧ |
| Контекст довіри (масштаб Ben) | >$70M ад-спенду за минулий рік | ⟦raSBSNu1fYE @2025-06-03⟧ |

> ⚠️ Cost per purchase із warm був «significantly lower», ніж із new, але конкретного числа у відео немає — **недостатньо даних**.
> ⚠️ Tracking-приклади (£96K→£58K; £15K→£3K) — це **специфічні кейси Ben** з recurring billing / довгим циклом рішення (>7 днів), де 7-денне вікно Meta структурно недозвітує. Це не універсальний розрив для будь-якого акаунта. Числа Meta-звітності з відео — приклади з акаунтів Ben, не заміряні бенчмарки.

## Як було раніше і що змінилось
- ❌ Раніше: **окрема cold-кампанія + окрема warm/retargeting-кампанія** як стандарт. Пост-Andromeda це виглядає «silly»: Meta ретаргетить warm усередині cold-адсета і ллє на cold усередині retargeting-адсета — два адсети часто б'ють по одних людях. ⟦superseded by YZ_zNzXHOio @2026-04-03⟧
- ❌ Раніше: custom audiences = жорсткий таргетинг (як Meta «used to operate» з original audience setups). Зараз вони в **suggestion audience** → Meta може їх проігнорувати (хіба що примусово зняти «use as suggestion» / deselect «Advantage custom audience» / перейти на original audience options). ⟦superseded by YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧
- ❌ Раніше типовий підхід — жорстко **сегментувати воронку** (крок за кроком, ригідно: спершу цей етап, потім той). За 5–10 років маркетинг зрозумів вагу brand-building і відходить від цього на користь «найкращі ads — якомога більшій к-сті людей (частина warm, частина cold)». ⟦superseded by raSBSNu1fYE @2025-06-03⟧
- ⚠️ Хибна «нова» порада, яку відео спростовує: «раз Meta ретаргетить сама — можна не робити custom audiences / не ставити Pixel». Це **bad advice / absolutely false**: і те, і інше досі потрібне. ⟦YZ_zNzXHOio @2026-04-03⟧
- ✅ Зараз: **hybrid-адсет** (warm+cold в одному) з dynamic budget reallocation; retargeting-only — лише під конкретний сценарій через hard-constraint режим. Альтернатива hybrid — **ASC**, де Meta повністю автоматизує спліт cold/engaged/existing (для багатьох клієнтів стабільніше). ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧
- ⚠️ **UI-зміна в процесі** (наступні ~6 міс): екран вибору «ASC vs manual» на рівні кампанії зникає; перемикання на manual-тип переїде на **рівень адсета**. Самі стратегії лишаються чинними — змінюється лише інтерфейс. ⟦raSBSNu1fYE @2025-06-03⟧
- ⚠️ Термінологія: **Advantage+ Shopping (ASC)** перейменовується в більшості акаунтів на **Advantage+ Sales campaign**. ⟦raSBSNu1fYE @2025-06-03⟧

## Помилки / anti-patterns
- ❌ Тримати **окрему warm-кампанію поруч із cold** «за звичкою» — фрагментує дані й створює **auction overlap** (Meta планує частоту в одному адсеті, а людину паралельно б'є інший → плутанина в доставці). ⟦YZ_zNzXHOio @2026-04-03⟧
- ❌ Робити дві кампанії/адсети на **тих самих людей з тим самим оффером** замість однієї. ⟦YZ_zNzXHOio @2026-04-03⟧
- ❌ Викинути **custom audiences** на підставі «Meta й так ретаргетить» — bad advice; вони визначають audience segments і покривають аудиторії поза вікном Meta. ⟦YZ_zNzXHOio @2026-04-03⟧
- ❌ Зняти **Pixel / conversion events** на тій же підставі — «absolutely false»; Meta втратить видимість дій на сайті. ⟦YZ_zNzXHOio @2026-04-03⟧
- ❌ Робити креатив **тільки під warm** у hybrid-адсеті — він має працювати і на cold теж (бо ті самі ads побачать обидві аудиторії). ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧
- ❌ У retargeting-only забути **зняти «use as suggestion»** — тоді адсет працює як звичайний hybrid і не обмежує доставку лише на warm. ⟦YZ_zNzXHOio @2026-04-03⟧
- ❌ У warm-адсеті (Стратегія 1b) **лишити ввімкненим «Advantage custom audience»** — Meta вийде за межі твоїх списків і покаже ads людям поза warm-аудиторією, зруйнувавши задумане розділення. ⟦raSBSNu1fYE @2025-06-03⟧
- ❌ У cold-адсеті **виключати warm НЕ в audience controls, а лише в Advantage+ audience** — там це лише suggestion (не hard constraint), warm все одно можуть побачити ads. Виключення має бути в audience controls. ⟦raSBSNu1fYE @2025-06-03⟧
- ❌ **Кидатися розділяти warm/cold там, де це не дає цінності** (типове e-com) — додає складність без виграшу; краще «put best foot forward» на всіх. Розділення виправдане лише коли реально потрібен різний меседж/знижка (high-ticket, складні послуги). ⟦raSBSNu1fYE @2025-06-03⟧
- ❌ Оцінювати recurring-бізнес / довгий цикл лише по даних Meta — занижена картина (subsequent payments і конверсії за межами 7-денного вікна не видно), ризик неправильної оптимізації. ⟦YZ_zNzXHOio @2026-04-03⟧ ⟦raSBSNu1fYE @2025-06-03⟧

## Застосування в аналізі/оптимізації
- **Audience-segments аудит**: відкрити Breakdown → Audience segments по кожному «cold» адсету; якщо значна частка spend пішла на engaged/existing — окрема warm-кампанія надлишкова, рекомендувати консолідацію в hybrid.
- **Прапор фрагментації**: дві кампанії (нібито cold і warm) б'ють той самий сегмент тим самим оффером → ризик auction overlap, злити в один адсет.
- **Чек налаштувань**: «all unknown» у розбивці → не визначені audience segments (engaged/existing) — поставити в Advertising settings (manual) або в reporting-секції (ASC).
- **Вибір стратегії під клієнта**: потрібен різний меседж/знижка для warm? Якщо ні (e-com) → hybrid-адсет або ASC, найкращі ads на всіх. Якщо так (high-ticket/складні послуги) → або розділити warm/cold адсети (Стратегія 1b), або omnipresent content campaign на прогрів паралельно з ASC/manual sales. → [[06-creatives/creative-strategy-volume]].
- **High-ticket чек (>$1 000 з клієнта)**: запропонувати omnipresent content campaign для прогріву поряд із прямими offer-кампаніями.
- **Вікна аудиторій**: для лідів старших за 90 днів / сторінкових engagers старших за 365 / візитерів старших за 180 — рекомендувати завантаження зовнішніх списків (особливо новим акаунтам).
- **Attribution-розрив**: для recurring/LTV/довгоциклових бізнесів (рішення довше за 7 днів) звіряти Meta з зовнішнім трекером (Hyros-клас) перед рішеннями про масштабування/паузу — Meta структурно недозвітує через 7-денне вікно. → [[10-measurement/significance-thresholds]].
- Звʼязок: [[00-philosophy/andromeda-era]] · [[03-targeting/advantage-plus-audience]] · [[03-targeting/exclusions-overlap]] · [[03-targeting/value-rules]] · [[12-testing/post-andromeda-testing]] · [[01-structure/campaign-structure]] · [[04-budget-scaling/big-spend-scaling]] · [[10-measurement/significance-thresholds]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "Meta is very much going to retarget… whether I set the campaign to do it or not." — Ben Heath ⟦YZ_zNzXHOio @2026-04-03⟧
> "Why have two ad sets or two campaigns targeting the same people with the same offer when you can have one?" — Ben Heath ⟦YZ_zNzXHOio @2026-04-03⟧
> "Yes, Meta is going to retarget automatically… but it is still absolutely worth you setting up your custom audiences." — Ben Heath ⟦YZ_zNzXHOio @2026-04-03⟧
> "Make sure that you don't have use as suggestion ticked… Meta is going to put ads in front of these people and these people only." — Ben Heath ⟦YZ_zNzXHOio @2026-04-03⟧
> "This looks like a warm audience adset but it's not, it's a hybrid adset." — Ben Heath ⟦raSBSNu1fYE @2025-06-03⟧
> "The targeting inputs we're putting in here are suggestions, it's not a hard constraint." — Ben Heath ⟦raSBSNu1fYE @2025-06-03⟧
> "Let's just put our best ads in front of everyone… that real distinction is becoming more of an old school way of doing things." — Ben Heath ⟦raSBSNu1fYE @2025-06-03⟧
> "With ASCs, the retargeting is handled for us." — Ben Heath ⟦raSBSNu1fYE @2025-06-03⟧
