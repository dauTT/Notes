# Systemctl

### List of services

```text
systemctl list-units --type=service
```

### Remove a systemd service

```text
Remove a systemd service

systemctl stop [servicename]
systemctl disable [servicename]
rm /etc/systemd/system/[servicename]
rm /etc/systemd/system/[servicename] # and symlinks that might be related
rm /usr/lib/systemd/system/[servicename] 
rm /usr/lib/systemd/system/[servicename] # and symlinks that might be related
systemctl daemon-reload
systemctl reset-failed
```

### FAQ

#### Issue: No journal files were found

```text
# https://unix.stackexchange.com/questions/288243/why-does-journalctl-say-no-entries
# run 
systemctl restart systemd-journald.service

```



