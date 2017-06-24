---
layout: post
title: Install LIGHTTPD web server on Raspberry Pi
tags: [Raspberry Pi, lighttpd, server]
category: Raspberry Pi Tutorials
thumbnail : /thumbs/install-lighttpd-on-raspberry-pi.png
description: Lighttpd is a webserver optimized for speed and reduced CPU-load. It provides setting up a web server without loading the limited processing capability which is ideal for providing web access to the Raspberry Pi as a monitoring tool, or as a lightweight webserver for a personal use.
---
<div class="row">
<div class="col-md-10">
<div class="intro">
<img src="{{ page.thumbnail }}" alt="{{page.title}}">
<i class="fa fa-quote-left fa-2x fa-pull-left fa-border"></i>
<p>{{page.description}}</p>
</div>
</div>
</div>

[Lighttpd](http://www.lighttpd.net/) is an open-source web server optimized for speed-critical, high-performance environments while maintaining standards-compliant, secure and flexible.

It has a very low memory footprint compared to other web servers and takes care of CPU-load.
Running a light webserver on Linux with Lighttpd and Raspberry Pi:

* Do not remove this line (it will not be displayed)
{:toc}

## A. General

Overview and comparison of Memory Usage and Connection Requests.

#### Memory Usage


 ![Webserver Memory Usage Graph]({{site.url}}/images/Webserver_memory_graph.png "Webserver Memory Usage Graph"){: .center-image }

 From the above image it is clearly seen that Lighttpd uses less memory compared to others which is quite good for Raspberry Pi.


#### Connection Request


 ![Webserver Request Graph]({{site.url}}/images/Webserver_requests_graph.png "Webserver Request Graph"){: .center-image }

Also the requests per second for Lighttpd is suitable for  applications running on Raspberry Pi.


## B. Setting up

#### 1. Installing lighttpd

To install the lighttpd web server type the following commands in terminal


```
sudo apt-get install lighttpd
```

This will install the web server and other required dependencies.

#### 2. Enabling CGI

CGI and FastCGI are not necessary though.

```
sudo lighttpd-enable-mod cgi
```


#### 3. Enabling FastCGI


```
sudo lighttpd-enable-mod fastcgi
```


## C. Configuring Server


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


## D. Restarting Server


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


## E. Set permissions on the web directory

Change the permissions on the `www` directory to allow user to update the webpages without needing to be root.




Change the directory owner and group

```
 sudo chown www-data:www-data /var/www
```

To allow the group to write to the directory type the following in terminal

```
 sudo chmod 775 /var/www
```

 To add the pi user to the www-data group

```
 sudo usermod -a -G www-data pi
```

 > It is necessary to logout current user and login again to make the group permissions.
 It is better to `restart` the Raspberry Pi to set the permissions.

## E. Testing the server

Once the setup is complete you can access the web page by typing the IP address of the Raspberry Pi in web browser.

 You have successfully installed and configured Lighttpd web server on Raspberry Pi!
