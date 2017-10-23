# Threads
- ## Different between thread and process is:
    - __Threads share same memory, while processeses do not__
    - Benfits of sharing memory space (Threads over processes):
        - Efficiency in context switches, as values dont need to be copied over
        - Access to global same variables, structs, data, etc.
    - Cons:
        - One thread dying kills all related threads (Seg faults, etc.)
    - Benefits of processes over threads:
        - processes are independent, while threads depend on each other
        - Things like orphans are actually beneficial in this way
        - Security, as memory spaces are sepearate
        
__Threads created through clone() as opposed to fork() for processeses__

```c
void *busy(void *ptr){
    puts("hello world");
    return null;
}

int main() {
    pthread_t id;
    pthread_create(&id, NULL, busy, "Hi");
    while(1) {} //Loop Forever
} 
```

User Threads   |   Kernel Threads
--- | ---
Scheduled in user space   |   Scheduled in kernel space


