# Git Commands

## $git config

You can use it to configure the author's name, email address, file formats and many more to be used with your commits.

```sh
$ git config --global user.name "Pushpank"
$ git config --global user.email "pushpank@gmail.com"
```

Remove github user

```sh
$ git credential-manager delete https://github.com
```

## $git init

Using this command you make it sure that your git repository is initialized and creates the initial .git directory in a new or in an existing project. The output will be the following:
Initialized empty Git repository in /path/.git/
```sh
$ git init
```

###### Note. You can undo a $git init with rm -rf .git.

## $git clone <path>

This creates a working copy of a Git repository from a remote source to your local repository. This is the first command you want to use when you are cloning a Git repository.

```sh
$ git clone git@github:user/repository.git
```

###### Note. You can clone one specific branch at a time:

```sh
$ git clone -b branch_name git@github:user/repository.git
```

## $git add

Add one or more files in your working directory to your index.

To add a single file:

```sh
$ git add <filename>
```

To add everything at once:

```sh
$ git add .
```

## $git commit

Take all your changes written in the index to the HEAD branch with a -m message.

```sh
$ git commit -m "Initial Commit"
```

## $git status

It shows you the status difference between an index and working directory files. Lists the files you've changed, untracked because they are only in your working directory and staged since they are ready to be committed.

```sh
$ git status
```
## $git remote

Shows all the remote versions of your repository.

```sh
$ git remote
origin
```

## $git checkout

You can switch from an existing branch to another one 

```sh
$ git checkout <branch_name>
```

You can create a new branch and switch to it

```sh
$ git checkout -b <branch_name>
```

## $git branch

With this, you can simply list all existing branches, including remote branches by using -a or create a new branch if a branch name is provided.

```sh
$ git branch
* master
```

```sh
$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
```

 Delete a branch
 
 ```sh
$ git branch -d <branch_name>
```

## $git push

After committing your changes, the next thing you want to do is send your changes to the remote server. Git push uploads your commits to the remote repository.

```sh
$ git push <remote> <branch-name>
```

However, if your branch is newly created, then you also need to upload the branch with the following command:

```sh
$ git push -u origin <branch_name>
```

## $git pull

The git pull command is used to get updates from the remote repo. This command is a combination of git fetch and git merge which means that, when we use git pull, it gets the updates from remote repository (git fetch) and immediately applies the latest changes in your local (git merge).

```sh
$ git pull <remote>
```
###### Note. This operation may cause conflicts that you need to solve manually.


## $git diff

Show changes between your working tree and the index, between two branches, or changes between two files on disk.

```sh
$ git diff <source_branch> <target_branch>
```

## $git log

It shows a listing of commits on a branch with corresponding details.

```sh
$ git diff <source_branch> <target_branch>
commit 35e16d379a466012216c2263592181f0bab99f36 (HEAD -> new, origin/master, origin/HEAD, master)
Author: pushpankq@gmail.com <pushpankq@gmail.com>
Date:   Sun Aug 2 12:18:42 2020 +0530

    Second commit

commit 0a6c41d8d223d7d268d378354f35d5c19008da23
Merge: fc88733 641b9cf
Author: kumar_1994 <31385878+Kumar@users.noreply.github.com>
Date:   Sun Aug 2 12:12:51 2020 +0530

    Merge pull request #1 from kumar/dev
    
    added text data

commit 641b9cf72ed3a2b61a4ef805b9368b690983a610 (origin/dev)
Author: kumar_1994 <kumar@gmail.com>
Date:   Sun Aug 2 12:06:22 2020 +0530

    added text data
```

## $git revert

Sometimes we need to undo the changes that we've made. There are various ways to undo our changes locally or remotely (depends on what we need), but we must carefully use these commands to avoid unwanted deletions.

A safer way that we can undo our commits is by using git revert. To see our commit history, first we need to use git log -- oneline:

```sh
$ git log --oneline 
35e16d3 (HEAD -> new, origin/master, origin/HEAD, master) Second commit
0a6c41d Merge pull request #1 from Kumar/dev
641b9cf (origin/dev) added text data
fc88733 initial commit
```

Then we just need to specify the hash code next to our commit that we would like to undo:

```sh
$ git revert 35e16d3 
```

After this, you will see a screen like below - just press shift + q to exit:

```sh
hint: Waiting for your editor to close the file... 
Revert "changes"

This reverts commit 7c3da500c13ecd1149e767dc1924fb85c98e920d.



# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch new
# Changes to be committed:
#       modified:   NewText.txt
#
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"~/TestingRepo/.git/COMMIT_EDITMSG" 11L, 289C
```

The advantage of using git revert is that it doesn't touch the commit history. This means that you can still see all of the commits in your history, even the reverted ones. 

Another safety measure here is that everything happens in our local system unless we push them to the remote repo. That's why git revert is safer to use and is the preferred way to undo our commits.

## $git merge

