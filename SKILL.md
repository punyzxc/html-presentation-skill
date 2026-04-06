---
name: html-presentation
description: "Создание HTML-презентаций с glassmorphism дизайном и анимациями. Триггеры: создай презентацию, сделай презу, make presentation, slides, слайды. Генерирует полноценный интерактивный HTML-файл с навигацией, прогресс-баром и адаптивной типографикой."
argument-hint: "Тема презентации"
---

> ⚠️ **ВАЖНО: НЕ использовать Reveal.js и другие внешние библиотеки!**  
> Презентации должны работать **полностью офлайн** — возможны проблемы с сетью во время выступлений.

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

## Технические ограничения

❌ **НЕ использовать:**
- Reveal.js или другие фреймворки
- Внешние JS-библиотеки (CDN)
- Обязательные внешние ресурсы

✅ **Использовать:**
- Чистый HTML/CSS/JS в одном файле
- Google Fonts с fallback на системные (`system-ui, sans-serif`)
- `scroll-snap` для навигации
- `IntersectionObserver` для отслеживания слайдов
- CSS-анимации (@keyframes)

---

## Шаг 1: Выбор визуального стиля

> **Спроси пользователя или выбери по теме.** Если стиль не подошёл — предложи альтернативу.

### 🔮 GLASSMORPHISM (по умолчанию)
Стеклянный эффект, размытый фон, тёмная тема с глубиной
```css
--bg-dark: #0a0a0f;
--glass: rgba(255, 255, 255, 0.05);
--glass-border: rgba(255, 255, 255, 0.1);
backdrop-filter: blur(20px);
border-radius: 16px;
```
**Когда:** Технологии, AI, стартапы, современные темы  
**Шрифт:** `Inter`, `Space Grotesk`

---

### 🌙 MINIMAL DARK
Чистый минимализм, много пространства, без blur-эффектов
```css
--bg: #09090b;
--surface: #18181b;
--border: #27272a;
--text-primary: #fafafa;
--text-secondary: #a1a1aa;
/* Чёткие границы, без backdrop-filter */
```
**Когда:** Бизнес, аналитика, серьёзные темы, право  
**Шрифт:** `DM Sans`, `Inter`

---

### ☀️ MINIMAL LIGHT
Светлая тема, чистота, профессионализм
```css
--bg: #ffffff;
--surface: #f4f4f5;
--text-primary: #18181b;
--text-secondary: #52525b;
--border: #e4e4e7;
--accent: #2563eb;
```
**Когда:** Медицина, образование, официальные презентации, печать  
**Шрифт:** `Source Sans Pro`, `Inter`

---

### 🌈 GRADIENT MESH
Яркие градиентные фоны, насыщенные цвета, энергия
```css
/* Каждый слайд может иметь свой градиент */
--gradient-1: linear-gradient(135deg, #667eea, #764ba2);
--gradient-2: linear-gradient(135deg, #f093fb, #f5576c);
--gradient-3: linear-gradient(135deg, #4facfe, #00f2fe);
--text: #ffffff;
/* Белый текст, тёмные карточки для контраста */
```
**Когда:** Креатив, маркетинг, дизайн, мода, музыка  
**Шрифт:** `Sora`, `Poppins`

---

### 🔳 NEOMORPHISM
Мягкие выпуклые элементы, тонкие тени, тактильность
```css
--bg: #e0e5ec;
--text-primary: #2d3436;
--text-secondary: #636e72;
/* Двойные тени для эффекта выпуклости */
box-shadow: 8px 8px 16px #b8bec4, -8px -8px 16px #ffffff;
border-radius: 20px;
```
**Когда:** UI/UX презентации, продуктовый дизайн, мягкие темы  
**Шрифт:** `DM Sans`, `Nunito`

---

### ⚡ BRUTALIST
Резкий контраст, жёсткие линии, bold типографика, без скруглений
```css
--bg: #000000;
--text: #ffffff;
--accent: #ff0000; /* или #00ff00, #ffff00 */
border: 3px solid var(--accent);
border-radius: 0; /* Без скруглений! */
font-weight: 900;
text-transform: uppercase;
```
**Когда:** Искусство, авангард, провокационные темы, молодёжь  
**Шрифт:** `Space Mono`, `JetBrains Mono`

---

### 🏢 CORPORATE
Строгий корпоративный стиль, синие тона, надёжность
```css
--bg: #f8fafc;
--surface: #ffffff;
--primary: #1e40af;
--secondary: #3b82f6;
--text: #1e293b;
--border: #e2e8f0;
/* Тонкие линии, сдержанные акценты */
```
**Когда:** Бизнес-отчёты, инвесторам, корпоративные презентации  
**Шрифт:** `Source Sans Pro`, `IBM Plex Sans`

---

### 🎮 RETRO / NEON
Ретро-футуризм, неоновые цвета, synthwave эстетика
```css
--bg: #0f0f23;
--neon-pink: #ff2a6d;
--neon-cyan: #05d9e8;
--neon-purple: #d300c5;
text-shadow: 0 0 10px currentColor, 0 0 20px currentColor;
/* Сетка на фоне, свечение текста */
background-image: linear-gradient(transparent 95%, rgba(5,217,232,0.1) 95%),
                  linear-gradient(90deg, transparent 95%, rgba(5,217,232,0.1) 95%);
```
**Когда:** Игры, развлечения, ретро-темы, молодёжные мероприятия  
**Шрифт:** `Orbitron`, `Space Mono`

