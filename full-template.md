# Полный шаблон HTML-презентации

## HTML-структура

```html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Название презентации</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    /* === CSS ЗДЕСЬ === */
  </style>
</head>
<body>
  <!-- Background Effects -->
  <div class="bg-wrap">
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>
  </div>
  <div class="bg-grid"></div>

  <!-- Navigation Dots -->
  <nav class="nav-dots">
    <div class="nav-dot active"></div>
    <div class="nav-dot"></div>
    <!-- ... по количеству слайдов -->
  </nav>

  <!-- Progress Bar -->
  <div class="progress-wrap">
    <div class="progress-bar"></div>
  </div>

  <!-- Slide Counter -->
  <div class="slide-counter"><span>01</span> / XX</div>

  <!-- Navigation Zones -->
  <div class="nav-zone nav-left"><span>←</span></div>
  <div class="nav-zone nav-right"><span>→</span></div>

  <!-- SLIDES -->
  <section>...</section>
  <section>...</section>

  <script>
    /* === JS ЗДЕСЬ === */
  </script>
</body>
</html>
```

---

## Полный CSS

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
  scroll-snap-type: y mandatory;
  overflow-x: hidden;
}

body {
  font-family: 'Inter', system-ui, sans-serif;
  background: var(--bg-dark);
  color: var(--text-primary);
  line-height: 1.6;
  overflow-x: hidden;
}

:root {
  --bg-dark: #0a0a0f;
  --bg-surface: #0f172a;
  --glass: rgba(255, 255, 255, 0.05);
  --glass-hover: rgba(255, 255, 255, 0.08);
  --glass-border: rgba(255, 255, 255, 0.1);
  --text-primary: #f1f5f9;
  --text-secondary: rgba(255, 255, 255, 0.65);
  --text-muted: rgba(255, 255, 255, 0.4);
  
  /* ACCENT COLORS — подставить из палитры */
  --accent-1: #a855f7;
  --accent-2: #8b5cf6;
  --accent-3: #3b82f6;
  --accent-4: #22d3ee;
  --gradient: linear-gradient(135deg, var(--accent-1), var(--accent-3), var(--accent-4));
  --glow: rgba(139, 92, 246, 0.4);
}

/* ═══════════════════════════════════════
   NAVIGATION DOTS
   ═══════════════════════════════════════ */
.nav-dots {
  position: fixed;
  right: 30px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1000;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.nav-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  cursor: pointer;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.nav-dot:hover {
  background: rgba(255, 255, 255, 0.4);
  transform: scale(1.2);
}

.nav-dot.active {
  background: var(--accent-2);
  border-color: rgba(255, 255, 255, 0.5);
  box-shadow: 0 0 20px var(--accent-2);
}

/* ═══════════════════════════════════════
   PROGRESS BAR
   ═══════════════════════════════════════ */
.progress-wrap {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 3px;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.05);
}

.progress-bar {
  height: 100%;
  background: var(--gradient);
  transition: width 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 0 2px 2px 0;
  box-shadow: 0 0 15px var(--glow);
}

/* ═══════════════════════════════════════
   SLIDE COUNTER
   ═══════════════════════════════════════ */
.slide-counter {
  position: fixed;
  left: 30px;
  bottom: 30px;
  z-index: 1000;
  font-size: 14px;
  color: var(--text-muted);
  font-weight: 500;
  letter-spacing: 2px;
}

.slide-counter span {
  color: var(--text-primary);
  font-size: 24px;
}

/* ═══════════════════════════════════════
   BACKGROUND EFFECTS
   ═══════════════════════════════════════ */
.bg-wrap {
  position: fixed;
  inset: 0;
  z-index: -1;
  overflow: hidden;
  pointer-events: none;
}

.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  opacity: 0.25;
  animation: floatOrb 25s ease-in-out infinite;
}

.orb-1 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, var(--accent-1), transparent);
  top: -10%;
  left: -5%;
  animation-duration: 28s;
}

.orb-2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, var(--accent-3), transparent);
  bottom: -10%;
  right: -5%;
  animation-delay: -8s;
  animation-duration: 24s;
}

.orb-3 {
  width: 350px;
  height: 350px;
  background: radial-gradient(circle, var(--accent-4), transparent);
  top: 40%;
  left: 50%;
  animation-delay: -15s;
  animation-duration: 30s;
  opacity: 0.15;
}

