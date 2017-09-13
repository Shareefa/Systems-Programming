# Moar C!!

Topics: stucts, enums, union, memory model

***

## Typedef

Used to shorten type name:
`typedef struct stat Stat;`

## Structs

Grouping of vars that are related

```c
struct stat{

    int sum;
    double avg;
    double stdev;
}



```

## Enum

Creates a type where there are a limited number of values.

Allows you to do stuff like `Day d1;` and then `d1 = MONDAY;`

```c
enum days{
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY
}


```

## Unions



```c
union num{
    int x;
    double y;
}
```
So what is the difference??

Union takes the memory of the largest data type

`union num`c only has the memory allocated for an int

BUT the char is the first byte

Ex.

```c
typedef union num Num;

Num k1;
k1.x = 33
```

## Some debugging stuff

```c
//in the middle of code

printf("In %s at line %d", __FILE__, __LINE__);

```


## Memory

This is stuff that I and **you** already now

Review static and dynamic

```c
int x;
int a[10];
//a and x can not point to anything else
//they are statically allocated


```

## String Representation in C

What is a string??

A string is a array of characters  with a **null terminating character**

```c

char str[] = {'h', 'e', 'l', 'l', 'o', '\0'};

```

Honestly this is like _sooooo basicccccc omg_
like __DAMN__


## Memory Model

Okay like on the off chance someone looks at this that doesn't know the memory model I'll do it here

| Memory | Address/Info |
| :------------- | :------------- |
| Stack | 0xffff |
| Heap| |
|BSS| |
|Data |Initialized global vars and string literals |
|Program Text (Op Code)| 0x0000|
