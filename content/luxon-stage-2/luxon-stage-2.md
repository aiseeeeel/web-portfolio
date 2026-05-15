+++
date = '2026-05-15T10:00:00+03:00'
draft = false
title = "Интеграция Bootstrap 5 в приложение с Luxon. Этап 2"
+++

## Исходный JavaScript-код

Для вывода даты и времени использовался файл `src/index.js`:

```javascript
import { DateTime } from 'luxon';
const hh = document.getElementById('hh');
setInterval(() => {
  hh.textContent = DateTime
    .local()
    .setLocale('ru')
    .toFormat('dd.LL.y HH:mm:ss');
}, 1000);
```

В первой строке импортируется объект `DateTime` из библиотеки `luxon`.
Далее через `document.getElementById('hh')` находится HTML-элемент, в который будет выводиться текущее время.

Функция `setInterval()` обновляет содержимое элемента каждую секунду.

Метод `DateTime.local()` получает текущие дату и время.

Метод `toFormat('dd.LL.y HH:mm:ss')` форматирует дату и время в виде день.месяц.год часы:минуты:секунды

---

## Создание страницы с Bootstrap 5

Для интерфейса приложения был изменён файл `index.html`:

```html
<!doctype html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Webpack Lab</title>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
  <main class="container min-vh-100 d-flex align-items-center">
    <div class="row w-100">
      <div class="col-2"></div>
      <div class="col-8 d-grid">
        <button type="button" class="btn btn-danger btn-lg py-5" data-bs-toggle="modal" data-bs-target="#timeModal">
          Показать время
        </button>
      </div>
      <div class="col-2"></div>
    </div>
  </main>
  <div class="modal fade" id="timeModal" tabindex="-1">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Agalarova Aisel</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal">
          </button>
        </div>
        <div class="modal-body text-center">
          <h2 id="hh">Загрузка...</h2>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">
            Закрыть
          </button>
        </div>
      </div>
    </div>
  </div>
  <script src="./dist/main.js"></script>
  <script
    src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js">
  </script>
</body>
</html>
```

На странице была создана сетка Bootstrap. Колонки имеют соотношение 2-8-2:

```html
<div class="row w-100">
  <div class="col-2"></div>
  <div class="col-8 d-grid">
  </div>
  <div class="col-2"></div>
</div>
```

В центральной колонке была размещена большая красная кнопка:

```html
<button
  type="button"
  class="btn btn-danger btn-lg py-5"
  data-bs-toggle="modal"
  data-bs-target="#timeModal">
  Показать время
</button>
```

`btn-danger` делает кнопку красной.
`btn-lg` увеличивает размер кнопки.
`d-grid` позволяет кнопке занимать всю ширину центральной колонки.

Для отображения времени использовано модальное окно Bootstrap:

```html
<div class="modal fade" id="timeModal" tabindex="-1">
```

В заголовке модального окна были указаны имя и фамилия:

```html
<h5 class="modal-title">Agalarova Aisel</h5>
```

Кнопка закрытия в правом верхнем углу:

```html
<button
  type="button"
  class="btn-close"
  data-bs-dismiss="modal">
</button>
```

Кнопка закрытия внизу окна:

```html
<button
  type="button"
  class="btn btn-secondary"
  data-bs-dismiss="modal">
  Закрыть
</button>
```

Атрибут `data-bs-dismiss="modal"` закрывает модальное окно.

---

## Сборка проекта

Сборка проекта:

```powershell
npx.cmd webpack
```

Запуск проекта:

```powershell
npx.cmd serve .
```

---

## Результат
![](../luxon-clock.png)
