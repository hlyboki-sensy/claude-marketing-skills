---
topic: "Повний плейбук запуску Meta-реклами post-Andromeda — від нуля до 6 опор перформансу"
category: structure
subcategory: full-playbook
status: active
era: post-andromeda
last_reviewed: 2026-06-03
confidence: high
sources:
  - { id: dAJyqo6wnq4, date: 2026-02-03, era: post-andromeda }
  - { id: JLlcwojiVtw, date: 2026-05-03, era: post-andromeda }
  - { id: kuSq-pmNfnM, date: 2025-10-03, era: post-andromeda }
  - { id: Wfy431Q2Dkw, date: 2025-06-03, era: post-andromeda }
  - { id: BZrio_G_1Cs, date: 2025-06-03, era: post-andromeda }
  - { id: ZZJdSrL4hQQ, date: 2024-06-03, era: pre-andromeda }
  - { id: KgO_J6pwv9I, date: 2024-06-03, era: pre-andromeda }
  - { id: QbTDo7jvjI0, date: 2023-06-03, era: pre-andromeda }
  - { id: _btnN3kQwW4, date: 2024-06-03, era: pre-andromeda }
---

# Повний плейбук запуску Meta-реклами post-Andromeda

## TL;DR
Цілісний end-to-end плейбук: **(1) структура** — Advantage+ де можливо, консолідація до мінімуму кампаній/адсетів, cold+warm разом; **(2) креатив** — UGC/influencer, native-to-platform, hook-варіації, 20 креативів/адсет; **(3) бюджет/масштабування** — старт «який не шкода втратити», масштабувати наявну кампанію + новий креатив; **(4) дані/атрибуція** — Pixel **і** CAPI, зовнішні дані, Hyros; **(5) вимір/оптимізація** — рішення за ROAS/CPA, не за vanity-метриками, не вимикати top-funnel оголошення; **(6) «beyond the buttons»** — бренд/офер/LTV поза кабінетом вирішують найбільше. Beginner-флоу (Business Manager → Ads Manager → campaign → adset → ad) — для тих, хто стартує з нуля. Глибокі деталі винесені в окремі файли (див. перехресні посилання). ⟦kuSq-pmNfnM @2025-10-03⟧

> Pre-Andromeda beginner-туторіали (2023-24: ZZJdSrL4hQQ, QbTDo7jvjI0, KgO_J6pwv9I) — це **прямі предки** теперішнього beginner-флоу. Каркас (auction · leads/sales · daily budget · highest volume · Advantage+ де є · Pixel) **не змінився**, тому вони підтверджують evergreen-спину. Окремий pre-Andromeda матеріал (_btnN3kQwW4) дає математику **LTGP:CAC** (опора №6) і копірайт-глибину (headline-first, call-out method, length∝ask). Усе, що в них застаріло (ручна сегментація адсетами під інтереси, «people living in», 5%-cap аудиторії, фіксований min-audience 250k/500k), винесено в «## Як було раніше і що змінилось». ⟦ZZJdSrL4hQQ @2024-06-03⟧ ⟦QbTDo7jvjI0 @2023-06-03⟧ ⟦_btnN3kQwW4 @2024-06-03⟧

## Принципи [P]

