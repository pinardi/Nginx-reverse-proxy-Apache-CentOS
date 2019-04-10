install salt master ubuntu**Table of Contents**

* [Installation](#installation)
* [activate service nginx](#activated)
* [allow firewall](#firewall)
* [test nginx](#test)

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
