# pre-stop
Syntax:
```
pre-stop exec|script
```
The pre-stop stanza will be executed before the job's stopping event is emitted and before the main process is killed.

example
* ```/etc/init/ntpd.conf```

```
pre-stop script
    /bin/rm -f /var/run/ntpd.pid
end script
```
