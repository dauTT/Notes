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

### Useful cmds

```text
# list all groups
compgen -g

# list all user
compgen -u

# create group 
sudo addgroup <groupname>

# create a user
sudo adduser <username> <groupname>


#Command to show users and their permissions
#For a list of users type:
cat /etc/passwd

# and for a list of groups with the users that belong to each, type:

cat /etc/group
#For access rights, you can use:

sudo find -user USERNAME /LOCATION

```

