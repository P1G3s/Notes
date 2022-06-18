# Process

 - Process is a running program
 - Processes use **Signal** to comunicate
 - Process has a clock (sleep -> kenel set the clock, process paused, wait for the kernel's signal)
	- **sleep()** = alarm() + pause()

#### (In General)

```mermaid
graph LR;
	Process --> PCB[PCB table] ;
	Process --> Mem[Memory allocated];
	PCB --> Status; Status --> Running; Status --> Ready; Status --> Blocked 
```

#### Creation of Process
 - TCB table + Memory(Stack, Heap, Data Seg, Code Seg ...)
 - ...
 - Insert The TCB to the queue?
- WIP

#### Creation of Process(Unix/Linux)
 - Every Process has a **Parent Process**
 - Use **fork()** to create a child process by exactly **copying** the parent process along with **Stack, Data, Heap, Code** etc.
 - **Exec()** tells the process to run another program's code instead of its parent code. ([Exec() family wont execute the code after themselves, because code has been replaced with new program](https://stackoverflow.com/questions/32899582/why-the-exec-family-of-functions-doesnt-execute-the-code-after-exec))
 - exec() = execute.   popen() = execute(__Set PipeEntrance__) && return execution ouput(__FILE *PipeExit__).
 - _WIP..._

### Signal
 - **Sigaction()** has **Blocked Signal Set** (sa_mask) whereas **Signal()** does not (A blocked signal handler needs to be inserted into the handler which **Signal** is refering to)
 - Protect **Critical Resource** from being corrupted.
```mermaid
graph LR;
	Signal --Coordinate--> ProcessA
	Signal --Coordinate--> ProcessB
	ProcessA --> Syn{Synchronized};
	ProcessB --> Syn{Synchronized};
	Syn --> CTS[Critical Resource];
```

