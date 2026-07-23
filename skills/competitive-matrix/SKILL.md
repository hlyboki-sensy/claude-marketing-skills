---
name: competitive-matrix
description: Будує конкурентну матрицю (feature-by-feature, ціни, позиціонування) для N конкурентів. Вихід — markdown-таблиця + PNG heatmap для вставки в слайди.
---

# Competitive Matrix

Створює порівняльну матрицю `N конкурентів × M критеріїв`.

## Коли викликати
- "Порівняй конкурентів за ..."
- "Зроби матрицю по ..."
- "Де ми програємо / виграємо?"

## Default критерії
1. **Pricing** — min / max / модель (subscription, one-time, freemium)
2. **Target segment** — хто їх ідеальний клієнт
3. **Key features** — топ-5 фіч
4. **Unique strengths** — чим вирізняються
5. **Weak points** — типові скарги
6. **Brand positioning** — тональність, месседжинг
7. **Marketing channels** — де активні

Користувач може додати свої критерії.

## Виконання
1. **Читай** `competitors.md` + готові досьє з `past-research/`
2. Якщо досьє немає — викликай `deep-competitor-research` для кожного конкурента
3. **Делегуй** `data-analyst`:
   - Markdown-таблиця всіх даних
   - PNG heatmap (`matplotlib` + `seaborn`) зі шкалою where we win/lose
4. **Синтезуй** коментар:
   - Де конкуренти випереджають нашу компанію
   - Де ми попереду
   - Де є **вікно** (слабке у всіх — можливість)

## Вихід
- Markdown-таблиця
- PNG heatmap: `~/knowledge/past-research/charts/matrix_{YYYY-MM-DD}.png`
- 3-буллет коментар з рекомендацією
