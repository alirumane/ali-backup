---
layout: post
title: Installing LIGHTTPD on Raspberry Pi
tags: [Raspberry Pi, lighttpd, server]
---
>You want to run a webserver on Raspberry Pi

[Lighttpd](http://www.lighttpd.net/) is an open-source web server optimized for speed-critical, high-performance environments while maintaining standards-compliant, secure and flexible.

 It has a very low memory footprint compared to other web servers and takes care of CPU-load.

## A. Setting up

#### 1. Installing lighttpd


```*.sh
sudo apt-get -y install lighttpd
```


#### 2. Enabling CGI


```
sudo lighttpd-enable-mod cgi
```


#### 3. Enabling FastCGI


```
sudo lighttpd-enable-mod fastcgi
```


## B. Configuring Server


You need to change the default location of html in web-directory.  Type the following command in terminal


```
 sudo nano /etc/lighttpd/lighttpd.conf
 ```


you will see

```apache2.conf
server.document-root        = "/var/www/html"
server.upload-dirs          = ( "/var/cache/lighttpd/uploads" )
server.errorlog             = "/var/log/lighttpd/error.log"
server.pid-file             = "/var/run/lighttpd.pid"
server.username             = "www-data"
server.groupname            = "www-data"
server.port                 = 80
```

Change

server.document-root        = "/var/www/html"


to


```
 server.document-root        = "/var/www/"
 ```
 

## C. Restarting Server


```
sudo /etc/init.d/lighttpd stop

sudo /etc/init.d/lighttpd start
```
