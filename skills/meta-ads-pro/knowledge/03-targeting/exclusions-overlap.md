---
topic: "Exclusions & Audience Overlap — detailed targeting exclusions (retired) vs custom audience exclusions (живі)"
category: targeting
subcategory: exclusions-overlap
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: aTJCB5ESyTc, date: 2025-06-03, era: post-andromeda }
---

# Exclusions & Audience Overlap — що Meta прибрала і що лишилось

## TL;DR
Meta **офіційно прибрала detailed targeting exclusions** — можливість виключати інтереси/поведінки/демографії з таргетингу (працювало лише в *original audience options*). Роллаут поетапний: нові кампанії/адсети не можуть це юзати з **29 липня**, наявні працювали до **31 січня** (за словами Ben). Причина від Meta: median **cost per conversion на 22.6% нижчий**, коли НЕ використовуєш detailed targeting exclusions (Meta-claim). Ben і раніше **не рекомендував** ці виключення (виключити 70% аудиторії через overlap ≠ чесний тест), хоча радив **окремі інтереси per adset** для тестування. Головне: **custom audience exclusions ЛИШАЮТЬСЯ** і вони набагато цінніші (funnel-stage таргетинг, офери лише для нових клієнтів) — це **hard boundary** і в original, і в Advantage+ Audience. Втрата detailed exclusions — «не катастрофа»; справжня тривога ринку — тренд «дедалі менше контролю в рук рекламодавця». ⟦aTJCB5ESyTc @2025-06-03⟧

## Принципи [P]
- [P] **Detailed targeting exclusions — це не те саме, що custom audience exclusions.** Перше (виключити інтерес/поведінку/демографію) Meta прибрала; друге (виключити warm-аудиторію — тих, хто вже взаємодіяв з бізнесом) лишається і працює. Не плутати ці два механізми. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **Виключати інтерес через overlap = нечесний тест.** Якщо інтерес адсета B на ~70% перетинається з інтересом адсета A і ти виключаєш цей перетин з B — ти тестуєш лише 30% «справжньої» аудиторії B. Це не дає валідного порівняння, *який інтерес працює краще*. Тому Ben ніколи не радив detailed targeting exclusions, навіть коли вони були популярні. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **Окремі інтереси per adset (БЕЗ взаємних виключень) — валідна тактика тесту.** Тримати по одному інтересу в адсеті, щоб бачити, який працює краще, і оптимізувати — це Ben рекомендував. Заборонене — це *виключати* інтерес одного адсета з інших. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **Інтереси, дотичні до продукту, природно сильно перетинаються.** Коли таргетуєш інтереси, повʼязані з твоїми товарами/послугами, вони зазвичай схожі один на одного → великий audience overlap між ними «з коробки». Саме тому колись і виник прийом виключень (щоб «розчепити» адсети). ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **Custom audience exclusions цінніші за detailed targeting exclusions.** Можливість виключити людей за стадією воронки (ліди, що не конвертнули; наявні клієнти) дає реальний бізнес-важіль; виключення інтересів — переважно псувало результат. Тому втрата другого не критична. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **В Advantage+ Audience exclusions custom audience = HARD BOUNDARY.** Усе в секції *audience controls* (location, minimum age, **excluded custom audiences**) — жорсткий кордон, який Meta зобовʼязана дотримати. Натомість detailed targeting у A+ — лише *suggestions*. Тому exclusions працюють «жорстко» навіть в автоматичному таргетингу. ⟦aTJCB5ESyTc @2025-06-03⟧ → [[03-targeting/advantage-plus-audience]]
- [P] **Detailed targeting exclusions «вмирали» поступово ще до офіційного прибирання.** З переходом на Advantage+ Audience (де detailed inputs — підказки, не жорсткі кордони) і open targeting прийом виключень використовувався дедалі менше; офіційне прибирання — фіналізація вже наявного тренду. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **Завжди є винятки під специфіку бізнесу.** Загальна порада (не виключати) не абсолютна: якщо рекламуєш дуже вузький підсегмент ніші й знаєш, що ширша аудиторія ніші не конвертить, виключення «широкого» інтересу могло давати кращий результат саме тобі. Загальне правило ≠ закон для кожного. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **«Cost per conversion» від Meta варте уваги; «cost per result» — з осторогою.** Коли Meta наводить *cost per result*, туди можуть входити link clicks/impressions/video views — звучить добре, але не означає дешевші ліди/продажі. Коли наводить *cost per conversion* — це справжній показник, важливий для більшості рекламодавців. Дані «22.6% дешевше» подані саме як cost per conversion → їм можна довіряти більше. ⟦aTJCB5ESyTc @2025-06-03⟧
- [P] **Напрям тренду: менше контролю в рук рекламодавця.** Прибирання detailed exclusions — частина довгого руху: дедалі більше таргетингових опцій забирають, дедалі більше «важкої роботи» бере на себе Meta. Реальна тривога ринку не про самі exclusions, а про питання «чи дійде до того, що доведеться повністю довіряти Meta без жодного інпуту». ⟦aTJCB5ESyTc @2025-06-03⟧

