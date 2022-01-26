# Github

### Check ssh connection

```
ssh -T git@github.com

# Adding your SSH key to the ssh-agent

```

* [https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

### Adding your SSH key to the ssh-agent <a href="#adding-your-ssh-key-to-the-ssh-agent" id="adding-your-ssh-key-to-the-ssh-agent"></a>

```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### Push a repository with a specific privKey

```


# Inside the local repository type
git config --add --local core.sshCommand 'ssh -i <<<PATH_TO_SSH_KEY>>>'

#example
git config --add --local core.sshCommand 'ssh -i  /home/dau/.ssh/id_ed25519'

# The remote repository need to configure accordingly with the corresponding pubKey
# https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account 
```
