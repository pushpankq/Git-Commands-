# Git Commands



![git-flow-768x513](https://user-images.githubusercontent.com/14274827/91470661-9d5a8780-e8b2-11ea-9ccb-0d813d2e35d1.png)



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

Adding Remote Repositories

```sh
$ git remote add pb https://github.com/paulboone/ticgit
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

List all remote or local branches

 ```sh
$ git branch -a
```

## $git push

After committing your changes, the next thing you want to do is send your changes to the remote server. Git push uploads your commits to the remote repository.

```sh
$ git push <remote> <branch-name>
```

#### Push all local branches to remote repository

```sh
$ git push —all
```

However, if your branch is newly created, then you also need to upload the branch with the following command:

```sh
$ git push -u origin <branch_name>
```

## $git pull

The git pull command is used to get updates from the remote repo. This command is a combination of git fetch and git merge which means that, when we use git pull, it gets the updates from remote repository (git fetch) and immediately applies the latest changes in your local (git merge).

```sh
$ git pull <branch_name> <remote_URL/remote_name>
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

Merge changes into current branch

```sh
$ git merge <branch_name>
```

## $git stash

To save changes made when they’re not in a state to commit them to a repository. This will store the work and give a clean working directory. For instance, when working on a new feature that’s not complete, but an urgent bug needs attention.

### Store current work with untracked files

```sh
$ git stash -u
```

### Bring stashed work back to the working directory

```sh
$ git stash pop
```

## $git tag

Listing the existing tags in Git is straightforward.

```sh
$ git tag
```

### Creating Tags

Git supports two types of tags: lightweight and annotated.

#### Annotated Tags


```sh
$ git tag -a v1.2 -m "version 1.2"
```

You can see the tag data along with the commit that was tagged by using the git show command:

```sh
$ git show v1.2
```

#### Lightweight Tags

```sh
$ git tag v1.2-lw
```

#### Tagging Later
You can also tag commits after you’ve moved past them. Suppose your commit history looks like this:

```sh
$ git tag -a v1.2 <commit_id>
```

#### Sharing Tags

```sh
$ git push origin v1.2
```

If you have a lot of tags that you want to push up at once, you can also use the --tags option to the git push command. This will transfer all of your tags to the remote server that are not already there.

```sh
$ git push origin --tags
```

#### Deleting Tag

```sh
$ git tag -d v1.2-lw
```

The second (and more intuitive) way to delete a remote tag is with:

```sh
$ git push origin --delete <tagname>
```

#### Checking out Tags

```sh
$ git checkout v2.0.0
```

