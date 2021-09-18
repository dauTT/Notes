# Scripts

### Intall s3cmd

```text
sudo apt update
sudo apt install s3cmd
```

### Config

```text
s3cmd --configure


#example

Access Key: XXXXXXXXX
  Secret Key: YYYYYYYYYYYYYYYYYYYYYY
  Default Region: sfo3
  S3 Endpoint: sfo3.digitaloceanspaces.com
  DNS-style bucket+hostname:port template for accessing a bucket: spacename.sfo3.digitaloceanspaces.com
  Encryption password: 108108108
  Path to GPG program: /usr/bin/gpg
  Use HTTPS protocol: True
  HTTP Proxy server name: 
  HTTP Proxy server port: 0
  
  
  # a config file will be save under
  ~/.s3cfg
  
```

### DigitalOcean script:

{% embed url="https://www.digitalocean.com/community/tutorials/how-to-automate-backups-digitalocean-spaces" %}



```text
#!/bin/bash
DATETIME=`date +%y%m%d-%H_%M_%S`
SRC=$1
DST=$2
GIVENNAME=$3
showhelp(){
        echo "\n\n############################################"
        echo "# bkupscript.sh                            #"
        echo "############################################"
        echo "\nThis script will backup files/folders into a single compressed file and will store it in the current folder."
        echo "In order to work, this script needs the following three parameters in the listed order: "
        echo "\t- The full path for the folder or file you want to backup."
        echo "\t- The name of the Space where you want to store the backup at (not the url, just the name)."
        echo "\t- The name for the backup file (timestamp will be added to the beginning of the filename)\n"
        echo "Example: sh bkupscript.sh ./testdir testSpace backupdata\n"
}
tarandzip(){
    echo "\n##### Gathering files #####\n"
    if tar -czvf $GIVENNAME-$DATETIME.tar.gz $SRC; then
        echo "\n##### Done gathering files #####\n"
        return 0
    else
        echo "\n##### Failed to gather files #####\n"
        return 1
    fi
}
movetoSpace(){
    echo "\n##### MOVING TO SPACE #####\n"
    if s3cmd put $GIVENNAME-$DATETIME.tar.gz s3://$DST; then
        echo "\n##### Done moving files to s3://"$DST" #####\n"
        return 0
    else
        echo "\n##### Failed to move files to the Space #####\n"
        return 1
    fi
}
if [ ! -z "$GIVENNAME" ]; then
    if tarandzip; then
        movetoSpace
    else
        showhelp
    fi
else
    showhelp
fi
```

### Example using the Script

```text
# source folder = ./backupthis
# spacename = chandrodaya
# destination folder = testBackup

sh BackupScript.sh ./backupthis chandrodaya  testBackup

```

