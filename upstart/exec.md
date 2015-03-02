# exec
Syntax:
```
exec COMMAND [ ARG ]...
```
Stanza that allows the specification of a single-line command to run. Note that if this command-line contains any shell meta-characters, it will be passed through a shell prior to being executed. This ensures that shell redirection and variable expansion occur as expected.

Example:
```
exec /usr/bin/nmbd -D
```

