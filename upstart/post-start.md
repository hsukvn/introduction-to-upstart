# post-start
Syntax:
```
post-start exec|script
```
Script or process to run after the main process has been spawned, but before the started(7) event has been emitted.


example
* ```/etc/init/smbd.conf```

```
post-start script
        /usr/etc/rc.sysv/S80samba.sh poststart_smbd || true
end script
```
