# User Job

* Upstart 1.3 and later
* placing job configuration in ```$HOME/.init/```
* syntax is indentical for system jobs
* allowing a non-privileged user to create and manage jobs

###Limitation
* cannot created with the same name as system job
    * system job take precedence
    * Stanzas manipulate resource limits may cause a job fail to start
        * limit, nice and oom
* User jobs output cannot be logged!!! (console log)

###Configuration
* set allow non-root users access to all the Upstart D-bus methods
    * ```/etc/dbus-1/system.d/Upstart.conf```


#Session Job
* managed by the users own Session Init
