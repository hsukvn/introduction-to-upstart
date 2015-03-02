# instance

1. run the same job with different arguments

```
#foo.conf
instance $BAR

script
  echo "hello from instance $BAR"
  sleep 999
end script
```
First
```
$ sudo start foo BAR=baz
```
```
foo (baz) start/running, process 1235
```

Further
```
$ sudo start foo BAR="hello world"
```
```
foo (baz) start/running, process 1235
foo (hello world) start/running, process 1236
```

* ```sudo start foo``` is not alowed
    * no input parameter
* ```sudo start foo BAR="hello world"``` again is not allowed
    * already exist
