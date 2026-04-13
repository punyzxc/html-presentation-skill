# 🎯 Инструкции для Copilot CLI по созданию ПРОФЕССИОНАЛЬНЫХ презентаций

> Используй эти инструкции для создания максимально красивых и наполненных HTML-презентаций. Никогда просто текста! Всегда контейнеры! Всегда SVG!

---

## 🚀 КАК СОЗДАВАТЬ ПРЕЗЕНТАЦИИ

**Когда пользователь говорит:** "Создай презентацию на тему X"

**Твой процесс:**

1. **Структурируй контент** в 7-10 логических блоков
2. **Выбери дизайн** в зависимости от темы
3. **Используй правильные контейнеры** (glass-card, grid, timeline)
4. **Заполни SVG иконками** вместо эмодзи
5. **Убедись что нет "голого текста"** - всё в контейнерах!
6. **Сгенерируй один HTML файл** полностью автономный

---

## 🏗️ СТРУКТУРА КАЖДОГО СЛАЙДА

```html
<section id="slide-X">
  <div class="slide-content">
    <!-- ОБЯЗАТЕЛЬНО: Badge -->
    <div class="badge">
      <span class="badge-dot"></span>
      Категория или номер раздела
    </div>
    
    <!-- ОБЯЗАТЕЛЬНО: Заголовок -->
    <h2>Название раздела</h2>
    
    <!-- ОБЯЗАТЕЛЬНО: Разделитель -->
    <hr class="divider">
    
    <!-- ОБЯЗАТЕЛЬНО: Контейнер с контентом (выбери один или несколько) -->
    
    <!-- Вариант 1: Простая карточка с текстом -->
    <div class="glass-card">
      <p>Текст внутри красивой карточки с фоном</p>
    </div>
    
    <!-- Вариант 2: Две карточки рядом -->
    <div class="grid-2">
      <div class="glass-card accent">
        <div class="icon-circle">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="10"></circle>
          </svg>
        </div>
        <h4>Первый пункт</h4>
        <p>Описание первого пункта</p>
      </div>
      <div class="glass-card accent">
        <div class="icon-circle">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <rect x="3" y="3" width="18" height="18" rx="2"></rect>
          </svg>
        </div>
        <h4>Второй пункт</h4>
        <p>Описание второго пункта</p>
      </div>
    </div>
  </div>
</section>
```

---

## 📦 ОСНОВНЫЕ КОНТЕЙНЕРЫ

### 1. Glass Card (для основного контента)

```html
<div class="glass-card">
  <!-- Текст, списки, что угодно -->
  <p>Содержимое</p>
</div>
```

### 2. Grid 2 (для двух колонок)

```html
<div class="grid-2">
  <div class="glass-card accent">
    <div class="icon-circle">SVG</div>
    <h4>Пункт 1</h4>
    <p>Описание</p>
  </div>
  <div class="glass-card accent">
    <div class="icon-circle">SVG</div>
    <h4>Пункт 2</h4>
    <p>Описание</p>
  </div>
</div>
```

### 3. Grid 3 (для статистики)

```html
<div class="grid-3">
  <div class="stat-card">
    <div class="stat-number">100%</div>
    <div class="stat-label">Успеха</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">500+</div>
    <div class="stat-label">Проектов</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">4.9★</div>
    <div class="stat-label">Рейтинг</div>
  </div>
</div>
```

### 4. Key Point (для выделения важного)

```html
<div class="key-point">
  <div class="key-point-icon">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
      <circle cx="12" cy="12" r="10"></circle>
      <line x1="12" y1="16" x2="12" y2="12"></line>
      <line x1="12" y1="8" x2="12.01" y2="8"></line>
    </svg>
  </div>
  <div class="key-point-content">
    <h4>Важно!</h4>
    <p>Ключевая информация</p>
  </div>
</div>
```

---

## 🎨 ВЫБОР ДИЗАЙНА ПО ТЕМЕ

| Тема | Дизайн | Цвета |
|------|--------|-------|
| IT, AI, программирование, стартапы | **Glassmorphism** | Фиолетовый + Голубой |
| Наука, исследования, образование | **Minimal Dark** | Серый + Синий |
| Бизнес, инвестиции, корпорации | **Corporate** | Тёмный + Белый |
| Дизайн, творчество, маркетинг | **Gradient Mesh** | Розовый + Жёлтый |
| Здоровье, экология, природа | **Green Gradient** | Зелёный + Голубой |

---

## 🎯 РЕЦЕПТЫ СЛАЙДОВ

### Рецепт 1: Content слайд (самый частый)

```html
<section id="slide-X">
  <div class="slide-content">
    <div class="badge"><span class="badge-dot"></span>Раздел 1</div>
    <h2>Название раздела</h2>
    <hr class="divider">
    
    <div class="grid-2">
      <div class="glass-card accent">
        <div class="icon-circle">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <!-- SVG ИКОНКА ЗДЕСЬ -->
          </svg>
        </div>
        <h4>Пункт 1</h4>
        <ul class="styled-list">
          <li>Подпункт 1</li>
          <li>Подпункт 2</li>
        </ul>
      </div>
      <div class="glass-card accent">
        <div class="icon-circle">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <!-- SVG ИКОНКА ЗДЕСЬ -->
          </svg>
        </div>
        <h4>Пункт 2</h4>
        <ul class="styled-list">
          <li>Подпункт 1</li>
          <li>Подпункт 2</li>
        </ul>
      </div>
    </div>
  </div>
</section>
```

