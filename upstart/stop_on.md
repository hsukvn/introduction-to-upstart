# stop on
This stanza defines the set of Events that will cause the Job to be automatically stopped.

Syntax:
```
stop on EVENT [[KEY=]VALUE]... [and|or...]
```
Each event EVENT is given by its name. Multiple events are permitted using the operators "and" and "or" and complex expressions may be performed with parentheses (within which line breaks are permitted).


The following command shows the condition of start on and stop on for a given job
```
initctl show-config myjob
```
