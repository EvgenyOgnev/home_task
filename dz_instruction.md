# Инструкция для работы с Git и удалёнными репозиториями

## Что такое Git?
Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.
## Подготовка репозитория
Для создание репозитория необходимо выполнить команду *git init*  в папке с репозиторием и у Вас создаться репозиторий (появится скрытая папка .git)

## Создание коммитов

### Git add
Для добавления измений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите *git add <имя файла>*

### Просмотр состояния репозитория
Для того, чтобы посмотреть состояние репозитория используется команда *git status*. Для этого необходимо в папке с репозиторием написать *git status*, и Вы увидите были ли измения в файлах, или их не было.

### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду *git commit*. Выполняется она так: *git commit -m "<сообщение к коммиту>*. Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

## Перемещение между сохранениями
Для того, чтобы перемещаться между коммитами, используется команда *git checkout*. Используется она в папке с пепозиторием следующим образом: *git checkout <номер коммита>*

## Журнал изменений
Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда *git log*. Для этого достаточно выполнить команду *git log* в папке с репозиторием

## Ветки в Git

### Создание ветки

Для того, чтобы создать ветку, используется команда *git branch*. Делается это следующим образом в папке с репозиторием: *git branch <название новой ветки>*

## Слияние веток

Для того чтобы дабавить ветку в текущую ветку используется команда *git merge <name branch>*

## Удаление веток
Для удаления ветки ввести команду "git branch -d 'name branch'"

## Как получить помощь?
Если вам нужна помощь при использовании Git, есть три способа открыть страницу руководства по любой команде Git:
```
    $ git help <команда>
    $ git <команда> --help
    $ man git-<команда>
```
Например, так можно открыть руководство по команде **git config**
```
$ git help config
```
Если вам нужна персональная помощь, вы можете попытаться поискать её по адресу <https://freenode.net>

Если вам нужно посмотреть только список опций, вы можете использовать опцию -h для вывода краткой инструкции по использованию:

```
$ git add -h
usage: git add [<options>] [--] <pathspec>...

  -n, --dry-run dry run
  -v, --verbose be verbose
  -i, --interactive interactive picking
  -p, --patch select hunks interactively
  -e, --edit edit current diff and apply
  -f, --force allow adding otherwise ignored files
  -u, --update update tracked files
  --renormalize renormalize EOL of tracked files (implies -u)
  -N, --intent-to-add record only the fact that the path will be added later
  -A, --all add changes from all tracked and untracked files
  --ignore-removal ignore paths removed in the working tree (same as --no-all)
  --refresh don't add, only refresh the index
  --ignore-errors just skip files which cannot be added because of errors
  --ignore-missing check if - even missing - files are ignored in dry run
  --chmod (+|-)x override the executable bit of the listed files
```

Вся книга __Pro Git__, написанная *Скоттом Чаконом и Беном Штраубом*, доступна здесь:<https://git-scm.com/book/ru/v2>

![Книга Pro Gir](Pro_Git.jpg)




