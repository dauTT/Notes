# User



### Create a user

```text
sudo useradd -m username
# cd /home/username

# https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/
```

### Change ownership

```text
#Use chown to change ownership and chmod to change rights.

#will change ownership (both user and group) of all files and directories inside of directory and directory itself.
sudo chown -R username:group directory

#will only change the permission of the folder directory but will leave the files and folders inside the directory alone
sudo chown username:group directory

#will only change the permission of the file 
sudo chown username:group fileName
```

### Elevate newuser to sudo privilege

```text
#elevate newuser to sudo privilege
usermod -aG sudo newuser

#Again, if you get an error, run the command with sudo as follows:
sudo usermod -aG sudo newuser
```



