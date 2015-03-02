# expect

```
expect fork
```
Upstart will expect the process executed to call fork exactly once.

```
expect daemon
```
Upstart will expect the process executed to call fork exactly twice.

| Forks | no expect           | expect fork         | expect daemon |
|-------|---------------------|---------------------|---------------|
| 0     | Correct             | start hangs         | start hangs   |
| 1     | Wrong pid tracked  | Correct             | start hangs   |
| 2     | Wrong pid tracked  | Wrong pid tracked  | Correct       |
