# Git-Commands

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

