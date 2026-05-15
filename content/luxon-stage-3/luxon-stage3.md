+++
date = '2026-05-15T18:00:00+03:00'
draft = false
title = "Интеграция Bootstrap 5 и Luxon с использованием Vite. Этап 3"
+++

## Используемые инструменты

В работе использовались:

- `Node.js` — среда выполнения JavaScript
- `npm` — менеджер пакетов
- `Vite` — инструмент сборки frontend-приложений
- `Bootstrap 5` — CSS-фреймворк для создания интерфейса
- `Luxon` — библиотека для работы с датой и временем

---

## Создание проекта Vite

Для создания нового проекта была использована команда:

```powershell
npm.cmd create vite@latest luxon-bootstrap-vite -- --template vanilla
```

После создания проекта я перешла в папку проекта:

```powershell
cd luxon-bootstrap-vite
```

Далее были установлены зависимости проекта:

```powershell
npm.cmd install
```

---

## Установка Bootstrap и Luxon

Для работы приложения были установлены библиотеки Bootstrap и Luxon:

```powershell
npm.cmd install bootstrap luxon
```

---

## Содержимое package.json

```json
{
  "name": "luxon-bootstrap-vite",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "devDependencies": {
    "vite": "^8.0.13"
  },
  "dependencies": {
    "bootstrap": "^5.3.8",
    "luxon": "^3.7.2"
  }
}
```

Команда:

```powershell
npm.cmd run build
```

используется для сборки проекта.

---

## Полное содержимое index.html

```html
<!doctype html>
<html lang="ru">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Luxon Bootstrap Vite</title>
  </head>

  <body>
    <main class="container min-vh-100 d-flex align-items-center">
      <div class="row w-100">
        <div class="col-2"></div>

        <div class="col-8 d-grid">
          <button id="openModal" class="btn btn-danger btn-lg py-5">
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
              id="closeX">
            </button>
          </div>

          <div class="modal-body text-center">
            <h2 id="hh">Загрузка...</h2>
          </div>

          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              id="closeButton">
              Закрыть
            </button>
          </div>

        </div>
      </div>
    </div>

    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```

---

## Полное содержимое src/main.js

```javascript
import { DateTime } from 'luxon';
import Modal from 'bootstrap/js/dist/modal';
import 'bootstrap/dist/css/bootstrap.min.css';
import './style.css';

const hh = document.getElementById('hh');

setInterval(() => {
  hh.textContent = DateTime
    .local()
    .setLocale('ru')
    .toFormat('dd.LL.y HH:mm:ss');
}, 1000);

const modalElement = document.getElementById('timeModal');
const timeModal = new Modal(modalElement);

document.getElementById('openModal').addEventListener('click', () => {
  timeModal.show();
});

document.getElementById('closeX').addEventListener('click', () => {
  timeModal.hide();
});

document.getElementById('closeButton').addEventListener('click', () => {
  timeModal.hide();
});
```

---

## Полное содержимое src/style.css

```css
body {
  background: #f5e8aa;
}

.modal-body h2 {
  font-size: 32px;
  font-weight: 700;
}
```

---

## Запуск проекта

Для локального запуска использовалась команда:

```powershell
npm.cmd run dev
```

После запуска Vite вывел локальный адрес:

```text
http://localhost:5173
```

---

## Сборка проекта

Для сборки проекта использовалась команда:

```powershell
npm.cmd run build
```

После сборки создаётся папка:

```text
dist
```

---

## Размер итогового бандла

После выполнения команды:

```powershell
npm.cmd run build
```

Vite выводит размеры итоговых файлов проекта.

Размер JavaScript и CSS бандла необходимо указать по результатам сборки.

---

## Результат работы

После запуска страницы отображается большая красная кнопка:

```text
Показать время
```

При нажатии на кнопку открывается модальное окно Bootstrap.

В заголовке окна отображается:

```text
Agalarova Aisel
```

Внутри окна отображаются текущие дата и время, обновляемые библиотекой Luxon.

Закрыть окно можно:

- крестиком в правом верхнем углу;
- кнопкой `Закрыть`.

![](../vite-luxon-bootstrap.png)

---

## Последовательность выполненных действий

```powershell
npm.cmd create vite@latest luxon-bootstrap-vite -- --template vanilla
cd luxon-bootstrap-vite
npm.cmd install
npm.cmd install bootstrap luxon
npm.cmd run dev
npm.cmd run build
npm.cmd run preview
```
