# Configure git on Linux

Git should be installed and to configure Git do this steps:

1. Configure Git with username and email
This will add in home directory file `.gitconfig`

```sh
git config --global user.name "First and Last Name"
git config --global user.email "myemail@gmail.com"
```

2. Generate ssh key

```sh
ssh-keygen -t ed25519 -C "githubaccountemail@address.com"
```

3. Add ssh key to an ssh-agent and public key to the Github account.

```sh
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

4. Test the connection

```sh
ssh -T git@github.com
```

## Configure Git portable in portable Vscode.

If it happens that you need to use only portable versions:

1. Download and unpack Git Portable form official website
2. in VScode go to File -> preferences -> settings type settings. and click edit in settings.json
3. Add this to the end of the file  
```
   "git.path": "C:\\Users\\username\\path\\to\\PortableGit\\bin\\git.exe"
   ```
4. Add path to portable git to Windows path and now can use git directly from powershell or cmd.
