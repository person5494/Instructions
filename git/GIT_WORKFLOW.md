# Git workflow — работа с задачами от `develop`

# ВАЖНО: КАЖДУЮ ЗАДАЧУ ВЫПОЛНЯТЬ В ОТДЕЛЬНОЙ ВЕТКЕ, СОЗДАННОЙ ОТ СВЕЖЕГО СОСТОЯНИЯ ВЕТКИ DEVELOP.
# ВАЖНО: ПРИ ДОБАВЛЕНИИ ИЗМЕНЕНИЙ В GIT С ПОМОЩЬЮ КОМАНДЫ `git add` ДОБАВЛЯЕМ ТОЛЬКО ИЗМЕНЁННЫЕ ИЛИ ВНОВЬ СОЗДАННЫЕ ФАЙЛЫ.

## 1. Первый запуск проекта

Клонировать рабочий репозиторий:

```bash
git clone https://github.com/PM-YandexPracticum/SkillSwap_55_3.git
```

Перейти в папку проекта:

```bash
cd SkillSwap_55_3
```

Посмотреть доступные ветки:

```bash
git branch -a
```

Перейти на `develop`:

```bash
git switch develop
```

ПОДТЯНУТЬ АКТУАЛЬНУЮ ВЕРСИЮ ВЕТКИ:

```bash
git pull
```

---

# Работа над новой задачей

## 2. Перед началом каждой задачи

Перейти на `develop`:

```bash
git switch develop
```

ОБЯЗАТЕЛЬНО ПОДТЯНУТЬ АКТУАЛЬНОЕ СОСТОЯНИЕ ВЕТКИ НА КОМПЬЮТЕР:

```bash
git pull
```

ОБЯЗАТЕЛЬНО Создать новую ветку от СВЕЖЕГО `develop` и сразу перейти в неё:

```bash
git switch -c feature/номер-задачи-название-задачи
```

Например:

```bash
git switch -c feature/verst-01-button
```

Проверить текущую ветку:

```bash
git branch
```

Текущая ветка отмечена `*`:

```text
develop
* feature/verst-01-button
```

> Важно: код изменяем только в своей feature-ветке.  
> В `develop` напрямую не работаем.

---

## 3. Выполнить задачу

Например, для Button:

```text
src/
└── shared/
    └── ui/
        └── Button/
            ├── Button.tsx
            └── Button.module.css
```

После завершения работы проверить изменения:

```bash
git status
```

---

## 4. Добавить изменения в Git

Добавить ТОЛЬКО изменённые или вновь созданные файлы:

```bash
git add Button.tsx Button.module.css
```

Создать коммит:

```bash
git commit -m "feat: add Button component"
```

---

## 5. Отправить feature-ветку на GitHub

При первом push ЭТОЙ ветки:

```bash
git push -u origin feature/verst-01-button
```

После `-u` для следующих push этой же ветки достаточно:

```bash
git push
```

---

## 6. Создать Pull Request

На GitHub создать PR:

```text
base:    develop
compare: feature/verst-01-button
```

То есть:

```text
feature/verst-01-button
      ↓
   develop
```

Проверить, что PR создаётся именно в `develop`, а не в `main`.

---

# Следующая задача

После того как работа над предыдущей задачей закончена:

```bash
git switch develop
git pull
git switch -c feature/verst-02-input
```

После выполнения:

```bash
git status
git add Input.tsx Input.module.css
git commit -m "feat: add Input component"
git push -u origin feature/verst-02-input
```

Затем создать:

```text
feature/verst-02-input → develop
```

---

# Короткая шпаргалка

## Начало новой задачи

```bash
git switch develop
git pull
git switch -c feature/номер-задачи-название-задачи
```

## После выполнения задачи

```bash
git status
git add FileName.tsx FileName.module.css
git commit -m "описание коммита"
git push -u origin feature/TaskNumber-TaskName
```

После этого создать Pull Request:

```text
feature/TaskNumber-TaskName → develop
```

---

# Главное правило

```text
develop
   │
   ├── feature/verst-01-button
   ├── feature/verst-02-input
   ├── feature/verst-33-avatar
   └── feature/verst-99-modal
```

Каждую новую feature-ветку создаём от СВЕЖЕГО `develop`.
Никогда не начинаем новую задачу от предыдущей feature-ветки.  
Никогда не пишем код напрямую в `develop`.
