# 📋 ПРИМЕРЫ ИДЕАЛЬНЫХ СЛАЙДОВ

> Используй эти примеры как шаблоны для своих презентаций

---

## 1️⃣ TITLE SLIDE (Титульный слайд)

```html
<section>
  <div class="slide-content">
    <h1 class="animate-on-view">Заголовок Презентации</h1>
    
    <div class="divider animate-on-view"></div>
    
    <p class="subtitle animate-on-view">Подзаголовок описания темы</p>
    
    <div class="authors-grid animate-on-view stagger">
      <div class="author-card">
        <div class="author-avatar">А</div>
        <div class="author-name">Актанов Д.</div>
      </div>
      <div class="author-card">
        <div class="author-avatar">А</div>
        <div class="author-name">Ашенов К.</div>
      </div>
      <div class="author-card">
        <div class="author-avatar">Т</div>
        <div class="author-name">Тарасов С.</div>
      </div>
    </div>
    
    <div class="group-badge animate-on-view">
      <span>ИМ-32</span>
      <span>•</span>
      <span>Margulan University</span>
    </div>
  </div>
</section>
```

**Стиль:**
- Крупный h1 заголовок
- Красивый divider
- Авторы в отдельных карточках
- Group badge внизу

---

## 2️⃣ CONTENT SLIDE (Слайд с контентом)

```html
<section>
  <div class="slide-content">
    <!-- Badge категории -->
    <div class="badge animate-on-view">
      <span class="badge-dot"></span>
      Основные концепции
    </div>
    
    <!-- Заголовок -->
    <h2 class="animate-on-view">Структура проекта</h2>
    
    <!-- Разделитель -->
    <hr class="divider animate-on-view">
    
    <!-- Контент в glass-card -->
    <div class="glass-card animate-on-view">
      <h4>Главная идея</h4>
      <p>Описание основной идеи вашего проекта. Текст должен быть в контейнере, никогда просто на фоне.</p>
      
      <ul class="styled-list">
        <li>Пункт первый с кратким описанием</li>
        <li>Пункт второй с деталями</li>
        <li>Пункт третий с выводом</li>
      </ul>
    </div>
  </div>
</section>
```

**Правила:**
- ✅ Badge с категорией вверху
- ✅ h2 заголовок слайда
- ✅ hr divider для разделения
- ✅ Весь текст в .glass-card

---

## 3️⃣ GRID-3 SLIDE (Сетка из 3 карточек)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      Этапы подготовки
    </div>
    
    <h2>Три ключевых этапа</h2>
    <hr class="divider">
    
    <div class="grid-3 stagger">
      <!-- Карточка 1 -->
      <div class="glass-card animate-on-view">
        <div class="icon-circle">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path>
          </svg>
        </div>
        <h4>Планирование</h4>
        <p>Определите цели и ключевые вехи вашего проекта на этом этапе</p>
      </div>
      
      <!-- Карточка 2 -->
      <div class="glass-card animate-on-view">
        <div class="icon-circle">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M9 2L4 6v12c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V6l-5-4H9z"></path>
          </svg>
        </div>
        <h4>Разработка</h4>
        <p>Создавайте и тестируйте компоненты в соответствии с планом</p>
      </div>
      
      <!-- Карточка 3 -->
      <div class="glass-card animate-on-view">
        <div class="icon-circle">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <polyline points="20 6 9 17 4 12"></polyline>
          </svg>
        </div>
        <h4>Завершение</h4>
        <p>Проведите финальную проверку и запустите ваш проект</p>
      </div>
    </div>
  </div>
