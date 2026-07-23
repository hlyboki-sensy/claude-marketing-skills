---
topic: "ASC vs Manual — вибір типу кампанії та рівня бюджету (Advantage+ / CBO-ABO / ASC existing-customers)"
category: structure
subcategory: asc-vs-manual
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: 6avwp4gBZsQ, date: 2025-06-03, era: post-andromeda }
  - { id: 13s-G9Uj51A, date: 2026-03-03, era: post-andromeda }
  - { id: 1Or1B4L_bdY, date: 2025-12-03, era: post-andromeda }
  - { id: HVfuErKRxUU, date: 2023-06-03, era: pre-andromeda }
  - { id: YZqWg06I5Qw, date: 2024-06-03, era: pre-andromeda }
---

# ASC vs Manual — вибір типу кампанії та рівня бюджету

## TL;DR
Дві сплетені розвилки: **(1) тип кампанії** — Advantage+ (автоматика) vs manual — і **(2) рівень бюджету** — на кампанії (CBO) vs на адсеті (ABO). **Post-Andromeda відповідь:** дефолт — **Advantage+** (ASC перейменовано на **Advantage Plus Sales**, повернулись три рівні, є й **Advantage Plus Leads**), а manual потребує **дуже вагомої причини**; «manual sales» і «manual sales з Advantage+ audience» раніше були РІЗНИМИ й плутали — тепер фактично злиті. Бюджет за замовчуванням — **на кампанії** (консолідація даних). Деталі повної структури → [[01-structure/campaign-structure]]. ⟦6avwp4gBZsQ @2025-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧

**Корінь розвилки (evergreen, ще з pre-Andromeda):** «Advantage Campaign Budget» — це **ребрендинг CBO** (Campaign Budget Optimization) без зміни механіки; ширший роллаут Advantage/Advantage+ — це здебільшого перейменування існуючих фіч (automatic placements → **Advantage+ placements**) заради вищого adoption, бо в середньому автоматика дає кращий результат. CBO/ACB (бюджет на кампанії) кращий для більшості **конверсійних** кампаній; ABO (бюджет на адсеті) лишають для важкого ручного тестування та **не-конверсійних** objectives (traffic / video views). ⟦HVfuErKRxUU @2023-06-03⟧

> ⚠️ era: цей файл — про **decision axis** ASC↔manual і CBO↔ABO. Поточна істина (TL;DR + «Тактики зараз») — post-Andromeda. Pre-Andromeda відео (HVfuErKRxUU, YZqWg06I5Qw) дають **корінь і механіку** розвилки + одну застарілу ASC-фічу; вони у блоці «Як було раніше».

