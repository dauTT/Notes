# pbcopy

### Installation reference:

{% embed url="https://coderwall.com/p/oaaqwq/pbcopy-on-ubuntu-linux" %}

```

# Install xclip
sudo apt-get install -y xclip

# Open .bashrc and add an alias

alias pbcopy="xclip -sel clip"

# Execute

source ~/.bashrc

# Now executing pbcopy < ~/.ssh/id_rsa.pub for example will copy your public SSH key to the clipboard

```
