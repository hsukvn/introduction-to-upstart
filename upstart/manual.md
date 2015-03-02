# manual
This stanza will tell Upstart to ignore the start on / stop on stanzas. It is useful for keeping the logic and capability of a job on the system while not having it automatically start at boot-up.

Example:
```
manual
```

***Note***: used in ```*.override```
