# nice
Change the jobs scheduling priority from the default. See nice(1).

range from -20 to 19

Example:
```
# run with lowest priority
nice 19
```

``` httpd-sys.conf
```
10:nice -10
```
