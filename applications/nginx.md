# Nginx

[how-to-install-nginx-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04#step-5-%E2%80%93-setting-up-server-blocks-\(recommended\))

[how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-let-s-encrypt-with-nginx-server-blocks-on-ubuntu-16-04)

[Setup Https on Digital Ocean Ubuntu Server (Nginx and Certbot)](https://www.youtube.com/watch?v=r-ljiO\_7MME)

[https://nymtech.net/docs/0.11.0/run-nym-nodes/validators](https://nymtech.net/docs/0.11.0/run-nym-nodes/validators)

[nginx-reverse-proxy-error14077438ssl-ssl-do-handshake-failed](https://coderedirect.com/questions/503281/nginx-reverse-proxy-error14077438ssl-ssl-do-handshake-failed)

#### 1) Nginx server

![](<../.gitbook/assets/image (9).png>)

#### 2) Subdomain creation

![](<../.gitbook/assets/image (11).png>)

#### 3) Configure Nginx



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
# sudo apt install certbot nginx python3

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

# Create Config file
nano /etc/nginx/conf.d/api-juno.conf

server {
  listen 82;
  listen [::]:82;

  server_name  api.juno.chandrodaya.net  ;
  
  location / {
   
    proxy_pass https://api-juno.nodes.guru ; 
    proxy_ssl_server_name on;

    if ($request_method = 'OPTIONS') {
        add_header 'Access-Control-Allow-Origin' '*';
        #
        # Om nom nom cookies
        #
        add_header 'Access-Control-Allow-Credentials' 'true';
        add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
        #
        # Custom headers and headers various browsers *should* be OK with but aren't
        #
        add_header 'Access-Control-Allow-Headers' 'DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type';
        #
        # Tell client that this pre-flight info is valid for 20 days
        #
        add_header 'Access-Control-Max-Age' 1728000;
        add_header 'Content-Type' 'text/plain charset=UTF-8';
        add_header 'Content-Length' 0;
        return 204;
     }
     if ($request_method = 'POST') {
        add_header 'Access-Control-Allow-Origin' '*';
        add_header 'Access-Control-Allow-Credentials' 'true';
        add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
        add_header 'Access-Control-Allow-Headers' 'DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type';
     }
     if ($request_method = 'GET') {
        add_header 'Access-Control-Allow-Origin' '*';
        add_header 'Access-Control-Allow-Credentials' 'true';
        add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
        add_header 'Access-Control-Allow-Headers' 'DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type';
     }

  }

    # following lines will be added by Certbot
    #listen 443 ssl; # managed by Certbot
    #ssl_certificate /etc/letsencrypt/live/api.juno.chandrodaya.net/fullchain.pem; # managed by Certbot
    #ssl_certificate_key /etc/letsencrypt/live/api.juno.chandrodaya.net/privkey.pem; # managed by Certbot
    #include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    #ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}


certbot --nginx -d api.orai.chandrodaya.net -m support@chandrodaya.net --agree-tos --noninteractive --redirect



```

### Delete certificate

```
# list all certificates
sudo certbot certificates

# delete interactive certificate
sudo certbot delete

# or delete by name
sudo certbot delete --cert-name $mydomain

# delete remaining configuration related to certifacate here:
/etc/nginx/sites-available/default

```



### Query logs

```
tail -20  /var/log/nginx/error.log
tail -20  /var/log/nginx/access.log
systemctl restart nginx
```

### Revert Changes

```
cp /etc/nginx/conf.d/backup/api-juno.conf  api-juno.conf
cp /etc/nginx/conf.d/backup/rpc-juno.conf  rpc-juno.conf
sudo systemctl restart nginx.service 
```

### Resources

* [https://stackoverflow.com/questions/29071168/nginx-upstream-with-http-https](https://stackoverflow.com/questions/29071168/nginx-upstream-with-http-httpshttps://support.hypernode.com/en/hypernode/nginx/how-to-create-a-reusable-config-to-include-in-custom-snippets)
* [https://support.hypernode.com/en/hypernode/nginx/how-to-create-a-reusable-config-to-include-in-custom-snippets](https://stackoverflow.com/questions/29071168/nginx-upstream-with-http-httpshttps://support.hypernode.com/en/hypernode/nginx/how-to-create-a-reusable-config-to-include-in-custom-snippets)
