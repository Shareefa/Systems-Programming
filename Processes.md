
# Process

Idk what a process is

But it has it's own memory
like it's own stack and heap?

What if they had the same mem?

* They interfere with each other (seg fault would destroy everything)

So now every process has its own:

* Memory (Stack, Heap, BSS, etc.)
* PID (Process ID)


When you start your machine one process starts and **starts all other processes**.

* Linux = init.d

**key point** = Process can make more processes

How do you see all processes?

* process table
    * PID
    * name
    * owner
    * resources


* ps = processes of the user
* ps -a = processes on entire machine
* top = real time ps (ps doesn't update live), include CPU usage and what not

How to create a new process?

* Use `fork()`
* `fork()` creates a copy of the current process
* PID is different but all mem (**stack** and **head**), PC is cloned
* In code below hello is printed twice

Ex code.

```c
main(){
    fork();
    printf("hello");
}
```

## Everything is copied EXCEPT FILE Descriptors

Need to close and reopen or else
File descriptors will messed up

## Do they run at the same time?
Depends on the processor but basically yeah

## Fork bomb

You unplug the machine to fix the problem


## What does fork() return

* -1 if it fails
* Positive num the childs PID
* You know you are the child if you PID is 0
* `getppid()` <- How child gets parent ID
* `#include<unistd.h>`


## Some weird behavior

What do you think happens?
```c
int main(){
    printf("Answer: %d PID:%d", answer, getpid());
    fork();
    return 0;
}
```

What is actually printed:

```bash
$ ./forking
$ Answer: 42 PID: 24664Answer: 42 PID: 24664
```

### Why?

* printf puts string in buffer
* buffer is in memory before actually printed
* fork copies memory
* at the end of the process child buffer gets flushed and printed

## Some more funcs

* Need to have a `waitpid(id, &status, 0)` so that child doesn't turn into a zombie
* `waitpid(id, &status, 0)` makes parent wait till child finishs
*
