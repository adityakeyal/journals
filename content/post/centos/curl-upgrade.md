---
title: "Curl Upgrade"
date: 2022-04-04T15:37:28+05:30
math: false
tags: []
categories: []
---
## Commands to upgrade curl
```
wget https://curl.haxx.se/download/curl-7.68.0.tar.gz --no-check-certificate
gunzip -c curl-7.68.0.tar.gz | tar xvf -
cd curl-7.68.0
./configure --with-ssl
make
make install
```
