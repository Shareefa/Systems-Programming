# Diving into C

Second Lecture

Topics: How C Works


***
## How Does This Code Work

```c
#include <stdio.h>

int main(){
    printf("Hello World!");
    //Also
    printf("%s", "Hello");

    return 0;
}
```

## Compilation Process

### Steps in C

1. Preprocess - Look for # signs

    Like `#include`

    Sidenote: `#include<>` mean look in std directory `#include""` means look in the current directory

    Also `#define` (Ex. `#define N 10`, replace N with 10 )

    ALSO macros (Ex. `#define MIN(A,B) A<B?A:B`, Replace MIN() with ternary operator)

    `#ifndef` and `#endif`

    `#ifndef [some defined term]` If your term is not defined include the code between the `#ifndef` and `#endif`

    
