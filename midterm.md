# Basic summary

There is a lot to read and review

# Weird C things

Types:
* union
* struct sizes
* struct 3 bytes of padding if one is not at the end
*

# Memory

BSS is uninitialized globals
Data initialized globals and string literals


# Malloc

## Metadata

Why Metadata?

* We are working on blocks of different sizes
* Metadata varies and creates boundaries between lists

* On every block you have a boundary with size and freed or not

* Also on every other block we need to have another layer/piece of metadata so that when freed you know to coalesce

* buddy allocation
