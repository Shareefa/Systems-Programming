


# Allocation

* Explicit allocation: Need to use malloc and free
* Implicit allocators: Like Java you don't need to worry about it (Garbage collectors)

## What is an allocator trying to do

* Be fast (High throughput)
* Utilize All available memory (Reduce fragmentation)

### Fragmentation
* Internal fragmentation - When the block allocated is bigger than the block allocated
* External fragmentation - When there is enough memory but all the blocks are of too small a size

## How to we do this?

* How to keep track of free blocks
* How to choose which free blocks
* Should we split the free blocks
* What to do with a block that has been just freed? (Coalescing)

### Implicit Free lists

So like the how do you keep track of all the blocks

* Use the first word keep track of block size and if it is allocated

* So if a word is 4 bytes and each block is double word aligned then the  memory address are multiples of 8
* This means that the last three bits of the word is always 0
* We can have a 1 word as a header

* We can traverse by the block size and 
