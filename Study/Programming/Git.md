## Commands

### init

При помощи команды `git init` создается пустой репозиторий:

```shell
git init
# Initialized empty Git repository in /path/to/repository/.git/
```

### status

При помощи команды `git status` можно узнать текущее состояние репозитория

```shell
touch readme.md
git status
# On branch main
#
# No commits yet
#
# Untracked files:
#   readme.md
```

### add

При помощи команды `gid add` можно добавить в отслеживаемые файлы

```shell
git add readme.md
git status
# On branch main
#
# No commits yet
#
# Change to be commited:
#   readme.md
```

### commit

При помощи команды `git commit` можно зафиксировать текущее состояние репозитория. После вызова данной команды откроется IDE или консольный редактор текста, в котором нужно будет написать сообщение фиксации (обычно пишут самую главную суть фиксации, например, `added readme.md`).

```shell
git commit
# [main (root-commit) <commit id>] added readme.md
# 1 file changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 readme.md
```

Также есть более упрощенный вариант данной последовательности. При помощи флага `m` можно сразу написать сообщение, которое описывает фиксацию статуса репозитория.

```shell
git commit -m [commit message]
# [main (root-commit) <commit id>] [commit message]
# 1 file changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 readme.md
```

### log

При помощи команды `git log` можно посмотреть историю коммитов репозитория.

```shell
git log
# commit <commit-uuid> (HEAD -> master)
# Author: <author> <email>
# Date: <commit date>
#
#      added readme.md
```

### .gitignore

Чтобы указать какие файлы/директории не отслеживались `git`, нужно создать файл `.gitignore` и записать в него соответствующие файлы/директории.

### branch и checkout

Для создания новой ветви в репозитории используют команду `git branch <name>` или `git checkout -b <name>`. Разница между ними заключается в том, что `git branch` просто создает новую ветвь, в то время как `git checkout -b` создает новую ветвь и переключается текущую на созданную. Все из-за того что изначально `git checkout` предназначена для смены ветви.

```shell
git branch new-branch
```

```shell
git checkout -b new-branch
```

### merge

Для того чтобы объединить состояние одной ветви с другой используется команда `git merge`

```shell
# We're in main branch
git merge new-branch
# Fast-forward
#	index.css  | 0
#	index.html | 0
#	2 files changed, 0 insertions(+), 0 deletions(-)
#	create mode 100644 index.css
#	create mode 100644 index.html
```

Иногда при слиянии происходят конфликты из-за чего не возможно перенести изменения с одной ветки в другую. Для автоматизации

### stash

Если появляется необходимость сменить ветвь, а изменения в текущей еще не достаточны чтобы сделать коммит, можно временно зафиксировать и сохранить текущее состояние репозитория при помощи команды `git stash`. Чтобы достать его нужно использовать `git stash apply`.

```shell
git stash
# Saved working directory and index state WIP on <branch name>: <commit uuid> <commit message>
```
