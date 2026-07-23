---
name: research-zettelkasten
description: |
  Запускає глибинне дослідницьке проєктування за методологією Zettelkasten (Niklas Luhmann, адаптовано kkarpushin для Claude Code).
  Використовуй для ДОВГОТРИВАЛИХ досліджень (5-50+ годин роботи): аналіз ринку, deep competitor research, регуляторний аналіз, дослідження методологій, аналіз великих масивів джерел (50+ URL).
  Структурує знання через 7 типів артефактів: sources / notes / claims / syntheses / contradictions / verdicts / experiments + machine-readable graph.
  Опціонально інтегрується з клієнтами ~/knowledge/clients/{slug}/past-research/.
  НЕ для швидких задач (рілси, пости, креативи) — для них використовуй спеціалізовані скіли.
  Тригери: почати дослідження, deep research, Zettelkasten, організувати джерела, дослідницький проєкт, аналіз ринку на тиждень, серйозне дослідження, база знань з джерел, research project, knowledge base, регуляторний аналіз, дослідження методології.
---

# Research Zettelkasten — Глибинне дослідницьке проєктування

## Що цей скіл робить

Скіл-обгортка над **university-template** (kkarpushin) — методологія Zettelkasten для довготривалих досліджень з Claude Code.

**Шлях до шаблону:** `~/templates/university/`

Створює структуроване середовище для проєкту, де ти кидаєш джерела (URL, документи) — Claude розкладає їх по 7 типах артефактів із cross-references.

## Коли НЕ використовувати

- Швидкі задачі (рілси, пости, креативи, листи) — є спеціалізовані скіли
- "Швидко глянути конкурента" — використай `deep-competitor-research`
- Один-два рази глянути ринок — використай `competitor-report`

## Коли використовувати

- Регуляторний аналіз (наприклад, технічний регламент UA 2026 для client-a)
- Deep market analysis (50+ джерел, місяць+ роботи)
- Дослідження методології конкурента (наприклад, повний розбір моделі Каті)
- Дисертаційне/книжне дослідження (особисте)

## АЛГОРИТМ РОБОТИ

### Крок 0: Визначення контексту

**Перше питання:**
> "Дослідницький проєкт буде для конкретного клієнта (client-a / client-b / client-c) чи окремий (особистий / для нового проєкту)?"

**Друге питання:**
> "Як називається проєкт дослідження? (одним рядком, латиницею через дефіси — це буде назва папки. Наприклад: ua-cosmetics-regulation-2026, client-b-competitors-deep, katya-program-methodology)"

### Крок 1: Створення проєкту через bootstrap

**Шлях створення (залежно від відповіді):**

- **Якщо для клієнта:**
  ```
  ~/knowledge/clients/{slug}/past-research/research-{topic}/
  ```
- **Якщо особисте/окреме:**
  ```
  ~/research-projects/{topic}/
  ```
  (Створи папку `research-projects/` якщо не існує: `mkdir -p ~/research-projects`)

**Виконай bootstrap:**

```bash
# Спершу переконайся, що папка research-projects/ існує (якщо особисте)
mkdir -p ~/research-projects

# Запуск bootstrap (підстав правильний TARGET_PATH)
~/templates/university/bootstrap.sh "<TARGET_PATH>"
```

Bootstrap автоматично:
- Створює структуру папок (sources/, notes/, claims/, syntheses/, contradictions/, verdicts/, experiments/, graph/)
- Копіює skeleton
- Створює Claude memory файли з правильними шляхами
- Запускає interview.py (інтерактивне опитування)

### Крок 2: 6 питань інтерв'ю (за автором)

Якщо interview.py запустився інтерактивно — користувач відповідає сам.
Якщо ні (terminal не підтримує interactive) — задай 6 питань самостійно через AskUserQuestion:

