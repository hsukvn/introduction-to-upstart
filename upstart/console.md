# console

1. console log
    * write log in ```/var/log/upstart/<name>.log```
2. console output
    * standard out log in console (not in ssh session)

###Debug

1. add console log to ```<job>.conf```
2. use the following command to trace the state transition of a job
```
initctl log-priority debug
```
