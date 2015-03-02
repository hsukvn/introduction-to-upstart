# Events
* Events can generally be thought of as
    * "signals" - non-blocking
    * "hooks" - blocking

## Events emitted by Upstart when job change state
* starting (hook) - This event is emitted by Upstart when a job has been scheduled to run and is about to start executing.
* started (signal) - This event is emitted by Upstart when a job is now running. Note that a job does not have to have an associated program or script so "running" does not necessarily imply that any additional process is executing.
* stopping (hook) - This event is emitted by Upstart when a job is about to be stopped.
* stopped (signal) - This event is emitted by Upstart when a job has completed (successfully or otherwise).

##Event types
* Event can be created by an administrator at any time

* Signals: Emitting an event of this type returns immediately, allowing the caller to continue.
```
# initctl emit --no-wait mysignal
```
* Hooks:
    * notification that something changed on the system
    * wait to complete before carrying on (blocking)
```
# initctl emit mysignal
```

***Note***: that an event name with the same name as a job is allowed.

##Order of Stop/Start Operations
* Upstart always handles stop on stanzas before handling start on stanzas

* Example for single job
    * When emit event-A, the job A will stop then start.

```
#A.conf
start on event-A
stop  on event-A
```

* Example for multiple jobs
    * Assume that job A is already running
        1. "foo" event emitted
        2. Upstart stop A
        3. Upstart start B

```
#A.conf
start on startup
stop on foo
```
```
#B.conf
start on foo
```

##Events that emit when DS bootup
| Event              | Description                                                                                    | Target                                                 |
|--------------------|------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| runlevel 1         | rootfs ready, basic filesystem (/tmp, /run, /sys) ready, syslog ready, swap ready              | service not depend on network, volume, share, and auth |
| runlevel 2         | user can login                                                                                 |                                                        ||

##Event when DS shutdown
| Event                   | Description                 |
|-------------------------|-----------------------------|
| runlevel 0              | system shutdown             |
| runlevel 6              | system reboot               |
| all-legacy-service-down | all service on rc.d stopped |