1. **Project Mission** — одним реченням, навіщо цей проєкт?
2. **Seed Docs** — які вже існуючі документи треба обробити першими?
3. **In-Scope Topics** — що приймаємо в обробку?
4. **Out-of-Scope Topics** — що відразу відкидаємо?
5. **Taxonomy** — теми/підтеми (формат: `<root>/<leaf>`, наприклад: `regulation/eu-cosmetic-directive`, `competitors/client-a/packaging`)
6. **Code/Docs Paths** — де лежать матеріали для порівняння з реальністю?

Відповіді запиши у `METHODOLOGY.md` проєкту.

### Крок 3: Інтеграція з knowledge base клієнта (якщо клієнт)

Якщо проєкт для клієнта — додай у METHODOLOGY.md секцію:

```markdown
## Контекст клієнта

- Клієнт: {slug}
- Company profile: ~/knowledge/clients/{slug}/company-profile.md
- ДНК клієнта (якщо є): ~/knowledge/clients/{slug}/past-research/client-dna-{slug}.md
- Tone of voice (якщо є): ~/knowledge/clients/{slug}/past-research/tone-of-voice-{slug}.md
- Попередні дослідження: ~/knowledge/clients/{slug}/past-research/
```

Це дозволить майбутньому Claude (коли користувач відкриє цей research-проєкт) автоматично підтягувати весь контекст клієнта.

### Крок 4: Інструкція користувачу

Покажи користувачу:
- Шлях до створеного проєкту
- Як кидати джерела (просто давай URL у чаті — Claude обробить за Zettelkasten)
- Що результати накопичуватимуться у відповідних папках
- Що через тиждень-місяць там буде структурована база знань

## Як працює Zettelkasten на практиці

Коли користувач у research-проєкті дає URL/документ, Claude:

1. **Source** → завантажує матеріал у `sources/<id>/` з summary
2. **Notes** → витягує атомарні ідеї (1 файл = 1 думка) у `notes/n-<slug>.md`
3. **Claims** → формулює перевірні твердження з доказами у `claims/c-<NNNN>.md`
4. **Cross-link** → додає зв'язки в `graph/edges.jsonl`
5. **Synthesis** → коли накопичується критична маса — синтез у `syntheses/syn-<topic>.md`
6. **Contradictions** → якщо знаходить суперечність між джерелами — фіксує у `contradictions/contr-<NNN>.md`
7. **Verdicts** → коли користувач приймає рішення на основі дослідження — у `verdicts/v-<slug>.md`

## Приклад використання

```
> "Почати deep research для client-a — регуляторний аналіз українського технічного регламенту 2026"

Скіл:
1. Підтверджує: клієнт = client-a, topic = ua-cosmetics-regulation-2026
2. TARGET_PATH = ~/knowledge/clients/client-a/past-research/research-ua-cosmetics-regulation-2026/
3. Запускає bootstrap.sh
4. Веде через 6 питань (mission, seed docs, scope, taxonomy)
5. Інтегрує контекст клієнта з company-profile
6. Покаже шлях і скаже: "Кидай мені URL — я розкладатиму за Zettelkasten"

Далі ти кидаєш:
> https://zakon.rada.gov.ua/laws/show/.../ua

Claude:
- Створює sources/2026-05-27-rada-regulation/summary.md
- Витягує claims: "Виробник зобов'язаний реєструвати продукт у X днів" → claims/c-0001.md
- Знаходить суперечність із попереднім джерелом → contradictions/contr-001.md
- Оновлює graph/edges.jsonl
```

## Важливі правила

1. **Цей скіл — стартовий**, він тільки створює структуру. Реальна робота йде в окремому research-проєкті (Claude автоматично підвантажує memory).
2. **Не запускай bootstrap двічі для тієї самої теми** — це затре існуючу базу. Якщо проєкт вже існує — скажи користувачу: "Проєкт з такою назвою існує. Хочеш доповнити чи створити з нуля (затре старе)?"
3. **Опціонально для всіх клієнтів** — research можна робити і без клієнта (особистий блог, навчання, тощо)
4. **Назва topic** — латиниця, через дефіси, без пробілів, без спецсимволів. Це назва папки.
