---
layout: post
title: Installing LIGHTTPD web server on Raspberry Pi
tags: [Raspberry Pi, lighttpd, server]
---
>You want to run a webserver on Raspberry Pi

[Lighttpd](http://www.lighttpd.net/) is an open-source web server optimized for speed-critical, high-performance environments while maintaining standards-compliant, secure and flexible.

 It has a very low memory footprint compared to other web servers and takes care of CPU-load.


#### Memory Usage


 ![Webserver Memory Usage Graph]({{site.url}}/images/Webserver_memory_graph.png "Webserver Memory Usage Graph")

 From the above image it is clearly seen that Lighttpd uses less memory compared to others which is quite good for Raspberry Pi.


#### Connection Request


 ![Webserver Request Graph]({{site.url}}/images/Webserver_requests_graph.png "Webserver Request Graph")

Also the requests per second for Lighttpd is suitable for  applications running on Raspberry Pi.


## A. Setting up

#### 1. Installing lighttpd

To install the lighttpd web server type the following commands in terminal


```
sudo apt-get install lighttpd
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

```apacheconf
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


You can restart the server with any two commands below


OR


* Direct Reload


```
 sudo service lighttpd force-reload
```


* Stop-Start Reload


```
sudo /etc/init.d/lighttpd stop

sudo /etc/init.d/lighttpd start
```


## D. Set permissions on the web directory

Change the permissions on the `www` directory to allow your user to update the webpages without needing them to be root.


 To allow the group to write to the directory type the following in terminal


```
 sudo chmod 775 /var/www
```

 > It is necessary to logout current user and login again to make the changes. It is better to `restart` the Raspberry Pi to set the permissions.

 You have successfully installed and configured lighttpd web server on Raspberry Pi!
