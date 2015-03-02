# pre-start
Syntax:
```
pre-start exec|script
```
Use this stanza to prepare the environment for the job. Clearing out cache/tmp dirs is a good idea, but any heavy logic is discouraged, as Upstart job files should read like configuration files, not so much like complicated software.

example
* ```/etc/init/smbd.conf```

```
pre-start script
        /usr/etc/rc.sysv/S80samba.sh prestart_smbd || true
end script
```
