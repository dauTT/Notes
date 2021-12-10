# Ngnx

[how-to-install-nginx-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04#step-5-%E2%80%93-setting-up-server-blocks-\(recommended\))

[how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04)

[Setup Https on Digital Ocean Ubuntu Server (Nginx and Certbot)](https://www.youtube.com/watch?v=r-ljiO\_7MME)

[https://nymtech.net/docs/0.11.0/run-nym-nodes/validators](https://nymtech.net/docs/0.11.0/run-nym-nodes/validators)

```
sudo apt update
sudo apt install nginx

sudo ufw allow 'Nginx Full'
sudo ufw allow  OpenSSH

sudo ufw status

#########################################################
To                         Action      From
--                         ------      ----
Nginx Full                 ALLOW       Anywhere                  
OpenSSH                    ALLOW       Anywhere                  
Nginx Full (v6)            ALLOW       Anywhere (v6)             
OpenSSH (v6)               ALLOW       Anywhere (v6)  
#########################################################


# Create Config file
nano /etc/nginx/conf.d/orai.conf

server {
  listen 80;
  listen [::]:80;
  server_name rpc.orai.chandrodaya.net;

  location / {
    proxy_pass http://134.209.25.201:26657;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header Host $host;
  }
}



# if using a VPS running Ubuntu 20:
sudo apt install python3-certbot-nginx

# otherwise
sudo apt install certbot nginx python3

certbot --nginx -d rpc.orai.chandrodaya.net -m support@chandrodaya.net --agree-tos --noninteractive --redirect

#########################################################
Congratulations! You have successfully enabled https://rpc.orai.chandrodaya.net

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=rpc.orai.chandrodaya.net
#########################################################

# Create Config file
nano /etc/nginx/conf.d/api-orai.conf

server {
  listen 81;
  listen [::]:81;
  server_name api.orai.chandrodaya.net;

  location / {
    proxy_pass http://134.209.25.201:1317;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header Host $host;
  }
}

certbot --nginx -d api.orai.chandrodaya.net -m support@chandrodaya.net --agree-tos --noninteractive --redirect
```
