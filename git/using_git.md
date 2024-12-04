# Using Git and Git commands

## Setup Git Bash on Windows

To start using Git download it from [this website](https://git-scm.com/downloads/win)

Generate ssh keys to authenticate yourself on github:  
It will create a `.ssh` folder in `c:\Users\YOU\.ssh`

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Upload publick key to your GitHub account in `https://github.com/settings/profile` under access and ssh keys.

In Git Bash start ssh agent and add a key

```sh
eval `ssh-agent.exe`
ssh-add c:\Users\me\.ssh\id_ed25519
```

Testing ssh connection

```sh
ssh -T git@github.com
```

---------

## Git commands

Clone repository from GitHub to local computer

```sh
git clone <clone_with_ssh-keys_from_github>
```

Check which branch you are on or how many branches you have:

```sh
git branch
```
Make a new git repo.  
On github create a new empty repository and link it with new local folder/repo  
`git init` will initialize a new local repository

```sh
git init
```

To link local with remote repo

```sh
git remote add origin <git@github.com:user/reponame>
```

Check connectrd remote repositories connected to local  

```sh
git remote -v
```

Push files to remote repo that is already linked with local repo

```sh
git push origin main
```

Check status of your repo

```sh
git status
```

Add files to be included in tracking version

`git add name_of_the_file` or add everything in the directory `git add .`

Commit changes with adding tittle and a description of a changes

```sh
git commit -m "Created some files" -m "More detailed description"
```

Make a new git branch:

```sh
git checkout -b name_of_the_branch
```

Check differences between 2 branches

```sh
git diff name_of_the_branch
```

Change between branches:
```sh
git checkout name_of_the_branch
```

Push to GitHub

```sh
git push --set-upstream origin name_of_the_branch
```

Pull from other branch to the master branch on GitHub.

Pull new merged main branch to your local

```sh
git pull origin main
```

Remove a merged unused branch

```sh
git branch -d name_of_the_branch
```

When a file or files are modified on a local repo there is no need to 'add' them. It is enough to use `-am` option  
```sh
git commit -am "title_of_a_commit" -m "more detailed_description"


When there is updated main branch (staying on a working branch) merge it to the working branch with

```sh
git merge main
```

To see all commits use

```sh
git log
```

To reset commits with all changes use

```sh
git reset --hard <hash_of_the_commit>
```

To revert changes to the 1 before

```sh
git reset HEAD~1
```






