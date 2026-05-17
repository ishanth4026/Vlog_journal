
# Basics
---
- Git is used to maintain your code with timelines, it's like a respawn point were we can go back to if something went wrong, and once we completed a feature or few lines of code we can set a new respawn point.
- Github is same as git but instead of the code stored in your computer it is stored in cloud
#### CMDS
- To open a file in file explorer `start .git`
- To create empty repository `git init`
- To add files `git add name`
- To commit `git commit`
- To give status `git status`
- To get Short status `git status -s`
- To make directory(folder) `mkdir name`
- To remove a file `git rm name`
- To list files `git ls-files`
- To rename files `git mv oldname newname`
- To remove files only from staging area `git rm --cached -r name`
- To see what changes that have to be commited `git diff --staged` , to see in editor use `git difftool --staged`(without --staged it will show only changes)
- To so log `git log`  we can use `--oneline` to get it in one liners(press 'Q' to exit and 'space' to go to next page)
- To remove the change from the staging are use `git restore --staged name` (it will restore it to the last commit)
- To remove the changes from working directory `git restore name` (it restores to the last copy of the staged one)
# Points
---
#### Git add
- While using git add, we need to use it when we need to add the file to the staging area, then we use commit to upload it to the server
- we can use git add *.txt to upload all files with the extension .txt or just us . to upload all files
- Even when we are deleting something we need to use git add to update it to the staging area

#### Git commit
- If we use just git commit it will open your default editor and in the first line we type our short message, give a line break and then type your long message(around 80 characters).
- If you want just a short message use `git commit -m "message"`
- Don't commit a single time for two different problems, always commit for one problem then move on to another.
- in `git commit -a -m` the -a represents all and -m message, it can also be written as `-am`.

#### Git remove
- If you use `rm name` instead of `git rm name`, you need to also perform `git add name` or else it won't update the staging area. If used with git no need to do it

#### Git rename
- If you use just `mv oldname newname` we need to perform commands `git add oldname` & `git add newname` then only it will update the staging area. If used with git no need to do this

#### To ignore files
- To ignore a file or folder we need to add it to .gitignore, we can do that by using `echo name/ > .gitignore` or just type `code .gitignore` and add the file and folder names inside it and save.
- If the file/folder you want to ignore is in staging are then the git won't ignore it, you have to remove the file/folder from staging area and commit the change.
- Error - While trying to ignore a file, it still shows in the untracked files, to fix it open the editor and change UTF - 16 LE to UTF-8

#### visual diff tools
- Error - When in use diff it only showed file name, not what changed, to fix it I was using `git name >> text` instead of `git text >> name`.

#### Viewing a commit
- To look at a specific commit `git show key`, the key is a series of strings and numbers that will be generated for each and every cmd
- We can also use `git show head~1` which loads the commit that is next of the head -> master


# Intermediate
Using branches, pull, push, merge, merge conflicts and more

main -> branch name
origin -> default name given to the repo you are working
commit_hash -> the series of letters and number generated for each commit
#### CMDS
- To create branch `git checkout -b name`
- To check existing branches `git branch`
- To rename branch `git branch -m newname` (renames the branch you are currently working in)
- To select branch `branch checkout name`
- To delete branch `git branch -d name`
- To merge branch `git merge name` (name of the branch that the branch you are working will be merged)
- To clone a repo from GitHub `git clone link`
- To upload from computer to GitHub `git push origin main` (use -u to create a shortcut if you are uploading to same branch for long time)
- To create a repo `git init`
- To upload a repo from comp to GitHub `git remote add orignin link`(before uploading create a repo in GitHub for it)
- To see your remote repo `git remote`
- To get changes from GitHub `git pull orignin main`
- To revert changes to previous commit `git reset commit_hash` (to show in editor also use --hard)


#### Fork
Rough copy of the repo, useful if you want to copy a open source repo to solve or play around.

#### Merge conflicts
During merge conflicts the code will be separated like:

<<<<<< HEAD -> code from another branch

   code
========= -> separation
>>>> Branch -> code from another branch
	code
it will show the code from both branches and ask which one to choose

#### Tips
- For adding only one change to staging area use `-p`
- Always commit for a single feature/error/reason for cleaner reading of commits logs