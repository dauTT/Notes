# Useful commands

### List all connection with are open

```text
sudo ss -plunt
```

### Change host name

```text
# Change host name:

1) hostnamectl
2) sudo hostnamectl set-hostname MyNewHostName
3) #Open the /etc/hosts file and change the old hostname to the new one
vi /etc/hosts 
4) check if the following file is available cloud.cfg:
ls -l /etc/cloud/cloud.cfg
5) if not, nothign to do.
6) if yes, edit file cloud.cfg, and set "preserve_hostname: true"
vi /etc/cloud/cloud.cfg
7) verify that the changes are done correctly:
hostnamectl

https://linuxize.com/post/how-to-change-hostname-on-ubuntu-18-04/
```

### Find a name

```text
# find anything which start with .ag-chain-cosmos
find . -name ".ag-chain-cosmos*"
```

### Set Time Zone

```text
timedatectl status
timedatectl list-timezones
sudo timedatectl set-timezone Europe/Zurich
```

