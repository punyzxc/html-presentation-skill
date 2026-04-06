---
name: html-presentation
description: "Создание HTML-презентаций с glassmorphism дизайном и анимациями. Триггеры: создай презентацию, сделай презу, make presentation, slides, слайды. Генерирует полноценный интерактивный HTML-файл с навигацией, прогресс-баром и адаптивной типографикой."
argument-hint: "Тема презентации"
---

> ⚠️ **ВАЖНО: НЕ использовать Reveal.js и другие внешние библиотеки!**  
> Презентации должны работать **полностью офлайн** — возможны проблемы с сетью во время выступлений.

# 🎨 HTML Presentation Generator

Создаёт профессиональные HTML-презентации с современным дизайном, плавными анимациями и полной навигацией.

## Когда использовать

- "Создай презентацию на тему X"
- "Сделай презу про Y"  
- "Make presentation about Z"
- "Нужны слайды на тему..."

## Входные данные

1. **Тема** — название презентации
2. **Материал** — текст, тезисы, файл `Материал.txt` (опционально)
3. **Количество слайдов** — если не указано, 8-15 оптимально
4. **Стиль** — если не указано, выбрать по теме

---

## 📝 Правила работы с контентом

### Язык презентации

> ⚠️ **СТРОГО:** Весь текст презентации должен быть на **ОДНОМ языке**.

- Если материал на русском → вся презентация на русском
- Если материал на английском → вся презентация на английском
- **НЕ смешивать** языки в одной презентации
- Термины переводить или оставлять с пояснением в скобках
- Цитаты на иностранном языке → перевод + оригинал курсивом

**Примеры:**
```
❌ "Используем machine learning для анализа"
✅ "Используем машинное обучение для анализа"

❌ "Метод peer review показал..."
✅ "Метод рецензирования (peer review) показал..."
```

### Подготовка материала

Перед созданием слайдов **обработай материал**:

1. **Структурируй** — выдели главные тезисы (1 слайд = 1 идея)
2. **Сократи** — убери избыточность, оставь суть
3. **Адаптируй** — переформулируй для устной подачи
4. **Визуализируй** — определи что показать схемой/иконкой/числом

### Структура материала по слайдам

| Тип слайда | Контент | Объём |
|------------|---------|-------|
| Title | Заголовок, подзаголовок, автор | 2-3 строки |
| Content | 1 тезис + пояснение или список | 3-5 пунктов |
| Grid | 3-6 карточек с короткими тезисами | 1-2 строки на карточку |
| Stats | 2-4 числа с подписями | Число + 5-7 слов |
| Quote | 1 цитата + автор | До 30 слов |
| Conclusion | 2-4 ключевых вывода | По 1 строке |

---

## Технические ограничения

❌ **НЕ использовать:**
- Reveal.js или другие фреймворки
- Внешние JS-библиотеки (CDN)
- Обязательные внешние ресурсы
- Внешние изображения (использовать SVG inline)

✅ **Использовать:**
- Чистый HTML/CSS/JS в одном файле
- Google Fonts с fallback на системные (`system-ui, sans-serif`)
- `scroll-snap` для навигации
- `IntersectionObserver` для отслеживания слайдов
- CSS-анимации (@keyframes)
- Inline SVG для иконок и схем

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
6. **Diagram Slide** — схема, процесс, связи
7. **Table Slide** — сравнительная таблица
8. **Timeline Slide** — хронология, этапы
9. **Conclusion Slide** — выводы
10. **Thank You Slide** — финал

---

## 🎨 SVG Иконки (анимированные)

> Использовать **inline SVG** — работает офлайн, можно анимировать через CSS.

### Базовая структура иконки в круге

```html
<div class="icon-circle">
  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
    <!-- SVG path здесь -->
  </svg>
</div>
```

```css
.icon-circle {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: var(--gradient);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}
```

### Популярные иконки (готовые SVG)

```html
<!-- Галочка -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <polyline points="20 6 9 17 4 12"></polyline>
</svg>

<!-- Стрелка вправо -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <line x1="5" y1="12" x2="19" y2="12"></line>
  <polyline points="12 5 19 12 12 19"></polyline>
</svg>

<!-- Лампочка (идея) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M9 18h6M10 22h4M12 2a7 7 0 0 0-4 12.7V17h8v-2.3A7 7 0 0 0 12 2z"></path>
</svg>

<!-- Пользователь -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="12" cy="7" r="4"></circle>
  <path d="M5 21v-2a7 7 0 0 1 14 0v2"></path>
</svg>

<!-- График (рост) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline>
  <polyline points="17 6 23 6 23 12"></polyline>
</svg>

<!-- Книга -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
  <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
</svg>

<!-- Шестерёнка (настройки) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="12" cy="12" r="3"></circle>
  <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path>
</svg>

<!-- Сердце -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M20.8 4.6a5.5 5.5 0 0 0-7.8 0L12 5.7l-1-1.1a5.5 5.5 0 0 0-7.8 7.8l1 1.1L12 21l7.8-7.5 1-1.1a5.5 5.5 0 0 0 0-7.8z"></path>
</svg>
```