### Філософія плейбука
- [P] **Старі стратегії 2-3-річної давності більше не дають кращий результат.** Чотири головні болі зараз: ростучі CPM, проблеми атрибуції, ad fatigue, опора на застарілі тактики (interest targeting, надмірна сегментація аудиторій). ⟦kuSq-pmNfnM @2025-10-03⟧
- [P] **Найбільший приріст ROAS приходить НЕ з кабінету.** Налаштування важливі, але exceptional-результат завжди має «щось іще» поза акаунтом: сильніший бренд, кращий офер/продукт. Це опора №6 «go beyond the buttons». ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦Wfy431Q2Dkw @2025-06-03⟧
- [P] **Offer + ad creative — те, на що витрачати більшість часу.** Платформа дедалі складніша (Meta нарощує функції для просунутих) — не загубись у placement-опціях/site-links; найбільше рухають результат офер і креатив. **Це справджувалось і pre-Andromeda:** уже в 2024 теза була «таргетинг гомогенізується між рекламодавцями (всі йдуть у broad/open), тож офер і ad creative — там, де отримуєш конкурентну перевагу». ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦KgO_J6pwv9I @2024-06-03⟧
- [P] **Offer — найважливіша частина оголошення (evergreen).** Коли реклама провалюється, найчастіша причина — або **офер недостатньо привабливий** (напр. знижка 2% — нема стимулу діяти), або його **недостатньо ясно** подано (людина не зчитала за мікросекунду). Слабкий офер не врятують ні креатив, ні налаштування. ⟦KgO_J6pwv9I @2024-06-03⟧ Деталі → [[06-creatives/why-ads-fail]] · [[06-creatives/case-studies-revenue]].
- [P] **Obsess over lifetime customer value.** Виграють не ті, у кого найнижчий CPL/CPA, а ті, хто витягує найбільше з кожного ліда/клієнта (subscription-inertia, AOV, reoccurring). Часто легше **подвоїти LTV, ніж вполовинити CPA** — бо CAC має «підлогу» (конкуренти на аукціоні бідять угору ціну), а LTGP можна підняти у 10× чи 100×. Це pre-Andromeda-теза, яка лишилась чинною. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦_btnN3kQwW4 @2024-06-03⟧
- [P] **LTGP:CAC ratio — головна метрика виживання й масштабування (evergreen).** `LTGP = AOV × сер. к-сть покупок за lifetime × gross margin`; `CAC = ad spend / нові клієнти за період`; ціль ratio **≥ 3:1** (не 2:1 — з gross profit ще треба покрити overhead/admin/insurance, які ростуть при масштабі). Це **НЕ те саме, що ROAS**: ROAS у кабінеті бачить лише першу транзакцію, а LTGP:CAC враховує всі повторні покупки за lifetime. Бізнес може бути збитковим на першій покупці й дуже прибутковим за lifetime (приклад McDonald's: клієнт «вартий $50k» за 50 років). ⟦_btnN3kQwW4 @2024-06-03⟧ Перетин з big-spend → [[04-budget-scaling/big-spend-scaling]].
- [P] **Keep it simple на старті, складність — потім.** Beginner свідомо ігнорує advanced-налаштування (collaborative ads, dynamic creative, site links, URL parameters, brand suitability), щоб зменшити барʼєр входу й набрати momentum. Та сама філософія була вже у 2023-24 туторіалах («I'm a big believer in starting simple… add complexity later»). ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [P] **Що ти просиш у Meta — те вона й дасть.** Machine learning дуже добре прогнозує, хто зробить запитану дію; обери objective під реальну бізнес-ціль (lead/sale), і Meta знайде тих людей. Це фундаментальна evergreen-теза, послідовно повторена від 2023 до 2026. ⟦QbTDo7jvjI0 @2023-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧

### Структура й таргетинг
- [P] **Less is more: консолідуй кампанії.** Дефолт — менше кампаній (іноді одна Advantage+). Консолідація зводить spend докупи й дає Meta швидше вчитися (більше конверсій в одній кампанії/адсеті). Деталі → [[01-structure/campaign-structure]]. ⟦kuSq-pmNfnM @2025-10-03⟧
- [P] **Cold і warm — в одній кампанії/адсеті за замовчуванням.** Навіть якщо налаштувати адсет «лише cold» чи «лише warm», без жорстких boundaries Meta трактує таргетинг як suggestions і однаково змішає аудиторії. Тож обʼєднуй і консолідуй дані. ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦JLlcwojiVtw @2026-05-03⟧
- [P] **Controls = hard boundaries, Advantage+ audience/suggestions = підказки.** Те, що в *audience controls* (локація, min age, мова), Meta здебільшого НЕ порушує; те, що в *Advantage+ audience* (інтереси, custom audiences, вік/стать) — підказка, від якої Meta вільно відходить. «Best of both worlds»: даєш напрям + лишаєш гнучкість. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧
- [P] **Campaign objective — одне з найважливіших налаштувань:** воно визначає, як Meta оптимізує. Оптимізація під «не те, що насправді треба» (traffic замість leads/sales) дає кліки, але не ліди/продажі — різниця в cost-per-lead між traffic- і lead-objective величезна й давно доведена. ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [P] **Performance goal може зіпсувати правильний objective.** Навіть з правильним objective (leads/sales) вибір *maximize link clicks / landing page views* зробить кампанію як traffic, а *daily unique reach / impressions* — як awareness. ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- [P] **Не звужуй локацію штучно.** Якщо обслуговуєш усю країну — таргеть усю країну, не лише «найбагатше місто»: Meta сама зллє більшість бюджету туди, де твої найкращі prospects, але знайде й гарних людей деінде. Локальний бізнес — таргеть лише там, куди реально дотягнешся. Та сама порада звучала вже у 2023-24 («don't think London's my best market so I'll just advertise London — Facebook works that out»). ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- [P] **Broad age-range, нехай ML звужує (evergreen).** Якщо ядро 35-45 — став ~25-55 (не вужче), Meta машинно знайде найкращих усередині; вгадувати руками гірше, ніж дати алгоритму простір. ⟦QbTDo7jvjI0 @2023-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧

### Креатив, копірайт, дані, оптимізація
- [P] **UGC-style video — king зараз.** Найкращі результати дають оголошення, що відчуваються native-to-platform (більше як контент, ніж як реклама). Якщо в першу частку секунди людина бачить «це реклама» — гортає далі. ⟦kuSq-pmNfnM @2025-10-03⟧
- [P] **Hook (перші ~3 сек відео) — ключ до успіху відео-оголошень.** Покращивши лише хук, залишивши решту відео тією ж, можна подвоїти+ ROAS. 90-95%+ людей не дивляться далі перших 3 сек. Деталі → [[06-creatives/hooks]]. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦kuSq-pmNfnM @2025-10-03⟧
- [P] **Креатив — єдина частина кампанії, яку реально бачить людина (evergreen).** Що більше таргетинг автоматизується (ML бере на себе адсет-рівень), то більше офер+креатив стають місцем конкурентної переваги. Уже у 2024 це формулювалось прямо. ⟦KgO_J6pwv9I @2024-06-03⟧, ⟦kuSq-pmNfnM @2025-10-03⟧
- [P] **Порядок СТВОРЕННЯ оголошення ≠ порядок СПРИЙНЯТТЯ (evergreen).** Людина сприймає: creative → headline → primary text. А будувати краще навпаки — **спершу headline** (бо він несе офер — найважливіше), потім primary text (підпирає headline), і **creative — в останню чергу**. ⟦KgO_J6pwv9I @2024-06-03⟧ Перетин з тестуванням великих важелів → [[12-testing/post-andromeda-testing]].
- [P] **Headline: ясність > креативність.** Не «загадковий/curiosity-провокуючий» хедлайн (це для email-subject/YouTube-title), а **дуже ясний** опис оферу + 1-2 вигоди. На стрічці людина за мікросекунду має зрозуміти, що це і для неї — інакше гортає, навіть якщо deal насправді чудовий. ⟦KgO_J6pwv9I @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧ Деталі → [[07-copywriting/ad-angles]].
- [P] **Call-out method — спосіб ТАРГЕТИНГУ через копірайт (evergreen, посилився post-Andromeda).** Почати primary text зі звертання до сегмента («Moving home or redecorating?», «New Yorkers», «Texans») → ад сам «фільтрує» потрібних людей, а engagement-сигнали кажуть Meta, кому ще показувати. Особливо цінно там, де таргетинг-опцій немає (Meta прибрала «recently moved»; для локального — «living in» замінено на «living in OR recently in», тож тури/гості ловлять ліди). Копія робить heavy lifting, якого вже не дає кабінет. ⟦KgO_J6pwv9I @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [P] **Length of copy ∝ size of the ask (evergreen).** Маленький ask (купити торт за £15) → коротка, punchy копія; великий ask (дорогий продукт/велика послуга) → більше reasons-why. Жорсткого ліміту немає: маєш 9 сильних benefits — постав усі 9, але не довше, ніж треба (не «вода»). ⟦KgO_J6pwv9I @2024-06-03⟧
- [P] **Tone під тип бізнесу (evergreen).** Playful/emotive для fun-продукту (торти: «smothered in white chocolate buttercream», емодзі), стримано-діловий для B2B/insurance. Той самий список вигод подається різним тоном залежно від продукту. ⟦KgO_J6pwv9I @2024-06-03⟧
- [P] **Meta AI потребує ТОЧНИХ даних.** AI робить дедалі більше таргетингу/оптимізації (скільки показів до покупки, який вік, де локація) — без точних конверсійних даних кампанії не оптимізуються нормально. Big spenders (8 фігур/рік) одержимі точністю даних. ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦Wfy431Q2Dkw @2025-06-03⟧
- [P] **+5% до точності даних → ~25% до ROAS (приблизний приклад масштабу).** Невелике покращення інпутів дає непропорційно великий приріст результату (за словами автора, з досвіду роботи з великими спендерами). ⟦kuSq-pmNfnM @2025-10-03⟧
- [P] **Рішення оптимізації — за ROAS / cost-per-conversion, не за vanity-метриками.** CTR/engagement іноді корелюють із ROAS, часто — ні (клікбейт-оголошення з високим CTR може мати гірший ROAS). На рівні кабінету фокус — на **cost-per-result** і **ROAS**, не на cost-per-click чи к-сті лайків (давня evergreen-настанова). ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [P] **Meta секвенсує оголошення в адсеті як воронку.** Одне оголошення може йти як top-funnel (перший показ), інші — як retarget-конвертери; для різних людей — різні послідовності (хтось одразу йде на конвертер). Тому не суди оголошення в адсеті лише за його ROAS. ⟦kuSq-pmNfnM @2025-10-03⟧

## Тактики зараз [T]

### Опора 1 — Структура кампанії
- [T] **Більшість рекламодавців → Advantage+ кампанії**, консолідувати кілька кампаній у меншу к-сть (іноді одну Advantage+). Винятки для розділення: різні країни або різні product ranges. ⟦kuSq-pmNfnM @2025-10-03⟧ Повна логіка структури → [[01-structure/campaign-structure]].
- [T] **Embrace Advantage+ за замовчуванням, але тестуй альтернативу.** Advantage+ Shopping, Advantage+ Audience, Advantage+ Placements зараз здебільшого б'ють non-Advantage+ еквівалент; це лише дефолт, не «завжди» — перевір під свій бізнес. Через AI/ML переваги Advantage+ з часом лише зростатимуть. ⟦Wfy431Q2Dkw @2025-06-03⟧
- [T] **Спрости структуру при direct-offer стратегії:** раніше 5+ адсетів під різні таргети — тепер рідко; таргетинг або автоматичний (ASC/tailored), або suggestion (Advantage+ audience), тож кілька адсетів під різні інтереси/lookalike безглузді. Можна тримати окремо testing-кампанію і scaling-кампанію, але всередині структура простіша. ⟦Wfy431Q2Dkw @2025-06-03⟧
- [T] **Дай Meta робити своє з delivery/targeting** — лізти вручну (розклад показів, ручні твіки доставки) лише з вагомої причини. ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **НЕ окрема retargeting-кампанія/адсет за замовчуванням** — гібрид cold+warm в одному. Якщо розмітити сегменти й порівняти спліт spend по new/engaged/existing в «retargeting»-адсеті vs «cold»-адсеті — часто він ОДНАКОВИЙ (Meta й так знаходить warm). Окремо ретаргетимо лише якщо warm одержує ІНШИЙ креатив/копірайт. Деталі → [[09-retargeting/retargeting-post-andromeda]]. ⟦JLlcwojiVtw @2026-05-03⟧, ⟦Wfy431Q2Dkw @2025-06-03⟧
- [T] **Розмітка аудиторних сегментів:** All tools → Advertising settings → визнач *engaged audience* (website visitors / email-list / engagers, напр. all website visitors 180 днів) і *existing customers* (підвʼязати customer list). Тоді в breakdown-даних видно спліт spend і результатів по new / engaged / existing на рівні кампанії/адсета/оголошення. ⟦JLlcwojiVtw @2026-05-03⟧

### Опора 2 — Креативна стратегія
- [T] **UGC + influencer/partnership ads** як основа. Influencer-контент native, особливо для його ж аудиторії; партнерські оголошення крутяться з твого і з акаунта креатора. Аутсорс продакшну + scroll-stopping power + вага рекомендації + побудова бренду. Працює не лише для e-com (іноді там менша конкуренція = перевага). ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Hook-варіації, щоб вичавити максимум з робочого оголошення:** взяти 42-сек тіло, що працює, і зробити 10 версій з різними першими 3 сек (різні intro-рядки, різні локації/фони). 90+% не бачать оригінальних 42 сек → нова обгортка хука обходить ad fatigue і фільтр «я це вже бачив». ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **Виробляй БІЛЬШЕ креативу — ціль 20 різних оголошень/адсет** (раніше ліміт 6). Post-Andromeda Meta пріоритезує creative diversity: персоналізує доставку (різним людям — різні оголошення) і відтерміновує ad fatigue. Деталі обсягу/різноманіття → [[00-philosophy/andromeda-era]]. ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Embrace різні формати:** не все відео. Відео — найкращий формат для більшості, але image-варіації швидші/дешевші; різні люди реагують на різні формати — тримай діапазон форматів live. ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Partnership ads — через Creator Marketplace:** All tools → Creator Marketplace; Meta дає рекомендації релевантних креаторів і спрощує контакт. Економіка: віддай ~10% бюджету креаторам, якщо це робить кампанію +40% ефективнішою — вигідна угода. ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Embrace Meta image-variations** при завантаженні креативу (AI підкаже варіації) + зовнішні AI-інструменти для batch-генерації хуків/кутів/форматів. ⟦JLlcwojiVtw @2026-05-03⟧

### Опора 3 — Бюджет і масштабування
- [T] **Старт малим — сумою, яку не шкода втратити** (новий продукт/офер/платформа). «Sweet spot»: міг би втратити, але трохи защемить — щоб був emotional investment і ти реально стежив. Сума дуже різна за бізнесом ($5-10/день … $1000-5000/день). Ця «sweet spot»-настанова незмінна від 2023. ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Масштабуй НАЯВНУ кампанію, не створюй нову**, і масштабуй НЕ лише бюджетом, а й КРЕАТИВОМ: при 10× бюджету одне оголошення навряд тримає перформанс на 10× людей — потрібен новий креатив, що теж тягне ліди/продажі. ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **Можна масштабувати агресивніше, ніж «10-20%»:** Meta заявила, що тепер можна піднімати бюджет більшими кроками (іноді подвоєння) без повторного learning phase — % залежить від поточного бюджету (на $10/день → $20 легко; на $10k/день подвоєння завелике). Особливо для time-sensitive оферів (Black Friday). Для evergreen лишайся обережним. Повна механіка → [[04-budget-scaling/big-spend-scaling]]. ⟦Wfy431Q2Dkw @2025-06-03⟧
- [T] Малобюджетним радять окремий підхід до тестів/економіки → [[04-budget-scaling/small-budget]]. ⟦JLlcwojiVtw @2026-05-03⟧

### Опора 4 — Дані й атрибуція
- [T] **Мінімум: Pixel І Conversions API**, обидва шлють точні конверсії. Це НЕ «або/або» — потрібні обидва. ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **Завантаж зовнішні дані:** email-списки, customer lists, люди, що взаємодіяли давніше за вікно трекінгу Pixel (>180 днів) — все, чого Meta ще не має. Потім сегментуй (engaged / existing / решта = cold). ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **Hyros — для найкращого трекінгу/атрибуції** (за словами автора, ним користуються всі великі гравці; він користується і для ads, і для organic). Причина критичності: у Meta максимальне вікно атрибуції **7 днів**, тож відкладені/recurring-конверсії Meta не бачить. Деталі why-it-matters → [[06-creatives/why-ads-fail]] (суміжне). ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦Wfy431Q2Dkw @2025-06-03⟧

### Опора 5 — Вимір і оптимізація
- [T] **Оптимізуй за ROAS / cost-per-conversion**, ігноруй vanity (CTR, engagement, video views), якщо вони не транслюються в ліди/продажі. ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **НЕ вимикай оголошення з низьким ROAS в адсеті** — ймовірно, воно у top-funnel ролі; вимкнеш → впаде ROAS «хорошого» конвертера. **Вимикай лише ті оголошення, на які Meta не витрачає бюджет** (це і є офіційна рекомендація Meta). Якщо Meta далі ллє на оголошення навіть з гіршим ROAS — лиши. ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **Ітеруй як у спортзалі:** регулярно вимикай оголошення без spend, заводь нові, копіюй переможні хуки → з часом великий приріст (за один «тренування» непомітно). ⟦kuSq-pmNfnM @2025-10-03⟧
- [T] **Opportunity score** (нова фіча, не в усіх акаунтів): score/100 + рекомендації; здебільшого поради гарні, особливо коли результати слабкі (напр. 72/100 → є що покращити). ⟦Wfy431Q2Dkw @2025-06-03⟧
- [T] **AI text generation в кабінеті — використовуй, але будь фільтром:** Meta згенерує 5 варіантів primary text/headline (іноді під персони-аватари); беремо 2-3, інколи тюнимо під voice бренду. Економія часу, але слідкуй — інакше ад-копі може втратити сенс. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧
- [T] **Creative enhancements — case-by-case, не «все увімкнути / все вимкнути».** Пройди кожне: text overlay (добре для простого e-com-зображення; погано, якщо вже багато тексту), image/background generation (добре для product-style; зле, якщо потрібне впізнаване обличчя founder для warm-аудиторії), музика/анімація/фільтри — оцінюй під свій креатив. Деталі → [[06-creatives/creative-enhancements]]. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧
- [T] **Creative Testing tool** для тонких A/B (хуки/overlay/фон), бо звичайний адсет схлопує схожі оголошення. Деталі → [[12-testing/post-andromeda-testing]]. ⟦JLlcwojiVtw @2026-05-03⟧

### Опора 6 — Beyond the buttons
- [T] **Збудуй конкурентну перевагу поза кабінетом:** сильніший бренд (personal brand дає впізнаваність → вищий CTR/конверсію), кращий продукт/офер, нижчий барʼєр входу (tripwire), вищий LTV (subscription/AOV/reoccurring). ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦Wfy431Q2Dkw @2025-06-03⟧
- [T] **Підіймай LTGP трьома важелями (evergreen, з _btnN3kQwW4):** (1) **знизити churn / збільшити к-сть покупок** — кращий продукт/сервіс, email/SMS-retargeting/referrals, знижка в пакуванні замовлення для повторної покупки; (2) **підняти ціну з доданою цінністю** (часто +ціна вдвічі коштує лише +10-30% витрат на доставку цінності); (3) **bundles/cross-sells/upsells** при product-бізнесі. Підняв LTGP достатньо → можеш спокійно дозволити CAC рости при масштабі чи подорожчанні CPM. ⟦_btnN3kQwW4 @2024-06-03⟧

### Просунуті тактики 2026 (з JLlcwojiVtw)
- [T] **Value rules** — впливай на те, кому Meta показує, БЕЗ жорстких обмежень: Advertising settings → value rules → create a rule set → критерій (вік/стать/локація…) → +% до bid для цінного сегмента (напр. 35+ = +30%). Meta далі показує всім, але «доплачує» за цінніших. Деталі → [[03-targeting/value-rules]]. ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Acquisition — на краях спектра, не в мід-рейнджі:** або free/дешевий tripwire (легко й операційно дешево віддати), або high-ticket/premium/high-touch (елонгований sales-процес окупається). Мід-рейндж найважче масштабувати (там уся конкуренція, важко диференціюватися, грошей замало для high-touch). ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Embrace WhatsApp у воронці** (локаційно-залежно): click-to-WhatsApp → автоматизовані перші меседжі → кваліфікація → людина. Менше friction за «лендинг+дзвінок через 3 дні», часто дешевше для бізнесу. UK: краще для high-ticket; India/Brazil: продається будь-що, у т.ч. low-ticket; US — поки WhatsApp слабкий (прогноз: зайде за 5-10 років). Можна слати marketing messages тим, хто взаємодіяв. ⟦JLlcwojiVtw @2026-05-03⟧
- [T] **Geo-fencing для локального бізнесу:** Meta прибрала опцію «people living in» (лишилось «living in OR recently in») → ліди з чужих локацій. Рішення: таргетувати потрібне місто/радіус + ВИКЛЮЧИТИ навколишні зони. Не 100% точно, але зріже витрату на нерелевантних з 20-30% до 2-5%. ⟦Wfy431Q2Dkw @2025-06-03⟧

### Beginner full-flow (з нуля)
- [T] **Крок 0 — структура акаунта:** створи Meta Business Manager (business.facebook.com, залогінений у FB-профіль) → у Settings додай **Facebook page** (add existing / request access / create), **Instagram account** (тільки professional; personal перемкнеться), **ad account** (claim existing за ad account ID / create new — правильні timezone+currency, потім важко змінити). Додай **people** і признач assets (включно з собою). Кроки незмінні від 2023-24 (тоді — «Meta Business Suite → settings → add asset»; інтерфейс трохи мінявся, логіка та сама). Повна деталізація → [[01-structure/business-account-setup]]. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Кампанію створюй в Ads Manager → Campaigns** (не в Business Suite). Три рівні: campaign → ad set → ad. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Campaign level:** buying type = **auction** (не reservation: reservation дешевший, але Meta дасть нижчоякісні impressions/prospects). Objective: для початківця — **leads** (є проміжний крок до покупки: дзвінок/форма) або **sales** (можна купити прямо на сайті). Awareness/traffic/engagement/app — лише за спецсценаріями (traffic — змушено, коли не можна трекнути конверсію). Назва кампанії — описова. Declare **special ad category** (фінанси/робота/житло/соц-політика), якщо підпадаєш — інакше ризик блоку акаунта. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Budget:** **daily budget** (гнучкіше, без фікс-дати, легше масштабувати) > lifetime (у lifetime останні 1-2 дні spend часто «з'їдається» без результату). Bid strategy = **highest volume** (default; не став bid cap на старті — ризик, що оголошення взагалі не покрутяться). Campaign budget (Advantage Campaign Budget/CBO) розподіляє бюджет на найкращі адсети — корисно початківцю; при 1 адсеті байдуже. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Adset level — conversion location:** website (вже є лендинг) / instant forms (швидко без сайту) / Messenger / Instagram / WhatsApp / calls. **Performance goal = maximize number of conversions** (якщо всі ліди рівноцінні) або **maximize value/ROAS** (різні чеки — особливо sales/e-com). НЕ обирай link clicks / landing page views / reach / impressions. Обери **dataset (Pixel)** і **conversion event** (lead/purchase). ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- [T] **Attribution setting — максимальна (7-day click / 1-day view).** Довше вікно = більше даних у кабінет (для оптимізації + для тебе): хто став лідом за 7 днів після кліку чи за 1 день після перегляду. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧ Сучасний розклад вікон і engage-through → [[00-philosophy/andromeda-era]].
- [T] **Adset — таргетинг:** *Controls* (hard): локація (де клієнти; не звужуй штучно; локальним — зняти «reach more people likely to respond»/interested-in-city, навіть якщо Meta лякає +X% дорожчим CPL), min age (18-25, лише під legal), мова. *Advantage+ / suggested* (м'яко): age-range (core, не вужче ~10-15 років), gender (all, якщо не 90/10), detailed targeting (1-4 очевидні інтереси, не перевантажуй), custom audiences (warm — додати пізніше). ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧
- [T] **Adset — placements:** при leads/sales лиши **Advantage+ placements** (Meta поставить туди, де буде конверсія). Якщо змушений на traffic → manual placements, прибрати **Audience Network** (найнижча якість), лишити feeds/stories/reels. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Ad level:** identity (правильні FB page / IG / Threads). Format = **single image or video** (початківцю — image: простіше; carousel — пізніше). Destination URL (перевір, що веде куди треба!). Завантаж медіа у **3 співвідношеннях** (square для feeds, vertical 9:16 для stories/reels, horizontal — найменш важливе); square-кроп у vertical ріже текст → краще окреме vertical-зображення. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- [T] **Ad — копірайт (build order: headline → primary text → creative):** короткий primary text, що тикає багато боксів (call-out аудиторії → agitate проблему → feature → benefit → scarcity/urgency → CTA). До **5 primary / 5 headline / 5 description** варіацій (тестуй копірайт ТУТ, окремі оголошення — для іншого КРЕАТИВУ). CTA-кнопка — за наступним кроком (learn more / book / shop now / get quote). Перед написанням — **виписати список причин, чому люди купують** твій продукт (вигода/економія/статус/час/емоція), і вплести найсильніші. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦KgO_J6pwv9I @2024-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- [T] **Ad — enhancements + AI images:** пройди по кожному (turn off те, що ламає сенс: enhanced media text на text-heavy зображенні, translate якщо не виконуєш мовою, overlays поверх щільного тексту); AI-варіації зображень бери лише ті, що працюють (founder-face НЕ замінюй на згенеровану людину для warm). Publish → рев'ю ~30 хв (перші оголошення довше). ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧
- [T] **Перевір billing** перед запуском (Ads Manager → Billing → payment method) — без платіжки Meta не запустить кампанію. ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- [T] **Після запуску — learning phase ~48 год** (на новому акаунті довше): Meta тестує час доби/під-сегменти аудиторії; перші результати можуть бути гіршими. Не суди по перших годинах. Деталі → [[05-optimization/learning-phase]]. ⟦QbTDo7jvjI0 @2023-06-03⟧

## Числа / бенчмарки

| Параметр | Значення | Джерело |
|---|---|---|
| Рекоменд. к-сть креативів/адсет | 20 (раніше ліміт 6) | ⟦JLlcwojiVtw @2026-05-03⟧ |
| Варіацій копірайту в одному оголошенні | до 5 primary / 5 headline / 5 description | ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧ |
| Hook | перші ~3 сек відео | ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦kuSq-pmNfnM @2025-10-03⟧ |
| % людей, що не дивляться далі хука | 90-95%+ | ⟦kuSq-pmNfnM @2025-10-03⟧ |
| Приклад hook-методу | те саме тіло (~42 сек) × 10 різних перших 3 сек | ⟦kuSq-pmNfnM @2025-10-03⟧ |
| Макс. вікно атрибуції Meta | 7 днів (звідси потреба в Hyros для відкладених/recurring) | ⟦Wfy431Q2Dkw @2025-06-03⟧ |
| Вікно трекінгу Pixel для warm | ~180 днів (давніших — вантажити вручну) | ⟦kuSq-pmNfnM @2025-10-03⟧ |
| Приклад value-rule | 35+ → +30% до bid | ⟦JLlcwojiVtw @2026-05-03⟧ |
| Min age (контрол) | 18-25 (лише під legal-обмеження) | ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧ |
| Розумна ширина age-suggestion | не вужче ~10-15 років (ядро 35-45 → став 25-55) | ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧ |
| Аспект-співвідношення креативу | square (feeds) · 9:16 vertical (stories/reels) · horizontal (найменш важливе) | ⟦dAJyqo6wnq4 @2026-02-03⟧ |
| Час рев'ю оголошення | ~30 хв (перші — довше; новий акаунт ~годину) | ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧ |
| Тривалість learning phase | ~48 год (на новому акаунті довше) | ⟦QbTDo7jvjI0 @2023-06-03⟧ |
| Економіка influencer | ~10% бюджету креатору → ~+40% ефективності кампанії | ⟦JLlcwojiVtw @2026-05-03⟧ |
| Geo-fencing: зріз нерелевантної витрати | з 20-30% до 2-5% | ⟦Wfy431Q2Dkw @2025-06-03⟧ |
| **LTGP:CAC — цільовий ratio** | ≥ 3:1 (бачені клієнтські 12:1, 20:1, навіть 60:1) | ⟦_btnN3kQwW4 @2024-06-03⟧ |
| **LTGP:CAC — приклад-розрахунок** | AOV $125 × 6 покупок × 50% margin = LTGP $375; spend $5k / 100 нових = CAC $50 ⇒ **7.5:1** | ⟦_btnN3kQwW4 @2024-06-03⟧ |
| **ROAS ≠ LTGP:CAC (той самий приклад)** | LTGP:CAC 7.5 ↔ кабінетний ROAS лише 2.5× (бачить тільки 1-шу з 6 покупок) | ⟦_btnN3kQwW4 @2024-06-03⟧ |
| Чому ціль не 2:1 | з gross profit ще треба покрити overhead/admin/insurance (ростуть при масштабі) | ⟦_btnN3kQwW4 @2024-06-03⟧ |
| Length of copy | ∝ розміру ask (малий ask → коротко; великий ask → більше reasons) | ⟦KgO_J6pwv9I @2024-06-03⟧ |
| Meta image-enhancement claim (pre-A) | «standard enhancements»: −3% cost-per-result, якщо НЕ ввімкнути | ⟦KgO_J6pwv9I @2024-06-03⟧ Meta-claim |
| **Meta-claim:** Advantage+ audience дешевший CPL | до 33% (pre-A; «up to» — ймовірно завищено) | ⟦ZZJdSrL4hQQ @2024-06-03⟧ Meta-claim |
| **Meta-claim:** +5% точності даних → ~25% ROAS (приклад масштабу) | приблизний приклад, не замір | ⟦kuSq-pmNfnM @2025-10-03⟧ |
| **Meta-claim:** site links знижують cost-per-result | до 4.5% | ⟦BZrio_G_1Cs @2025-06-03⟧ |
| **Meta-claim:** «reach more people interested in city» дешевший CPL | на 6.7% (але ліди можуть бути нерелевантні локально) | ⟦dAJyqo6wnq4 @2026-02-03⟧ |
| Масштаб автора (контекст довіри, 2026) | $200M+ за 12 років, 3000+ клієнтів | ⟦dAJyqo6wnq4 @2026-02-03⟧ |
| Масштаб автора (2025) | $100M+ за 11 років, 2000+ клієнтів | ⟦BZrio_G_1Cs @2025-06-03⟧ |
| Масштаб автора (pre-A, 2023-24) | агенція ~30-40+ осіб, сотні клієнтів, «tens of millions» ад-спенду; min-бюджет клієнта $3k/міс | ⟦QbTDo7jvjI0 @2023-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧ |

> ⚠️ Рядки з позначкою **Meta-claim** — це заяви Meta / приблизні приклади масштабу від автора, не незалежні заміри. У дистрибутиві подавати як claim, не як гарантію. LTGP:CAC-приклад (375/50 = 7.5) — навчальний розрахунок із гіпотетичними числами, не реальний кейс.

## Як було раніше і що змінилось
- ❌ **Раніше (pre-Andromeda, 2023-24 туторіали):** опора на **interest targeting і дрібну сегментацію аудиторій** — створювати 3-4+ адсети, у кожному ОДИН detailed-targeting інтерес (digital marketing / social media marketing / small business owners), щоб «порівняти, який краще»; **дублювати адсети через `duplicate`** для тесту таргетингу; **lookalike-аудиторії**; ручне розведення placements; **фіксований min-розмір аудиторії 250k (US 500k) і cap ~5% населення**; **«people living in this location»** як рекомендований вибір для локального бізнесу. ⟦superseded by kuSq-pmNfnM @2025-10-03⟧ ⟦superseded by JLlcwojiVtw @2026-05-03⟧ era: pre-andromeda ⟦QbTDo7jvjI0 @2023-06-03⟧ ⟦ZZJdSrL4hQQ @2024-06-03⟧
- ❌ **Раніше:** ліміт **~6 оголошень/адсет**; масштабування лише «10-20% раз на тиждень»; non-Advantage+ ручні кампанії «бо більше контролю». ⟦superseded by JLlcwojiVtw @2026-05-03⟧ ⟦superseded by Wfy431Q2Dkw @2025-06-03⟧ era: pre-andromeda
- ⚠️ **Конкретні зміни інтерфейсу/делівері pre→post:**
  - «people living in this location» **прибрали** → лишилось лише «living in OR recently in» (тури/гості тепер ловлять локальні ліди) ⟦superseded by Wfy431Q2Dkw @2025-06-03⟧; рішення тепер — **geo-fencing** (місто + exclude навколо) і **call-out method** у копії. ⟦Wfy431Q2Dkw @2025-06-03⟧
  - Ручні тести таргетингу окремими адсетами / `duplicate` → тепер таргетинг автоматичний (Advantage+ audience як suggestion), а тести — **через Creative Testing tool / окрему testing-кампанію**, бо дублі дають auction overlap. ⟦superseded by JLlcwojiVtw @2026-05-03⟧ → [[12-testing/post-andromeda-testing]] · [[04-budget-scaling/big-spend-scaling]]
  - Max attribution window був **28d click / 28d view** → тепер **7d click / 1d view**, плюс зʼявилась нова **engage-through** атрибуція. ⟦superseded by Wfy431Q2Dkw @2025-06-03⟧ → [[00-philosophy/andromeda-era]]
  - Sponsor-інструмент для відео в pre-A туторіалі (InVideo, шаблони) — це епізодична **реклама стороннього сервісу**, не методологія; зараз акцент на **UGC/influencer/AI-генерацію та Creator Marketplace**. ⟦KgO_J6pwv9I @2024-06-03⟧
- ✅ **Зараз:** Advantage+ як дефолт; консолідація до мінімуму кампаній/адсетів; cold+warm разом; 20 різнопланових креативів/адсет; копірайт через variations; масштабування можна агресивнішими кроками (іноді ×2) без re-learning, % спадає зі зростанням бюджету; рішення за ROAS/CPA, не за vanity; не вимикати top-funnel оголошення; новіші важелі — value rules, Creator Marketplace/partnership ads, Creative Testing tool, opportunity score, WhatsApp-воронки, geo-fencing.
- ✅ **Що НЕ змінилось (evergreen-спина, підтверджена pre- і post-):** auction (не reservation) · leads/sales objective (не traffic/awareness) · daily budget (не lifetime) · highest volume bid · «sweet spot» стартового бюджету · broad age + ML звужує · Advantage+ placements при leads/sales · прибрати Audience Network при traffic · max attribution window · Pixel обовʼязковий · «keep it simple на старті» · **offer = найважливіша частина** · **LTV/LTGP:CAC > гонитва за CPA** · headline-first build + ясність копії + call-out method + length∝ask.
- ⚠️ **Beginner-флоу теж зрушив у деталях:** у версії 2026 (⟦dAJyqo6wnq4⟧) додалися Threads як платформа placement, окрема опція «reach more people likely to respond» для локального бізнесу, помітно покращена AI-генерація зображень (у 2023-24 її практично не було), value-rule preview в інтерфейсі. Базовий каркас лишився тим самим, що й у 2023-25 (⟦QbTDo7jvjI0⟧ ⟦BZrio_G_1Cs⟧). ⟦dAJyqo6wnq4 @2026-02-03⟧

## Помилки / anti-patterns
- ❌ **Оптимізувати під traffic**, очікуючи ліди/продажі — Meta дасть кліки, не конверсії (давня класична помилка). ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Зіпсувати правильний objective performance-goal'ом** (link clicks / landing page views / reach / impressions замість conversions). ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- ❌ **Вимкнути top-funnel оголошення** «бо жере бюджет без конверсій» → впаде ROAS конвертера. Вимикай лише ті, на які Meta не ллє spend. ⟦kuSq-pmNfnM @2025-10-03⟧
- ❌ **Гнатися за vanity-метриками** (CTR/engagement) як за метою оптимізації; engagement-objective дасть лайки/коменти, але ті люди рідше стають лідами/покупцями. ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Pixel АБО CAPI** як «або/або» — треба обидва. ⟦kuSq-pmNfnM @2025-10-03⟧
- ❌ **Масштабувати лише бюджет без нового креативу** — одне оголошення не тримає 10× аудиторії; і **створювати нову кампанію** замість масштабувати наявну. ⟦kuSq-pmNfnM @2025-10-03⟧
- ❌ **Сегментувати cold/warm вручну** в окремі кампанії/адсети — Meta усе одно змішає (overlap), втрачаєш консолідацію. ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦JLlcwojiVtw @2026-05-03⟧
- ❌ **Тестувати дрібні варіації звичайними адсетами** — Meta схлопне в одне; бери Creative Testing tool. ⟦JLlcwojiVtw @2026-05-03⟧
- ❌ **Сліпо вмикати/вимикати ВСІ creative enhancements** і бездумно брати ВЕСЬ AI-копірайт/AI-зображення — будь фільтром (founder-face не замінювати на згенеровану людину для warm). ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧
- ❌ **Штучно звужувати локацію** (лише «найбагатше місто»), коли обслуговуєш усю країну. І навпаки — **локальному бізнесу таргетити надто широко** / лишати «interested in city», ловлячи нерелевантні ліди. ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Reservation buying type для початківця** — дешевше, але нижча якість prospects/impressions. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Bid cap / cost-per-result goal на старті** — ризик, що оголошення взагалі не покрутяться (важко вгадати реальний CPL без історії). Старт — highest volume. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Lifetime budget для evergreen-кампанії** — закінчується, важко продовжити/масштабувати, останні дні spend «з'їдається». Daily краще. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Не declare special ad category**, коли підпадаєш — ризик блоку всього акаунта. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Загрузнути в advanced-налаштуваннях** (placement/site-links/brand suitability/URL params/dynamic creative/AB-tool) на старті замість офера й креативу. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Square-зображення в 9:16** без окремого vertical — ріже текст, оголошення «не працює». ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦ZZJdSrL4hQQ @2024-06-03⟧
- ❌ **Лишити Audience Network** при traffic-кампанії (немає трекінгу конверсії) — дешеві, але низькоякісні placements. ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- ❌ **Цілитись у мід-рейндж** для acquisition (найважче масштабувати/диференціюватися). ⟦JLlcwojiVtw @2026-05-03⟧
- ❌ **Гнатися за найнижчим CPL/CPA**, ігноруючи LTV — виграє той, хто витягує більше з клієнта. Симетрична evergreen-помилка — **дивитись лише на lifetime REVENUE без margin** (бізнес із 90% маржі й бізнес із 10% при однаковому $750 revenue мають $675 vs $75 gross profit). ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦_btnN3kQwW4 @2024-06-03⟧
- ❌ **Плутати ROAS у кабінеті з реальною економікою** — кабінетний ROAS бачить лише першу транзакцію й 7-денне вікно; recurring/lifetime-цінність він НЕ показує (звідси хибне «реклама не окупається» при насправді 7.5:1 LTGP:CAC). ⟦_btnN3kQwW4 @2024-06-03⟧
- ❌ **«Загадковий»/curiosity-headline** на стрічці — це для email/YouTube, не для Meta; тут потрібна миттєва ясність оферу. ⟦KgO_J6pwv9I @2024-06-03⟧
- ❌ **Будувати оголошення «як його бачать» (creative-first)** замість headline-first — губиш фокус на офері; і **wordy/«водяна» копія** довша, ніж потребує ask. ⟦KgO_J6pwv9I @2024-06-03⟧
- ❌ **Не звести AOV до середнього** («ну це залежить, хтось $10, хтось $5000») — для LTGP:CAC потрібне саме середнє, інакше метрику не порахувати. ⟦_btnN3kQwW4 @2024-06-03⟧
- ❌ **Розраховувати, що «правильний кабінет» = exceptional-результат** без переваги поза кабінетом (бренд/офер/продукт). ⟦kuSq-pmNfnM @2025-10-03⟧

## Застосування в аналізі/оптимізації
- **Аудит за 6 опорами** — швидкий чекліст здоров'я акаунта: (1) структура консолідована? Advantage+? (2) креатив — ≥10-20 різнопланових/адсет, UGC/influencer, hook-варіації? (3) бюджет масштабується наявною кампанією + новим креативом? (4) Pixel **і** CAPI активні, зовнішні дані залиті, Hyros? (5) рішення за ROAS/CPA, top-funnel оголошення не вимикають? (6) є перевага поза кабінетом (бренд/офер/LTV)? Будь-яке «ні» → прапор.
- **Якщо результати слабкі** — спершу перевір не кабінет, а офер + ad creative + LTV-економіку (опори №2 і №6), бо саме вони рухають найбільше. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦kuSq-pmNfnM @2025-10-03⟧, ⟦KgO_J6pwv9I @2024-06-03⟧
- **Якщо 0 лідів/продажів** — діагностуй насамперед **офер** (привабливість + ясність), не налаштування. → [[06-creatives/why-ads-fail]] · [[06-creatives/case-studies-revenue]].
- **Економічна валідація перед масштабом:** порахуй **LTGP:CAC** (AOV × purchases × margin ÷ CAC). <3:1 → працювати над LTGP (churn/ціна/bundles/реактивація) перш ніж лити бюджет; ≥3:1 → можна масштабувати, прийнявши, що кабінетний ROAS виглядатиме нижчим за реальну економіку. → [[04-budget-scaling/big-spend-scaling]]. ⟦_btnN3kQwW4 @2024-06-03⟧
- **Оголошення з великими витратами й майже без конверсій** при хорошому CPL інших — НЕ вимикати наосліп (ймовірний автоматичний top-funnel у послідовності Meta). ⟦kuSq-pmNfnM @2025-10-03⟧
- **Перевір objective + performance goal + dataset** як перший крок діагностики «багато кліків, мало лідів» (класична помилка traffic/wrong-goal). ⟦BZrio_G_1Cs @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦QbTDo7jvjI0 @2023-06-03⟧
- **Локальний бізнес з лідами «не звідти»** → geo-fencing (місто + exclude навколо), call-out method у копії («[City]-ians…»), і зняти «interested in city». ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦dAJyqo6wnq4 @2026-02-03⟧, ⟦KgO_J6pwv9I @2024-06-03⟧
- **Слабка копія в аудиті** → перевір порядок (headline несе офер?), ясність (зрозуміло за мікросекунду?), call-out на початку primary text, length∝ask, tone під бізнес, наявність CTA в кінці. → [[07-copywriting/ad-angles]]. ⟦KgO_J6pwv9I @2024-06-03⟧
- **Розрив reported-vs-actual ROAS** (особливо recurring/довгий цикл рішення >7 днів) → потрібен Hyros, бо Meta не бачить за 7-денним вікном. ⟦Wfy431Q2Dkw @2025-06-03⟧, ⟦kuSq-pmNfnM @2025-10-03⟧
- **Opportunity score < 100** → пройти рекомендації (здебільшого валідні), особливо коли перформанс просів. ⟦Wfy431Q2Dkw @2025-06-03⟧
- **Звʼязок:** [[01-structure/business-account-setup]] · [[01-structure/campaign-structure]] · [[00-philosophy/andromeda-era]] · [[02-objectives/choosing-objective]] · [[03-targeting/value-rules]] · [[03-targeting/advantage-plus-audience]] · [[04-budget-scaling/big-spend-scaling]] · [[04-budget-scaling/small-budget]] · [[05-optimization/learning-phase]] · [[06-creatives/creative-enhancements]] · [[06-creatives/why-ads-fail]] · [[06-creatives/case-studies-revenue]] · [[06-creatives/hooks]] · [[07-copywriting/ad-angles]] · [[09-retargeting/retargeting-post-andromeda]] · [[12-testing/post-andromeda-testing]].

## Цитати (INTERNAL — у дистрибутиві перефразувати)
> "I've got a full playbook. I've got a number of steps, number of things I'd recommend you do." — Ben Heath ⟦kuSq-pmNfnM @2025-10-03⟧
> "Less is more. Less allows you to consolidate ad spend. It allows Meta to learn faster." — Ben Heath ⟦kuSq-pmNfnM @2025-10-03⟧
> "UGC style video… is king right now. That's what's producing the best results across the board." — Ben Heath ⟦kuSq-pmNfnM @2025-10-03⟧
> "It's not a either or when it comes to the pixel or Cappy. You want both set up and installed." — Ben Heath ⟦kuSq-pmNfnM @2025-10-03⟧
> "Turn off ads… that Meta is not spending any money on. That's their recommendation." — Ben Heath ⟦kuSq-pmNfnM @2025-10-03⟧
> "If you want incredible results, you have to have something that goes beyond the buttons." — Ben Heath ⟦kuSq-pmNfnM @2025-10-03⟧
> "We now aim for 20 different ad creatives per ad set. We used to be limited to six." — Ben Heath ⟦JLlcwojiVtw @2026-05-03⟧
> "Offers an ad creative… where you should be spending the majority of your time." — Ben Heath ⟦Wfy431Q2Dkw @2025-06-03⟧
> "Let's keep it simple. We can add complexity later on." — Ben Heath ⟦dAJyqo6wnq4 @2026-02-03⟧
> "What you ask Meta to get you is what they will get you." — Ben Heath (pre-A) ⟦ZZJdSrL4hQQ @2024-06-03⟧
> "I'm a big believer in starting simple… you can always add in complexity when you feel more comfortable." — Ben Heath (pre-A) ⟦ZZJdSrL4hQQ @2024-06-03⟧
> "When an ad doesn't succeed, one of the main reasons is often because the headline doesn't make the offer clear enough, or the offer just isn't appealing enough." — Ben Heath (pre-A) ⟦KgO_J6pwv9I @2024-06-03⟧
> "The length of your ad copy should be related to the size of the ask." — Ben Heath (pre-A) ⟦KgO_J6pwv9I @2024-06-03⟧
> "Obsess over your LTGP." — Ben Heath (pre-A) ⟦_btnN3kQwW4 @2024-06-03⟧
> "It's often a lot easier to increase your lifetime gross profit than to decrease your cost to acquire a customer." — Ben Heath (pre-A) ⟦_btnN3kQwW4 @2024-06-03⟧
> "A McDonald's customer is worth $50,000… they'll be loss-making on that first transaction but a very profitable business." — Ben Heath (pre-A) ⟦_btnN3kQwW4 @2024-06-03⟧
