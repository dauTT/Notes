# SSH Key

### Adding a new SSH Key Github

{% embed url="https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account" %}

### SSH Key

```text
Add SSH KEY to vultr /digitalocean
# https://www.vultr.com/docs/how-to-add-and-delete-ssh-keys

# ED25519 
ssh-keygen -t ed25519 -C dautruong@gmail.com
ssh-copy-id -i ~/.ssh/id_ed25519.pub root@xxx.xx.xxxx

# RSA
ssh-keygen -t rsa  -C dautruong@gmail.com

# Copy content
pbcopy < ~/.ssh/id_rsa.pub
 
# Authorized key
./.ssh/authorized_keys

# https://www.vultr.com/docs/how-to-add-and-delete-ssh-keys
# Delete SSH Key
1) SSH to your server.
2) Edit ~/.ssh/authorized_keys.
3) Remove the line containing your key.
4) Save and exit.
```

### Disable password authentication

```text
sudo nano /etc/ssh/sshd_config

# Change to yes to disable tunnelled clear text passwords
PasswordAuthentication yes

# Reload your SSH configurations
sudo service sshd reload
```

### Start / Stop ssh-agent

```text
# stop
eval "$(ssh-agent -k)"

#start
eval "$(ssh-agent -s)"

```



