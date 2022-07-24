# Инструкция для работы с Git и удалёнными репозиториями

## Что такое Git?
Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.

У Git есть три основных состояния, в которых могут находиться ваши файлы: 
1. изменён (modified),
> К изменённым относятся файлы, которые поменялись, но ещё не были зафиксированы.
2. индексирован (staged),
> Индексированный — это изменённый файл в его текущей версии, отмеченный для
включения в следующий коммит.
3. зафиксирован (committed).
> Зафиксированный значит, что файл уже сохранён в вашей локальной базе


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

Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда *`git log`*. Для этого достаточно выполнить команду *`git log`* в папке с репозиторием. 
>По умолчанию (без аргументов) *`git log`* перечисляет коммиты, сделанные в репозитории в обратном к хронологическому порядке — последние коммиты находятся вверху.

Команда *`git log`* имеет очень большое количество опций для поиска коммитов по разным критериям.

Одним из самых полезных аргументов является *`-p`* или *`--patch`*, который показывает разницу (выводит патч), внесенную в каждый коммит. Так же вы можете ограничить количество записей в выводе команды; используйте параметр *`-2`* для вывода только двух записей:
```
$ git log -p -2
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number

diff --git a/Rakefile b/Rakefile
index a874b73..8f94139 100644
--- a/Rakefile
+++ b/Rakefile
@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
 spec = Gem::Specification.new do |s|
     s.platform  =   Gem::Platform::RUBY
     s.name      =   "simplegit"
-    s.version   =   "0.1.0"
+    s.version   =   "0.1.1"
     s.author    =   "Scott Chacon"
     s.email     =   "schacon@gee-mail.com"
     s.summary   =   "A simple gem for using Git in Ruby code."

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    Remove unnecessary test

diff --git a/lib/simplegit.rb b/lib/simplegit.rb
index a0a60ae..47c6340 100644
--- a/lib/simplegit.rb
+++ b/lib/simplegit.rb
@@ -18,8 +18,3 @@ class SimpleGit
     end

 end
-
-if $0 == __FILE__
-  git = SimpleGit.new
-  puts git.show
-end
```
Опции *`oneline`* и *`format`* являются особенно полезными с опцией *`--graph`* команды *`log`*. С этой опцией вы сможете увидеть небольшой граф в формате ASCII, который показывает текущую ветку и историю слияний:
```
$ git log --pretty=format:"%h %s" --graph
* 2d3acf9 Ignore errors from SIGCHLD on trap
*  5e3ee11 Merge branch 'master' of git://github.com/dustin/grit
|\
| * 420eac9 Add method for getting the current branch
* | 30e367c Timeout code and tests
* | 5a09431 Add timeout protection to grit
* | e1193f8 Support for heads with slashes in them
|/
* d6016bc Require time for xmlschema
*  11d191e Merge branch 'defunkt' into local
```

## Ветки в Git

### Создание ветки

По умолчанию, имя основной ветки в Git — 
`master`.
Для того, чтобы создать новую ветку, используется команда `git branch`. Делается это следующим образом в папке с репозиторием: `git branch <название новой ветки>`

### Переключение веток

Для переключения на существующую ветку выполните команду `git checkout`. Давайте переключимся на ветку `testing`:
```
$ git checkout testing
```
В результате указатель `HEAD` переместится на ветку `testing`.

### Слияние веток

Для того чтобы дабавить ветку в текущую ветку используется команда *git merge <name branch>*

### Удаление веток

Для удаления ветки ввести команду *`git branch -d name_branch`*

Команда `git branch` делает несколько больше, чем просто создаёт и удаляет ветки. При запуске без параметров, вы получите простой список имеющихся у вас веток:
```
$ git branch
  iss53
* master
  testing
```
Обратите внимание на символ `*`, стоящий перед веткой `master`: он указывает на ветку, на которой вы находитесь в настоящий момент (т. е. ветку, на которую указывает `HEAD`). Это означает, что если вы сейчас сделаете коммит, ветка `master` переместится вперёд в соответствии с вашими последними изменениями. Чтобы посмотреть последний коммит на каждой из веток, выполните команду `git branch -v`:
```
$ git branch -v
  iss53   93b412c Fix javascript issue
* master  7a98805 Merge branch 'iss53'
  testing 782fd34 Add scott to the author list in the readme
```
Опции `--merged` и `--no-merged` могут отфильтровать этот список для вывода только тех веток, которые слиты или ещё не слиты в текущую ветку. Чтобы посмотреть те ветки, которые вы уже слили с текущей, можете выполнить команду `git branch --merged`:
```
$ git branch --merged
  iss53
* master
```
Ветка `iss53` присутствует в этом списке потому что вы ранее слили её в `master`. Те ветки из этого списка, перед которыми нет символа `*`, можно смело удалять командой `git branch -d`.

Чтобы увидеть все ветки, содержащие наработки, которые вы пока ещё не слили в текущую ветку, выполните команду `git branch --no-merged`:
```
$ git branch --no-merged
  testing
```
Вы увидите оставшуюся ветку. Так как она содержит ещё не слитые наработки, попытка удалить её командой `git branch -d` приведёт к ошибке:
```
$ git branch -d testing
error: The branch 'testing' is not fully merged.
If you are sure you want to delete it, run 'git branch -D testing'.
```

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




