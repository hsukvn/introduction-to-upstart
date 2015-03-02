# oom score
Linux has an "Out of Memory" killer facility.
* kill the rogue process to avoid it impacting the system
* Normally the OOM killer regards all processes equally
* This stanza advises the kernel to treat this job differently

The "adjustment" value provided to this stanza is an integer value from -999 to 1000
* -999 - very unlikely to be killed by the OOM killer
* 1000 - very likely to be killed by the OOM killer
* special value: never - ignored by the OOM killer

example

hotplugd.conf
```
8:oom score -999
```

pgsql-adapter.conf
```
5:oom score -999
```

syslog-ng.conf
```
6:oom score -999
```
httpd-sys.conf
```
11:oom score -999
```
findhostd.conf
```
7:oom score -999
```
