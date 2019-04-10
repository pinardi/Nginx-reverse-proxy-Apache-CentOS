# Nginx-reverse-proxy-Apache-CentOS

**Table of Contents**
* [Installation](#installation)
* [activate service nginx](#activated)
* [allow firewall](#firewall)
* [test nginx](#test)
* [Configure nginx](#Configure_nginx)

# Installation
## install & download Nginx at CentOS
```bash
```bash
yum install epel-release
yum install nginx
```

```
# activate service nginx
## start nginx
```bash
systemctl start nginx
```

# allow firewall
## allow firewall zone public http & https
```bash
firewall-cmd --permanent --zone=public --add-service=http 
firewall-cmd --permanent --zone=public --add-service=https
firewall-cmd --reload
```
# test nginx
## restart service salt master
```bash
http://server_domain_ip//
```
# source
source : https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-centos-7

# Configure_nginx 
## 
```bash
nano /etc/nginx/conf.d/default.conf
```
```bash
server {
        listen   80; 

        root /usr/share/nginx/html/; 
        index index.php index.html index.htm;

        server_name _; 

        location / {
        try_files $uri $uri/ /index.php;
        }

        location ~ \.php$ {
        
        proxy_set_header X-Real-IP  $remote_addr;
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_set_header Host $host;
        proxy_pass http://127.0.0.1:8080;

         }

         location ~ /\.ht {
                deny all;
        }
}
```
# Install and configure Apache
## Install Apache
```bash
yum update
yum install httpd
```
## start and ennable apache
```bash
systemctl enable httpd.service
systemctl start httpd.service
```
## Configure Apache
modify
```bash
nano /etc/httpd/conf/httpd.conf
```
```bash
 Listen 127.0.0.1:8080
 DocumentRoot "/usr/share/nginx/html/" 
 ```
 
 # Install PHP5
 ## Install PHP
 ```bash
 yum install php
 ```
 ## configure php
 create new file
 ```bash
 nano /usr/share/nginx/html/info.php
 ```
 paste
 ```bash
 <?php phpinfo(); ?>
 ```
 open your IP
 
 ## source : https://www.hugeserver.com/kb/configure-nginx-reverse-proxy-apache-centos/
 ##             https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-server-blocks-on-centos-7
