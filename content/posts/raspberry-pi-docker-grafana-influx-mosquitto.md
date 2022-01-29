---
title: Raspberry PI with Grafana Influx and Mosquitto on Docker
subtitle: How to use Grafana, Influx, Mosquito on Docker
category:
  - PI
author: lenambac
date: 2022-01-29T17:49:56.800Z
featureImage: /uploads/pico_neopixel.png
---

Hi all, in this post we are going to run the following components via [Docker](https://www.docker.com/) on Raspberry PI:
- [Grafana](https://grafana.com/)
- [Influx](https://www.influxdata.com/)
- [Mosquitto MQTT broker](https://mosquitto.org/)
- [Telegraf](https://www.influxdata.com/time-series-platform/telegraf/)
- [Proftpd](http://www.proftpd.org/)

These are the steps:

## 1. Raspberry Pi OS intallation

First of all you need to [install the OS](https://www.raspberrypi.com/documentation/computers/getting-started.html) in the raspberry PI, there are several options you can use: Raspberry PI OS, Ubuntu, NOOBS, OSMC, OpenELEC ... , we'll use Raspberry PI OS (previopusly called Raspbian)

Follow the instrucctions on https://www.raspberrypi.com/software/ to install the Operating system.

### Static IP configuration

Because raspberry will be used as a server which will run several services, you can configure a static IP adress to make easy the configuration of all devices which needs to connect with raspberry.

If your local network is 192.168.1/24 and your default gateway is 192.168.1.1

Edit /etc/dhcpcd.conf file and modify the following lines:
```
# Example static IP configuration:
interface eth0
static ip_address=192.168.1.{IP_number}/24
static routers=192.168.1.1
static domain_name_servers=8.8.8.8
noipv6
``` 
Update the {IP_number} with a number of your choice between 2 and 254.
It is recommended that you configure your DHCP Server (usually on your router) in order to indicate that this IP adress is static and avoid IP duplication errors on your network. 



## 2. Docker installation

After the basic raspberry PI configuration is done we are going to install Docker.
Please see the [reference](https://phoenixnap.com/kb/docker-on-raspberry-pi)

```console
sudo apt-get update && sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

Add a non_root user to the Docker Group

```console
sudo usermod -aG docker [user_name]
sudo usermod -aG docker Pi
```
Check Docker Version
```console
docker version
```
Run Hellow World
```console
docker run hello-world
```


## 3. Clone your Git reposity
If you have a gitlab repository with all your code, scripts, ... clone it in order to use them
Install git client and configure your [personal token](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

```
git config --global user.name "manelcab"
git config --global user.email "manelcab@gmail.com"
```

If you want to avoid entering always the token you can follow these steps, but remember that this token will not be encrypted on you system

```
git config --global credential.helper store
cat ~/.git-credentials

``` 

## 4. Copy your data
After clonning your repository you can copy your data and secrets, for exempla on /home/pi/config
An easy way is to use a USB drive where you can place all you data and config. Remember to do backup copies!.

Check the devices with:
```
lsblk -fp
fdisk -l
```

Create a new partition type 83 (Linux)
```
fdisk /dev/sda
sudo mkfs.ext4 /dev/sda1
``` 
Copy the PARTUUID

```
sudo blkid
```
Inclue the following line int /etc/fstab with the correct PARTUUID

```
PARTUUID=XXXXXXXX-XX /mnt/usb0 ext4 defaults,auto,users,rw,nofail 0 0

```

## 5. Starting mosquitto
## 6. Starting influx
## 7. Starting telegraf
## 8. Starting Grafana
## 5. Starting mosquitto