## Тактики зараз [T]
- [T] **Перестати покладатися на detailed targeting exclusions** — їх немає для нових адсетів. Якщо акаунт ще має наявний адсет, що їх юзає, і вони реально корисні — НЕ редагувати той адсет (правки вбʼють фічу), дати докрутити до дедлайну. ⟦aTJCB5ESyTc @2025-06-03⟧
- [T] **Замість виключень інтересів — окремі інтереси per adset** (один інтерес/адсет) для тесту, який працює краще; переможця масштабувати. Без взаємних виключень. ⟦aTJCB5ESyTc @2025-06-03⟧
- [T] **Funnel-stage таргетинг через custom audience exclusions:** створити custom audience «стали лідами» + custom audience «конвертували» → у кампанії на дожим виключити «конвертували», щоб бити лише по тих, хто ще не купив. ⟦aTJCB5ESyTc @2025-06-03⟧
- [T] **Офер «лише для нових клієнтів»:** створити custom audience з наявних клієнтів → виключити її, щоб старі/наявні клієнти не бачили акцію «тільки для нових» і не дратувались. ⟦aTJCB5ESyTc @2025-06-03⟧
- [T] **Де виключати custom audience (original audience options):** ad set level → секція *Custom audiences* → кнопка **Add exclusions**. Працює і коли ввімкнено original audience options. ⟦aTJCB5ESyTc @2025-06-03⟧
- [T] **Де виключати custom audience (Advantage+ Audience):** ad set level → *Audience controls* → *Edit* → **Show more options** → виключити custom audiences. Це той самий hard boundary, що і в original. ⟦aTJCB5ESyTc @2025-06-03⟧
- [T] **Якщо специфіка бізнесу того вимагала** (вузький підсегмент ніші) і detailed exclusions давали виграш — встигнути «вичавити» з наявних адсетів до дедлайну, а далі шукати заміну через креатив/офер/звуження на рівні custom audiences. ⟦aTJCB5ESyTc @2025-06-03⟧

## Числа / бенчмарки
| Факт | Значення | Джерело |
|---|---|---|
| Зниження median cost per conversion БЕЗ detailed targeting exclusions | −22.6% | ⟦aTJCB5ESyTc⟧ Meta-claim |
| Дата старту прибирання (нові кампанії/адсети) | 29 липня | ⟦aTJCB5ESyTc⟧ |
| Дедлайн для наявних кампаній/адсетів | 31 січня (за словами Ben — «January 31st 2025») | ⟦aTJCB5ESyTc⟧ |
| Типовий overlap між дотичними інтересами (приклад «нечесного тесту») | ~70% | ⟦aTJCB5ESyTc⟧ (ілюстрація, не замір) |
| Рекомендована к-сть інтересів на адсет (для тесту) | 1 інтерес/адсет | ⟦aTJCB5ESyTc⟧ |

> ⚠️ «−22.6% cost per conversion» — заява Meta з її матеріалу про «a recent advertiser test» (median), не незалежний замір; позначати як Meta-claim. Ben окремо підкреслює, що це подано як *cost per conversion* (а не розмитий *cost per result*), тож показник вагоміший. Дати «29 липня / 31 січня» — як озвучив Ben (формулювання «January 31st 2025» у джерелі внутрішньо неузгоджене зі стартом у липні; передано verbatim, рік не перевіряти проти липневого старту). ~70% overlap — ілюстративна цифра «нечесного тесту», не виміряна константа.

## Як було раніше і що змінилось
- ❌ Раніше: **detailed targeting exclusions існували** (original audience options) — можна було виключати інтереси/поведінки/демографії з адсета. Популярний прийом ~кілька років тому: один інтерес/адсет + виключати інтерес адсета A з адсетів B/C/D, щоб уникнути audience overlap і «чистіше» тестувати. ⟦superseded by aTJCB5ESyTc @2025-06-03⟧
- ✅ Зараз: detailed targeting exclusions **прибрані** (нові адсети не мають; наявні — до дедлайну). Для тесту — окремі інтереси per adset БЕЗ взаємних виключень; для overlap-контролю покладатись на delivery Meta. ⟦aTJCB5ESyTc @2025-06-03⟧
- ❌ Раніше прийом виключень мав сенс, бо detailed targeting був жорстким кордоном і overlap між схожими інтересами реально дублював аудиторію в аукціоні. ⟦superseded by aTJCB5ESyTc @2025-06-03⟧
- ✅ Зараз detailed targeting inputs — здебільшого **suggestions** (особливо в A+ Audience), Meta сама керує overlap-ом і доставкою → потреба у ручних виключеннях інтересів майже зникла. ⟦aTJCB5ESyTc @2025-06-03⟧ → [[03-targeting/advantage-plus-audience]]
- ✅ **Не змінилось і не планує:** **custom audience exclusions** лишаються (і в original, і в A+ як hard boundary). Ben не бачить, щоб Meta їх прибирала найближчим часом — вони надто цінні для funnel-таргетингу й new-customer-оферів. ⟦aTJCB5ESyTc @2025-06-03⟧
- ⚠️ Куди йде далі: тренд — забирати дедалі більше ручних таргетингових опцій; гіпотетична межа — повна довіра Meta без інпутів рекламодавця. Ben не очікує цього «скоро», але напрям такий. ⟦aTJCB5ESyTc @2025-06-03⟧

