# Jobs
* Task Job: short-running process like deleting a file
    * Has a definite lifetime and end state
    * example: ```rm -rf /path/of/a/file```
* Service Job: long-running process (daemon) ex. nmbd
* Abstact Job: has no script sections or exec stanzas ex. pgsql-adapter

###Job States
| CurrentState | Goal|      |
|--------------|------------|---------------------------|
|              | **start**      |  **stop**
||||
| waiting      | starting   | n/a                       |
| starting     | pre-start   | stopping                  |
| pre-start    | spawned    | stopping                  |
| spawned      | post-start | stopping                  |
| post-start   | running    | stopping                  |
| running      | stopping   | pre-stop or stopping |
| pre-stop     | running    | stopping                  |
| stopping     | killed     | killed                    |
| killed       | post-stop  | post-stop                 |
| post-stop    | starting   | waiting                   |

### State Flow Chart
![](http://10.13.21.141/upstart_flowchart.png)

###Detail of states
* waiting : initial state.
* starting : job is about to start.
* pre-start : running pre-start section.
* spawned : about to run script or exec section.
* post-start : running post-start section.
* running : interim state set after post-start section processed denoting job is running (But it may have no associated PID!)
* pre-stop : running pre-stop section.
* stopping : interim state set after pre-stop section processed.
* killed : job is about to be stopped.
* post-stop : running post-stop section.

##Job Configuation File
Job configuration files are named
```
<name.conf>
```
###Job Configuration
Jobs live in the following directory:
```
/etc/init/
```

###Start and Stop a Job
Start a job by an Administrator
```
* initctl start <job>
or
* start <job>
```

Stop a job by an Administrator
```
* initctl stop <job>
or
* stop <job>
```

###Job with no "stop on" or "start on"
* Such a job can only be controlled by an Administrator.
