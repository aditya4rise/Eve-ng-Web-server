Download Image

http://www.eve-ng.net/documentation/h...

1) Create Directory

mkdir /opt/unetlab/addons/qemu/linux-tinycore-6.4/

2) Save the config

/opt/unetlab/wrappers/unl_wrapper -a fixpermissions

WebServer Commands
======================
1)change root password 

sudo su
passwd

2)Install and start ssh

tce-load -w -i openssh

3)Install Web-server

tce-load -wi busybox-httpd.tcz

4)Create a directory for index.html file
sudo mkdir /mnt/sda1/wwwsite

sudo su

5)Start the SSH and tftpd services

cd /usr/local/etc/init.d/
./openssh start
cd /etc/init.d/services/
./tftpd start

6)Edit bootloader to load everything whenever you boot the box

7)sudo vi /opt/bootlocal.sh

cp /mnt/sda1/wwwsite/index.html /usr/local/httpd/bin/index.html
cd usr/local/httpd/bin
./busybox httpd -p 80 -h /usr/local/httpd/bin/
cd /usr/local/etc/init.d/
./openssh start
cd /etc/init.d/services/
./tftpd start

8)take backup
filetool.sh -b

9)sudo reboot