@keyframes floatOrb {
  0%, 100% { transform: translate(0, 0) scale(1); }
  25% { transform: translate(50px, -40px) scale(1.1); }
  50% { transform: translate(-30px, 50px) scale(0.95); }
  75% { transform: translate(40px, 30px) scale(1.05); }
}

.bg-grid {
  position: fixed;
  inset: 0;
  background-image: 
    linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
  z-index: -1;
}

/* ═══════════════════════════════════════
   SECTIONS / SLIDES
   ═══════════════════════════════════════ */
section {
  min-height: 100vh;
  scroll-snap-align: start;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 60px 80px;
  overflow: hidden;
}

@media (max-width: 768px) {
  section { padding: 40px 24px; }
  .nav-dots { right: 15px; }
  .slide-counter { left: 15px; bottom: 15px; }
}

.slide-content {
  max-width: 1200px;
  width: 100%;
  z-index: 1;
}

/* ═══════════════════════════════════════
   TYPOGRAPHY
   ═══════════════════════════════════════ */
h1 {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.02em;
  color: var(--text-primary);
}

h2 {
  font-size: clamp(1.75rem, 3.5vw, 2.5rem);
  font-weight: 700;
  line-height: 1.2;
  letter-spacing: -0.02em;
  color: var(--text-primary);
  margin-bottom: 24px;
}

h3 {
  font-size: clamp(1.25rem, 2vw, 1.5rem);
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 12px;
}

h4 {
  font-size: clamp(1rem, 1.5vw, 1.2rem);
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 8px;
}

p {
  color: var(--text-secondary);
  font-size: clamp(1rem, 1.5vw, 1.2rem);
  line-height: 1.7;
  margin-bottom: 16px;
}

p:last-child { margin-bottom: 0; }

strong {
  color: var(--text-primary);
  font-weight: 600;
}

/* ═══════════════════════════════════════
   GRADIENT TEXT
   ═══════════════════════════════════════ */
.gradient-text {
  background: var(--gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ═══════════════════════════════════════
   GLASS CARDS
   ═══════════════════════════════════════ */
.glass-card {
  background: var(--glass);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 24px;
  transition: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

.glass-card:hover {
  background: var(--glass-hover);
  border-color: rgba(255, 255, 255, 0.15);
  transform: translateY(-4px);
  box-shadow: 0 20px 60px var(--glow);
}

.glass-card h4 { margin-bottom: 8px; }
.glass-card p { font-size: clamp(0.9rem, 1.2vw, 1rem); margin: 0; }

.glass-card.accent { position: relative; overflow: hidden; }

.glass-card.accent::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 3px;
  background: var(--gradient);
  border-radius: 16px 16px 0 0;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.glass-card.accent:hover::before { opacity: 1; }

/* ═══════════════════════════════════════
   GRIDS
   ═══════════════════════════════════════ */
.grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
.grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
.grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; }

@media (max-width: 768px) {
  .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; }
}

/* ═══════════════════════════════════════
   BADGE / TAG
   ═══════════════════════════════════════ */
.badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px;
  border-radius: 100px;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  background: linear-gradient(135deg, rgba(168, 85, 247, 0.15), rgba(59, 130, 246, 0.15));
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: var(--accent-1);
  margin-bottom: 16px;
  width: fit-content;
}

.badge-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--accent-1);
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(0.7); }
}

/* ═══════════════════════════════════════
   DIVIDER
   ═══════════════════════════════════════ */
.divider {
  height: 4px;
  width: 60px;
  border-radius: 4px;
  background: var(--gradient);
  margin: 16px 0 24px;
  border: none;
}

.divider.center { margin-left: auto; margin-right: auto; }

/* ═══════════════════════════════════════
   LISTS
   ═══════════════════════════════════════ */
ul.styled-list { list-style: none; padding: 0; margin: 0; }

ul.styled-list li {
  position: relative;
  padding: 8px 0 8px 28px;
  font-size: clamp(1rem, 1.3vw, 1.1rem);
  color: var(--text-secondary);
  line-height: 1.6;
}

ul.styled-list li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--gradient);
}

/* ═══════════════════════════════════════
   QUOTE BLOCK
   ═══════════════════════════════════════ */
.quote-block {
  background: var(--glass);
  backdrop-filter: blur(20px);
  border-left: 4px solid var(--accent-1);
  border-radius: 0 16px 16px 0;
  padding: 32px 40px;
  margin: 24px 0;
}

