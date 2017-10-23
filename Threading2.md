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


```c
// After function returns, function gets taken off the thread, which means start might have 
// a different address after function gets returned
pthread_t start_threads() {
    int start = 42;
    pthread_t tid;
    pthread_create(&tid, 0, myfunc, &start); //subdivides curr memory space to create space for thread
    return tid;
    // start_threads() might get returned before myFunc inside create gets run, which means int start
    // might not have same val
}

// Stack remains until tid exits, which means vars such as start keep same address till end
void start_threads() {
     int start = 42;
     void *result;
     pthread_t tid;
     pthread_create(&tid, 0, myfunc, &start);
     pthread_join(tid, &result);
     // Join essentially waits for pthread to finish, and start_threads() does not return until that happens
}
```
__Until pthread_join() is called, nothing actually happens to the thread__

```c
void* myfunc(void* ptr) {
    int i= *((int *) ptr);
    printf("%d ",i);
    return NULL;
}

int main() {
    //create 10 threads calling myfunc with successively higher numbers
    
    int i=0;
    pthread_t tid;
    
    for(i = 0; i<10; i++) {                        // i++ causes race condition, so values actually arent printed in order
        pthread_create(&tid, NULL, myfunc, &i);
    }
    
    pthread_exit(NULL);
}

```