## Принципи [P]
- [P] **Дефолт — Advantage+, manual лише за вагомою причиною.** Перемикаючись на manual, втрачаєш Meta AI, звужуєш аудиторію й опускаєш campaign score. Manual — свідомо й рідко. ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **«Advantage» у назві ≠ нова фіча.** Багато з роллауту Advantage/Advantage+ — це **ребрендинг** наявного: «Advantage Campaign Budget» = той самий **CBO** (та сама механіка, те саме місце в інтерфейсі, той самий дефолт OFF); «Advantage+ placements» = старі **automatic placements**; bid strategy **highest volume** = старий **lowest cost**. Це наскрізна теза, підтверджена і pre-, і post-Andromeda. ⟦HVfuErKRxUU @2023-06-03⟧ ⟦1Or1B4L_bdY @2025-12-03⟧ ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **Meta перейменовує вибірково й навмисно — це сигнал.** Не все стало «Advantage»: певні фічі дістали назву, щоб підняти їх usage, бо команда вважає, що **в середньому** використання дає кращий результат (а кращі результати → більший спенд → більший дохід Meta; інтереси збігаються). Тож «Advantage»-назва — м'який індикатор того, що Meta радить це вмикати. ⟦HVfuErKRxUU @2023-06-03⟧ ⟦6avwp4gBZsQ @2025-06-03⟧
- [P] **CBO (бюджет на кампанії) → кращий результат для більшості, особливо short-term.** Більше бюджету автоматично йде на адсети з кращим результатом: на $100/день із 4 адсетами рівний розподіл ($25 кожному) витратить однаково на адсет із CPL $2 і на адсет із CPL $15; з CBO адсет із CPL $2 забере значно більше → загальний CPL кампанії суттєво кращий. Ця логіка evergreen і прямо лягає в post-Andromeda консолідацію. ⟦HVfuErKRxUU @2023-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧
- [P] **ABO (бюджет на адсеті) = більше контролю → швидші дані в потрібних місцях.** Форсуючи спенд на конкретні адсети, отримуєш дані по них швидше й можеш оптимізувати точково. Виправдано для рекламодавця, що проводить **багато ручного тестування** й хоче гарантувати витрати на окремі адсети. ⟦HVfuErKRxUU @2023-06-03⟧
- [P] **CBO-рекомендація прив'язана до КОНВЕРСІЙНОГО objective.** Для leads/sales (де Meta оптимізує прямо під кінцевий результат і «знає, чого ти хочеш») CBO працює добре. Для **не-конверсійних** (traffic, video views) типово беруть ABO: кампанія не оптимізується під кінцевий результат сама — є проміжні кроки (напр. адсет дає дешевший клік, але ті люди не купують), і зовнішнього треку в Meta може не бути → більший контроль стає важливішим. ⟦HVfuErKRxUU @2023-06-03⟧
- [P] **Highest volume = lowest cost.** Дефолтна bid strategy «highest volume» — те саме, що старий «lowest cost»: за заданий бюджет витягнути максимум бажаного результату. Набір опцій історично варіювався між акаунтами (lowest cost / + highest volume / інші) залежно від типу кампаній і навіть гео акаунта. Рекомендація — лишати дефолт highest volume для більшості. Деталі бід-стратегій → [[05-optimization/bid-strategies]]. ⟦HVfuErKRxUU @2023-06-03⟧
- [P] **Чим менше контролю в рекламодавця в ASC/Advantage+ — тим важливіше дати Meta якісні дані.** В Advantage+ Shopping таргетинг майже не контролюєш — ти довіряєш Meta вирішувати, кому показати. Тому будь-який сигнал, який підказує Meta, кому ти продаєш (хто вже купував), **скорочує шлях до оптимізації** і дає кращі результати швидше — фактично вбудований lookalike. Особливо критично для **нових кампаній / нових акаунтів**, де даних ще мало. ⟦YZqWg06I5Qw @2024-06-03⟧
- [P] **ASC/Advantage+ схильні бути retargeting-heavy.** Щоб дати найкращий результат якнайшвидше, Meta тяжіє до **теплих аудиторій**. Звідси типова претензія до ASC: чудовий результат короткий час, а коли warm-аудиторії «вигоріли» й залишаються майже самі cold — результати падають. Це evergreen-ризик автоматики, який post-Andromeda адресують консолідацією cold+warm в одному адсеті + контролем сегментів. ⟦YZqWg06I5Qw @2024-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧
- [P] **Напрям еволюції — більше даних від рекламодавця в обмін на більше контролю над cold/new.** Meta рухається до того, щоб показувати, який % показів пішов у existing customers (retargeting) vs справді cold, і дати рекламодавцю диктувати **частку бюджету на нових клієнтів** (як уже є в Google — «new customer acquisition»). Ставлячи existing-customers сигнал зараз, ти і покращуєш дані, і готуєшся до цих майбутніх контролів. ⟦YZqWg06I5Qw @2024-06-03⟧

## Тактики зараз [T]
- [T] **Дефолтитись на Advantage+** (Advantage Plus Sales / Advantage Plus Leads), не на manual. Перемикатись на manual лише за конкретною вагомою причиною; повна механіка вибору й рівнів → [[01-structure/campaign-structure]]. ⟦6avwp4gBZsQ @2025-06-03⟧
- [T] **Бюджет тримати на рівні кампанії** (консолідація даних → швидший вихід з learning phase, краща оптимізація). ABO лишати для свідомого ручного тестування або не-конверсійних objectives. Деталі learning phase → [[05-optimization/learning-phase]]. ⟦13s-G9Uj51A @2026-03-03⟧ ⟦HVfuErKRxUU @2023-06-03⟧
- [T] **Лишати дефолтну bid strategy highest volume** для більшості (= старий lowest cost). ⟦HVfuErKRxUU @2023-06-03⟧
- [T] **Завести existing-customers сигнал для Advantage+/ASC** (досі актуальна 30-секундна дія, era-agnostic): Ads Manager → three lines → **All tools** → **Ad account settings** (НЕ business settings) → прокрутити донизу → секція **Advantage+ shopping campaign** → **existing customers** → вибрати custom audience (-и) попередніх покупців. Можна створити нову прямо звідси (**Create new**). ⟦YZqWg06I5Qw @2024-06-03⟧
- [T] **Давати максимум типів custom audiences як existing customers**, не лише піксельну: (а) **website purchases 180d** (піксель — корисно, але якщо кампанії вже крутились, Meta переважно вже має ці дані); (б) **customer file** / email-список (з MailChimp тощо) — критично для покупців, **старших за вікно треку Meta** (>180 днів), яких Meta інакше не «бачить»; (в) покупці з **інших, не-трекованих Meta джерел** (інші канали, давня реклама). Що більше якісних списків — то краще, особливо для нових акаунтів. ⟦YZqWg06I5Qw @2024-06-03⟧
- [T] **Якщо бачиш у звітах ASC, що спенд майже весь у warm/existing** — це очікувано (ASC retargeting-heavy); для частки на cold/new стеж за роллаутом контролю «частка бюджету на нових клієнтів» і користуйся audience-segment звітами (new / engaged / existing) → [[01-structure/campaign-structure]]. ⟦YZqWg06I5Qw @2024-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧

