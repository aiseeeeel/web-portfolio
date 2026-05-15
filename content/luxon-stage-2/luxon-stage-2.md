+++
date = '2026-05-15T10:00:00+03:00'
draft = false
title = "Интеграция Bootstrap 5 в приложение с Luxon. Этап 2"
+++

## Используемые инструменты

В работе использовались:

- `Node.js` - среда выполнения JavaScript
- `npm` - менеджер пакетов
- `Webpack` - сборщик проекта
- `webpack-cli` - интерфейс командной строки для Webpack
- `serve` - локальный сервер для запуска страницы
- `luxon` - библиотека для работы с датой и временем
- `Bootstrap 5` - CSS-фреймворк для создания интерфейса
- `Bootstrap Modal` - компонент Bootstrap для всплывающих окон

---

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

Далее через:

```javascript
document.getElementById('hh')
```

находится HTML-элемент, в который будет выводиться текущее время.

Функция:

```javascript
setInterval(...)
```

обновляет содержимое элемента каждую секунду.

Метод:

```javascript
DateTime.local()
```

получает текущие дату и время.

Метод:

```javascript
setLocale('ru')
```

устанавливает русскую локаль.

Метод:

```javascript
toFormat('dd.LL.y HH:mm:ss')
```

форматирует дату и время в виде:

```text
день.месяц.год часы:минуты:секунды
```

---

## Создание страницы с Bootstrap 5

Для интерфейса приложения был изменён файл `index.html`:

```powershell
notepad index.html
```

В файл был добавлен следующий код:

```html
<!doctype html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Webpack Lab</title>

  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
    rel="stylesheet">
</head>

<body>
  <main class="container min-vh-100 d-flex align-items-center">
    <div class="row w-100">
      <div class="col-2"></div>

      <div class="col-8 d-grid">
        <button
          type="button"
          class="btn btn-danger btn-lg py-5"
          data-bs-toggle="modal"
          data-bs-target="#timeModal">
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

          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal">
          </button>
        </div>

        <div class="modal-body text-center">
          <h2 id="hh">Загрузка...</h2>
        </div>

        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal">
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

---

## Создание сетки Bootstrap

На странице была создана сетка Bootstrap:

```html
<div class="row w-100">
  <div class="col-2"></div>

  <div class="col-8 d-grid">
  </div>

  <div class="col-2"></div>
</div>
```

Колонки имеют соотношение:

```text
2 - 8 - 2
```

Центральная колонка используется для размещения кнопки.

---

## Создание кнопки

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

Класс:

```html
btn-danger
```

делает кнопку красной.

Класс:

```html
btn-lg
```

увеличивает размер кнопки.

А класс:

```html
d-grid
```

у родительского контейнера позволяет кнопке занимать всю ширину центральной колонки.

---

## Создание модального окна

Для отображения времени использовалось модальное окно Bootstrap:

```html
<div class="modal fade" id="timeModal" tabindex="-1">
```

В заголовке модального окна были указаны имя и фамилия:

```html
<h5 class="modal-title">Agalarova Aisel</h5>
```

Основное содержимое окна:

```html
<h2 id="hh">Загрузка...</h2>
```

Именно в этот элемент JavaScript вставляет текущие дату и время.

Связь между HTML и JavaScript происходит через идентификатор:

```html
id="hh"
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

Атрибут:

```html
data-bs-dismiss="modal"
```

закрывает модальное окно.

---

## Сборка проекта

После изменения файлов была выполнена сборка проекта:

```powershell
npx.cmd webpack
```

Webpack успешно собрал проект и создал файл:

```text
dist/main.js
```

При сборке появилось предупреждение:

```text
The 'mode' option has not been set, webpack will fallback to 'production' for this value.
```

Это предупреждение не является ошибкой. Проект был успешно собран.

---

## Запуск локального сервера

Для запуска проекта использовалась команда:

```powershell
npx.cmd serve .
```

После запуска сервер вывел локальный адрес:

```text
http://localhost:3000
```

По этому адресу приложение стало доступно в браузере.

---

## Результат работы

После запуска страницы отображается большая красная кнопка:

```text
Показать время
```

При нажатии на кнопку открывается модальное окно Bootstrap.

В заголовке окна отображаются имя и фамилия выполнившего работу:

```text
Agalarova Aisel
```

Внутри окна отображаются текущие дата и время, полученные с помощью библиотеки `luxon`.

Закрыть окно можно двумя способами:

- крестиком в правом верхнем углу;
- кнопкой `Закрыть` в правом нижнем углу.

![](../luxon-bootstrap.png)

---

## Последовательность выполненных действий

```powershell
cd D:\webpack-lab
notepad src\index.js
notepad index.html
npx.cmd webpack
npx.cmd serve .
```
