---
topic: "Діагностика Facebook-кампаній — як аналізувати дані правильно (primary vs secondary метрики, парування для діагнозу)"
category: measurement
subcategory: diagnostics
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: mycqb92wJqk, date: 2025-06-03, era: post-andromeda }
  - { id: NY-_GV7TNes, date: 2025-11-03, era: post-andromeda }
  - { id: Fs4ixLR3xxs, date: 2023-06-03, era: pre-andromeda }
  - { id: 4pvsrbroMps, date: 2024-06-03, era: pre-andromeda }
---

# Діагностика Facebook-кампаній — аналіз даних правильно

## TL;DR
Аналіз = (1) рішення «куди дати бюджет / що вимкнути» приймай ТІЛЬКИ за **primary-метрикою** — **cost per result** (lead-based) або **ROAS** (sale-based); (2) **secondary-метрики** (hook rate, CTR link, CPC, CPM, hold rate, link-click→LPV discrepancy) НЕ для оптимізації, а щоб **зрозуміти ЧОМУ** один елемент кращий і відтворити це в нових оголошеннях. Велика частина оптимізації — банально: порівняти елементи → вимкнути гірший → вчитися в кращого → клонувати з варіаціями → бити цей результат. Усе пропускати крізь **common-sense filter**. Передумова будь-якого аналізу — **точні дані** (Pixel + Conversions API встановлені правильно). ⟦mycqb92wJqk @2025-06-03⟧ ⟦NY-_GV7TNes @2025-11-03⟧

