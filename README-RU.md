# uBlock-YT

<p align="center">
  <img src="info/a1.png" alt="Баннер uBlock-YT" width="100%">
</p>

<p align="center">
  <a href="https://github.com/a111et/ublock-yt/blob/main/README.md"><img src="https://img.shields.io/badge/English-README-blue?style=for-the-badge&logo=github" alt="English README"></a>
  <a href="https://github.com/a111et/ublock-yt/stargazers"><img src="https://img.shields.io/github/stars/a111et/ublock-yt?style=for-the-badge&logo=github&color=333" alt="Звезды"></a>
  <a href="https://github.com/a111et/ublock-yt/issues"><img src="https://img.shields.io/github/issues/a111et/ublock-yt?style=for-the-badge&logo=github&color=666" alt="Проблемы"></a>
  <a href="https://subscribe.adblockplus.org/?location=https://raw.githubusercontent.com/a111et/ublock-yt/refs/heads/main/ublock-YT-Clinin.txt&title=uBlock-YT%20Filters"><img src="https://img.shields.io/badge/Subscribe-Filter%20List-red?style=for-the-badge&logo=ublockorigin" alt="Подписаться"></a>
</p>

---

## 🎯 Цель проекта
Главная задача этого проекта — сделать YouTube чище, аккуратнее и удобнее в использовании. Он направлен на удаление отвлекающих элементов, алгоритмического мусора и дефектов верстки. 

*Планы на будущие обновления:* Пользовательские темы (скины) и специализированные пользовательские скрипты для дальнейшего улучшения или настройки интерфейса.

## 📦 Что это такое?
Этот репозиторий содержит тщательно подобранную коллекцию пользовательских правил для **uBlock Origin**, созданных специально для YouTube. Он нацелен на устранение раздражающих элементов интерфейса, лишнего мусора и сдвигов верстки, которые остаются после стандартной блокировки рекламы.

> [!TIP]
> Большое спасибо за использование моих фильтров! Если вы заметите какие-либо баги, нарушения верстки или у вас есть предложения по улучшению, пожалуйста, откройте Issue или Pull Request с вашим решением. Я с радостью добавлю его в общий список. Наслаждайтесь чистым YouTube!

---

## 🚀 Быстрая настройка и установка

### Вариант 1: Автоматическая подписка (рекомендуется)
Нажмите на кнопку ниже, чтобы автоматически импортировать список фильтров и подписаться на него в uBlock Origin:

[![Подписаться на список фильтров](https://img.shields.io/badge/Click%20to%20Subscribe-uBlock%20Origin-red?style=for-the-badge&logo=ublockorigin)](https://subscribe.adblockplus.org/?location=https%3A%2F%2Fraw.githubusercontent.com%2Fa111et%2Fublock-yt%2Frefs%2Fheads%2Fmain%2Fublock-YT-Clinin.txt&title=uBlock-YT+Filters)

### Вариант 2: Ручной импорт
1. Скопируйте ссылку на исходный файл фильтров: `https://raw.githubusercontent.com/a111et/ublock-yt/refs/heads/main/ublock-YT-Clinin.txt`
2. Откройте **Панель управления uBlock Origin** -> вкладку **Списки фильтров**.
3. Прокрутите страницу вниз, установите флажок **Имровать...** (Import...), вставьте ссылку и нажмите **Применить изменения**.

---

## 🛠️ Разбор включенных правил

### 1. Улучшенная сетка (4 видео в ряд)
Принудительно отображает ровно 4 видео в ряд на главной странице YouTube для лучшей видимости и менее тесного вида.

![Превью макета](info/a1.png)

```adblock
youtube.com##ytd-rich-grid-renderer:style(--ytd-rich-grid-items-per-row: 4 !important;)
youtube.com##ytd-rich-grid-renderer:style(--ytd-rich-grid-posts-per-row: 4 !important;)
youtube.com##ytd-two-column-browse-results-renderer.grid-6-columns:style(width: 100% !important;)
youtube.com##ytd-two-column-browse-results-renderer.grid:not(.grid-disabled):style(max-width: 100% !important;)
youtube.com##ytd-rich-grid-renderer, html:style(--ytd-rich-grid-slim-items-per-row: 7 !important;)
youtube.com##ytd-rich-grid-renderer, html:style(--ytd-rich-grid-game-cards-per-row: 7 !important;)
youtube.com##+js(set-attr, ytd-rich-shelf-renderer, is-show-more-hidden)
youtube.com##+js(ra, hidden, ytd-rich-item-renderer, stay)
