---
name: html-presentation
description: "Создание HTML-презентаций с glassmorphism дизайном и анимациями. Триггеры: создай презентацию, сделай презу, make presentation, slides, слайды. Генерирует полноценный интерактивный HTML-файл с навигацией, прогресс-баром и адаптивной типографикой."
argument-hint: "Тема презентации"
---

# 🎨 HTML Glassmorphism Presentation Generator

Создаёт профессиональные HTML-презентации с современным glassmorphism дизайном, плавными анимациями и полной навигацией.

## Когда использовать

- "Создай презентацию на тему X"
- "Сделай презу про Y"  
- "Make presentation about Z"
- "Нужны слайды на тему..."

## Входные данные

1. **Тема** — название презентации
2. **Материал** — текст, тезисы, файл `Материал.txt` (опционально)
3. **Количество слайдов** — если не указано, 8-15 оптимально

---

## Шаг 1: Выбор цветовой палитры

| Тема контента | Палитра | CSS-переменные |
|---------------|---------|----------------|
| Технологии, AI, психология, инновации | Purple-Cyan | `--accent-1: #a855f7; --accent-2: #8b5cf6; --accent-3: #3b82f6; --accent-4: #22d3ee;` |
| Бизнес, наука, медицина, аналитика | Blue-Teal | `--accent-1: #3b82f6; --accent-2: #0ea5e9; --accent-3: #14b8a6; --accent-4: #06b6d4;` |
| Дизайн, креатив, маркетинг, мода | Pink-Purple | `--accent-1: #ec4899; --accent-2: #d946ef; --accent-3: #a855f7; --accent-4: #8b5cf6;` |
| Экология, здоровье, природа | Green-Cyan | `--accent-1: #10b981; --accent-2: #14b8a6; --accent-3: #06b6d4; --accent-4: #22d3ee;` |
| Спорт, энергия, мотивация | Orange-Red | `--accent-1: #f97316; --accent-2: #ef4444; --accent-3: #ec4899; --accent-4: #f59e0b;` |
| Образование, педагогика, история | Warm Academic | `--accent-1: #f59e0b; --accent-2: #d97706; --accent-3: #ea580c; --accent-4: #78716c;` |
| Философия, право, официальное | Indigo-Slate | `--accent-1: #6366f1; --accent-2: #818cf8; --accent-3: #a5b4fc; --accent-4: #94a3b8;` |

**Градиент:** `--gradient: linear-gradient(135deg, var(--accent-1), var(--accent-3), var(--accent-4));`

## Шаг 2: Выбор шрифтов

| Стиль | Google Fonts |
|-------|--------------|
| Универсальный | `Inter:wght@400;500;600;700;800` |
| Технологии | `Inter` + `JetBrains+Mono` |
| Академический | `Merriweather` + `Source+Sans+Pro` |
| Креативный | `Poppins:wght@300;400;500;600;700;800` |

## Шаг 3: Определить типы слайдов

1. **Title Slide** — заголовок, подзаголовок, автор
2. **Content Slide** — заголовок + текст/списки
3. **Grid Slide** — сетка карточек (2-4 колонки)
4. **Stats Slide** — крупные числа
5. **Quote Slide** — цитата
6. **Conclusion Slide** — выводы
7. **Thank You Slide** — финал

## Шаг 4: Создать HTML-файл

Используй полный шаблон из [references/full-template.md](./references/full-template.md).

---

## Быстрый CSS-минимум

```css
:root {
  --bg-dark: #0a0a0f;
  --glass: rgba(255, 255, 255, 0.05);
  --glass-border: rgba(255, 255, 255, 0.1);
  --text-primary: #f1f5f9;
  --text-secondary: rgba(255, 255, 255, 0.65);
  /* + accent colors */
}

html { scroll-snap-type: y mandatory; }
section { min-height: 100vh; scroll-snap-align: start; }

.glass-card {
  background: var(--glass);
  backdrop-filter: blur(20px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
}

.gradient-text {
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

h1 { font-size: clamp(2.5rem, 5vw, 4rem); }
h2 { font-size: clamp(1.75rem, 3.5vw, 2.5rem); }
p  { font-size: clamp(1rem, 1.5vw, 1.2rem); }
```

## Обязательные компоненты

- Фоновые орбы с `@keyframes floatOrb`
- Navigation dots (`.nav-dots`)
- Progress bar (`.progress-wrap > .progress-bar`)
- Slide counter
- Keyboard navigation (стрелки, пробел)
- IntersectionObserver для scroll

## Чек-лист

- [ ] Слайды умещаются в viewport
- [ ] Навигация работает
- [ ] nav-dots = количество секций
- [ ] Единая цветовая палитра
