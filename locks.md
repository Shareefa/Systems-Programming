## What is this class about??

## Critical Sections

## Mutual Exclusions

## Locks are atomic instructions

What does it mean that memory and heap is shared in multithearded environment?

* All memory is shared!
* BUT heap is the only safe place to put stuff

## Semaphore

So the way this works is like instead of locks in just keeps track of the resources so that threads aren't waiting on specific locks but rather it waits till at least one resource is free.

Is a semaphore enough?

Nah you need to a mutex on it.

## Condition Variables

You need this