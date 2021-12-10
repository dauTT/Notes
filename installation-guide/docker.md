# Docker



### Official guide: &#x20;

### [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

### Check Ubuntu release and make sure is compatible with docker.

```
cat /etc/release
```

### Uninstall old version

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### Install using the convenience script

```
curl -fsSL https://get.docker.com -o get-docker.sh
DRY_RUN=1 sh ./get-docker.sh
sudo sh get-docker.sh
```

### Check docker is install by running

```
sudo docker version
```

### Docker-Compose installation

### Official guide:&#x20;

### [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### Check docker compose is installed properly:

```
docker-compose version
```
