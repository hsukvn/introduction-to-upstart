# emits
Syntax:
```
emits <values>
```
clarify the events which will be emitted in this job

***Note***: the job still can emit those events which is not clarified

Example: ``` umount-root-fs.conf:19```
```
initctl emit --no-wait kill-all-again RETRY_COUNT=$RETRY_COUNT || true
```
Although the ```kill-all-again``` is not clarified using ```emits```, it still works
