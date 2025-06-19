# Git manual/information  

## Git configuration  

To change the initial branch name to use in all new repos - global config change:  

```
git config --global init.defaultBranch <name>
```

Change the default Git editor to vim

```
git config --global core.editor "vim"
```

To list help how to use git config use: `git config` 

Config file is stored in a local repo directory: `~/project_name/.git/config`  

To list all configurations of git: `git config --list`  

To add local congig use from below. It is section.keyname format:  
`git config --add --local section_name.name Piggy`
`git config --add --local section_name.position Tazzy`
`git config --add --local section_name.value over9000`

To unset a value: `git config --unset section_name.value`

## Starting a local repo and commiting changes  

`git init` to initialize a local repo  

Files in repo can have 3 stages:  
- untracked
- staged which is that is marked for next commit
- commited which is saved to the repo's history

command `git status` shows current state of the repo  

add files to be tracked for changes in the repo with `git add .`

commit changes with 'git commit -m "Description of the commit"'

## Viewing repo's logs

git --no-pager log -n 10

## Viewing commits  

Commits are stores as objects in `.git/objects/21/e1a3tofhash`  
To view it use `git cat-file -p 21abcde` to view a specific object
It will give an output similar to this one:  

```
$ git cat-file -p 21e1a3
tree 5b21d4f16a4b07a6cde5a3242187f6a5a68b060f
author Name Surname <myemail@gmail.com> 1750111097 +0200
committer Name Surname <myemail@gmail.com> 1750111097 +0200
```

Order of viewing is like this:

- cat commit out
- take root directory tree in this case `5b21d4`, cat that and it will give the file:
```
git cat-file -p 5b21d4
100644 blob ef7e93fc61a91deecaa551c4707e4c3049af42c9    contents.md
```
- cat blob hash in this case `git cat-file -p ef7e93` and it will give a content of the initial file:
```
$ git cat-file -p ef7e93
# contents
```

## Branching

All branches heads are stored in local repo in directory: `.git/refs/heads/`.
Use `git cat-file -p <hashvalue>` to see the commit

Change a branch name from master to main use:  

```
git branch -m oldname newname
```

Create a new branch and switch to it:

```
git switch -c new_branch_name
```

To just move from one branch to another use `git switch branch_name`. Old way is to use `git checkout`  

Check on which branch are we: `git branch`  

## Logs  

To check logs use `git log` can be used with a parameter `--decorate=no, full or short`

Short and more compact log: `git log --oneline`  

More visual output showing all branches`git log --graph --oneline --all`

## Merge

To merge other branch to our main one first check the current branch: `git branch`  
git merge other_branch

Minute 1.09.00
