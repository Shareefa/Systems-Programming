
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
* GetPPID <- How child gets parent ID