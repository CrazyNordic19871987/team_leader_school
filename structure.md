# 🏗️ Структура проекта "ИнноСити 2026"

## 📁 Архитектура файлов
innocity-2026-marketing-plan/
│
├── 📄 index.html # Главный файл маркетингового плана
├── 📄 README.md # Описание проекта (англ./рус.)
├── 📄 STRUCTURE.md # Этот файл структуры
├── 📄 .gitignore # Исключенные файлы для Git
│
├── 📁 assets/ # Ресурсы (опционально)
│ ├── 📁 images/ # Изображения для README
│ │ ├── screenshot-dashboard.png
│ │ ├── screenshot-kanban.png
│ │ └── screenshot-calendar.png
│ ├── 📁 fonts/ # Локальные шрифты (если нужны)
│ └── 📁 icons/ # Дополнительные иконки
│
├── 📁 docs/ # Документация
│ ├── 📁 presentations/ # Презентации для школ
│ ├── 📁 print/ # PDF версии для печати
│ └── 📁 templates/ # Шаблоны писем/постов
│
└── 📁 backups/ # Бэкапы (игнорируются Git)
└── *.bak



## 🧩 Внутренняя структура HTML

### 1. **CSS-архитектура (стили)**

```css
:root {
    --primary: #0B1A33;      /* Основной фон */
    --accent: #00C48C;       /* Акцентный зеленый */
    --accent-alt: #FFB800;    /* Желтый */
    --accent-purple: #A855F7; /* Фиолетовый */
    --accent-teal: #2DD4BF;   /* Бирюзовый */
    --gradient-1: linear-gradient(135deg, var(--accent), var(--accent-alt));
    --gradient-2: linear-gradient(135deg, var(--accent-purple), var(--accent));
}

Компоненты стилей:

nav-sidebar — левое навигационное меню

main-content — основной контент с отступом под меню

tabs — верхние вкладки для быстрой навигации

kpi-grid — сетка KPI-карточек

section — блоки с контентом

data-table — стилизованные таблицы

funnel — визуализация воронки продаж

bar-chart — столбчатые диаграммы

2. JavaScript-функционал
javascript
// Основные функции
function switchTab(tabName)     // Переключение между вкладками
function toggleSidebar()        // Свернуть/развернуть боковое меню
function exportToPDF()          // Печать/экспорт в PDF

// Интерактивность
checklist-checkbox              // Кликабельные чекбоксы
nav-item.active                 // Подсветка активного пункта меню
🗂️ Структура разделов (17 вкладок)
Блок 1: Стратегия (№1-4)
#	Раздел	ID	Назначение
1	📊 Обзор	overview	Главный дашборд, KPI
2	📅 Смены	shifts	График лагерных смен
3	👥 Аудитории	audience	Сегментация ЦА
4	📱 Каналы	channels	Каналы продвижения
Блок 2: Тактика (№5-8)
#	Раздел	ID	Назначение
5	🗓️ Календарь	calendar	Понедельный план
6	📝 Контент	content	Контент-матрица
7	💰 Бюджет	budget	Распределение средств
8	✅ Чек-лист	checklist	Интерактивный To-Do
Блок 3: Операционка (№9-12)
#	Раздел	ID	Назначение
9	🎯 Офферы	offers	УТП и акции
10	📋 Канбан	kanban	Доска задач
11	📆 Недели	weekly	Детальный план
12	📊 Метрики	metrics	CPL, ROI, аналитика
Блок 4: Аналитика (№13-17)

#	Раздел	ID	Назначение
13	🎯 Сценарии	scenarios	Прогнозы (3 варианта)
14	📣 Кампании	campaigns	План постов, Email
15	🔍 SWOT	swot	Анализ и конкуренты
16	📈 Трекинг	tracking	Ежедневный мониторинг
17	🔄 Ретаргет	retargeting	Сегменты для повторных касаний
🔗 Навигационные связи
text
Боковое меню (nav-sidebar)
        ↓
   [Пункт 1..17]
        ↓
   data-slide="overview"
        ↓
   switchTab('overview')
        ↓
   tab-overview.active

Верхние вкладки (tabs)
        ↓
   tab-btn onclick
        ↓
   switchTab('overview')
        ↓
   tab-overview.active
📊 Типы данных в проекте
KPI-карточки
html
<div class="kpi-card">
    <div class="kpi-value">300</div>     <!-- Значение -->
    <div class="kpi-label">Заявок</div>  <!-- Метка -->
    <div class="progress-bar">...</div>  <!-- Прогресс -->
</div>
Таблицы
html
<table class="data-table">
    <thead>...</thead>  <!-- Заголовки -->
    <tbody>...</tbody>  <!-- Данные -->
</table>
Чекбоксы
html
<div class="checklist-item">
    <div class="checklist-checkbox" onclick="this.classList.toggle('checked')"></div>
    <span>Задача</span>
</div>
🎨 Визуальные компоненты
Компонент	CSS-класс	Где используется
Карточка	.card	Офферы, акции
Бейдж	.badge	Статусы, приоритеты
Прогресс-бар	.progress-bar	KPI, выполнение
Воронка	.funnel	Конверсия
График	.bar-chart	Динамика заявок
Канбан	.kanban-column	Задачи
📱 Адаптивность
css
@media (max-width: 1200px) {
    .grid-4 { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 768px) {
    .nav-sidebar { width: 70px; }           /* Сворачиваем меню */
    .main-content { margin-left: 70px; }    /* Сдвигаем контент */
    .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; }
}
🖨️ Печать (PDF)
css
@media print {
    .nav-sidebar, .nav-toggle, .export-btn, .tabs {
        display: none !important;  /* Скрываем навигацию */
    }
    .main-content {
        margin-left: 0;            /* На всю ширину */
        max-width: 100%;
    }
}
🔧 Расширение проекта
Как добавить новую вкладку:
Добавить пункт в боковое меню:

html
<div class="nav-item" data-slide="new-tab" onclick="switchTab('new-tab')">
    <span class="nav-item-num">18</span>✨ Новая вкладка
</div>
Добавить кнопку в верхние табы:

html
<div class="tab-btn" onclick="switchTab('new-tab')">✨ Новая</div>
Создать контейнер для контента:

html
<div id="tab-new-tab" class="tab-pane">
    <div class="section">
        <h2 class="section-title"><span>✨ Новая вкладка</span></h2>
        <!-- Ваш контент -->
    </div>
</div>
📌 Итог
Проект построен по принципу "все в одном":

✅ Единый HTML-файл

✅ Встроенные стили (не нужно подключать CSS)

✅ Встроенный JavaScript (не нужно подключать JS)

✅ Адаптивный дизайн

✅ Готов к печати

✅ Легко расширяется

Это делает его идеальным инструментом для быстрого развертывания и совместной работы над маркетинговым планом без необходимости настройки сервера или сборки.

<p align="center"> 🔄 Обновлено: Март 2026 </p> ```