## Принципи [P]
- [P] **Не можна отримати найкращий результат, просто запустивши кампанію й сподіваючись.** Аналіз даних і покращення — обовʼязкова частина роботи, не опція. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Дві primary-метрики для рішень: cost per result АБО ROAS** — вибір залежить від бізнесу. Якщо оптимізуєш під purchases і маєш дані про виторг → рішення за **ROAS**. Якщо під leads / complete registration (і це найглибша точка, яку точно трекаєш) → за **cost per result**. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Рішення за primary-метрикою — НЕЗАЛЕЖНО від secondary.** Оголошення з ROAS 4× перемагає оголошення з 3×, навіть якщо у 3×-оголошення кращі CTR і CPC. Кращий CTR/CPC ≠ привід лишати гірший за ROAS елемент. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Secondary-метрики потрібні, щоб зрозуміти ЧОМУ**, а не для оптимізації. Знаючи, чому A дає 4×, а B 3×, ти робиш нові оголошення схожими на переможця. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Primary і secondary часто НЕ корелюють** — у цьому й суть. Оголошення з hook rate 16% може мати дорожчий cost-per-purchase, ніж оголошення з hook rate 10%. Тому не можна судити про результат за secondary. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Велика частина оптимізації проста й «верхньорівнева»:** дивишся на створені елементи → «оце краще за оце» → вимикаєш гірше → вчишся з кращого → робиш схожі для повторного тесту → намагаєшся побити переможця з часом. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Усе пропускати крізь common-sense filter.** Приклад: engagement-bait оголошення збирає купу кліків, але не продає — бо в ньому толком не презентовано продукт; це не «вина лендінгу», а брак конгруентності ad↔лендінг. Метрика без здорового глузду вводить в оману. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **CPM визначається попитом в аукціоні, не «дешевизною» твоїх оголошень.** Дорожчий CPM = ти потрапляєш до якіснішої аудиторії, за яку конкурують інші рекламодавці (бізнес-власники, high-net-worth). Високий CPM може йти разом із кращою конверсією, бо аудиторія якісніша. Тому оптимізувати «на найнижчий CPM» — помилка. **Друга вісь того ж — demand/supply на рівні всієї платформи** (підтверджено pre-Andromeda): CPM = попит рекламодавців проти пропозиції показів; коли Meta нарощує **ad supply** швидше за приріст користувачів (Q1'23: показів +26% YoY при ~+4–5% користувачів), середня **ціна за показ падає** (−17% YoY) — це видно в клієнтських акаунтах як нижчий CPM. Тобто читаючи свій CPM, тримай у голові і якість аудиторії (мікро-аукціон), і макро-баланс supply/demand. ⟦mycqb92wJqk @2025-06-03⟧ ⟦4pvsrbroMps @2024-06-03⟧
- [P] **CPC (cost per click) став набагато менш важливим**, бо платформи порозумнішали. Це досі корисна базова метрика digital-реклами, але не для рішень. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Frequency розповідає історію разом з reach/impressions.** frequency = impressions / reach. Висока частота сама по собі не погана; погано — коли результат падає СИНХРОННО зі зростанням частоти → це ad fatigue, час на нові креативи. Поріг залежить від «температури» аудиторії (див. бенчмарки). ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Демографічні дані з view-charts краще міняти меседжингом, а не таргетингом.** Якщо 83% результатів — чоловіки, таргет не звужуй, але майбутні оголошення можна зробити трохи більш «під них». При 93% — вже варто прямо звертатися до конкретної групи в копії (так, відсіче інших, але ти й так береш більшість з однієї підгрупи). ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Video-retention-крива показує посекундно, де губиш увагу.** Найцінніше — не загальний дроп, а місця, де падіння **більше/менше очікуваного**: плоска ділянка = людям заходить (роби більше такого), різкий додатковий дроп на конкретній секунді = там щось не так (роби менше такого). Це піднімає average play time і, ймовірно, результат. ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Точні дані в акаунті — передумова будь-якого аналізу/масштабування.** Без правильно встановлених Pixel + Conversions API рішення приймаються на хибних цифрах. **Наскрізна теза, підтверджена pre-Andromeda:** ще у 2023 (після iOS 14) Ben наголошував, що неточні дані б'ють **двічі** — (1) ти сам гірше оптимізуєш, бо не бачиш, який саме елемент перформить найкраще; (2) у самої Meta менше даних для ML → доставка/результати можуть просісти. Тобто «accurate data» — це не лише про звітність, а про якість і твоїх, і алгоритмічних рішень. ⟦NY-_GV7TNes @2025-11-03⟧ ⟦mycqb92wJqk @2025-06-03⟧ ⟦Fs4ixLR3xxs @2023-06-03⟧
- [P] **Дані з Ads Manager заслуговують на базову довіру.** Meta — публічно торгована компанія: брехня про аудиторні/доставкові показники = маніпуляція ціною акцій (fraud), на що вона не піде. Тому платформні цифри (DAU/MAU, impressions, price-per-ad) — точні; «moaning» про платформу рідко виправданий. Це фон до common-sense filter: коли результат поганий, **спершу шукай причину у себе** (офер/креатив/таргет), а не «платформа зламалась». ⟦4pvsrbroMps @2024-06-03⟧ ⟦mycqb92wJqk @2025-06-03⟧
- [P] **Розділяй scaling-кампанію і testing-кампанію.** Scaling — для переможних оголошень, забирає більшість бюджету; testing — для нового креативу й експериментів. Це робить діагностику чистішою (стабільний кістяк vs зона ризику). Деталі → [[04-budget-scaling/big-spend-scaling]]. ⟦NY-_GV7TNes @2025-11-03⟧
- [P] **Customer lifetime value (LTV) — рамка для інтерпретації cost-per-result.** $23 cost-per-purchase за клієнта, що платить $97/міс, — чудово; «сирий» ROAS у Ads Manager на subscription-продукті враховує лише першу транзакцію й СИЛЬНО занижений. Чим більше заробляєш з клієнта (повтори/підписки/реферали), тим більше можеш платити за його залучення. ⟦mycqb92wJqk @2025-06-03⟧ ⟦NY-_GV7TNes @2025-11-03⟧

## Тактики зараз [T]
- [T] **Постав власний column-preset** (Ads Manager → Columns → Customize columns; ~90 доступних). Базовий набір Ben: delivery · actions (opportunity score) · budget · amount spent · [conversion event, який оптимізуєш] · cost per [той event] · purchase conversion value · ROAS · reach · impressions · frequency · CPM · hook rate (custom) · video average play time · link clicks · landing page views · CPC (link) · CTR (link). ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Колонку результату називай саме тим event, який оптимізуєш** (purchases / leads / complete registrations), а не завжди «purchases». Поряд став **cost per [event]** — одна з найважливіших метрик при порівнянні елементів. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Додай колонку actions** (це shortcut на нову фічу opportunity score) — нагадує, що Meta пропонує optimization-дії для адсета. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Створи custom-метрику hook rate** = 3-second video plays / impressions, виражено у %. (Customize columns → Create a custom metric.) Можна робити й складніші custom-метрики під специфіку бізнесу. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Бери link-метрики, не загальні.** В аналіз — **link clicks** (не clicks), **CPC = cost per link click**, **CTR = link click-through rate**. Clicks/CTR (all) роздуті: рахують unmute відео, клік «see more», рух по каруселі — це НЕ цільова дія. Ще точніше — outbound / unique link clicks. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Постав landing page views поряд з link clicks** і дивись discrepancy. ~20% дропу — норм; >50% → сигнал: повільний лендінг, або багато випадкових кліків (часто через traffic-кампанію з показами в Audience Network). ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Тримай reach + impressions + frequency разом** — читати як одну «історію» доставки/насиченості. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **При падінні результату звір з frequency:** якщо результат просів і це збіглося зі зростанням частоти → ad fatigue → вводь нові креативи. → [[04-budget-scaling/big-spend-scaling]] · [[06-creatives/creative-strategy-volume]]. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Парування secondary-метрик для діагнозу (video ads):**
  - **hook rate + cost-per-result:** одне оголошення найкраще «чіпляє» (вищий hook), але інше краще конвертує → візьми «мʼясо» (тіло) кращого за конверсією + хук кращого за hook rate → виграш з обох. ⟦mycqb92wJqk @2025-06-03⟧
  - **hook rate + video average play time:** hook високий, average play time низький → або хук оманливий/не звʼязаний з рештою, або тіло відео незахопливе. ⟦mycqb92wJqk @2025-06-03⟧
  - **hook rate + CTR(link):** hook >10%, але CTR link <0.5% → зачепили, але не переконали клікнути → або слабкий **offer**, або **бракує proof** (відгуки, скрін акаунтів клієнтів). ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Парування для не-відео / загальне (діагноз воронки):**
  - **CTR(link) добрий, але конверсії погані** (e-com conversion rate з кліку <2%) → проблема в **лендінгу**, не в оголошенні (неконгруентність, несподівана доставка/комісія, мало proof). ⟦mycqb92wJqk @2025-06-03⟧
  - **link clicks >> landing page views** → setup-проблема (Audience Network на traffic-кампанії) або швидкість лендінгу. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Discount несумісні формати при порівнянні** secondary-метрик: каруселі з дуже низьким hook rate не порівнюй «яблуко до яблука» з відео — це інша механіка. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Враховуй довжину відео при читанні average play time:** для дуже коротких відео «2 сек» може бути ОК; довге відео природно дає вищий average play time (хтось досмотрить до кінця й підніме середнє). Для коротких роликів ця метрика малоінформативна. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Відкрий View charts** на оголошенні (виділити галочкою → View charts) для глибшого аналізу: демографія (стать/вік + cost per result по них), платформа (Facebook vs Instagram: reach і результати окремо), ad previews, **video-retention-крива**. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Платформенний спліт із view-charts** — діагностика, не привід різати: якщо Facebook дає 36 покупок vs Instagram 24 за схожого спенду → для цього оферу FB сильніший (але це не універсально по всіх оферах). ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Читай video-retention-криву посекундно:** шукай ділянки, де дроп більший за очікуваний (там «прибери це» в наступному відео) і плоскі/зростаючі ділянки (там «зроби більше такого»). Лінія інформативніша за стовпчики 25/50/75%. ⟦mycqb92wJqk @2025-06-03⟧
- [T] **Постав Pixel + Conversions API правильно** (передумова точних даних) і ганяй influencer-відео як **partnership ads**. → [[10-measurement/capi-event-match]]. ⟦NY-_GV7TNes @2025-11-03⟧
- [T] **Окремі кампанії scaling vs testing** як операційна гігієна для чистої діагностики. → [[12-testing/post-andromeda-testing]] · [[04-budget-scaling/big-spend-scaling]]. ⟦NY-_GV7TNes @2025-11-03⟧

## Числа / бенчмарки
| Метрика | Орієнтир | Джерело |
|---|---|---|
| Frequency — cold audience (не перевищувати) | ≤2.5 | ⟦mycqb92wJqk⟧ |
| Frequency — більшість бізнесів (стеля) | ~6–8 | ⟦mycqb92wJqk⟧ |
| Frequency — warm/retargeting (допустимо) | до 10–12, бачили до 16 | ⟦mycqb92wJqk⟧ |
| Hook rate (3-sec views / impressions) — добре | >10% | ⟦mycqb92wJqk⟧ |
| Hook rate — погано | <5% | ⟦mycqb92wJqk⟧ |
| Hook rate — «у проміжку» | 5–10% = ОК | ⟦mycqb92wJqk⟧ |
| CTR (link) — добре | >1% | ⟦mycqb92wJqk⟧ |
| CTR (link) — дуже добре | >2% | ⟦mycqb92wJqk⟧ |
| CTR (link) — погано | <0.75% | ⟦mycqb92wJqk⟧ |
| CTR (link) приклад «низький» для діагнозу | <0.5% | ⟦mycqb92wJqk⟧ |
| Link clicks → landing page views discrepancy — норма | ~20% (іноді трохи більше) | ⟦mycqb92wJqk⟧ |
| Link clicks → LPV discrepancy — тривожно | >50% дропу | ⟦mycqb92wJqk⟧ |
| E-commerce conversion rate (з кліку) — нижче норми | <2% | ⟦mycqb92wJqk⟧ |
| Приклад кейс-кампанії (retargeting, FB Ads Mastery) | ~£2 000 spend / 60 днів; 60 purchases; £25 cost-per-purchase; CPM £73; frequency 10.43; hook rate адсета 8.38% | ⟦mycqb92wJqk⟧ |
| Demographic skew у кейсі | 83% чоловіки (cost per result кращий на чоловіках) | ⟦mycqb92wJqk⟧ |
| Платформа у кейсі | FB 36 purchases vs IG 24 (схожий спенд) | ⟦mycqb92wJqk⟧ |
| LTV-приклад | продукт £97/міс; £23–25 cost-per-purchase ≈ 4× ROAS на 1-й транзакції, реально ~20× з повторами | ⟦mycqb92wJqk⟧ |
| Масштаб Ben (контекст довіри) | >$200M продажів з FB/IG ads за 9 років (mycqb92wJqk) / 12 років (NY-_GV7TNes) | ⟦mycqb92wJqk⟧ ⟦NY-_GV7TNes⟧ |
| Точність website-конверсій після iOS 14 (pre-andromeda) | ~70% | ⟦Fs4ixLR3xxs⟧ |
| Точність in-app (instant forms / FB shop, pre-andromeda) | ~100% | ⟦Fs4ixLR3xxs⟧ |
| Платформа: Family DAU / MAU (Q1'23, pre-andromeda) | 3.02 млрд (+5% YoY) / 3.81 млрд (+5%) | ⟦4pvsrbroMps⟧ Meta-report |
| Платформа: FB DAU / MAU (Q1'23) | 2.04 млрд (+4%) / 2.99 млрд (+2%) | ⟦4pvsrbroMps⟧ Meta-report |
| Ad impressions YoY (Q1'23) vs price-per-ad YoY | показів +26% / ціна за показ −17% | ⟦4pvsrbroMps⟧ Meta-report |

> ⚠️ Пороги hook rate / CTR / frequency **сильно варіюються між індустріями** (B2B зазвичай нижчий hook/CTR і дорожчий CPM, ніж health/fitness). Це орієнтири Ben, не жорсткі норми — завжди читай у контексті ніші. Кейс-числа (£25 CPP, 8.38% hook, 83% чоловіки) — це РЕТАРГЕТИНГ на теплу аудиторію самого Ben, не універсальний бенчмарк. «20× ROAS з LTV» — оцінка для нового subscription-продукту, не заміряно. Рядки «Meta-report» (DAU/MAU, impressions, price-per-ad) — це **Q1 2023** з офіційного звіту Meta (датовані, не поточні; наведені як ілюстрація demand/supply, а не сьогоднішній бенчмарк). Точність 70% / 100% — pre-Andromeda оцінки Ben для тодішнього стану трекінгу, сьогодні неактуальні як цифри.

## Як було раніше і що змінилось
- ➕ Нове/уточнене (не суперечить існуючому): чіткий поділ **primary vs secondary метрик** і правило «рішення — лише за primary, secondary — для пояснення ЧОМУ». ⟦mycqb92wJqk @2025-06-03⟧
- ⚠️ **CPC втратив вагу** для рішень у міру порозумнішання платформ — лишається базовою, але не вирішальною метрикою. ⟦mycqb92wJqk @2025-06-03⟧
- ⚠️ **«Сирий» ROAS у Ads Manager занижений на subscription/recurring продуктах** (часто лише перша транзакція) — реальний ROAS рахуй з LTV, не з цифри в колонці. Перегукується з темою недозвіту Meta → [[10-measurement/capi-event-match]]. ⟦mycqb92wJqk @2025-06-03⟧
- ⚠️ Ads Manager буває **багований** (метрика, що feed-илась учора, сьогодні «не тягнеться») — це нормально, не привід для паніки; знай, що так буває. ⟦mycqb92wJqk @2025-06-03⟧

### Передісторія: як добивались точних даних до Andromeda (era: pre-andromeda)
> Контекст: відео Fs4ixLR3xxs (2023) — **до анонсу Andromeda (груд. 2024)** і ще на піку болю від iOS 14.5. Описує, ЯК тоді компенсували недозвіт, щоб мати на чому аналізувати кампанії. Evergreen-ядро (точні дані = передумова аналізу; «двічі болить») винесене вище як [P] corroboration. Конкретні **методи** нижче — pre-Andromeda і здебільшого **superseded** пізнішим стеком CAPI + розширені атрибуційні вікна + (за потреби) сторонній трекінг. ⟦superseded by NY-_GV7TNes @2025-11-03⟧
- ❌ Раніше (era: pre-andromeda) дефолтний шлях «website-конверсії» давав лише **~70% точності** після iOS 14; щоб аналізувати по-чесному, пропонувались два обхідні шляхи: **low-effort** (тримати людину in-app) і **high-effort** (унікальні лендінги). ⟦Fs4ixLR3xxs @2023-06-03⟧
- ❌ Раніше (era: pre-andromeda) **low-effort спосіб 100% даних — перевести кампанії в in-app destination:** (a) **lead-gen instant forms** (форма всередині FB/IG) — дешевші ліди (менше тертя), АЛЕ зазвичай нижча якість (менше фільтрує незацікавлених, важче доконтактувати/сконвертувати) → радилось **A/B-тестити** website-ліди проти instant-form; (b) **Facebook Shop** для e-com — точніші дані, але менше фіч/інструментів, ніж Shopify. Сам факт, що дані 100% точні, був вагомим аргументом за тест. ⟦Fs4ixLR3xxs @2023-06-03⟧ → [[02-objectives/leads-vs-sales-vs-traffic]]
- ❌ Раніше (era: pre-andromeda) **high-effort спосіб — унікальні лендінги** (окремий URL під кампанію/адсет/навіть оголошення): через Google Analytics видно посекційно, де людина зайшла і з якою % сконвертувала → точно ясно, який елемент дає найкращий результат. **Trade-off:** ці точні дані **НЕ повертаються в ad-акаунт**, тож ML Meta оптимізує так само, як на ~70% (ти оптимізуєш краще — алгоритм ні). Плюс — можна лишатися на власному сайті. ⟦Fs4ixLR3xxs @2023-06-03⟧
- ❌ Раніше (era: pre-andromeda) питання «чому не просто **UTM**?» — Ben тестував: UTM **менш точні** за унікальні лендінги; якщо точність критична й трафік іде на сайт — лендінги, не UTM. (Сьогодні дефолт інший — CAPI + server-side, а не самописний GA-трекінг.) ⟦Fs4ixLR3xxs @2023-06-03⟧
- ⚠️ Раніше (era: pre-andromeda) спостереження: in-app реклама (instant forms) діставала **нижчий CPM**, ніж трафік на сайт — Meta схоже заохочувала тримати людей у застосунку (не доведено остаточно). Лягає в evergreen-тезу «CPM = аукціонний попит + поведінка платформи», а не «дешевші оголошення». ⟦Fs4ixLR3xxs @2023-06-03⟧
- ✅ Зараз (post-andromeda): замість самописних обходів дефолт — **правильні Pixel + Conversions API з high event match quality**, **розширені атрибуційні вікна** (view-through, щоб ловити «безклікові» покупки) і **сторонній трекінг** (Hyros-клас) на великих/мульти-канальних бюджетах. In-app формати (instant forms / shops) лишаються опцією для точності, але вже не єдиний шлях. ⟦NY-_GV7TNes @2025-11-03⟧
- ⚠️ Контекст здоров'я платформи (era: pre-andromeda, 2024): «FB у занепаді» — міф; Family DAU/MAU росли (+5% YoY), сам FB DAU +4% / MAU +2%, і core-ринки (US/Canada, Europe) стабільні/відновлюються. Це фон до того, чому платформним цифрам можна вірити і чому винуватити «вмираючу платформу» за поганий результат — невиправдано. Деталі тренду → [[00-philosophy/industry-news]] · [[00-philosophy/andromeda-era]]. ⟦4pvsrbroMps @2024-06-03⟧

## Помилки / anti-patterns
- ❌ **Оптимізувати за secondary-метриками в першу чергу** (CPM / CPC / hook rate / CTR) замість cost-per-result чи ROAS — головна помилка аналізу. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Лишати елемент із кращим CTR/CPC, але гіршим ROAS/cost-per-result.** Secondary не переважують primary. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Гнатися за найнижчим CPM** як за «дешевшою рекламою» — низький CPM часто = гірша/дешевша аудиторія; високий CPM може конвертити краще. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Аналізувати clicks / CTR(all) замість link clicks / CTR(link).** «4% CTR» звучить чудово, але якщо це all-clicks (карусель-свайпи, unmute, see-more) — метрика оманлива. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Судити про результат за secondary**, ігноруючи що вони не корелюють з primary (16% hook ≠ дешевша покупка). ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Порівнювати різні формати «в лоб»** (hook rate каруселі vs відео) — не apples-to-apples. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Вважати високу frequency автоматично поганою.** Погано лише, коли результат падає синхронно з ростом частоти (тоді — fatigue). На warm/retargeting 10–12+ буває нормою. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Робити висновки без common-sense filter:** напр. списати слабку конверсію engagement-bait-оголошення на «поганий лендінг», хоча проблема — оголошення не продає продукт. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Міняти таргетинг на основі демографічного спліту** замість меседжингу (при помірному skew ~83%). Звужувати таргет передчасно. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Робити висновки на крихітному обсязі** (3 purchases — «не так багато даних»). Замало конверсій → рішення ненадійне. → [[10-measurement/significance-thresholds]]. ⟦mycqb92wJqk @2025-06-03⟧
- ❌ **Аналізувати/масштабувати на хибних даних** — без правильних Pixel + CAPI цифри в акаунті неточні. ⟦NY-_GV7TNes @2025-11-03⟧ ⟦mycqb92wJqk @2025-06-03⟧ ⟦Fs4ixLR3xxs @2023-06-03⟧
- ❌ **Винуватити «платформу»/«вмираючий FB» за поганий результат** замість аудиту власного оферу/креативу/таргету. Платформні цифри точні (публічна компанія), база користувачів росте — діагноз майже завжди в зоні твого контролю. ⟦4pvsrbroMps @2024-06-03⟧
- ❌ **Брати instant-form ліди за «такі ж» як website-ліди** при аналізі: вони дешевші, але часто нижчої якості (гірший response/конверсія в продаж) — порівнюй по кінцевій якості ліда, не лише по cost-per-lead. (era: pre-andromeda) ⟦Fs4ixLR3xxs @2023-06-03⟧
- ❌ **Брати «сирий» ROAS за чисту монету на subscription-продукті** — він враховує лише першу транзакцію й сильно занижує реальний з LTV. ⟦mycqb92wJqk @2025-06-03⟧

## Застосування в аналізі/оптимізації
- **Базовий цикл оптимізації:** обери primary-метрику під бізнес (ROAS для sale-based з даними виторгу; cost-per-result для lead-based) → порівняй елементи ЛИШЕ за нею → вимкни гірші, лиши/клонуй кращі → потім підключай secondary, щоб зрозуміти ЧОМУ переможець виграв, і відтвори це в нових креативах.
- **Чек secondary-метрик (порядок під час diving):** для відео — hook rate → average play time → CTR(link), парами; для воронки — CTR(link) vs кінцева конверсія; завжди link clicks vs LPV.
- **Дерево діагнозу (з транскрипту):**
  - discrepancy link clicks ↔ LPV велика? → setup (Audience Network на traffic) або швидкість лендінгу.
  - hook добрий, average play time поганий? → лагодь тіло відео.
  - hook + average play time добрі, але CTR(link) низький? → слабкий offer або мало proof (відгуки/скріни).
  - CTR(link) добрий, але кінцева конверсія погана? → проблема лендінгу (конгруентність, несподівані витрати, мало proof). → [[08-landing-cvr/landing-best-practices]].
- **Frequency-тригер:** падіння результату + зростання frequency = ad fatigue → свіжі РІЗНІ креативи. → [[06-creatives/creative-strategy-volume]] · [[04-budget-scaling/big-spend-scaling]].
- **View-charts аудит:** демографічний skew → коригуй меседжинг (не таргет, поки <~90%); платформенний спліт → діагноз, не різати; video-retention-крива → де додатковий дроп (прибрати) / плоско (лишити/посилити).
- **Передумова перед будь-якими рішеннями:** перевір, що Pixel + CAPI стоять правильно й дані точні; influencer-відео — як partnership ads; scaling- і testing-кампанії розділені. → [[10-measurement/capi-event-match]] · [[12-testing/post-andromeda-testing]].
- **Якщо дані все одно «дірчасті»** (недозвіт, неможливо чесно порівняти елементи): сучасний шлях — розширити атрибуційні вікна + сторонній трекінг; як **fallback для 100% точності** лишаються in-app формати (instant forms / FB shop) і унікальні лендінги під елемент (GA-трекінг) — але пам'ятай trade-offs (instant-form ліди дешевші, але нижчої якості; самописний трекінг лендінгів НЕ годує ML Meta). → [[02-objectives/leads-vs-sales-vs-traffic]].
- **«Платформа винна»?** Перш ніж списати просадку на Meta — звір базу: платформні метрики точні, користувацька база росте; шукай діагноз в офері/креативі/таргеті/даних. → [[00-philosophy/industry-news]].
- **LTV-рамка:** інтерпретуй cost-per-result через customer LTV, а не «сирий» ROAS у колонці (особливо subscription/recurring) — інакше недооціниш прибуткові кампанії. → [[10-measurement/capi-event-match]].
- **Звʼязок:** [[00-philosophy/andromeda-era]] · [[04-budget-scaling/big-spend-scaling]] · [[12-testing/post-andromeda-testing]] · [[06-creatives/hooks]] · [[06-creatives/video-ads]] · [[06-creatives/creative-strategy-volume]] · [[10-measurement/capi-event-match]] · [[10-measurement/capi-event-match]] · [[10-measurement/significance-thresholds]] · [[11-troubleshooting/account-health-bans]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "You very much cannot get the best results from just creating a Facebook ad campaign… and hoping." — Ben Heath ⟦mycqb92wJqk @2025-06-03⟧
> "Base most of your optimization decisions around either your cost per conversion or your return on ad spend." — Ben Heath ⟦mycqb92wJqk @2025-06-03⟧
> "Those are secondary metrics that don't matter anywhere near as much." — Ben Heath ⟦mycqb92wJqk @2025-06-03⟧
> "Don't optimize for those, use those to understand what's going on." — Ben Heath ⟦mycqb92wJqk @2025-06-03⟧
> "You have to run all these things through a common sense filter." — Ben Heath ⟦mycqb92wJqk @2025-06-03⟧
> "Your cpms are going to be more expensive if your ads are being put in front of higher quality audiences." — Ben Heath ⟦mycqb92wJqk @2025-06-03⟧
> "Make sure that you've got the Meta pixel and the conversions API set up… You need accurate data." — Ben Heath ⟦NY-_GV7TNes @2025-11-03⟧
> "Obsess over your customer lifetime value." — Ben Heath ⟦NY-_GV7TNes @2025-11-03⟧
> "That lack of data also affects facebook's machine learning process… results can drop off." — Ben Heath ⟦Fs4ixLR3xxs @2023-06-03⟧ (pre-andromeda)
> "A lot of people want to moan about the platform… make better ads, create better offers, put in the time and research." — Ben Heath ⟦4pvsrbroMps @2024-06-03⟧ (pre-andromeda)
