---
title: Security Camera ftp
subtitle: Provide ftpd docker for security cameras
category:
  - About Developer
author: Daniel Kelly
date: 2019-08-02T04:27:56.800Z
featureImage: /uploads/resource-grid-hero.jpg
---
The `ResourceGrid` powers the grid display of both posts and categories in the Awake template. It's a powerful, fast, and flexible component to grab a grid of any size or content when you need it.


## run
```
docker run --rm --name proftpd -d -p 21:21 -p 50000-50050:50000-50050 -v /home/pi/config/ftpd/conf.d:/etc/proftpd/conf.d -v /home/pi/config/ftpd/users:/users -v /home/pi/config/ftpd/data:/proftpd rpi-proftpd
```