.quote-block p {
  font-size: clamp(1.2rem, 2vw, 1.5rem);
  font-style: italic;
  line-height: 1.6;
  color: var(--text-primary);
  margin-bottom: 16px;
}

.quote-block cite {
  font-size: 0.9rem;
  color: var(--text-muted);
  font-style: normal;
}

/* ═══════════════════════════════════════
   STATS / NUMBERS
   ═══════════════════════════════════════ */
.stat-card { text-align: center; padding: 32px 24px; }

.stat-number {
  font-size: clamp(3rem, 6vw, 5rem);
  font-weight: 800;
  line-height: 1;
  margin-bottom: 8px;
}

.stat-label {
  font-size: clamp(0.9rem, 1.2vw, 1rem);
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 4px;
}

.stat-desc {
  font-size: clamp(0.8rem, 1vw, 0.9rem);
  color: var(--text-muted);
}

/* ═══════════════════════════════════════
   TITLE SLIDE
   ═══════════════════════════════════════ */
.title-slide {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.title-slide h1 { margin-bottom: 16px; }

.title-slide .subtitle {
  font-size: clamp(1rem, 1.5vw, 1.25rem);
  color: var(--text-secondary);
  margin-bottom: 32px;
  max-width: 600px;
}

.title-slide .meta {
  display: flex;
  gap: 24px;
  color: var(--text-muted);
  font-size: 0.9rem;
}

/* ═══════════════════════════════════════
   CONCLUSION CARD
   ═══════════════════════════════════════ */
.conclusion-card {
  background: linear-gradient(135deg, rgba(168, 85, 247, 0.1), rgba(34, 211, 238, 0.1));
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 24px;
  padding: 40px 48px;
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
}

/* ═══════════════════════════════════════
   NAVIGATION ZONES
   ═══════════════════════════════════════ */
.nav-zone {
  position: fixed;
  top: 0;
  width: 80px;
  height: 100%;
  z-index: 100;
  cursor: pointer;
  opacity: 0;
  transition: opacity 0.3s ease;
  display: flex;
  align-items: center;
}

.nav-zone:hover { opacity: 1; }

.nav-left {
  left: 0;
  background: linear-gradient(90deg, var(--glow), transparent);
  justify-content: flex-start;
  padding-left: 20px;
}

.nav-right {
  right: 0;
  background: linear-gradient(-90deg, var(--glow), transparent);
  justify-content: flex-end;
  padding-right: 20px;
}

.nav-zone span {
  font-size: 24px;
  color: rgba(255, 255, 255, 0.3);
}

/* ═══════════════════════════════════════
   ANIMATIONS
   ═══════════════════════════════════════ */
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}

.animate-in { animation: fadeInUp 0.6s ease-out forwards; }
.animate-fade { animation: fadeIn 0.5s ease-out forwards; }
.animate-scale { animation: scaleIn 0.5s ease-out forwards; }

/* Stagger delays */
.stagger > *:nth-child(1) { animation-delay: 0.1s; }
.stagger > *:nth-child(2) { animation-delay: 0.2s; }
.stagger > *:nth-child(3) { animation-delay: 0.3s; }
.stagger > *:nth-child(4) { animation-delay: 0.4s; }
.stagger > *:nth-child(5) { animation-delay: 0.5s; }
.stagger > *:nth-child(6) { animation-delay: 0.6s; }
.stagger > *:nth-child(7) { animation-delay: 0.7s; }
.stagger > *:nth-child(8) { animation-delay: 0.8s; }