### Анимации для SVG

```css
/* Пульсация иконки */
.icon-pulse svg {
  animation: iconPulse 2s ease-in-out infinite;
}
@keyframes iconPulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}

/* Вращение (для шестерёнки) */
.icon-spin svg {
  animation: iconSpin 3s linear infinite;
}
@keyframes iconSpin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* Рисование линии (stroke-dasharray) */
.icon-draw svg path,
.icon-draw svg polyline {
  stroke-dasharray: 100;
  stroke-dashoffset: 100;
  animation: drawLine 1s ease forwards;
}
@keyframes drawLine {
  to { stroke-dashoffset: 0; }
}

/* Появление с масштабом */
.icon-pop {
  animation: iconPop 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55) forwards;
}
@keyframes iconPop {
  from { transform: scale(0); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}

/* Покачивание */
.icon-shake svg {
  animation: iconShake 0.5s ease-in-out;
}
@keyframes iconShake {
  0%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(-10deg); }
  75% { transform: rotate(10deg); }
}
```

---

## 📊 Таблицы

### Стилизованная таблица

```html
<div class="styled-table-wrap">
  <table class="styled-table">
    <thead>
      <tr>
        <th>Заголовок 1</th>
        <th>Заголовок 2</th>
        <th>Заголовок 3</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Данные</td>
        <td>Данные</td>
        <td>Данные</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.styled-table-wrap {
  overflow-x: auto;
  margin: 20px 0;
}

.styled-table {
  width: 100%;
  border-collapse: collapse;
  font-size: clamp(0.85rem, 1.1vw, 1rem);
}

.styled-table thead {
  background: var(--gradient);
}

.styled-table th {
  padding: 14px 18px;
  text-align: left;
  font-weight: 600;
  color: white;
}

.styled-table th:first-child { border-radius: 12px 0 0 0; }
.styled-table th:last-child { border-radius: 0 12px 0 0; }

.styled-table td {
  padding: 12px 18px;
  border-bottom: 1px solid var(--glass-border);
  color: var(--text-secondary);
}

.styled-table tbody tr {
  transition: background 0.3s ease;
}

.styled-table tbody tr:hover {
  background: var(--glass);
}

/* Таблица сравнения (две колонки) */
.comparison-table td:first-child {
  font-weight: 600;
  color: var(--text-primary);
}
```

### Таблица "за и против"

```html
<div class="pros-cons">
  <div class="pros">
    <h4>✅ Преимущества</h4>
    <ul class="styled-list">
      <li>Пункт 1</li>
      <li>Пункт 2</li>
    </ul>
  </div>
  <div class="cons">
    <h4>❌ Недостатки</h4>
    <ul class="styled-list">
      <li>Пункт 1</li>
      <li>Пункт 2</li>
    </ul>
  </div>
</div>
```

---

## 📈 Схемы и диаграммы

### Блок-схема процесса (горизонтальная)

```html
<div class="process-flow">
  <div class="process-step">
    <div class="step-icon">1</div>
    <div class="step-label">Этап 1</div>
  </div>
  <div class="process-arrow">→</div>
  <div class="process-step">
    <div class="step-icon">2</div>
    <div class="step-label">Этап 2</div>
  </div>
  <div class="process-arrow">→</div>
  <div class="process-step">
    <div class="step-icon">3</div>
    <div class="step-label">Этап 3</div>
  </div>
</div>
```

```css
.process-flow {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 16px;
  flex-wrap: wrap;
}

.process-step {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

.step-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: var(--gradient);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: 700;
  color: white;
  box-shadow: 0 8px 30px var(--glow);
}

.step-label {
  font-size: 0.9rem;
  color: var(--text-secondary);
  text-align: center;
}

.process-arrow {
  font-size: 1.5rem;
  color: var(--accent-1);
  animation: arrowPulse 1.5s ease-in-out infinite;
}

@keyframes arrowPulse {
  0%, 100% { opacity: 1; transform: translateX(0); }
  50% { opacity: 0.5; transform: translateX(5px); }
}
```

### Вертикальный таймлайн

```html
<div class="timeline">
  <div class="timeline-item">
    <div class="timeline-marker"></div>
    <div class="timeline-content glass-card">
      <div class="timeline-date">2020</div>
      <h4>Событие 1</h4>
      <p>Описание</p>
    </div>
  </div>
  <div class="timeline-item">
    <div class="timeline-marker"></div>
    <div class="timeline-content glass-card">
      <div class="timeline-date">2022</div>
      <h4>Событие 2</h4>
      <p>Описание</p>
    </div>
  </div>
</div>
```

