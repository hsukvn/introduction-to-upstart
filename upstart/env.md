# env
Syntax:
```
env KEY[=VALUE]
```
Allows an environment variable to be set which is accessible in all script sections.

Example:
```
env myvar="hello world"
console out

script
  echo "myvar='$myvar'"
end script
```

