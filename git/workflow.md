# Basic Git GitHub workflow

1. Cloning Repository from GitHub
2. Create new branch and start working on it
3. Edit files locally
4. Review and commit changes
5. Push new branch to GitHub

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

## Edit Files

Just to be sure before editing check on which branch are you working with `git branch`.  
If on a correct one just open, edit and save files. 

## Review and commit changes

First check what was changed with `git status`  
Next step is to stage the changes. Use `git add .` to stage all files and directories.

```sh
git add file1.md file2.md
```

To commit changes use first `-m "text"` as title and second as a more detailed description

```sh
git commit -m "Updated files" -m "What files got updated and why"
```

## Push new branch to GitHub

Push the new branch
The -u option sets origin my-new-branch as the default tracking branch, so next time just use `git push` without arguments.  

```sh
git push -u origin my-new-branch
```

or use without setting up defaults

```sh
git push ....... edit and finish it
```


