# Полный шаблон HTML-презентации

> ⚠️ **Офлайн-режим:** Все презентации работают без интернета. Google Fonts имеют fallback на системные.

---

## Содержание

1. [HTML-структура](#html-структура)
2. [Стили по темам](#стили-по-темам)
3. [Базовый CSS](#базовый-css-glassmorphism)
4. [JavaScript навигация](#javascript-навигация)
5. [Компоненты слайдов](#компоненты-слайдов)

---

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

## Стили по темам

### 🔮 GLASSMORPHISM (тёмный, стекло)
```css
:root {
  --bg-dark: #0a0a0f;
  --bg-surface: #0f172a;
  --glass: rgba(255, 255, 255, 0.05);
  --glass-hover: rgba(255, 255, 255, 0.08);
  --glass-border: rgba(255, 255, 255, 0.1);
  --text-primary: #f1f5f9;
  --text-secondary: rgba(255, 255, 255, 0.65);
  --text-muted: rgba(255, 255, 255, 0.4);
}
body { background: var(--bg-dark); }
.glass-card { backdrop-filter: blur(20px); }
```

### 🌙 MINIMAL DARK
```css
:root {
  --bg-dark: #09090b;
  --bg-surface: #18181b;
  --glass: #18181b;
  --glass-hover: #27272a;
  --glass-border: #27272a;
  --text-primary: #fafafa;
  --text-secondary: #a1a1aa;
  --text-muted: #71717a;
  --neon-blue: #00d9ff;
  --neon-purple: #a855f7;
}
body { 
  background: var(--bg-dark);
  position: relative;
  overflow-x: hidden;
}
/* Параллакс фон */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background: 
    radial-gradient(circle at 20% 30%, rgba(168, 85, 247, 0.08) 0%, transparent 40%),
    radial-gradient(circle at 80% 70%, rgba(0, 217, 255, 0.08) 0%, transparent 40%);
  pointer-events: none;
  z-index: -1;
  animation: parallaxBg 30s ease-in-out infinite;
}
@keyframes parallaxBg {
  0%, 100% { transform: translateY(0) scale(1); }
  50% { transform: translateY(-50px) scale(1.05); }
}
/* Анимированный текст */
h1, h2 {
  background: linear-gradient(90deg, var(--text-primary) 0%, var(--neon-blue) 50%, var(--neon-purple) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: textGlow 3s ease-in-out infinite;
}
@keyframes textGlow {
  0%, 100% { filter: drop-shadow(0 0 0px rgba(0, 217, 255, 0)); }
  50% { filter: drop-shadow(0 0 20px rgba(0, 217, 255, 0.5)); }
}
/* 3D карты */
.glass-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  transform-style: preserve-3d;
  perspective: 1000px;
  transition: all 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
.glass-card:hover {
  transform: rotateX(5deg) rotateY(-5deg) scale(1.05) translateZ(20px);
  box-shadow: 0 25px 50px rgba(0, 217, 255, 0.2), 0 0 40px rgba(168, 85, 247, 0.1);
  border-color: var(--neon-blue);
}
/* Стагерированные списки */
ul li {
  opacity: 0;
  animation: slideInWithGlow 0.8s ease-out forwards;
}
@keyframes slideInWithGlow {
  0% { opacity: 0; transform: translateX(-30px); filter: blur(5px); }
  100% { opacity: 1; transform: translateX(0); filter: blur(0); }
}
ul li:nth-child(1) { animation-delay: 0.2s; }
ul li:nth-child(2) { animation-delay: 0.4s; }
ul li:nth-child(3) { animation-delay: 0.6s; }
ul li:nth-child(4) { animation-delay: 0.8s; }
.bg-wrap { display: none; }
```

### ☀️ MINIMAL LIGHT
```css
:root {
  --bg-dark: #ffffff;
  --bg-surface: #f4f4f5;
  --glass: #ffffff;
  --glass-hover: #f4f4f5;
  --glass-border: #e4e4e7;
  --text-primary: #18181b;
  --text-secondary: #52525b;
  --text-muted: #a1a1aa;
  --soft-blue: #3b82f6;
  --soft-pink: #ec4899;
  --soft-purple: #a855f7;
}
body { 
  background: linear-gradient(135deg, #ffffff 0%, #f9fafb 50%, #f3f4f6 100%);
  background-attachment: fixed;
}
/* Микропаттерн */
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: 
    radial-gradient(1px 1px at 1px 1px, rgba(0, 0, 0, 0.02), transparent),
    radial-gradient(1px 1px at 2px 2px, rgba(0, 0, 0, 0.01), transparent);
  background-size: 20px 20px;
  pointer-events: none;
  z-index: -1;
}
/* Морфирующие карты */
.glass-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  transition: all 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: relative;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.04), 0 4px 12px rgba(0, 0, 0, 0.02);
}
.glass-card:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1), 0 0 40px rgba(59, 130, 246, 0.1);
  border-color: var(--soft-blue);
}
/* Плавающие элементы */
h1, h2 {
  animation: floatText 4s ease-in-out infinite;
}
@keyframes floatText {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-5px); }
}
h1 { animation-duration: 5s; }
h2 { animation-duration: 4.5s; animation-delay: -0.5s; }
.bg-wrap { display: none; }
.nav-dot { background: rgba(0,0,0,0.2); }
.nav-dot.active { background: var(--soft-blue); }
```

### 🌈 GRADIENT MESH
```css
:root {
  --text-primary: #ffffff;
  --text-secondary: rgba(255,255,255,0.85);
  --glass: rgba(0,0,0,0.2);
  --glass-border: rgba(255,255,255,0.2);
}
body { 
  background: linear-gradient(-45deg, #667eea, #764ba2, #f093fb, #4facfe, #00f2fe);
  background-size: 400% 400%;
  background-attachment: fixed;
  animation: meshGradient 5s ease infinite;
}
@keyframes meshGradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
/* Волны */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 1200 120' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M0,20 Q300,50 600,20 T1200,20 L1200,120 L0,120 Z' fill='rgba(255,255,255,0.05)'/%3E%3C/svg%3E");
  background-size: 600px 100px;
  background-repeat: repeat-x;
  pointer-events: none;
  z-index: 1;
  animation: waveAnimation 20s linear infinite;
}
@keyframes waveAnimation {
  0% { background-position: 0 0; }
  100% { background-position: 600px 0; }
}
/* Карты с клип-пас */
.glass-card {
  background: var(--glass);
  backdrop-filter: blur(10px);
  border: 1px solid var(--glass-border);
  transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: relative;
  overflow: hidden;
  clip-path: polygon(0 0, 100% 0, 100% calc(100% - 20px), calc(100% - 20px) 100%, 0 100%);
}
.glass-card:hover {
  transform: scale(1.05) rotateX(2deg) rotateY(-2deg);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
}
/* Морфинг текста */
h1, h2 {
  animation: morphText 4s ease-in-out infinite;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}
@keyframes morphText {
  0%, 100% { transform: scale(1) skewX(0deg); filter: drop-shadow(0 0 0px rgba(255, 255, 255, 0)); }
  50% { transform: scale(1.02) skewX(2deg); filter: drop-shadow(0 0 15px rgba(255, 255, 255, 0.4)); }
}
.bg-wrap { display: none; }
```

### 🔳 NEOMORPHISM
```css
:root {
  --bg-dark: #e0e5ec;
  --text-primary: #2d3436;
  --text-secondary: #636e72;
  --text-muted: #b2bec3;
  --shadow-light: #ffffff;
  --shadow-dark: #b8bec4;
}
body { 
  background: linear-gradient(135deg, #e0e5ec 0%, #d5dce3 50%, #e0e5ec 100%);
  position: relative;
}
/* Инвертирующиеся карты */
.glass-card {
  background: var(--bg-dark);
  border: none;
  border-radius: 20px;
  box-shadow: 12px 12px 24px var(--shadow-dark), -12px -12px 24px var(--shadow-light);
  transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: relative;
  overflow: hidden;
}
.glass-card:hover {
  box-shadow: inset 12px 12px 24px var(--shadow-dark), inset -12px -12px 24px var(--shadow-light);
  transform: scale(0.95);
}
/* Анимированные заголовки */
.glass-card h4 {
  animation: titlePulse 3s ease-in-out infinite;
}
@keyframes titlePulse {
  0%, 100% { color: var(--text-primary); text-shadow: none; }
  50% { color: #a29bfe; text-shadow: 0 0 20px rgba(162, 155, 254, 0.3); }
}
/* Клип-пас элементы */
.badge {
  clip-path: polygon(20px 0, 100% 0, calc(100% - 20px) 100%, 0 100%);
  animation: badgeFlip 2s ease-in-out infinite;
}
@keyframes badgeFlip {
  0%, 100% { transform: rotateX(0deg); }
  50% { transform: rotateX(10deg); }
}
/* Текст с морфингом */
p {
  animation: morphLine 4s ease-in-out infinite;
}
@keyframes morphLine {
  0%, 100% { letter-spacing: 0; transform: skewX(0deg); }
  50% { letter-spacing: 2px; transform: skewX(-2deg); }
}
.bg-wrap { display: none; }
.nav-dot { background: #d1d5db; box-shadow: 2px 2px 4px #b8bec4, -2px -2px 4px #fff; }
```

### ⚡ BRUTALIST
```css
:root {
  --bg-dark: #000000;
  --text-primary: #ffffff;
  --text-secondary: #ffffff;
  --accent-1: #ff0000;
  --accent-2: #ffff00;
  --glass: transparent;
  --glass-border: #ff0000;
}
body { 
  background: #000000;
  font-family: 'Space Mono', monospace;
  position: relative;
  overflow-x: hidden;
}
/* Анимированная сетка */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: 
    linear-gradient(90deg, rgba(255, 0, 0, 0.1) 1px, transparent 1px),
    linear-gradient(rgba(255, 0, 0, 0.1) 1px, transparent 1px);
  background-size: 20px 20px;
  pointer-events: none;
  z-index: -1;
  animation: gridShift 20s linear infinite;
}
@keyframes gridShift {
  0% { background-position: 0 0; }
  100% { background-position: 20px 20px; }
}
/* Пульсирующие заголовки */
h1, h2 {
  text-transform: uppercase;
  font-weight: 900;
  letter-spacing: 0.1em;
  animation: brutalPulse 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55) infinite;
  text-shadow: 0 0 20px rgba(255, 0, 0, 0.5);
}
h1 { animation-duration: 1s; }
h2 { animation-duration: 0.8s; }
@keyframes brutalPulse {
  0%, 100% { transform: scale(1) skewX(0deg); text-shadow: 0 0 5px rgba(255, 0, 0, 0.3); }
  50% { transform: scale(1.05) skewX(-2deg); text-shadow: 0 0 20px rgba(255, 0, 0, 0.8), 0 0 40px rgba(255, 255, 0, 0.4); }
}
/* Глиттер и карты */
.glass-card {
  background: transparent;
  border: 3px solid var(--accent-1);
  border-radius: 0;
  position: relative;
  overflow: hidden;
  transition: all 0.2s ease;
}
.glass-card:hover {
  border-color: var(--accent-2);
  box-shadow: 0 0 30px rgba(255, 0, 0, 0.6), inset 0 0 0 3px rgba(255, 255, 0, 0.5);
  transform: scale(0.98) rotate(-1deg);
}
/* Резкие анимации списков */
ul li {
  animation: jumpIn 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
@keyframes jumpIn {
  0% { opacity: 0; transform: translateY(-20px) rotateX(90deg); }
  50% { transform: translateY(5px); }
  100% { opacity: 1; transform: translateY(0) rotateX(0deg); }
}
ul li:nth-child(1) { animation-delay: 0.1s; }
ul li:nth-child(2) { animation-delay: 0.2s; }
ul li:nth-child(3) { animation-delay: 0.3s; }
ul li:nth-child(4) { animation-delay: 0.4s; }
.bg-wrap, .bg-grid { display: none; }
```

### 🏢 CORPORATE
```css
:root {
  --bg-dark: #f8fafc;
  --bg-surface: #ffffff;
  --glass: #ffffff;
  --glass-border: #e2e8f0;
  --text-primary: #1e293b;
  --text-secondary: #475569;
  --text-muted: #94a3b8;
  --accent-blue: #1e40af;
  --accent-sky: #3b82f6;
}
body { 
  background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 50%, #e0f2fe 100%);
  background-attachment: fixed;
}
/* Морфирующие карты */
.glass-card {
  background: var(--glass);
  border: 2px solid var(--glass-border);
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
  position: relative;
  overflow: hidden;
}
.glass-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08), 0 0 40px rgba(30, 64, 175, 0.1);
  border-color: var(--accent-blue);
}
/* Градиентный текст */
h1, h2 {
  background: linear-gradient(135deg, var(--text-primary) 0%, var(--accent-sky) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: textGradientShift 4s ease-in-out infinite;
}
@keyframes textGradientShift {
  0%, 100% { background: linear-gradient(135deg, var(--text-primary) 0%, var(--accent-sky) 100%); }
  50% { background: linear-gradient(45deg, var(--accent-sky) 0%, var(--text-primary) 100%); }
}
/* Списки */
ul li {
  transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
  padding-left: 28px;
}
ul li:hover {
  transform: translateX(8px);
  color: var(--accent-blue);
  padding-left: 36px;
}
ul li::before {
  transition: all 0.3s ease;
  background: var(--accent-blue);
  box-shadow: 0 2px 8px rgba(30, 64, 175, 0.2);
}
ul li:hover::before {
  box-shadow: 0 4px 16px rgba(30, 64, 175, 0.4);
  transform: scale(1.2);
}
.bg-wrap { display: none; }
```

### 🎮 RETRO / NEON
```css
:root {
  --bg-dark: #0f0f23;
  --text-primary: #ffffff;
  --text-secondary: rgba(255,255,255,0.8);
  --accent-1: #ff2a6d;
  --accent-2: #05d9e8;
  --accent-3: #d300c5;
  --glass: rgba(255,255,255,0.03);
  --glass-border: rgba(5,217,232,0.3);
}
body { 
  background: #0f0f23;
  position: relative;
  overflow-x: hidden;
}
/* Сканлайны */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(255, 255, 255, 0.03) 2px,
    rgba(255, 255, 255, 0.03) 4px
  );
  pointer-events: none;
  z-index: -1;
  animation: scanlineFlicker 0.15s infinite;
}
@keyframes scanlineFlicker {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.95; }
}
/* Мерцающие заголовки */
h1, h2 {
  text-shadow: 0 0 10px var(--accent-2), 0 0 20px var(--accent-2), 0 0 40px var(--accent-2);
  animation: neonFlicker 0.15s ease-in-out infinite;
  font-weight: 900;
  letter-spacing: 0.05em;
}
@keyframes neonFlicker {
  0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
    text-shadow: 0 0 10px var(--accent-2), 0 0 20px var(--accent-2), 0 0 40px var(--accent-2);
    opacity: 1;
  }
  20%, 24%, 55% {
    text-shadow: 0 0 5px var(--accent-2), 0 0 10px var(--accent-2);
    opacity: 0.8;
  }
}
h1 { color: var(--accent-1); animation-duration: 0.13s; }
h2 { color: var(--accent-2); animation-duration: 0.15s; }
/* Карты с RGB сдвигом */
.glass-card {
  background: var(--glass);
  backdrop-filter: blur(5px);
  border: 2px solid var(--glass-border);
  border-radius: 0;
  position: relative;
  overflow: hidden;
  box-shadow: 0 0 20px var(--accent-2), inset 0 0 20px rgba(5, 217, 232, 0.1);
  transition: all 0.3s ease;
}
.glass-card:hover {
  border-color: var(--accent-1);
  box-shadow: 0 0 30px var(--accent-1), 0 0 50px var(--accent-2), inset 0 0 30px rgba(255, 42, 109, 0.2);
  animation: glitchCard 0.2s ease-in-out;
}
@keyframes glitchCard {
  0%, 33%, 66%, 100% { transform: translate(0) skewX(0deg); }
  34% { transform: translate(-2px) skewX(-2deg); }
  67% { transform: translate(2px) skewX(2deg); }
}
/* РГБ гличчы */
ul li {
  animation: colorShift 3s ease-in-out infinite;
}
@keyframes colorShift {
  0%, 100% { color: var(--text-secondary); }
  50% { color: var(--accent-2); }
}
/* Сетка на фоне */
.bg-grid {
  background-image: 
    linear-gradient(transparent 97%, rgba(5,217,232,0.15) 97%),
    linear-gradient(90deg, transparent 97%, rgba(5,217,232,0.15) 97%);
  background-size: 40px 40px;
}
```

---

## Базовый CSS (Glassmorphism)

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

/* Появление снизу (основное) */
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Простое появление */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
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

/* Появление сверху */
@keyframes slideInDown {
  from { opacity: 0; transform: translateY(-30px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Пульсация */
@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.6; transform: scale(0.85); }
}

/* Свечение (для NEON стиля) */
@keyframes glow {
  0%, 100% { text-shadow: 0 0 10px currentColor, 0 0 20px currentColor; }
  50% { text-shadow: 0 0 20px currentColor, 0 0 40px currentColor, 0 0 60px currentColor; }
}

/* Печатная машинка */
@keyframes typewriter {
  from { width: 0; }
  to { width: 100%; }
}

/* Градиентный сдвиг */
@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

/* Классы анимаций */
.animate-in { animation: fadeInUp 0.6s ease-out forwards; }
.animate-fade { animation: fadeIn 0.5s ease-out forwards; }
.animate-scale { animation: scaleIn 0.5s ease-out forwards; }
.animate-left { animation: slideInLeft 0.6s ease-out forwards; }
.animate-right { animation: slideInRight 0.6s ease-out forwards; }
.animate-down { animation: slideInDown 0.5s ease-out forwards; }
.animate-glow { animation: glow 2s ease-in-out infinite; }
.animate-pulse { animation: pulse 2s ease-in-out infinite; }

/* Stagger delays — элементы появляются по очереди */
.stagger > *:nth-child(1) { animation-delay: 0.1s; }
.stagger > *:nth-child(2) { animation-delay: 0.2s; }
.stagger > *:nth-child(3) { animation-delay: 0.3s; }
.stagger > *:nth-child(4) { animation-delay: 0.4s; }
.stagger > *:nth-child(5) { animation-delay: 0.5s; }
.stagger > *:nth-child(6) { animation-delay: 0.6s; }
.stagger > *:nth-child(7) { animation-delay: 0.7s; }
.stagger > *:nth-child(8) { animation-delay: 0.8s; }

/* Быстрый stagger */
.stagger-fast > *:nth-child(1) { animation-delay: 0.05s; }
.stagger-fast > *:nth-child(2) { animation-delay: 0.1s; }
.stagger-fast > *:nth-child(3) { animation-delay: 0.15s; }
.stagger-fast > *:nth-child(4) { animation-delay: 0.2s; }
.stagger-fast > *:nth-child(5) { animation-delay: 0.25s; }
.stagger-fast > *:nth-child(6) { animation-delay: 0.3s; }

/* Медленный stagger */
.stagger-slow > *:nth-child(1) { animation-delay: 0.2s; }
.stagger-slow > *:nth-child(2) { animation-delay: 0.4s; }
.stagger-slow > *:nth-child(3) { animation-delay: 0.6s; }
.stagger-slow > *:nth-child(4) { animation-delay: 0.8s; }

/* Элементы скрыты до появления */
.animate-on-view { opacity: 0; }
.animate-on-view.animate-in { opacity: 1; }

/* Hover-эффекты */
.hover-lift {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.hover-lift:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
}

.hover-glow {
  transition: box-shadow 0.3s ease;
}
.hover-glow:hover {
  box-shadow: 0 0 30px var(--glow);
}
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

---

## Дополнительные компоненты

### Process Flow Slide (горизонтальный процесс)
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view" style="text-align: center;">Процесс</h2>
    <hr class="divider center animate-on-view">
    <div class="process-flow stagger">
      <div class="process-step animate-on-view">
        <div class="step-icon">1</div>
        <div class="step-label">Анализ</div>
      </div>
      <div class="process-arrow animate-on-view">→</div>
      <div class="process-step animate-on-view">
        <div class="step-icon">2</div>
        <div class="step-label">Разработка</div>
      </div>
      <div class="process-arrow animate-on-view">→</div>
      <div class="process-step animate-on-view">
        <div class="step-icon">3</div>
        <div class="step-label">Тестирование</div>
      </div>
      <div class="process-arrow animate-on-view">→</div>
      <div class="process-step animate-on-view">
        <div class="step-icon">4</div>
        <div class="step-label">Внедрение</div>
      </div>
    </div>
  </div>
</section>
```

### Timeline Slide (вертикальный таймлайн)
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view">История развития</h2>
    <hr class="divider animate-on-view">
    <div class="timeline stagger">
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2020</div>
          <h4>Начало проекта</h4>
          <p>Описание первого этапа</p>
        </div>
      </div>
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2022</div>
          <h4>Масштабирование</h4>
          <p>Описание второго этапа</p>
        </div>
      </div>
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2024</div>
          <h4>Результаты</h4>
          <p>Описание текущего этапа</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

### Table Slide (сравнительная таблица)
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view">Сравнение подходов</h2>
    <hr class="divider animate-on-view">
    <div class="styled-table-wrap animate-on-view">
      <table class="styled-table">
        <thead>
          <tr>
            <th>Критерий</th>
            <th>Подход А</th>
            <th>Подход Б</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Скорость</td>
            <td>Высокая</td>
            <td>Средняя</td>
          </tr>
          <tr>
            <td>Стоимость</td>
            <td>Низкая</td>
            <td>Высокая</td>
          </tr>
          <tr>
            <td>Сложность</td>
            <td>Средняя</td>
            <td>Низкая</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</section>
```

### Diagram Slide (SVG схема связей)
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view" style="text-align: center;">Структура системы</h2>
    <hr class="divider center animate-on-view">
    <svg class="mindmap animate-on-view" viewBox="0 0 500 300" width="100%" height="300" style="max-width: 600px; margin: 0 auto; display: block;">
      <!-- Линии -->
      <line x1="250" y1="150" x2="100" y2="60" stroke="var(--accent-1)" stroke-width="2" opacity="0.4"/>
      <line x1="250" y1="150" x2="400" y2="60" stroke="var(--accent-2)" stroke-width="2" opacity="0.4"/>
      <line x1="250" y1="150" x2="100" y2="240" stroke="var(--accent-3)" stroke-width="2" opacity="0.4"/>
      <line x1="250" y1="150" x2="400" y2="240" stroke="var(--accent-4)" stroke-width="2" opacity="0.4"/>
      
      <!-- Центр -->
      <circle cx="250" cy="150" r="45" fill="url(#grad1)"/>
      <text x="250" y="155" text-anchor="middle" fill="white" font-size="14" font-weight="600">Ядро</text>
      
      <!-- Узлы -->
      <circle cx="100" cy="60" r="35" fill="var(--glass)" stroke="var(--accent-1)" stroke-width="2"/>
      <text x="100" y="65" text-anchor="middle" fill="var(--text-primary)" font-size="11">Модуль 1</text>
      
      <circle cx="400" cy="60" r="35" fill="var(--glass)" stroke="var(--accent-2)" stroke-width="2"/>
      <text x="400" y="65" text-anchor="middle" fill="var(--text-primary)" font-size="11">Модуль 2</text>
      
      <circle cx="100" cy="240" r="35" fill="var(--glass)" stroke="var(--accent-3)" stroke-width="2"/>
      <text x="100" y="245" text-anchor="middle" fill="var(--text-primary)" font-size="11">Модуль 3</text>
      
      <circle cx="400" cy="240" r="35" fill="var(--glass)" stroke="var(--accent-4)" stroke-width="2"/>
      <text x="400" y="245" text-anchor="middle" fill="var(--text-primary)" font-size="11">Модуль 4</text>
      
      <defs>
        <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" style="stop-color:var(--accent-1)"/>
          <stop offset="100%" style="stop-color:var(--accent-3)"/>
        </linearGradient>
      </defs>
    </svg>
  </div>
</section>
```

### Icon Cards Slide (карточки с SVG иконками)
```html
<section>
  <div class="slide-content">
    <h2 class="animate-on-view">Наши преимущества</h2>
    <hr class="divider animate-on-view">
    <div class="grid-3 stagger">
      <div class="glass-card accent animate-on-view">
        <div class="icon-circle icon-pulse">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="20 6 9 17 4 12"></polyline>
          </svg>
        </div>
        <h4>Качество</h4>
        <p>Высокие стандарты на каждом этапе</p>
      </div>
      <div class="glass-card accent animate-on-view">
        <div class="icon-circle icon-pulse">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="10"></circle>
            <polyline points="12 6 12 12 16 14"></polyline>
          </svg>
        </div>
        <h4>Скорость</h4>
        <p>Быстрая реализация проектов</p>
      </div>
      <div class="glass-card accent animate-on-view">
        <div class="icon-circle icon-pulse">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M12 2L2 7l10 5 10-5-10-5z"></path>
            <path d="M2 17l10 5 10-5M2 12l10 5 10-5"></path>
          </svg>
        </div>
        <h4>Масштабируемость</h4>
        <p>Гибкая архитектура решений</p>
      </div>
    </div>
  </div>
</section>
```

---

## CSS для дополнительных компонентов

```css
/* Process Flow */
.process-flow {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
  margin: 30px 0;
}

.process-step {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

.step-icon {
  width: 64px;
  height: 64px;
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
  font-size: 0.95rem;
  color: var(--text-secondary);
  text-align: center;
  max-width: 100px;
}

.process-arrow {
  font-size: 1.8rem;
  color: var(--accent-1);
  animation: arrowPulse 1.5s ease-in-out infinite;
}

@keyframes arrowPulse {
  0%, 100% { opacity: 1; transform: translateX(0); }
  50% { opacity: 0.5; transform: translateX(5px); }
}

/* Timeline */
.timeline {
  position: relative;
  padding-left: 50px;
  max-width: 600px;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 18px;
  top: 0;
  bottom: 0;
  width: 3px;
  background: var(--gradient);
  border-radius: 3px;
}

.timeline-item {
  position: relative;
  margin-bottom: 28px;
}

.timeline-marker {
  position: absolute;
  left: -50px;
  top: 24px;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--accent-1);
  border: 3px solid var(--bg-dark);
  box-shadow: 0 0 0 4px var(--accent-1);
}

.timeline-content {
  padding: 18px 22px;
}

.timeline-date {
  font-size: 0.8rem;
  color: var(--accent-1);
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 8px;
}

/* Styled Table */
.styled-table-wrap {
  overflow-x: auto;
  margin: 24px 0;
  border-radius: 12px;
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
  padding: 16px 20px;
  text-align: left;
  font-weight: 600;
  color: white;
}

.styled-table th:first-child { border-radius: 12px 0 0 0; }
.styled-table th:last-child { border-radius: 0 12px 0 0; }

.styled-table td {
  padding: 14px 20px;
  border-bottom: 1px solid var(--glass-border);
  color: var(--text-secondary);
}

.styled-table tbody tr {
  transition: background 0.3s ease;
}

.styled-table tbody tr:hover {
  background: var(--glass);
}

.styled-table tbody tr:last-child td:first-child { border-radius: 0 0 0 12px; }
.styled-table tbody tr:last-child td:last-child { border-radius: 0 0 12px 0; }

/* Icon animations */
.icon-circle {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: var(--gradient);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  margin-bottom: 16px;
}

.icon-pulse svg {
  animation: iconPulse 2s ease-in-out infinite;
}

@keyframes iconPulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}

.icon-spin svg {
  animation: iconSpin 3s linear infinite;
}

@keyframes iconSpin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.icon-draw svg path,
.icon-draw svg polyline,
.icon-draw svg line {
  stroke-dasharray: 100;
  stroke-dashoffset: 100;
  animation: drawLine 1.5s ease forwards;
}

@keyframes drawLine {
  to { stroke-dashoffset: 0; }
}

/* Pros/Cons */
.pros-cons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}

.pros, .cons {
  padding: 24px;
  border-radius: 16px;
}

.pros {
  background: linear-gradient(135deg, rgba(16, 185, 129, 0.1), rgba(20, 184, 166, 0.1));
  border: 1px solid rgba(16, 185, 129, 0.2);
}

.cons {
  background: linear-gradient(135deg, rgba(239, 68, 68, 0.1), rgba(249, 115, 22, 0.1));
  border: 1px solid rgba(239, 68, 68, 0.2);
}

.pros h4, .cons h4 {
  margin-bottom: 16px;
}

@media (max-width: 768px) {
  .pros-cons { grid-template-columns: 1fr; }
  .timeline { padding-left: 40px; }
  .timeline::before { left: 13px; }
  .timeline-marker { left: -40px; }
}
```

---

## SVG Иконки (библиотека)

### Базовые иконки
```html
<!-- Галочка -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <polyline points="20 6 9 17 4 12"></polyline>
</svg>

<!-- Крестик -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <line x1="18" y1="6" x2="6" y2="18"></line>
  <line x1="6" y1="6" x2="18" y2="18"></line>
</svg>

<!-- Стрелка вправо -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <line x1="5" y1="12" x2="19" y2="12"></line>
  <polyline points="12 5 19 12 12 19"></polyline>
</svg>

<!-- Плюс -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <line x1="12" y1="5" x2="12" y2="19"></line>
  <line x1="5" y1="12" x2="19" y2="12"></line>
</svg>

<!-- Звезда -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
</svg>

<!-- Сердце -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <path d="M20.8 4.6a5.5 5.5 0 0 0-7.8 0L12 5.7l-1-1.1a5.5 5.5 0 0 0-7.8 7.8l1 1.1L12 21l7.8-7.5 1-1.1a5.5 5.5 0 0 0 0-7.8z"></path>
</svg>
```

### Бизнес иконки
```html
<!-- График роста -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline>
  <polyline points="17 6 23 6 23 12"></polyline>
</svg>

<!-- Пользователь -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="12" cy="7" r="4"></circle>
  <path d="M5 21v-2a7 7 0 0 1 14 0v2"></path>
</svg>

<!-- Команда -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="9" cy="7" r="4"></circle>
  <path d="M3 21v-2a4 4 0 0 1 4-4h4a4 4 0 0 1 4 4v2"></path>
  <circle cx="17" cy="11" r="3"></circle>
  <path d="M21 21v-2a3 3 0 0 0-3-3h-1"></path>
</svg>

<!-- Деньги -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <line x1="12" y1="1" x2="12" y2="23"></line>
  <path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"></path>
</svg>

<!-- Цель -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="12" cy="12" r="10"></circle>
  <circle cx="12" cy="12" r="6"></circle>
  <circle cx="12" cy="12" r="2"></circle>
</svg>
```

### Технологии
```html
<!-- Код -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <polyline points="16 18 22 12 16 6"></polyline>
  <polyline points="8 6 2 12 8 18"></polyline>
</svg>

<!-- База данных -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <ellipse cx="12" cy="5" rx="9" ry="3"></ellipse>
  <path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"></path>
  <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"></path>
</svg>

<!-- Облако -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"></path>
</svg>

<!-- Шестерёнка -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="12" cy="12" r="3"></circle>
  <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 1 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 1 1-4 0v-.09a1.65 1.65 0 0 0-1.08-1.51 1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 1 1-2.83-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 1 1 0-4h.09a1.65 1.65 0 0 0 1.51-1.08 1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 1 1 2.83-2.83l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 1 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 1 1 2.83 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9c.26.6.8 1.02 1.51 1.08H21a2 2 0 1 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"></path>
</svg>
```

### Образование
```html
<!-- Книга -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
  <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
</svg>

<!-- Лампочка (идея) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M9 18h6M10 22h4M12 2a7 7 0 0 0-4 12.7V17h8v-2.3A7 7 0 0 0 12 2z"></path>
</svg>

<!-- Диплом -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <circle cx="12" cy="8" r="6"></circle>
  <path d="M15.5 13.5L17 22l-5-3-5 3 1.5-8.5"></path>
</svg>
```
