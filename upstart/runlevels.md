# Runlevels
* 0 : System poweroff
* 1 : rootfs ready, basic filesystem (/tmp, /run, /sys) ready, syslog ready, swap ready
* 2 : User can login
* 6 : System reboot

##Display runlevels
```
$ /sbin/runlevel
or
$runlevel
```
```
DS:DS415p init> runlevel
1 2
```
The output above shows that:
* Previous runlevel is 1
* Current runlevel is 2

###manually change the current runlevel
* telinit

```
DS:DS415p init> telinit 3
DS:DS415p init> runlevel
2 3
```

###Default Runlevel

The default runlevel the DS will boot into is written in
```
/etc/init/rc-sysinit.conf
```
