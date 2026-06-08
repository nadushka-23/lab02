# Отчет по лабораторной работе №2: Работа с системой контроля версий Git
## Часть I. Базовый workflow
### Команды и вывод:
```
Bash
mkdir lab02 && cd lab02
git init
# Вывод: Initialized empty Git repository in /home/nadushka_23/workspace/lab02/.git/

git config --global user.name "nadushka-23"
git config --global user.email "n3370229@gmail.com"

# После создания файлов:
git status
# Вывод: Untracked files: hello.cpp, print.cpp, print.hpp

git add .
git status
# Вывод: Changes to be committed: new file: hello.cpp, print.cpp, print.hpp

git commit -m "init: hello world program"
# Вывод: [master (root-commit) 14bcf05] init: hello world program

git remote add origin https://github.com/nadushka-23/lab02.git
git push -u origin master
# Вывод: * [new branch] master -> master
```
## Часть II. Ветка patch1 и Pull Request
### Команды и вывод:
```
Bash
git checkout -b patch1
# Вывод: Switched to a new branch 'patch1'

# После изменения print.cpp:
git add -A
git status
# Вывод: Changes to be committed: modified: print.cpp

git commit -m "style: remove using namespace std"
# Вывод: [patch1 def86cc] style: remove using namespace std

git push -u origin patch1
# Вывод: * [new branch] patch1 -> patch1
```
## Часть III. Ветка patch2 + Rebase
```
Bash
git checkout -b patch2
git commit -am "style: add comment to hello.cpp"
# Вывод: [patch2 aa653d2] style: add comment to hello.cpp

git fetch origin
git rebase origin/master
# Вывод: CONFLICT (content): Merge conflict in hello.cpp
# error: could not apply aa653d2... style: add comment to hello.cpp

# После ручного редактирования файла hello.cpp:
git add hello.cpp
git rebase --continue
# Вывод: Successfully rebased and updated refs/heads/patch2.

git push -f origin patch2
# Вывод: * [new branch] patch2 -> patch2
```
## Завершение работы
```
Bash
git checkout master
git pull origin master
# Вывод: Updating 14bcf05..aca9054, Fast-forward
```