### Рецепт 2: Статистика

```html
<section id="slide-X">
  <div class="slide-content">
    <h2>Результаты</h2>
    <hr class="divider">
    
    <div class="grid-3">
      <div class="stat-card">
        <div class="icon-circle" style="margin: 0 auto 12px;">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <!-- SVG ИКОНКА -->
          </svg>
        </div>
        <div class="stat-number">300%</div>
        <div class="stat-label">Рост</div>
      </div>
      <!-- Ещё 2 карточки -->
    </div>
  </div>
</section>
```

### Рецепт 3: Ключевая информация

```html
<section id="slide-X">
  <div class="slide-content">
    <h2>Главное</h2>
    <hr class="divider">
    
    <div class="key-point">
      <div class="key-point-icon">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="12" cy="12" r="10"></circle>
        </svg>
      </div>
      <div class="key-point-content">
        <h4>Запомните</h4>
        <p>Это самое важное из всего, что было сказано.</p>
      </div>
    </div>
  </div>
</section>
```

---

## 🚫 ЗАПРЕТЫ

❌ **НИКОГДА:**
- Просто текст без контейнера
- Эмодзи вместо SVG
- Рубленый текст менее 0.9rem
- Белый текст прямо на фоне без карточки
- Картинки вместо SVG иконок

✅ **ВСЕГДА:**
- Текст в glass-card или grid
- SVG иконки для всех графиков
- Минимум 0.9rem размер шрифта
- Контейнер с backdrop-filter для текста
- Встроенные SVG (не картинки)

---

## 📝 ПРОЦЕСС СОЗДАНИЯ

### Шаг 1: Анализ контента
- Выдели 7-10 главных идей
- 1 слайд = 1 идея
- Убедись что есть логическая последовательность

### Шаг 2: Выбор дизайна
- Смотри таблицу выше
- Выбери цвета, соответствующие теме
- Придумай фон (градиент, орбы и т.д.)

### Шаг 3: Структурирование слайдов
- Слайд 1: Титульный (title-slide)
- Слайды 2-8: Контент (content-slide с grid-2/3)
- Слайд 9-10: Выводы и "Спасибо"

### Шаг 4: Подбор иконок
- Смотри SVG_ICONS_GUIDE.md
- Выбери подходящие иконки для каждого пункта
- Вставь inline SVG в .icon-circle

### Шаг 5: Финализация
- Проверь что всё в контейнерах
- Убедись что нет "голого текста"
- Проверь читаемость текста
- Сгенерируй один HTML файл

---

## 🎨 ПРИМЕРЫ SVG ИКОНОК

```html
<!-- Книга -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
  <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
</svg>

<!-- Идея (лампа) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M15 21H9v-2h6v2z"></path>
  <path d="M12 3a6 6 0 0 0-9 5.5c0 2.75 1.5 5 3.75 6.25v2.5h10v-2.5c2.25-1.25 3.75-3.5 3.75-6.25A6 6 0 0 0 12 3z"></path>
</svg>

<!-- Галочка (успех) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <polyline points="20 6 9 17 4 12"></polyline>
</svg>

<!-- График -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <polyline points="23 6 13.5 15.5 8.5 10.5 1 18"></polyline>
  <polyline points="17 6 23 6 23 12"></polyline>
</svg>

<!-- Люди (группа) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
  <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
  <circle cx="9" cy="7" r="4"></circle>
  <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
  <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
</svg>
```

---

## 🔧 ТЭМПЛЕЙТ ПОЛНОЙ ПРЕЗЕНТАЦИИ

Используй этот шаблон для создания базовой структуры:

```html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Название презентации</title>
  <style>
    /* ВСЕ СТИЛИ ЗДЕСЬ */
  </style>
</head>
<body>
  <!-- СЛАЙД 1: Титульный -->
  <section id="slide-1">
    <div class="slide-content title-slide">
      <!-- ... -->
    </div>
  </section>
  
  <!-- СЛАЙДЫ 2-8: Контент -->
  <section id="slide-X">
    <div class="slide-content">
      <!-- ... -->
    </div>
  </section>
  
  <!-- ФИНАЛЬНЫЙ СЛАЙД: Спасибо -->
  <section id="slide-final">
    <!-- ... -->
  </section>
  
  <script>
    <!-- ВСЕ СКРИПТЫ ЗДЕСЬ -->
  </script>
</body>
</html>
```

---

## ✅ ФИНАЛЬНЫЙ ЧЕКЛИСТ

Перед тем как показать презентацию, проверь:

- [ ] 7-10 слайдов минимум?
- [ ] Каждый слайд в контейнере (glass-card/grid)?
- [ ] Нет просто текста на фоне?
- [ ] Используются SVG иконки, не эмодзи?
- [ ] У каждой иконки есть .icon-circle обёртка?
- [ ] Текст читаемый (0.9rem минимум)?
- [ ] Есть badge на каждом слайде?
- [ ] Есть divider под заголовком?
- [ ] Используется правильный дизайн для темы?
- [ ] Всё работает offline (нет external links)?

---

**ПОМНИ:** Если текст не в контейнере - переделай. Если иконка - эмодзи - замени на SVG. Если слайд выглядит пустой - добавь контента!

**Версия**: 2.0  
**Используй эти инструкции для максимальной профессиональности!**
