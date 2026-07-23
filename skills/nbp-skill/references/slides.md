# Presentation Slides

Professional slide visuals for decks and pitches.

## Design Principles

### One Slide = One Idea
Не комбінуй непов'язані концепції. Аудиторія запам'ятовує 65% візуального проти 10% почутого.

### Content Limits
- Max 5 пунктів на слайді
- 15-20 слів у блоці тексту
- Заголовок + список АБО абзац, не обидва

### Typography
```
Заголовок: 44-54 pt, bold
Підзаголовок: 28-36 pt, medium
Текст: 18-24 pt, regular (min 18 для читабельності)

Шрифти: sans-serif основний (Inter, Helvetica, Roboto)
Serif лише для акценту
```

### Contrast & Color
- 3-4 кольори max (основний + 2-3 акценти)
- Один нейтральний фон (white/black/gray)
- Контраст min 4.5:1
- Уникай pure white #fff на чорному — використовуй #f5f5f5

### Whitespace
- Контент має дихати
- Асиметричні макети (2/3 + 1/3) динамічніші за центровані
- Якщо тісно — розбий на два слайди

### Visual Consistency
- Один стиль: фото АБО ілюстрації АБО мінімал-графіка
- Змішування = візуальний хаос
- High-res only, кожен образ підсилює ідею

### Checklist
```
☐ Один слайд = одна ідея
☐ Max 5 пунктів
☐ Заголовок 44-54pt, текст 18-24pt
☐ 3-4 кольори, високий контраст
☐ Достатньо whitespace
☐ High-res візуали, єдиний стиль
```

---

## Slide Types

### Hero Title (Dark)
```
Create dramatic title slide for [CONTEXT] presentation.

Background: Gradient from [DARK hex] to #0a0a0a.
Atmospheric: subtle mist at lower edge.

Typography:
"[MAIN TITLE]" in extra bold, white, extremely large, upper third
"[SUBTITLE]" in thin, muted, 5x smaller, below

Mood: Confident, premium
Format: 16:9
```

### Data Visualization
```
Create data slide for [CONTEXT] presentation.

Background: Dark gradient [hex] to [hex].

Hero number: "[METRIC]" in bold, [ACCENT], center
Trend: [up/down arrow] in [green/red]
Supporting: 3-4 smaller metrics below

Chart: [TYPE] showing [DATA]

Mood: Analytical, impactful
Format: 16:9
```

### Comparison (Light)
```
Create comparison slide for [CONTEXT].

Background: Off-white #fafafa to #f0efed.

Split layout:
Left: "[OPTION A]" with details
Right: "[OPTION B]" with details

Emphasis: Right side accent bar #3b82f6

Mood: Clear, objective
Format: 16:9
```

### Insight/Problem
```
Create insight slide for [CONTEXT].

Background: Clean off-white.

Focal: "[KEY MESSAGE]" in bold, centered
Supporting: "[CONTEXT]" smaller, below
Emphasis bar: [ACCENT] strip with data point

Mood: Clarity, focus
Format: 16:9
```

### Process/Timeline
```
Create process slide for [CONTEXT].

Flow: [HORIZONTAL/VERTICAL]
Stages: [1]→[2]→[3]→[4]
Each: icon + "[LABEL]" + description
Connectors: arrows in [ACCENT]

Format: 16:9
```

## Typography

**Hierarchy:**
- Hero: "Extremely large, dominating upper third"
- Primary: "Large, commanding"
- Secondary: "3-5x smaller than hero"
- Footer: "Minimal"

**Weight:** thin | regular | medium | bold | extra bold
**Position:** "upper third", "left aligned 10% margin", "centered"

## Color Systems

**Dark palette:**
- Near-black: #0a0a0a, #121212
- Deep tones: #0d3d2d, #1a2a3a
- Text: #ffffff, #e0e0e0

**Light palette:**
- Off-white: #fafafa, #f8f9fa
- Warm gray: #f5f5f4
- Text: #1a1a1a, #374151

**Data colors:**
- Positive: #22c55e
- Negative: #dc2626
- Highlight: #3b82f6

## Atmospheric Effects

- "Subtle gradient haze"
- "White mist at ground level"
- "Soft vignette darkening edges"
- "Noise texture for premium feel"

---

## Layout Systems

Універсальні правила верстки. Працюють із будь-яким візуальним стилем.

---

### Bento Grid

Модульна система з блоків різного розміру.

**Core Rules:**
- Батьківський контейнер із явними межами модулів
- Ієрархія: важливий контент → великі блоки, другорядний → дрібні
- Max 9 блоків (інакше перевантаження)
- Однакові gaps (16px стандарт)
- Пов'язаний контент групується в одному блоці

