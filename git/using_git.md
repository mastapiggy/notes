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

git