.animate-on-view { opacity: 0; }
.animate-on-view.animate-in { opacity: 1; }
```

---

## JavaScript навигация

```javascript
document.addEventListener('DOMContentLoaded', () => {
  const sections = document.querySelectorAll('section');
  const dots = document.querySelectorAll('.nav-dot');
  const progressBar = document.querySelector('.progress-bar');
  const counter = document.querySelector('.slide-counter');
  let current = 0;
  const total = sections.length;

  function goTo(index) {
    if (index < 0 || index >= total) return;
    current = index;
    sections[current].scrollIntoView({ behavior: 'smooth' });
    updateUI();
  }

  function updateUI() {
    // Update dots
    dots.forEach((d, i) => d.classList.toggle('active', i === current));
    
    // Update progress bar
    progressBar.style.width = ((current + 1) / total * 100) + '%';
    
    // Update counter
    counter.innerHTML = `<span>${String(current + 1).padStart(2, '0')}</span> / ${String(total).padStart(2, '0')}`;
    
    // Trigger animations on current slide
    sections[current].querySelectorAll('.animate-on-view').forEach(el => {
      el.classList.add('animate-in');
    });
  }

  // Keyboard navigation
  document.addEventListener('keydown', e => {
    if (e.key === 'ArrowRight' || e.key === 'ArrowDown' || e.key === ' ') {
      e.preventDefault();
      goTo(current + 1);
    }
    if (e.key === 'ArrowLeft' || e.key === 'ArrowUp') {
      e.preventDefault();
      goTo(current - 1);
    }
    if (e.key === 'Home') {
      e.preventDefault();
      goTo(0);
    }
    if (e.key === 'End') {
      e.preventDefault();
      goTo(total - 1);
    }
  });

  // Click navigation zones
  document.querySelector('.nav-left')?.addEventListener('click', () => goTo(current - 1));
  document.querySelector('.nav-right')?.addEventListener('click', () => goTo(current + 1));

  // Dot navigation
  dots.forEach((dot, i) => dot.addEventListener('click', () => goTo(i)));

  // Intersection Observer for scroll detection
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        current = [...sections].indexOf(entry.target);
        updateUI();
      }
    });
  }, { threshold: 0.5 });

  sections.forEach(s => observer.observe(s));
  
  // Initial state
  updateUI();
});
```

---

## Примеры слайдов

### Title Slide
```html
<section>
  <div class="slide-content title-slide">
    <div class="badge animate-on-view">
      <span class="badge-dot"></span>
      Категория
    </div>
    <h1 class="gradient-text animate-on-view">Название презентации</h1>
    <p class="subtitle animate-on-view">Краткое описание</p>
    <hr class="divider center animate-on-view">
    <div class="meta animate-on-view">
      <span>Автор</span>
      <span>•</span>
      <span>2024</span>
    </div>
  </div>
</section>
```

### Content Slide
```html
<section>
  <div class="slide-content">
    <div class="badge animate-on-view">
      <span class="badge-dot"></span>
      Раздел
    </div>
    <h2 class="animate-on-view">Заголовок слайда</h2>
    <hr class="divider animate-on-view">
    <p class="animate-on-view">Текст слайда...</p>
    <ul class="styled-list stagger">
      <li class="animate-on-view">Пункт 1</li>
      <li class="animate-on-view">Пункт 2</li>
      <li class="animate-on-view">Пункт 3</li>
    </ul>
  </div>
</section>
```

### Grid Cards Slide
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view">Заголовок</h2>
    <hr class="divider animate-on-view">
    <div class="grid-3 stagger">
      <div class="glass-card accent animate-on-view">
        <h4>Карточка 1</h4>
        <p>Описание</p>
      </div>
      <div class="glass-card accent animate-on-view">
        <h4>Карточка 2</h4>
        <p>Описание</p>
      </div>
      <div class="glass-card accent animate-on-view">
        <h4>Карточка 3</h4>
        <p>Описание</p>
      </div>
    </div>
  </div>
</section>
```

### Stats Slide
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view" style="text-align: center;">Статистика</h2>
    <hr class="divider center animate-on-view">
    <div class="grid-4 stagger">
      <div class="glass-card stat-card animate-on-view">
        <div class="stat-number gradient-text">85%</div>
        <div class="stat-label">Эффективность</div>
        <div class="stat-desc">По исследованиям</div>
      </div>
      <!-- ... ещё карточки -->
    </div>
  </div>
</section>
```

### Quote Slide
```html
<section>
  <div class="slide-content">
    <blockquote class="quote-block animate-on-view">
      <p>"Важная цитата, которая подчёркивает ключевую мысль."</p>
      <cite>— Автор</cite>
    </blockquote>
  </div>
</section>
```

### Conclusion Slide
```html
<section>
  <div class="slide-content">
    <div class="conclusion-card animate-on-view">
      <h2>Выводы</h2>
      <hr class="divider center">
      <p>Главный вывод презентации...</p>
    </div>
  </div>
</section>
```

### Thank You Slide
```html
<section>
  <div class="slide-content title-slide">
    <h1 class="gradient-text animate-on-view">Спасибо за внимание!</h1>
    <hr class="divider center animate-on-view">
    <p class="animate-on-view" style="color: var(--text-muted);">Вопросы?</p>
  </div>
</section>
```
