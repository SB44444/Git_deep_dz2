**Урок 1. Работа с удалёнными репозиториями.**  
Выберите какой-нибудь проект на изучаемом вами языке программирования,  
с которым вы будете тренироваться работать в Git, и инициализируйте  
в папке этого проекта локальный репозиторий.  
Создайте непустой удалённый репозиторий (например, с файлом README.md)  
с именем, соответствующим имени этого проекта.  
Подключите свой проект к этому удалённому репозиторию и отправьте в него  
код этого проекта. Самостоятельно разрешите конфликты и проблемы,  
если они возникнут при выполнении данного задания  

PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git init  
Initialized empty Git repository in K:/Git/_Git_Pro/Git_deep/Git_deep_dz1/.git/  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1>  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git add *  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git commit -m"git init git readme 1"   
[master (root-commit) 265103f] git init git readme 1  
1 file changed, 10 insertions(+)  
create mode 100644 README.md  

PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git add *  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git commit -m"git init git readme 1 comand"  
[master abcf44f] git init git readme 1 comand  
1 file changed, 9 insertions(+), 1 deletion(-)  
  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git remote add origin   https://github.com/SB44444/Git_deep_dz1.git  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git branch -M master  
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git push -u origin master  
To https://github.com/SB44444/Git_deep_dz1.git   
 ! [rejected]        master -> master (fetch first)  
error: failed to push some refs to 'https://github.com/SB44444/Git_deep_dz1.git'  
hint: Updates were rejected because the remote contains work that you do not  
hint: have locally. This is usually caused by another repository pushing to  
hint: the same ref. If you want to integrate the remote changes, use  
hint: 'git pull' before pushing again.  
hint: See the 'Note about fast-forwards' in 'git push --help' for details. 

PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git remote -v
origin  https://github.com/SB44444/Git_deep_dz1.git (fetch)
origin  https://github.com/SB44444/Git_deep_dz1.git (push)

PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git remote show origin
  HEAD branch: master
  Remote branch:
    master tracked
  Local ref configured for 'git push':
    master pushes to master (local out of date)
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git log origin/master     
commit 2f414c78193761a02c45f647e9bb56bae2f5fb95 (origin/master)
Author: SB44444 <115193888+SB44444@users.noreply.github.com>
Date:   Sat Jan 27 05:51:47 2024 +0300

    Create README.md at github
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git merge origin/master --allow-unrelated-histories        
error: Your local changes to the following files would be overwritten by merge:
        README.md
Please commit your changes or stash them before you merge.
Aborting
Merge with strategy ort failed.
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git commit -m"git init git readme 1 comand fix1"
[master fa2bdc2] git init git readme 1 comand fix1
 1 file changed, 1 insertion(+)
Auto-merging README.md
CONFLICT (add/add): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git add *
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> git commit -m"git init git readme 1 comand fix3"
[master 35a084b] git init git readme 1 comand fix3
PS K:\Git\_Git_Pro\Git_deep\Git_deep_dz1> 

**Урок 2. Работа с изменениями.**  
Домашнее задание  
Данное домашнее задание является продолжением домашнего задания, которое
вы выполняли на предыдущем семинаре в репозитории с собственным проектом
Просмотрите историю коммитов в своём проекте и выберите три случайных
коммита.  
Просмотрите изменения, которые были в них сделаны. Верните эти изменения командой git revert последовательно, чтобы в итоге получилось тоже три коммита. Попробуйте отменить эти три коммита:  

○ Последний — командами git reset --soft и git restore  
○ Предпоследний — командой git reset --mixed и git restore
○ Первый — командой git reset --hard 

git reset --soft README.md # Не затрагивает индексный файл или рабочее дерево, сбрасывает заголовок коммита, оставляет все файлы  подлежащие фиксации.
  
git reset --mixed  README.md # Сбрасывает индекс, измененные файлы сохраняются, но не помечены для фиксации и сообщает о том, что не было обновлено. Это действие по умолчанию, равно git reset README.md
git add .
git commit -m 'changes --mixed' Закомитить изменения

git restore --staged README.md #  Переведёт изменения из индекса в изменённое состояние
git restore --staged README.md # Удалить эти изменения

git revert -n HEAD  # Удалит последний коммит  
git revert HEAD^   # Удалит предпоследний коммит
git revert -54e224d  # Удалит коммит по хешу, выхода из vim :wq
git revert 35a084b --no-edit # Вернет новый коммит без запуска редактора сообщения
  
git reset HEAD~1  # Отменить последний коммит, сохранит файлы  подлежащие фиксации
git reset --hard 35a084b # вернуть репозиторий в состояние коммита с указанным хешем Важно! не соранится работа 
git reset --hard HEAD~1  # Вернет ветку HEAD на первый коммит. Также можно указать певые цифры хеша коммита 54e224d. Удалит все изменения!

git checkout 35a084b  # Вернет файл README.md к указанной версии и сразу добавится в индекс
 
Info:
To set main as the default branch name do:  

$ git config --global init.defaultBranch main  

Checking Your Settings
If you want to check your configuration settings, you can use the git config --list command to list all the settings Git

You may see keys more than once, because Git reads the same key from different files ([path]/etc/gitconfig and ~/.gitconfig, for example). In this case, Git uses the last value for each unique key it sees.

You can also check what Git thinks a specific key’s value is by typing git config <key>:

$ git config user.name new_name  

Зафиксировать все свои изменения и переключиться на ветку master:  

$ git checkout master  
Switched to branch 'master'  

Создадать новую ветку, реализуем исправление.

$ git checkout -b hotfix  
Switched to a new branch 'hotfix'  
$ vim index.html  
$ git commit -a -m 'Fix broken email address'    

Выполнить слияние ветки hotfix с веткой master для включения изменений в продукт.  
командой git merge:  

$ git checkout master  
$ git merge hotfix  

https://github.com/SB44444/Git_deep_dz2