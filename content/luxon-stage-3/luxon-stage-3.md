+++
date = '2026-05-15T10:00:00+03:00'
draft = false
title = "Интеграция Bootstrap 5 и Luxon с использованием Vite. Этап 3"
+++

## Создание проекта Vite

Для создания нового проекта была использована команда:

```powershell
npm.cmd create vite@latest luxon-bootstrap-vite -- --template vanilla
```

Далее в папке проекта я установила зависимости проекта:

```powershell
npm.cmd install
```

А также, установила библиотеки Bootstrap и Luxon:

```powershell
npm.cmd install bootstrap luxon
```

---

## Запуск проекта

Для локального запуска использовалась команда:

```powershell
npm.cmd run dev
```

## Сборка проекта

Для сборки проекта использовалась команда:

```powershell
npm.cmd run build
```

После сборки создаётся папка:

```text
dist
```

## Размер итогового бандла

После выполнения команды:

```powershell
npm.cmd run build
```

Vite вывел размеры итоговых файлов:

```text
dist/index.html                     1.40 kB │ gzip: 0.61 kB
dist/assets/index-D1mow-3j.css   230.10 kB │ gzip: 30.71 kB
dist/assets/index-tcSKembw.js     94.01 kB │ gzip: 29.37 kB
```

---

## Результат работы

![](../vite-luxon-bootstrap.png)

