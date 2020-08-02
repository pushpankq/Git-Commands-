# Git Commands

## $git config

You can use it to configure the author's name, email address, file formats and many more to be used with your commits.

```sh
$ git config --global user.name "Pushpank"
$ git config --global user.email "pushpank@gmail.com"
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
