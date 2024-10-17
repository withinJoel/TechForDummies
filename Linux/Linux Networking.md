# Linux Networking
* Let's get into networking

## To get the ip address
* type `ip addr show`
* The 1.lo: after `inet` is your local ip address.
* The 2. enp2s0: after `inet` is your actual ip address.
* output:
```
user1@sysadmin-OptiPlex-3020:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether b0:83:fe:8c:ab:91 brd ff:ff:ff:ff:ff:ff
    inet 10.0.102.14/22 brd 10.0.103.255 scope global dynamic noprefixroute enp2s0
       valid_lft 2791sec preferred_lft 2791sec
    inet6 fe80::c5c9:64da:af01:bb60/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```
## To find the Gateway
* type `ip route | grep default`
* After `via` and before `dev` is your gateway address.
* output:
```
user1@sysadmin-OptiPlex-3020:~$ ip route | grep default
default via 10.0.100.1 dev enp2s0 proto dhcp metric 100
```

## To find DNS Servers
* type `cat /etc/resolv.conf`
* The `nameserver` is your DNS address.
```
user1@sysadmin-OptiPlex-3020:~$ cat /etc/resolv.conf
# This is /run/systemd/resolve/stub-resolv.conf managed by man:systemd-resolved(8).
# Do not edit.
#
# This file might be symlinked as /etc/resolv.conf. If you're looking at
# /etc/resolv.conf and seeing this text, you have followed the symlink.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs should typically not access this file directly, but only
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a
# different way, replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0 trust-ad
search .
```

## To connect via SSH
```
ssh root@54.245.191.10
```
```
ssh hema@10.0.102.33
```
* `root` is not the name of the user but rather the super user.
* `hema` is the name of the user.
## To connect via SSH with GUI support
* Note: It will not open like a GUI based OS but rather you can open images and other media files which you will not be able to in the above command.
```
ssh -X root@54.201.45.37
```
