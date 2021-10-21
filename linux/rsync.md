# rsync

### Installation

```
app install rsync
```

### Tutorial

{% embed url="https://www.atlantic.net/vps-hosting/how-to-use-rsync-copy-sync-files-servers/#:~:text=Rsync%20is%20a%20great%20way,runs%20on%20a%20specified%20port." %}

{% embed url="https://www.alibabacloud.com/blog/speeding-up-network-file-transfers-with-rsync_594337" %}

### Usage example

```
# example: I am in server xxx, I am pulling /mnt/volume_sfo3_02/orai folder to my folder /root/backup in server xxx
rsync -av root@143.198.155.218:/mnt/volume_sfo3_02/orai   /root/backup
```