</section>
```

**Структура:**
- 3 карточки в .grid-3
- Каждая с иконкой в .icon-circle
- SVG иконки (не эмодзи)
- Иерархия: иконка → h4 → текст

---

## 4️⃣ STATS SLIDE (Статистика)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      Результаты и метрики
    </div>
    
    <h2>Впечатляющие цифры</h2>
    <hr class="divider">
    
    <div class="grid-4">
      <div class="stat-card animate-on-view">
        <div class="stat-number">98%</div>
        <div class="stat-label">Удовлетворённость</div>
        <div class="stat-description">пользователей довольны результатом</div>
      </div>
      
      <div class="stat-card animate-on-view">
        <div class="stat-number">500+</div>
        <div class="stat-label">Проектов</div>
        <div class="stat-description">успешно завершено</div>
      </div>
      
      <div class="stat-card animate-on-view">
        <div class="stat-number">4.9★</div>
        <div class="stat-label">Рейтинг</div>
        <div class="stat-description">на независимых платформах</div>
      </div>
      
      <div class="stat-card animate-on-view">
        <div class="stat-number">24/7</div>
        <div class="stat-label">Поддержка</div>
        <div class="stat-description">всегда готовы помочь</div>
      </div>
    </div>
  </div>
</section>
```

**Дизайн:**
- Большие числа/проценты
- Краткие подписи
- Дополнительная информация под числом
- 4 колонки автоматически адаптируются

---

## 5️⃣ TIMELINE SLIDE (Хронология)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      История развития
    </div>
    
    <h2>Основные вехи</h2>
    <hr class="divider">
    
    <div class="timeline">
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2020</div>
          <h4>Начало проекта</h4>
          <p>Первая версия была запущена и получила положительные отзывы</p>
        </div>
      </div>
      
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2021</div>
          <h4>Расширение функций</h4>
          <p>Добавлены новые возможности на основе отзывов пользователей</p>
        </div>
      </div>
      
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2022</div>
          <h4>Мировое признание</h4>
          <p>Проект получил награды и международное признание</p>
        </div>
      </div>
      
      <div class="timeline-item animate-on-view">
        <div class="timeline-marker"></div>
        <div class="timeline-content glass-card">
          <div class="timeline-date">2023</div>
          <h4>Текущий статус</h4>
          <p>Продолжаем развитие и внедрение инновационных решений</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Элементы:**
- Вертикальная линия
- Маркеры для каждого события
- Glass-card с контентом
- Дата для каждого события

---

## 6️⃣ KEY-POINT SLIDE (Выделение)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      Главное
    </div>
    
    <h2>Ключевые моменты</h2>
    <hr class="divider">
    
    <div class="key-points-grid">
      <div class="key-point animate-on-view">
        <div class="icon-circle">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="1"></circle>
            <circle cx="19" cy="12" r="1"></circle>
            <circle cx="5" cy="12" r="1"></circle>
          </svg>
        </div>
        <div class="key-point-content">
          <h4>Первое ключевое понимание</h4>
          <p>Детальное объяснение первого важного момента, на который нужно обратить внимание</p>
        </div>
      </div>
      
      <div class="key-point animate-on-view">
        <div class="icon-circle">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M12 5v14M5 12h14"></path>
          </svg>
        </div>
        <div class="key-point-content">
          <h4>Второе ключевое понимание</h4>
          <p>Объяснение второго критически важного момента в контексте темы</p>
        </div>
      </div>
    </div>
  </div>
</section>
```

**Структура:**
- Иконка слева
- Текст справа
- Flex layout с align-items: center
- На мобильных переходит в column

---

## 7️⃣ QUOTE SLIDE (Цитата)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      Вдохновение
    </div>
    
    <h2>Важное высказывание</h2>
    <hr class="divider">
    
    <div class="quote-box animate-on-view">
      <div class="quote-mark">"</div>
      <p class="quote-text">
        Это великая цитата, которая содержит мудрость и вдохновение 
        для понимания важного концепта или идеи вашей презентации.
      </p>
      <div class="quote-author">
        <strong>Автор Цитаты</strong>
        <span class="quote-source">Источник или контекст</span>
      </div>
    </div>
  </div>
</section>
```

**Дизайн:**
- Большая кавычка
- Выделенный текст цитаты
- Автор и источник
- Центрированный layout

---