**Розміри:** широкі/пласкі (hero) | вузькі/високі (списки) | квадратні (іконки)

**Сітки:**
```
3-block:           6-block:             9-block:
┌───────┬───┐     ┌───┬───┬───┐       ┌─────┬───┬───┐
│ HERO  │SEC│     │ S │ S │ S │       │HERO │MED│ S │
├───────┴───┤     ├───┴───┼───┤       ├──┬──┴───┼───┤
│  FOOTER   │     │ CHART │LST│       │S │ MED  │ S │
└───────────┘     └───────┴───┘       └──┴──────┴───┘
```

**Prompt:**
```
Layout: bento grid, [N] blocks
Hero block: [MAIN], Medium: [SECONDARY], Small: [ICONS]
Gaps: uniform spacing
```

---

### Asymmetric Grid

Динамічні композиції з візуальним балансом.

**Rules:**
- Починай із базової сітки, потім ламай усвідомлено
- Балансуй вагу: великий елемент зліва = кілька дрібних справа
- Rule of Thirds для природного балансу
- Ключові елементи виділяй розміром і положенням

**Застосовувати:** креативні презентації, портфоліо, fashion, стартапи
**НЕ застосовувати:** банки, держпортали, B2B з великими даними, старша аудиторія

**Prompt:**
```
Layout: asymmetric composition
Left: [LARGE - 60%], Right: [2-3 SMALLER stacked]
Balance: visual weight distributed
Rule of thirds positioning
```

---

### Negative Space

Простір як інструмент фокусування.

**Rules:**
- Структурує, а не створює порожнечу заради естетики
- Керує увагою, фокусує на головному
- Gestalt: елементи з простором = окремі, близько = пов'язані

**Застосовувати:** преміальні бренди, мінімалістичні презентації, hero-секції
**НЕ застосовувати:** новинні портали, дашборди, мобільні версії

**Prompt:**
```
Layout: generous whitespace
Focal point: [ELEMENT] with breathing room
Empty space: intentional, guides eye to [CTA]
```

---

### Split Screen

Двоколонкова композиція.

**Пропорції:**
- 50/50 — рівноцінні елементи
- 60/40 — акцент на одній стороні
- 70/30 — явний герой + підтримка

**Prompt:**
```
Layout: split-screen [RATIO]
Left: [CONTENT], Right: [CONTENT]
Divider: [sharp / gradient / none]
```

---

### Brutalist

Сира естетика, величезні шрифти, яскраві кольори.

**Rules:**
- Зберігай чітку навігацію та ієрархію
- Читабельність > експресія
- Застосовуй селективно: яскраві кольори АБО величезні шрифти

**Застосовувати:** портфоліо художників, fashion, стартапи
**НЕ застосовувати:** e-commerce, корпорати, освіта, фінтех

**Prompt:**
```
Style: brutalist design
Typography: massive, raw
Colors: high contrast, bold
Hierarchy: clear despite unconventional styling
```

---

## Futuristic / SaaS Style

Apple Keynote minimalism + glassmorphism + 3D objects.

### Visual Language
```
Style: Apple Keynote + SaaS + glassmorphism
Mood: premium, immersive, clean, breathable
Lighting: volumetric, ray-traced reflections, ambient occlusion
Base: deep void black OR pure ceramic white
Accents: aurora gradients (neon purple, electric blue, coral, cyan)
```

### Glassmorphism Cards
```
Material: frosted glass with blur
Edges: delicate white borders
Shadow: soft, diffused
Spacing: generous internal whitespace
```

### 3D Visual Anchors
```
Purpose: abstract 3D artifacts as focal points
Materials: polished metal, iridescent acrylic, transparent glass, soft silicone
Shapes: capsules, spheres, shields, Möbius strips, fluid waves
Quality: looks like expensive collectibles
```

### Composition by Type

**Cover:** huge 3D glass object center + bold title + aurora background
**Content:** bento grid + 3D icons in small cards + text in large cards  
**Data:** split-screen (text left, glowing 3D chart right)

### Charts Style
```
3D donut charts, glowing
Capsule-shaped progress bars
Floating numbers with neon glow
Style: looks like glowing neon toys
```

### Example Prompt
```
Create a futuristic SaaS slide for product presentation.

Style: Apple Keynote + glassmorphism.
Mood: premium, immersive, clean.
Background: void black with aurora gradient (purple → cyan).

Layout: bento grid, 6 blocks.
Cards: frosted glass, blur, white edges, soft shadows.
Hero block: floating iridescent sphere.
Data blocks: glowing 3D donut chart, neon metrics.

Typography: clean sans-serif, high contrast white.
Format: 16:9
```
