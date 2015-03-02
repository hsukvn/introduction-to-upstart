# How to add a job

###Follow these steps
1. Clarify what job you want to add
2. What condition will trigger this job
3. Write an upstart job config named ```*.conf```
    * In source tree the upstart is named as ```daemon_name.upstart```
        * for example: ```ntpd.upstart```
        * Rename it as ```daemon_name.conf``` and put it in ``` /etc/init/``` when remoteinstall
4. An example for upstart job
    * nec: necessary to write
    * opt: option, write them if needed

```bash
description "NetBIOS name server"              #nec: describe the usage of this job

stop on runlevel [06]                          #opt: condition to stop this job

console log                                    #opt: port the out and err to /var/log/upstart/job_name.log in order to help debug and support

expect fork                                    #nec: please put the right stanza according to the number that the job forks
respawn                                        #opt: respawn when job terminate abnormal
respawn limit 5 10                             #opt: must write this stanza followed by respawn

pre-start script
    # do something before daemon start

    echo "netatalk start" || true

    #Note: any command which returns a none zero value will cause job start/stop fail
    #In order to avoid this, you can add || true after execute a command.
    #Write a bash if there are many works to do

end script

script
    exec /usr/sbin/nmbd -D
    #The only command to do here is to run daemon up, any other commands like "cat", "echo", ......, will cause upstart trace the wrong pid
end script

post-start script
    # do something after daemon start
end script

pre-stop script
    # do something before daemon stop
end script

# Upstart kill tracked pid

post-stop script
    # do something after daemon stop
end script
```

##Verify the upstart Job
* ```initctl start job_name``` to start a job
    * if success: ```job_name start/running, process pid```
    * if failure: ``` start: Job failed to start```
* ```initctl status job_name``` to track the job status and pid
    * compare the pid with the pid shown in```ps```, if the pid is not conssistant, then the ```expect``` stanza might be wrong which cause upstart to track the wrong pid
* If the job has ```respawn```, kill the process and check whether it respawn with another pid
* ```initctl reload job_name``` to reload the job
    * make sure the job reload correctly
* ```initctl restart job_name``` to restart the job
    * make sure the job restart correctly
* ```initctl stop job_name``` to stop the job
    * check the job status is **stop/waiting** by ```initctl status job_name```

***Note***
* ```initctl status``` result for Adapter is **start/running** without pid
* ```initctl reload``` is not work for adaper

##Debug information
1. ```/var/log/upstart/*.log``` - standard output and standard error
2. use the following command to trace the state transition of a job
```
initctl log-priority debug
```


