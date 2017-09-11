# Diving into C

Second Lecture

Topics: How C Works, Compilation, Structs, Enums


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

### 4 Steps in C

1. Preprocess - Look for # signs

    Like `#include`

    Sidenote: `#include<>` mean look in std directory `#include""` means look in the current directory

    Also `#define` (Ex. `#define N 10`, replace N with 10 )

    ALSO macros (Ex. `#define MIN(A,B) A<B?A:B`, Replace MIN() with ternary operator)

    `#ifndef` and `#endif`

    `#ifndef [some defined term]` If your term is not defined include the code between the `#ifndef` and `#endif`

    At the end of this you end up with ONE c file


    GCC options

    -E just do Preprocessors

    Sidenote: `gcc Intro.c > a.out` overwrite a.out

    Sidenote(2): `gcc Intro.c >> a.out` append to a.out

2. Compilation: File to assembly

    -S to get the assembly

3. Assembly to Binary
    -c assemble the code to binary

4. Linker

    -o name the out file

Keywords:


## Structs

What is a struct?

A collection of vars

```c

struct stats{

    double average;
    int sum;
    double stddev;
} v1;

v1.sum = 10;

```

## enums and unions

enums is like a var with a certain amount of values

union share var space
