# Basic Git GitHub workflow

1. Cloning Repository from GitHub
2. Create new branch and start working on it
3. Edit files locally
4. Review and commit changes
5. Push new branch to GitHub
6. Review on GitHub and create a Pull Request *PR*
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
git push origin my-new-branch
```

## Review on GitHub and create a Pull Request *PR*

On Github repo page in the UI change the branch and verify changes.  
After changes are ok create a Pull Request *PR*.  
Make sure that base branch is `main` and compare branch is `my-new-branch`, add title and descriptionand click `Create pull request`.
Now changes what were done in `my-new-branch` are merged to the `main` branch. Next step is to delete `my-new-branch` and update `main` one locally.  

After everything is checked and merged just delete unused branch on GitHub and on local system.  

## Update local main branch

Change to the `main` branch

```sh
git checkout main
```

Now update `main` branch by pulling it from GitHub repo because changes are merged and `main` branch is actual

```sh
git pull origin main
```

Now local main branch is up to date with branch on GitHub

Optionally remove a branch on local computer

```sh
git branch -d my-new-branch
```
