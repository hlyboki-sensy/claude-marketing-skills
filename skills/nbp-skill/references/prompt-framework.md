# Prompt Framework

Структурований підхід до створення промптів для NBP. Адаптовано з community best practices.

## Task Types (Навички)

Визнач тип задачі — це задає стратегію промпта:

| Type | Коли використовувати | Ключові елементи |
|------|-------------------|-------------------|
| **Photorealistic** | Фото людей, продуктів, сцен | Освітлення, матеріали, атмосфера |
| **Illustration** | Стікери, іконки, арт | Стиль, контури, палітра |
| **Product/Commercial** | Продуктова зйомка | Поверхня, відблиски, композиція |
| **Minimalist** | Негативний простір | Що прибрати важливіше, ніж що додати |
| **Sequential** | Комікси, сторіборди | Панелі, переходи, наратив |
| **Editing** | Зміна наявного | Конкретні інструкції, що міняти |
| **Style Transfer** | Перенесення стилю | Референс + новий контент |
| **Composite** | Об'єднання елементів | Зв'язність, освітлення, масштаб |
| **Text Rendering** | Текст на зображенні | Точні лапки, позиція, вага |

## Universal Elements (Чекліст)

Пройдись по списку — не все треба вказувати, але корисно перевірити:

**Обов'язкові:**
- **Суб'єкт** — хто/що в центрі уваги
- **Контекст** — для чого це (визначає стиль)

**За ситуацією:**
- **Дія** — що відбувається
- **Оточення** — де це відбувається
- **Камера** — крупність плану (close-up, wide shot тощо)
- **Освітлення** — тип світла (NBP сам обере, якщо не вказати)
- **Настрій** — емоція сцени
- **Матеріали** — текстури поверхонь
- **Палітра** — кольори (краще hex)
- **Формат** — співвідношення сторін

> ⚠️ **Не вказуй:** параметри об'єктива (50mm, 85mm), f-stop, ISO — NBP це ігнорує. Він «думаючий», сам обирає оптимальне.

## Detail Modes (Режими)

**Concise** — одне речення, для швидких ітерацій:
```
Minimalist poster: white background, single red apple, centered, dramatic shadow.
```

**Standard** — 1-2 абзаци, баланс контролю й гнучкості:
```
Create a product shot for premium headphones marketing.

Matte black headphones on dark slate surface. Single spotlight from upper left creates dramatic shadow. Background gradient from #1a1a1a to pure black.

Format: 16:9
```

**Verbose** — максимум деталей для складних сцен:
```
Create a cinematic wide shot for sci-fi film concept art.

Setting: Abandoned space station observation deck. Massive curved window spans entire wall, revealing dying red giant star filling half the frame. Station interior in deep shadow except where crimson light bleeds through.

Subject: Lone astronaut in weathered EVA suit, helmet off, sitting on debris pile. Back to camera, facing the star. Pose suggests exhaustion and acceptance.

Atmosphere: Dust particles float in zero-g, catching red light. Abandoned equipment scattered - coffee cup frozen mid-float, papers suspended. Frost crystals on interior surfaces where life support failed.

Mood: Melancholic beauty, end of an era
Lighting: Volumetric god rays from star through window
Format: 2.39:1 cinemascope
```

## Output Structure

Створюючи промпт, видавай:

**1. Prompt** — готовий до використання

**2. Parameters** — якщо нестандартні:
- Aspect ratio (якщо не 1:1)
- Resolution (якщо потрібно 2K/4K)

**3. Exclusions** — що виключити (опційно):
> Формулюй позитивно! NBP краще розуміє "clean background", ніж "no clutter"

**4. Assumptions** — що додумано, якщо користувач не вказав

## Quick Decision Tree

```
Що створюємо?
├── Фото реального об'єкта/людини → Photorealistic
├── Малюнок/арт → Illustration  
├── Товар на продаж → Product/Commercial
├── Багато порожнього місця → Minimalist
├── Кілька кадрів/історія → Sequential
├── Міняємо наявне фото → Editing
├── «Як на цій картинці» → Style Transfer
├── Збираємо з кількох елементів → Composite
└── Текст — головний елемент → Text Rendering
```

## Examples by Type

### Photorealistic
```
Portrait of a weathered fisherman, 60s, deep wrinkles and sun-damaged skin.
Early morning golden hour on wooden dock.
Holding fresh catch, genuine smile of satisfaction.
Background: misty harbor, fishing boats soft focus.
Mood: authentic, documentary style
```

### Product/Commercial
```
Product shot: luxury watch on raw concrete slab.
Single hard light from upper right, creating defined shadow.
Watch face at 10:10 position, metal bracelet draped naturally.
Background: gradient gray, vignette edges.
Style: high-end catalog, editorial
Format: 4:5
```

### Minimalist
```
Single origami crane, red paper, centered.
Pure white infinite background.
Soft diffused light, barely visible shadow.
Extreme negative space - crane occupies <10% of frame.
Format: 1:1
```

### Text Rendering
```
Motivational poster for gym.

Background: dark textured concrete, subtle vignette.

Text:
"DISCIPLINE" in extra bold, white, centered upper third
"beats talent" in thin weight, #808080, centered below

Small icon: minimal dumbbell silhouette, bottom center
Format: 9:16 (stories)
```
