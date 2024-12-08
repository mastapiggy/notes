# workflow from the book

take a local directory that is currently not under version control, and turn it into a Git repository

mkdir your-repository  
cd your-repository/  

Work on files and get them ready to be versioned

`git init` will initiate Git repository skeleton

### Steps of version controlling

Start version-controlling existing files   
begin tracking those files - `git add .`  
Whenever creating a file or modifying an existing one to stage them always use `git add .` or `git add exact_file`  
and do an initial commit - `git commit -m 'Title_of_a_commit' -m 'Description_of_a_commit'  
Checking status of your local files - `git status`  

Skipping the Staging Area  
To skip the staging area use `git commit -a -m 'Title_of_a_commit'` - this command makes Git automatically stage every file that is already tracked before doing the commit skipping `git add file_name`.  





### Removing Files and Moving Files
Do notes from bottom of this page.
https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository



### Ignoring Files

Create a file named `.gitignore` and it content is as follows:

Here is an example .gitignore file:

```
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```





















-----
# Git Remotes

1. Check Current Remotes
Before making changes, it's a good idea to verify the existing remotes. Use:

``git remote -v`

2. Remove the Upstream Remote
If you see an upstream remote that you no longer need, remove it with:

`git remote remove upstream`

3. If you accidentally remove the wrong remote, you can re-add it using:

`git remote add <name> <URL>`

-----------------

# Starting from creating a repo locally and uploading to GitHub
If you have a project directory that is currently not under version control and you want to start controlling it with Git, you first need to go to that project’s directory.  
mkdir your-repository  
cd your-repository/  
echo "# your-repository" >> README.md  
git init  
git add README.md  
git status  
git commit -m "first commit" -m "Just a description"  
git remote add origin git@github.com:m4testingaccount/your-repository.git  
git remote -v  
git push origin main  

8. Pulling and Pushing Changes  
Pull latest changes:  

git pull origin main  

Push local commits:  
git push origin main

-----

Set up a remote to the original repository (upstream), so you can fetch any updates when owner makes changes:

bash
Copy code
git remote add upstream https://github.com/mastapiggy/demo-repo.git






