## Числа / бенчмарки
| Параметр | Значення | Джерело |
|---|---|---|
| Existing-customers custom audience (приклад) | website purchases **180d** | ⟦YZqWg06I5Qw⟧ |
| Час на налаштування existing-customers | ~30 секунд | ⟦YZqWg06I5Qw⟧ |
| ABO-приклад (чому CBO кращий) | $100/день, 4 адсети: рівний $25 vs CBO — більше на адсет із CPL $2 (проти CPL $15) | ⟦HVfuErKRxUU⟧ |
| Advantage Campaign Budget дефолт | OFF (як і CBO) | ⟦HVfuErKRxUU⟧ |
| Highest volume | = старий lowest cost | ⟦HVfuErKRxUU⟧ |
| Advantage+ placements | = старі automatic placements | ⟦HVfuErKRxUU⟧ ⟦1Or1B4L_bdY⟧ |
| Agency min budget (контекст Ben, 2023) | $3k/міс | ⟦HVfuErKRxUU⟧ |

> ⚠️ Числа з pre-Andromeda відео — ілюстративні приклади з 2023–24 ($100/день × 4 адсети; CPL $2 vs $15; website purchases 180d), не заміряні бенчмарки. ASC-секція existing-customers в Ad account settings актуальна, але інтерфейс Meta з часом міняє назви/розташування.

## Як було раніше і що змінилось
- ❌ Раніше (2024, era: pre-andromeda): при sales objective Meta питала «**ASC чи manual sales**»; ASC (Advantage Plus Shopping) зливала campaign+adset у **два рівні** з мінімальним контролем таргетингу; «manual sales» і «manual sales з Advantage+ audience» були РІЗНИМИ опціями й плутали рекламодавців; leads мали «manual» або «tailored» (tailored ≈ ASC). ⟦superseded by 6avwp4gBZsQ @2025-06-03⟧
- ✅ Зараз: **Advantage Plus Sales** (ASC перейменовано) з трьома рівнями (campaign/adset/ad) + **Advantage Plus Leads**; «manual sales» і «manual sales з Advantage+ audience» фактично злиті; дефолт — Advantage+, manual — лише за вагомою причиною. Повна структура → [[01-structure/campaign-structure]]. ⟦6avwp4gBZsQ @2025-06-03⟧
- ❌ Раніше (2023, era: pre-andromeda): розвилка називалась **CBO vs ABO**; «Advantage Campaign Budget» щойно з'явився як **ребрендинг CBO** (роллаут стейджено, не у всіх акаунтів одразу), дефолт OFF, але з «заохочувальнішою» назвою → вищий очікуваний adoption. Механіка не змінилась. ⟦HVfuErKRxUU @2023-06-03⟧
- ✅ Зараз цей самий вибір — частина ширшого «Advantage+ vs manual»; бюджет на кампанії (CBO/ACB) лишається дефолтом для консолідації, ABO — свідомий виняток. ⟦13s-G9Uj51A @2026-03-03⟧
- ⚠️ Pre-Andromeda стан (2024): ASC помітно **retargeting-heavy**; Meta тоді ще НЕ показувала розбивку «existing vs cold» у звітах і не давала контролю «частка бюджету на нових». Ben прогнозував, що **і те, і те з'явиться** (як «new customer acquisition» у Google). **Справдилось частково:** post-Andromeda вже є **audience-segment reporting** (new / engaged / existing) на рівні кампанії. ⟦YZqWg06I5Qw @2024-06-03⟧ ⟦13s-G9Uj51A @2026-03-03⟧ → [[01-structure/campaign-structure]]
- ⚠️ Pre-Andromeda порада «дай ASC сигнал existing-customers» лишається валідною й сьогодні (механіка корисна era-agnostic), просто тепер вона — частина ширшої теми якості даних і консолідації cold+warm, а не окремий «hidden hack». ⟦YZqWg06I5Qw @2024-06-03⟧

