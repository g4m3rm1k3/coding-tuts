# Version Control System
Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.



## git status
```console
git status
```

## git init
```console
git init
```

## staging
```console
git add filename.txt
```
git status shows
```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   characters.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        outline.txt
```

## long commit message
leave off the -m "" message to use the default editor
```shell
git commit
```
![[Pasted image 20230819130610.png]]
## recover a file from previous commit
```shell
git restore --source=335f7 --worktree --staged MoodBoard/goodbye.py
```
## git --help
```console
git add --help
```
opens html page apparently
## Where is git stored?
```shell
type git
```
output:
```bash
$ type git
git is hashed (/mingw64/bin/git)
```
check version from location
```shell
$ /mingw64/bin/git version
git version 2.41.0.windows.3
```
## Posh-git (PowerShell)
install posh git
```powershell
Install-Module posh-git -Scope Currentuser -Force
```
or maybe?
```powershell
PowerShellGet\Install-Module posh-git -Scope CurrentUser -Force
```
to update
```powershell
PowerShellGet\Update-Module posh-git
```
instgall via chocolatey
```powershell
choco install poshgit
```
import module posh-git
```powershell
Import-Module posh-git
```
Add posh git to powershell profile
```powershell
Add-PoshGitToProfile -Force
```
## rename master branch
```shell
git config --global init.defaultBranch main
```
changed the branch name from master to main

## check global configurations
```shell
➜ git config --global --list
core.editor="C:\Users\g4m3r\AppData\Local\Programs\Microsoft VS Code\bin\code" --wait
user.email=g4m3rm1k3@hotmail.com
user.name=Michael McLean
init.defaultbranch=main
```

## git reset
```shell
git reset
```
removes all files from git add .

# Branch
create a new branch
```shell
git branch <branchname>
```
display branches in repo
```shell
git branch -a
```

```shell
  feature
* main
```
chechout branch
```shell
git checkout <branchname>
```
now running git branch -a shows
```shell
➜ git branch -a       
* feature
  main
  ```
  ![[Pasted image 20230820053702.png]]
  ## Merge
  ```shell
  git merge <branchname> -m "commit messsage"
```
## git log
```shell
git log --oneline
```
output
```shell
➜ git log --oneline
7d747f5 (HEAD -> main) Merge feature branch into main
912dd65 add pinch of salt to vanilla ingredients
fbc2737 (feature) add new step to frozen mocha
19ed07e Change whole milk to almond milk
d41e0bf Fixed Caramel file header
3d97e98 Add hot beverages, iced beverages, and syrups
```
show how branches merged
```shell
➜ git log --oneline --graph
*   7d747f5 (HEAD -> main) Merge feature branch into main
|\
| * fbc2737 (feature) add new step to frozen mocha
| * 19ed07e Change whole milk to almond milk
* | 912dd65 add pinch of salt to vanilla ingredients
|/
* d41e0bf Fixed Caramel file header
* 3d97e98 Add hot beverages, iced beverages, and syrups
```
notice (feature) is showing we will delete the feature branch in the next step
## delete branch
```shell
git branch -d <branchname>
```
output
```shell
➜ git branch -d feature
Deleted branch feature (was fbc2737).
```
```shell
➜ git log --oneline --graph
*   7d747f5 (HEAD -> main) Merge feature branch into main
|\
| * fbc2737 add new step to frozen mocha
| * 19ed07e Change whole milk to almond milk
* | 912dd65 add pinch of salt to vanilla ingredients
|/
* d41e0bf Fixed Caramel file header
* 3d97e98 Add hot beverages, iced beverages, and syrups
```
notice the (feature) branch is no longer showing 
```shell
➜ git branch -a
* main
```
## add remote
```shell
git remote add <any name> <url>
```
example adding remote to github and naming it origin
```shell
git remote add origin https://github.com/g4m3rm1k3/coffee-shop-recipes.git
```

show remote
```shell
git remote -v
```
## git push
-u : upstream
used the first time to tell the remote repository to create tracking
next time git push
## git pull
```shell
git pull
```
pulls from the main 

git fetch
```
git fetch 
git status
```
shows the differences between origin and local
## git amend
```shell
git commit --amend
```
amend last commit message
will add any newly staged files to commit

![[Pasted image 20230820075750.png]]
git reset --soft
```shell
g4m3r@LAPTOP-AJ5LV3I9 MINGW64 ~/Documents/newFolder/coffee-shop-recipes (main)
$ git log --oneline
c8c5eaa (HEAD -> main) adding file 7
7fad959 adding file 6
9eb08f0 adding file 5
818c47c adding file 4
3ff7a71 adding file 3
932b69e adding file 2
bf49175 adding file 1
ae20c8a (origin/main, origin/HEAD) Update README.md
e76c893 Update README.md
ea32018 Initial commit

g4m3r@LAPTOP-AJ5LV3I9 MINGW64 ~/Documents/newFolder/coffee-shop-recipes (main)
$ git reset --soft HEAD~2

g4m3r@LAPTOP-AJ5LV3I9 MINGW64 ~/Documents/newFolder/coffee-shop-recipes (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 5 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   file6.md
        new file:   file7.md
```
git reset --hard
```shell
g4m3r@LAPTOP-AJ5LV3I9 MINGW64 ~/Documents/newFolder/coffee-shop-recipes (main)
$ git reset --hard 818c47c
HEAD is now at 818c47c adding file 4

g4m3r@LAPTOP-AJ5LV3I9 MINGW64 ~/Documents/newFolder/coffee-shop-recipes (main)
$ git log --oneline
818c47c (HEAD -> main) adding file 4
3ff7a71 adding file 3
932b69e adding file 2
bf49175 adding file 1
ae20c8a (origin/main, origin/HEAD) Update README.md
e76c893 Update README.md
ea32018 Initial commit

g4m3r@LAPTOP-AJ5LV3I9 MINGW64 ~/Documents/newFolder/coffee-shop-recipes (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 4 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
powershell log
```powershell
   07:52:37  coffee-shop-recipes  main   4ms 
```
## git reflog
only local
limited time (90days)
```powershell
➜ git reflog
818c47c (HEAD -> main) HEAD@{0}: reset: moving to 818c47c
b33dd36 HEAD@{1}: commit: adding file 7
e545001 HEAD@{2}: commit: adding file 6
9eb08f0 HEAD@{3}: reset: moving to HEAD~1
b19c8d9 HEAD@{4}: commit: adding files 6 and 7
9eb08f0 HEAD@{5}: reset: moving to HEAD~2
c8c5eaa HEAD@{6}: commit (amend): adding file 7
8113c9a HEAD@{7}: commit: adding file 8
7fad959 HEAD@{8}: commit: adding file 6
9eb08f0 HEAD@{9}: commit: adding file 5
818c47c (HEAD -> main) HEAD@{10}: commit: adding file 4
3ff7a71 HEAD@{11}: commit: adding file 3
932b69e HEAD@{12}: commit: adding file 2
bf49175 HEAD@{13}: commit: adding file 1
ae20c8a (origin/main, origin/HEAD) HEAD@{14}: clone: from https://github.com/a-a-ron/coffee-shop-recipes
```
## cherry-pick
```powershell
$ git cherry-pick 9eb08f0
[main 3e80d10] adding file 5
 Date: Sun Aug 20 07:54:03 2023 -0400
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file5.md
```
notice the id in the cherry pick line is from the file5 commit of reflog
