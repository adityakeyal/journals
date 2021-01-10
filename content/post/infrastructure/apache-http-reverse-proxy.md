---
title: "Apache Http Reverse Proxy"
date: 2021-01-10T17:01:59+05:30
math: false
tags: [apache-httpd]
categories: [infrastructure]
---

# Using Apache HTTP as Reverse Proxy

## What is a Reverse Proxy
A reverse proxy acts as a middle man to all incoming traffic. All incoming traffic first comes to the reverse proxy and from the proxy it is routed to the next component.

The below diagram shows the example of a reverse proxy in action

![Reverse Proxy](/infrastructure/2021-01-10-17-20-49.png)

The idea behind the above setup is to protect all internal servers from the external world.
While this does present a Single point of Failure, it also provides many additional benefits as explained below.

## Why use a Reverse Proxy

There are some common use cases for a reverse proxy
 - SSL termination
 - CORS protection
 - Load Balancing
 - Caching layer
 - Common compression for incoming and outgoing data

As evident from the above list, a large function of the reverse proxy architecture is to speed up the operations and enable quicker request reslution.
Additionally in cases where you have multiple application (running on multiple ports), to the external world only 1 port is exposed.


## Configuring Apache Httpd

Some important configuration is as below:

> vi /etc/httpd/conf/httpd.conf

```bash
Listen 80
<VirtualHost *:80>
	SSLProxyEngine on
	ProxyPreserveHost On
	ProxyPass / https://localhost:8080/
	ProxyPassReverse / https://localhost:8080/
</VirtualHost>
```

> vi /etc/httpd/conf.d/ssl.conf

```bash
Listen 443
<VirtualHost *:443>
	ServerName mysite.com
	SSLEngine on
	SSLCertificateFile "/location_to_file/cert.pem"
	SSLCertificateKeyFile "/location_to_file/key.pem"
	SSLProxyEngine on
	ProxyPreserveHost On
	ProxyPass / https://localhost:8080/
	ProxyPassReverse / https://localhost:8080/
</VirtualHo
```


## Adding compression for static content

> vi /etc/httpd/conf.modules.d/compression.conf

```bash
# Load the Gzipping module
LoadModule deflate_module modules/mod_deflate.so

# Add compression for the below content types
 
AddOutputFilterByType DEFLATE text/plain
AddOutputFilterByType DEFLATE text/html
AddOutputFilterByType DEFLATE text/xml
AddOutputFilterByType DEFLATE text/css
AddOutputFilterByType DEFLATE application/xml
AddOutputFilterByType DEFLATE application/xhtml+xml
AddOutputFilterByType DEFLATE application/rss+xml
AddOutputFilterByType DEFLATE application/javascript
AddOutputFilterByType DEFLATE application/x-javascript
AddOutputFilterByType DEFLATE image/svg+xml
```
