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