## Помилки / anti-patterns
- ❌ **Виключати інтерес адсета A з адсетів B/C/D** «щоб уникнути overlap» — навіть коли це було можливо, це псувало результат (Meta-дані: +22.6% дорожчі конверсії) і робило тест нечесним (виключаєш 70% аудиторії). Зараз ще й технічно неможливо для нових адсетів. ⟦aTJCB5ESyTc @2025-06-03⟧
- ❌ **Плутати втрату detailed exclusions із втратою custom audience exclusions** і панікувати, що «не можна виключати клієнтів/конвертованих». Custom audience exclusions живі — funnel-таргетинг і new-customer-офери працюють. ⟦aTJCB5ESyTc @2025-06-03⟧
- ❌ **Редагувати наявний адсет, що ще тримає detailed exclusions**, до дедлайну — будь-яка правка вимикає фічу достроково. Якщо вони корисні саме тобі — не чіпати до кінцевої дати. ⟦aTJCB5ESyTc @2025-06-03⟧
- ❌ **Сприймати «cost per result» від Meta як доказ дешевших лідів/продажів.** Туди можуть входити link clicks/impressions/video views; орієнтуватись на *cost per conversion*. ⟦aTJCB5ESyTc @2025-06-03⟧
- ❌ **Сприймати прибирання detailed exclusions як катастрофу.** Для більшості рекламодавців це не біда (вони й так псували результат); біда була б — прибирання custom audience exclusions. ⟦aTJCB5ESyTc @2025-06-03⟧
- ❌ **Сліпо застосовувати «не виключати» як абсолют.** Для вузького підсегмента ніші виключення «широкого» інтересу могло допомагати; винятки під специфіку бізнесу існують. ⟦aTJCB5ESyTc @2025-06-03⟧

## Застосування в аналізі/оптимізації
- **Аудит таргетингу:** якщо акаунт історично будувався на «один інтерес/адсет + взаємні detailed exclusions» → пояснити, що фічі більше немає і вона псувала результат; перевести на окремі інтереси без виключень або broad + value rules. → [[03-targeting/advantage-plus-audience]] · [[03-targeting/value-rules]].
- **Перевірка funnel-логіки:** чи правильно налаштовані **custom audience exclusions** (виключені конвертовані з кампаній на дожим; виключені наявні клієнти з new-customer-оферів) — часта дірка, що шле акцію не тим людям. → [[09-retargeting/retargeting-post-andromeda]].
- **Overlap-діагностика:** не намагатись «лікувати» audience overlap ручними виключеннями інтересів (неможливо й шкідливо) — довіряти delivery Meta; справжній overlap-ризик зараз — **auction overlap від дублювання кампаній**, а не audience overlap інтересів. → [[04-budget-scaling/big-spend-scaling]].
- **Коли клієнт скаржиться, що «прибрали виключення»:** зʼясувати, які саме — detailed (прибрані, ок, вони псували результат) чи custom audience (живі, перевірити налаштування). Не змішувати.
- **A+ Audience hard boundaries:** памʼятати, що excluded custom audiences лишаються жорстким кордоном навіть під автоматичним таргетингом → можна спокійно тримати broad/open і водночас гарантовано не бити по виключених. → [[03-targeting/advantage-plus-audience]].
- **Звʼязок:** [[03-targeting/advantage-plus-audience]] · [[03-targeting/value-rules]] · [[09-retargeting/retargeting-post-andromeda]] · [[04-budget-scaling/big-spend-scaling]] · [[00-philosophy/andromeda-era]] · [[01-structure/asc-vs-manual]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "We have officially just lost another Facebook ads targeting option." — Ben Heath ⟦aTJCB5ESyTc @2025-06-03⟧
> "The median cost per conversion was 22.6% lower when not using detail targeting exclusions." — Ben Heath / Meta data ⟦aTJCB5ESyTc @2025-06-03⟧ Meta-claim
> "That's actually much more valuable than being able to exclude detailed targeting options." — Ben Heath (про custom audience exclusions) ⟦aTJCB5ESyTc @2025-06-03⟧
> "If they got rid of custom audience exclusions… a much bigger deal." — Ben Heath ⟦aTJCB5ESyTc @2025-06-03⟧
> "Excluding 70% of the audience… that's not a really very fair test." — Ben Heath ⟦aTJCB5ESyTc @2025-06-03⟧
> "Whenever they say cost per conversion, that's a much better data point." — Ben Heath ⟦aTJCB5ESyTc @2025-06-03⟧
