# Make

### Rule
**Targets... : Prerequisites**<br>
&emsp;   **Recipes...** 

### Implicit Rule
 - Pattern Rule
	- Automatic Variable
		- $@ (File name of the target of the rule)
		- $% (Target member name)
		- $^ (Names of all  prerequisites)
 - Prerequisite (also a target)
	- if the prerequisite cant not be found, then Make would see it as a target and execute the implicit rule for each one of them. (make $(EXE))


### Caution
 - [The list of libraries should go to LDLIBS, not CFLAGS](https://stackoverflow.com/questions/57383111/appending-library-name-to-cflags-in-makefile)
 - Use "+=" to append text to variable itself
 - [Target order does matter](https://stackoverflow.com/questions/6856263/what-is-the-difference-between-make-and-make-all)