## Помилки / anti-patterns
- ❌ **Дефолтитись на manual** без вагомої причини (втрата Meta AI, звуження аудиторії, падіння score). ⟦6avwp4gBZsQ @2025-06-03⟧
- ❌ **Плутати «manual sales» і «manual sales з Advantage+ audience»** як одне й те саме — pre-Andromeda це були різні речі; зараз злиті, але історична плутанина лишила сліди в старих гайдах. ⟦6avwp4gBZsQ @2025-06-03⟧
- ❌ **Вважати «Advantage Campaign Budget» новою фічею** й боятись/уникати її як «чорну скриньку» — це той самий CBO. ⟦HVfuErKRxUU @2023-06-03⟧
- ❌ **Тримати ABO «за звичкою» на конверсійних кампаніях**, коли не ведеш активного ручного тестування — рівний розподіл бюджету гальмує загальний CPL/ROAS проти CBO. ⟦HVfuErKRxUU @2023-06-03⟧
- ❌ **Вмикати CBO на не-конверсійних objectives** (traffic/video views) і дивуватись, що дешеві кліки не дають продажів — там виправданий ABO (більше контролю + зовнішній трек проміжних кроків). ⟦HVfuErKRxUU @2023-06-03⟧
- ❌ **Не давати ASC/Advantage+ сигнал existing-customers** («навіщо ретаргетити тих, хто вже купив») — ти плутаєш ретаргетинг із даними для оптимізації: навіть якщо НЕ хочеш ретаргетити покупців, сам список existing-customers різко покращує доставку (вбудований lookalike), особливо на нових акаунтах. ⟦YZqWg06I5Qw @2024-06-03⟧
- ❌ **Обмежуватись лише піксельним списком** покупців як existing-customers — пропускаєш клієнтів, старших за вікно треку Meta (>180 днів) і з не-трекованих джерел; для них потрібен customer-file / email-список. ⟦YZqWg06I5Qw @2024-06-03⟧
- ❌ **Списувати ASC як «зливає в ретаргетинг»** і вимикати її, не спробувавши дати їй якісніші cold-сигнали / стежити за контролем частки на нових клієнтів. ⟦YZqWg06I5Qw @2024-06-03⟧

## Застосування в аналізі/оптимізації
- **Аудит типу кампанії:** якщо акаунт ще на старій ASC/manual-розвилці — нагадати про роллаут Advantage Plus Sales/Leads (3 рівні) і що manual тепер потребує свідомої причини; повна механіка → [[01-structure/campaign-structure]].
- **Аудит рівня бюджету:** ABO на конверсійній кампанії без активного тестування → прапор, рекомендувати CBO/ACB (консолідація). CBO на traffic/awareness → перевірити, чи не краще ABO + чистка placements (audience network) → [[03-targeting/placements]].
- **ASC existing-customers чек:** чи заведено custom audiences у Ad account settings → Advantage+ shopping → existing customers? Чи є серед них **не лише** піксельний список (customer file / email)? Якщо ні — швидкий win (~30 сек + підготовка списків).
- **ASC retargeting-heavy діагностика:** якщо ASC дала чудовий старт і просіла — перевірити частку warm/existing у звітах (audience-segment reporting), не списувати на «Andromeda»; розглянути контроль частки бюджету на нових клієнтів, коли доступний.
- **Bid strategy:** дефолт highest volume (= lowest cost) для більшості; відхилення — свідомо → [[05-optimization/bid-strategies]].
- **Звʼязок:** [[01-structure/campaign-structure]] · [[00-philosophy/andromeda-era]] · [[05-optimization/bid-strategies]] · [[05-optimization/learning-phase]] · [[04-budget-scaling/big-spend-scaling]] · [[03-targeting/advantage-plus-audience]] · [[03-targeting/placements]] · [[09-retargeting/retargeting-post-andromeda]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> _(pre-A)_ "It is a rebranding… there's no actual changes to the way this works from CBO." — Ben Heath ⟦HVfuErKRxUU @2023-06-03⟧
> _(pre-A)_ "The majority of Facebook advertisers want to turn what's now called advantage campaign budget on." — Ben Heath ⟦HVfuErKRxUU @2023-06-03⟧
> _(pre-A)_ "Ad set budgets do provide more control… if you're going to be really detailed." — Ben Heath ⟦HVfuErKRxUU @2023-06-03⟧
> _(pre-A)_ "Highest volume… that's the same as what used to be called lowest cost." — Ben Heath ⟦HVfuErKRxUU @2023-06-03⟧
> _(pre-A)_ "If meta knows who's bought from you previously that's going to massively shortcut the optimization process." — Ben Heath ⟦YZqWg06I5Qw @2024-06-03⟧
> _(pre-A)_ "They do retarget too much… once you burn through those warm audiences… results can tend to drop off." — Ben Heath ⟦YZqWg06I5Qw @2024-06-03⟧
> _(pre-A)_ "Even if you don't want to specifically retarget previous customers you absolutely want to get those custom audiences set up." — Ben Heath ⟦YZqWg06I5Qw @2024-06-03⟧