---

## Шаг 2: Выбор цветовой палитры (акценты)

| Тема контента | Палитра | Цвета |
|---------------|---------|-------|
| Технологии, AI, психология | Purple-Cyan | `#a855f7` `#3b82f6` `#22d3ee` |
| Бизнес, наука, медицина | Blue-Teal | `#3b82f6` `#0ea5e9` `#14b8a6` |
| Дизайн, креатив, маркетинг | Pink-Purple | `#ec4899` `#a855f7` `#8b5cf6` |
| Экология, здоровье | Green-Cyan | `#10b981` `#14b8a6` `#22d3ee` |
| Спорт, энергия | Orange-Red | `#f97316` `#ef4444` `#ec4899` |
| Образование, история | Warm | `#f59e0b` `#ea580c` `#d97706` |
| Право, философия | Indigo | `#6366f1` `#818cf8` `#a5b4fc` |

---

## Шаг 3: Выбор шрифтов

| Назначение | Google Fonts | Fallback |
|------------|--------------|----------|
| Универсальный | `Inter` | `system-ui, sans-serif` |
| Технологии | `Space Grotesk` | `system-ui, sans-serif` |
| Код/моно | `JetBrains Mono` | `monospace` |
| Академический | `Crimson Pro` | `Georgia, serif` |
| Креативный | `Sora`, `Poppins` | `system-ui, sans-serif` |
| Минимализм | `DM Sans` | `system-ui, sans-serif` |
| Брутализм | `Space Mono` | `monospace` |
| Элегантный | `Playfair Display` | `Georgia, serif` |
| Корпоративный | `Source Sans Pro` | `system-ui, sans-serif` |

> **Всегда указывай fallback!** `font-family: 'Inter', system-ui, -apple-system, sans-serif;`

---

## Шаг 4: Определить типы слайдов

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

---

## Анимации

### Появление элементов

```css
/* Базовое появление снизу */
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Появление с масштабом */
@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}

/* Появление слева */
@keyframes slideInLeft {
  from { opacity: 0; transform: translateX(-40px); }
  to { opacity: 1; transform: translateX(0); }
}

/* Появление справа */
@keyframes slideInRight {
  from { opacity: 0; transform: translateX(40px); }
  to { opacity: 1; transform: translateX(0); }
}

/* Плавное появление */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
```

### Stagger-эффект (элементы по очереди)

```css
.stagger > *:nth-child(1) { animation-delay: 0.1s; }
.stagger > *:nth-child(2) { animation-delay: 0.2s; }
.stagger > *:nth-child(3) { animation-delay: 0.3s; }
.stagger > *:nth-child(4) { animation-delay: 0.4s; }
.stagger > *:nth-child(5) { animation-delay: 0.5s; }
.stagger > *:nth-child(6) { animation-delay: 0.6s; }

.animate-on-view { opacity: 0; }
.animate-on-view.animate-in { 
  animation: fadeInUp 0.6s ease-out forwards; 
}
```

### Фоновые эффекты

```css
/* Плавающие орбы */
@keyframes floatOrb {
  0%, 100% { transform: translate(0, 0) scale(1); }
  25% { transform: translate(50px, -40px) scale(1.1); }
  50% { transform: translate(-30px, 50px) scale(0.95); }
  75% { transform: translate(40px, 30px) scale(1.05); }
}

/* Пульсация для акцентов */
@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.6; transform: scale(0.85); }
}

/* Свечение (для NEON стиля) */
@keyframes glow {
  0%, 100% { text-shadow: 0 0 10px currentColor, 0 0 20px currentColor; }
  50% { text-shadow: 0 0 20px currentColor, 0 0 40px currentColor; }
}
```

### Hover-эффекты

```css
/* Подъём карточки */
.glass-card {
  transition: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}
.glass-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 60px var(--glow);
}

/* Линия сверху при hover */
.glass-card.accent::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: var(--gradient);
  opacity: 0;
  transition: opacity 0.3s ease;
}
.glass-card.accent:hover::before { opacity: 1; }
```

### Настройка под стиль

| Стиль | Рекомендуемые анимации |
|-------|------------------------|
| Glassmorphism | `fadeInUp`, `floatOrb`, плавные hover |
| Minimal | `fadeIn`, минимум движения |
| Gradient Mesh | `scaleIn`, смена градиентов |
| Neomorphism | Мягкие `fadeIn`, без резких движений |
| Brutalist | Без анимаций или резкие `slideIn` |
| Corporate | Сдержанные `fadeIn`, `fadeInUp` |
| Retro/Neon | `glow`, `pulse`, мерцание |

---

## Чек-лист

- [ ] Слайды умещаются в viewport
- [ ] Навигация работает
- [ ] nav-dots = количество секций
- [ ] Единая цветовая палитра
