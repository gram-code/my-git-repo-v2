# my-git-repo-v2
Вторая версия ДЗ с учетом p2p

## 1. Комментарий p2p
1. название дополнительной ветки feture-banch (опечатка)
2. commit message можно было бы делать менее время зависимыми(added) и дополнительно в 2 строки
3. README можно было сделать менее подробным (опустить такие команды как echo и т.д.)
4. index.html как таковой не имеет html кода (для задания не критично)


## 2. Клонирование репозитория

### Задание
- Клонируйте репозиторий "my-git-repo" на свой компьютер с использованием команды `git clone`.
- Убедитесь, что репозиторий успешно склонирован на ваш компьютер.

### Решение
```bash
git clone git@github.com:gram-code/my-git-repo-v2.git
cd my-git-repo-v2
ls -alh
```

## 3. Добавление файлов и коммит

### Задание
- Внесите некоторые изменения в файл `README.md`, добавьте некоторый текст или контент.
- Используйте команду `git status`, чтобы увидеть, какие файлы были изменены.
- Используйте команду `git add`, чтобы добавить измененные файлы в индекс.
- Используйте команду `git commit`, чтобы зафиксировать изменения с информативным сообщением о коммите.
- Повторите процесс изменения файлов, добавления в индекс и коммита несколько раз.

### Решение
Внесли некоторые изменения в `README.md`. Вывод команды `git status`:
```bash
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
Добавим изменения с помощью команды `git add`:
```bash
git add README.md
```
Создадим коммит:
```bash
git commit -m "Added info in README.md"
```
И запушим на GitHub
```bash
git push
```
Сделаем еще один коммит и запушим его
```bash
git add README.md
git commit -m "Added info in README.md - second commit"
git push
```

## 4. Использование `.gitignore`
### Задание
- Создайте файл `log.txt` и напишите в нем некоторый текст.
- Создайте файл `notes.txt` и напишите в нем некоторый текст.
- Создайте файл `.gitignore` в корневом каталоге вашего репозитория.
- В файле `.gitignore` добавьте следующие строки: `log.txt`. Это гарантирует, что файл `log.txt` будет игнорироваться Git.
- Сохраните изменения в файле `.gitignore` и зафиксируйте его в вашем репозитории.
- Убедитесь, что файл `log.txt` больше не отображается при выполнении команды `git status`, но файл `notes.txt` по-прежнему видим.

### Решение
Cоздадим файлы
```bash
echo "некоторый текст" > log.txt
echo "некоторый текст" > notes.txt
echo "log.txt" > .gitignore
```

Фиксируем изменения
```bash
git add README.md .gitignore README.md
git commit -m "Task No. 4"
git push
```

Вывод команды `git status` 
```bash
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        notes.txt

nothing added to commit but untracked files present (use "git add" to track)
```

## 5. Слияние веток и разрешение конфликтов
### Задание
- Создайте новую ветку "feature-branch" в вашем репозитории.
- Внесите изменения в файл `index.html` в ветке "feature-branch", например, добавьте новую строку.
- Сохраните изменения и зафиксируйте их.
- Переключитесь обратно на основную ветку.
- Внесите другие изменения в файл `index.html` в основной ветке, например, измените существующую строку.
- Сохраните изменения и зафиксируйте их.
- Попробуйте слить ветку "feature-branch" в основную ветку с использованием команды `git merge`.
- Разрешите возникшие конфликты при слиянии веток в файле `index.html`, сохраните файл с правильными изменениями.
- Зафиксируйте разрешение конфликтов и завершите процесс слияния.

### Решение 
Создадим и переключимся на новую ветку:
```bash
git checkout -b feature-brach
```
Создадим файл и запишем текст:
```bash
echo "новая строка" > index.html
```
Зафиксируем изменения:
```bash
git add index.html
git commit -m "Task No. 5 - feature-brach commit"
git push origin feature-brach
```
Переключимся на основную ветку, создадим там файл и зафиксируем изменения:
```bash
git checkout main
echo "новая строка 2" > index.html
git add index.html README.md
git commit -m "Task No. 5 - main commit"
git push origin main
```
Пробуем слить ветки с помощью `git merge feature-brach`:
```bash
Auto-merging index.html
CONFLICT (add/add): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```
Файл `index.html` содержит два варианта строки, обернутые специальными служебными скобками.
Сохраним обе строки, файл `index.html` теперь выглядит так:
```
новая строка 2
новая строка
```
И зафиксируем:
```
git add index.html
git commit -m "MERGE!!!!"
git push
```