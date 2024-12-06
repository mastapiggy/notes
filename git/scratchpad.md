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

