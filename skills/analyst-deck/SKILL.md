---
name: analyst-deck
description: Генерує senior-рівня аналітичну презентацію (.pptx) з досліджень і даних. Використовує Action Titles і McKinsey/BCG-структуру.
---

# Analyst Deck

Продукує .pptx презентацію executive-рівня.

## Коли викликати
- "Зроби презентацію з цього дослідження"
- "Побудуй дек для борду"
- "Презентація по конкуренту X"

## Вхід
- Research досьє (з `past-research/`)
- Аналітичний звіт з даними і графіками (з `past-research/`)
- Опціонально: аудиторія (CEO / інвестори / команда) — впливає на тон

## Виконання
1. **Читай** `presentation-style.md`
2. **Делегуй** `slide-builder`, який:
   - Використовує скіл `anthropic-skills:pptx`
   - Будує 10-секційну структуру (див. нижче)
   - Кожен заголовок — Action Title
   - Вставляє графіки з `/knowledge/past-research/charts/`
3. **Збережи** фінал: `~/knowledge/past-research/{topic}_{YYYY-MM-DD}.pptx`

## Структура (10 секцій)
1. Title
2. Executive summary (3-5 actionable буллетів)
3. Context
4. Methodology (коротко)
5. Key findings (1 фінд = 1 слайд)
6. Deep dives
7. Framework (SWOT / Porter's 5 / BCG / JTBD)
8. Recommendations (Now / Next / Later)
9. Next steps
10. Appendix (джерела, методологія, сирі дані)

## Вихід
- Шлях до .pptx
- Перелік 3-5 ключових Action Titles
