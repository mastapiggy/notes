# Basic Git GitHub workflow

1. Cloning Repository from GitHub
2. Create new branch and start working on it
3. Edit files locally
4. Review and commit changes

-----

## Cloning Repository from GitHub

Clone repo using ssh-keys or https. After that enter directory where it got saved.

| ssh-keys | https |
| :-----: | :-----: |
| `git clone git@github.com:m4testingaccount/mydemorepo.git` | `git clone https://github.com/m4testingaccount/mydemorepo.git` |
| ----- | ----- |

## Create new branch and start working on it

There are 2 ways to create a branch  
### First way is to create a branch and with `checkout` switch to it

```sh
git branch my-new-branch
```

and after that switch to newly created branch

```sh
git checkout my-new-branch
```

### Second way

This command creates a new branch and immediately checks it out.

```sh
git checkout -b my-new-branch
```












