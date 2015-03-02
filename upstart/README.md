# Upstart

##[event-based init daemon](https://launchpad.net/upstart)
* Upstart is an event-based replacement for the [```/sbin/init```](http://en.wikipedia.org/wiki/Init) daemon which handles starting of tasks and daemons during boot, stopping them during shutdown and supervising them while the system is running.


###Cons for System V init system
* Non-Potimal Performance
    * Slow in the sence that it makes no use of parallelism
    * does not make full use of system resource
    * incapable of handling dynamically changing system ("hot-plug")
* No respawn when daemon die


##Why Upstart
* Upstart starts a service when its required condition are met
* If multiple jobs have the same "start on" condition, Upstart will start those jobs **in parallel**.
* Ability to monitor daemon and respawn when daemon die


