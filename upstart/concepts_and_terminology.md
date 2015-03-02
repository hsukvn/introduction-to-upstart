# Concepts and Terminology
* Upstart is an event-based replacement for the ```/sbin/init``` daemon
* Handles starting upstart job during boot, stopping them during shutdown
* Supervising daemon job while the system is running.

##Upstart job config file
* Upstart config folder```/etc/init```

* Upstart jobs```/etc/init/<name>.conf```

    * The following command shows the current job list

    ```$ initctl list```

* log folder for jobs: ```/var/log/upstart/<name>.log```
    * rc information in bootup: ```/var/log/upstart/rc.log```
    * log for S01~S99 in bootup: ```/var/log/upstart/dsm-services.log```

##Jobs and Events
* Job - What task or service (daemon) you want to provide
* Event - What event happened
    * emit it to trigger **Jobs**
    * for example: DS starts ```ntpd``` when ```network is ready```
        * Job: run ```ntpd``` daemon
        * Condition: emit ```network is ready```
        * Event: Telling Upstart that the network is ready