## 8️⃣ FEATURE BLOCK SLIDE (Блок с иконками)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      Преимущества
    </div>
    
    <h2>Почему выбрать нас?</h2>
    <hr class="divider">
    
    <div class="grid-2">
      <div class="feature-block animate-on-view">
        <div class="feature-icon">
          <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <path d="M12 2L2 7v10c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V7l-10-5z"></path>
            <polyline points="10 17 14 13 10 9"></polyline>
          </svg>
        </div>
        <h4>Безопасность</h4>
        <p>Высокий уровень защиты ваших данных с использованием современных технологий</p>
      </div>
      
      <div class="feature-block animate-on-view">
        <div class="feature-icon">
          <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"></polyline>
          </svg>
        </div>
        <h4>Производительность</h4>
        <p>Максимальная скорость и оптимизация работы всех компонентов системы</p>
      </div>
    </div>
  </div>
</section>
```

**Компоненты:**
- Иконка сверху
- Заголовок h4
- Описание
- 2 колонки для баланса

---

## 9️⃣ CONCLUSION SLIDE (Выводы)

```html
<section>
  <div class="slide-content">
    <div class="badge">
      <span class="badge-dot"></span>
      Итоги
    </div>
    
    <h2>Главные выводы</h2>
    <hr class="divider">
    
    <div class="glass-card animate-on-view">
      <ul class="conclusion-list">
        <li>
          <span class="conclusion-number">1</span>
          <div>
            <strong>Первый вывод</strong>
            <p>Подробное объяснение первого основного вывода из представленной информации</p>
          </div>
        </li>
        <li>
          <span class="conclusion-number">2</span>
          <div>
            <strong>Второй вывод</strong>
            <p>Детальное описание второго важного вывода, который можно сделать</p>
          </div>
        </li>
        <li>
          <span class="conclusion-number">3</span>
          <div>
            <strong>Третий вывод</strong>
            <p>Объяснение третьего ключевого вывода и его значения</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</section>
```

**Структура:**
- Нумерованный список выводов
- Каждый с заголовком и описанием
- Внутри одной glass-card
- Аккуратный layout

---

## 🔟 THANK YOU SLIDE (Финал)

```html
<section>
  <div class="slide-content thank-you-content">
    <h1 class="animate-on-view">Спасибо за внимание!</h1>
    
    <div class="divider animate-on-view"></div>
    
    <div class="contact-info animate-on-view">
      <p>Вопросы и предложения:</p>
      <p class="contact-email">name@example.com</p>
    </div>
    
    <div class="social-links animate-on-view">
      <a href="#" class="social-link">
        <svg width="24" height="24"><!-- GitHub icon --></svg>
      </a>
      <a href="#" class="social-link">
        <svg width="24" height="24"><!-- LinkedIn icon --></svg>
      </a>
      <a href="#" class="social-link">
        <svg width="24" height="24"><!-- Twitter icon --></svg>
      </a>
    </div>
  </div>
</section>
```

**Элементы:**
- Крупный спасибо
- Контактная информация
- Ссылки на соцсети (SVG иконки)
- Центрированный layout

---

## 📋 УНИВЕРСАЛЬНЫЙ ЧЕКЛИСТ ДЛЯ СЛАЙДА

Перед тем как завершить презентацию, проверь каждый слайд:

- [ ] Есть ли badge с категорией?
- [ ] Есть ли h2 заголовок?
- [ ] Есть ли hr divider?
- [ ] Весь ли текст в контейнере (.glass-card, .grid-*, .timeline-content)?
- [ ] Используются ли только SVG иконки (не эмодзи)?
- [ ] Нет ли просто текста на фоне?
- [ ] Есть ли минимум 3 визуальных элемента?
- [ ] Правильно ли выглядит на мобильных?
- [ ] Работает ли навигация (стрелки, клавиатура)?
- [ ] Все ли читаемо на разных размерах экрана?

---

**Помни:** Каждый слайд — это возможность произвести впечатление. Используй эти примеры как основу и адаптируй под свой контент! 🎉
