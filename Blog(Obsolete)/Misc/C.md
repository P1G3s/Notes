### MISC-C (To-be-organized)

- Cannot change variable's type unless cast it to a new variable whose type is desired.
``` c
	int *yp, *xp;
	*(char *)yp = *((char *)xp + 1);
	//*yp is still a integer pointer, so is *xp
```
