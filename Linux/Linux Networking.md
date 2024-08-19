# Linux Networking
* Let's get into networking

## To get the ip address
* type `ip addr show`
* The `inet` is your ip address.
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
