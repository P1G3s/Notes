# IPC

### Pipe
**Pipe** is created by pipe() with two **file descriptor** representing **two sides of pipe - input(1) and output(0)**, To make pipe works like "|" in shell, following steps shall be taken (child | parent) ([by the way pipe run concurrently](https://unix.stackexchange.com/questions/37508/in-what-order-do-piped-commands-run))
- fork()
- change **stdout** to **pipe input** in child proccess
- exec child  program
- change **stdin** to **pipe output** in parent proccess
- exec parent program

### FIFO
**FIFO** is a file that can be raed or write by proccesses, **so fork() is no longer needed** as long as proccesses can access this file(FIFO)
- open blocked until another proccess open
- read blocked until another proccess finished writting?
- write blocked until another proccess finishes reading?
