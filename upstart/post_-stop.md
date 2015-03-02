# post-stop
Syntax:
```
post-stop exec|script
```

example
* ```/etc/init/smbd.conf```

```
post-stop script
        /usr/etc/rc.sysv/S80samba.sh poststop_smbd || true
end script
```

