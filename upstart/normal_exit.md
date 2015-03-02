# normal exit
Used to change Upstart's idea of what a "normal" exit status is. Conventionally, processes exit with status 0 (zero) to denote success and non-zero to denote failure. If your application can exit with exit status 13 and you want Upstart to consider this as an normal (successful) exit, then you can specify:

```
normal exit 0 13
```

example

netatalk.conf
```
8:normal exit 0 5
```

For example, to consider exit codes 0 and 13 as success and also to consider the program to have completed successfully if it exits on signal SIGUSR1 and SIGWINCH, specify:
```
normal exit 0 13 SIGUSR1 SIGWINCH
```

more example

dhcp-client.conf
```
3:normal exit 0 SIGKILL
```
