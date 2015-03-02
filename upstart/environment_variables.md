# Environment Variables

* Single task example

```bash
# /etc/init/env.conf
env TESTING=123

script
  # prints "TESTING='123'" to system log
  logger -t $0 "TESTING='$TESTING'"
end script
```

* Multiple task example

```bash
# /etc/init/A.conf
start on wibble
export foo

# /etc/init/B.conf
start on started A
script
  logger "value of foo is '$foo'"
end script
```
* use the following command to trigger
```bash
initctl emit wibble foo=bar
```

The env variable can always be overritten
```bash
start on wibble
env var=hello

script
  logger "value of var is '$var'"
end script
```

When we emit the required event...:
```bash
initctl emit wibble var=world
```

... the system log will have recorded:
```
value of var is 'world'
```

* The variables set by Upstart itself

| Variable            | Brief Description               | Details                                                                             |
|---------------------|---------------------------------|-------------------------------------------------------------------------------------|
| EXIT_SIGNAL         | Signal causing job to exit      | String such as "HUP" or "TERM", or numeric for unknown signals                      |
| EXIT_STATUS         | Exit code of job                |                                                                                     |
| INSTANCE            | Instance name of $JOB           | Variable set but with no value if instance stanza not specified                     |
| JOB                 | Name of job                     |                                                                                     |
| PROCESS             | Name of Job process type        | "main", "pre-start", "post-start", "pre-stop", "post-stop" or "respawn"             |
| RESULT              | Whether job was successful      | "ok" or "failed"                                                                    |
| UPSTART_EVENTS      | Events that caused job to start | Space-separated. Event environment not provided                                     |
| UPSTART_FDS         | File descriptor                 | Number of the file descriptor corresponding to the listening socket-event(7) socket |
| UPSTART_INSTANCE    | Instance name of $UPSTART_JOB   |                                                                                     |
| UPSTART_JOB         | Name of current job             |                                                                                     |
| UPSTART_SESSION     | Session Init D-Bus socket       | Allows initctl command to communicate with the appropriate Session Init             |
| UPSTART_STOP_EVENTS | Events that caused job to stop  | Space-separated. Event environment not provided                                     |