```css
.timeline {
  position: relative;
  padding-left: 40px;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 15px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--gradient);
}

.timeline-item {
  position: relative;
  margin-bottom: 24px;
}

.timeline-marker {
  position: absolute;
  left: -40px;
  top: 20px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--accent-1);
  border: 3px solid var(--bg-dark);
  box-shadow: 0 0 0 3px var(--accent-1);
}

.timeline-content {
  padding: 16px 20px;
}

.timeline-date {
  font-size: 0.8rem;
  color: var(--accent-1);
  font-weight: 600;
  margin-bottom: 6px;
}
```

### Круговая диаграмма (SVG)

```html
<svg class="pie-chart" viewBox="0 0 100 100" width="200" height="200">
  <!-- Фон -->
  <circle cx="50" cy="50" r="40" fill="none" stroke="var(--glass-border)" stroke-width="8"/>
  <!-- Сегмент 70% -->
  <circle cx="50" cy="50" r="40" fill="none" stroke="var(--accent-1)" stroke-width="8"
          stroke-dasharray="175.9 251.3" stroke-dashoffset="0"
          transform="rotate(-90 50 50)"
          class="pie-segment"/>
  <!-- Центр -->
  <text x="50" y="50" text-anchor="middle" dy="0.35em" 
        fill="var(--text-primary)" font-size="16" font-weight="700">70%</text>
</svg>
```

```css
.pie-segment {
  animation: pieGrow 1s ease-out forwards;
}

@keyframes pieGrow {
  from { stroke-dasharray: 0 251.3; }
  to { stroke-dasharray: 175.9 251.3; }
}
```

### Прогресс-бары

```html
<div class="progress-item">
  <div class="progress-label">
    <span>Навык 1</span>
    <span>85%</span>
  </div>
  <div class="progress-bar-bg">
    <div class="progress-bar-fill" style="--progress: 85%"></div>
  </div>
</div>
```

```css
.progress-item {
  margin-bottom: 16px;
}

.progress-label {
  display: flex;
  justify-content: space-between;
  margin-bottom: 8px;
  font-size: 0.9rem;
}

.progress-bar-bg {
  height: 8px;
  background: var(--glass);
  border-radius: 4px;
  overflow: hidden;
}

.progress-bar-fill {
  height: 100%;
  width: var(--progress);
  background: var(--gradient);
  border-radius: 4px;
  animation: progressGrow 1s ease-out forwards;
}

@keyframes progressGrow {
  from { width: 0; }
  to { width: var(--progress); }
}
```

### Связи/Mindmap (SVG)

```html
<svg class="mindmap" viewBox="0 0 400 300" width="100%" height="300">
  <!-- Линии связей -->
  <line x1="200" y1="150" x2="80" y2="80" stroke="var(--accent-1)" stroke-width="2" opacity="0.5"/>
  <line x1="200" y1="150" x2="320" y2="80" stroke="var(--accent-2)" stroke-width="2" opacity="0.5"/>
  <line x1="200" y1="150" x2="80" y2="220" stroke="var(--accent-3)" stroke-width="2" opacity="0.5"/>
  <line x1="200" y1="150" x2="320" y2="220" stroke="var(--accent-4)" stroke-width="2" opacity="0.5"/>
  
  <!-- Центральный узел -->
  <circle cx="200" cy="150" r="40" fill="var(--accent-1)"/>
  <text x="200" y="155" text-anchor="middle" fill="white" font-size="12" font-weight="600">Центр</text>
  
  <!-- Дочерние узлы -->
  <circle cx="80" cy="80" r="30" fill="var(--glass)" stroke="var(--accent-1)" stroke-width="2"/>
  <text x="80" y="85" text-anchor="middle" fill="var(--text-primary)" font-size="10">Тема 1</text>
  
  <circle cx="320" cy="80" r="30" fill="var(--glass)" stroke="var(--accent-2)" stroke-width="2"/>
  <text x="320" y="85" text-anchor="middle" fill="var(--text-primary)" font-size="10">Тема 2</text>
  
  <circle cx="80" cy="220" r="30" fill="var(--glass)" stroke="var(--accent-3)" stroke-width="2"/>
  <text x="80" y="225" text-anchor="middle" fill="var(--text-primary)" font-size="10">Тема 3</text>
  
  <circle cx="320" cy="220" r="30" fill="var(--glass)" stroke="var(--accent-4)" stroke-width="2"/>
  <text x="320" y="225" text-anchor="middle" fill="var(--text-primary)" font-size="10">Тема 4</text>
</svg>
```

---

## Шаг 5: Создать HTML-файл

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
