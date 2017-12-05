# Network Programing

OSI Model

Need to know Frames, packet

Focus on the transport and network level

## Transport Level Protocol

- TCP (Reliable in order, but slow because of overhead - streambased)

  check for lost packets
  keep a list of sequence 

- UDP (Fast, but not reliable)

## Network Level

- IP internet protocol
- packet encloses a hardware frame and it is wrapped in an IP address

## Socket

- Abstaction for the network programming
- Allow to connect to a machine
- it is treated like a file descriptor which allows us to integrate it into code easily
  - open()
  - close()
  - write()

- server
  - bind()
    - bind socket to a particular IP address because there are so many devices on a specific port 
  - listen()
    - listen on a bound socket (basically waiting till it hear something)
  - accept()
    - accept the connection and do the protocol action

- client
  - connect()
    - `connect(sockfd, (struct sockaddr*)&serv_addr, sizeof(serv_addr)) < 0)`

## Useful methods

- getaddrinfo()
  - fills in a struct with the right information in the right format

## Socket methods
- socket(AF_INET, SOCK_STREAM, 0)
  - AF_INET  is IPv4
  - AF_INET6 is IPv6
  - SOCK_STREAM -> TCP
  - SOCK_DGRAM ->UDG
  - SOCK_RAW -> socket that listens on the data link layer and you need to create packets yourself
  - 0??


## Useful utilities

- traceroute
-


## How do you create a non blocking socket

`fd = socket(AF_INET, SOCk_STREAM | SOCK_NONBLOCK, 0);`
socket returns a file descriptor

`SOCk_STREAM | SOCK_NONBLOCK` -> open a TCP socket and | makes it a nonblocking by masking it with the bitwise OR

## How to recieve input from a client

1. Create fd = socket(...)
2. bind(fd, with port and address)
3. listen(fd, ...)
4. accept(fd ... )// return fd2 -> loop back to listen



# Remate Procedure Call

- Make socket communication between machines as seemless as possible

```c

main(){
  char* a = foo("hello");
}

foo(char * s){
  /* series of calls to open socket read write and close then return*/


}
```

## What is the big deal?

### Marshalling

- Endianness, make sure that the architecture  and nonsense so bytes are interpretted properly
- Linked lists being sent back and forth need to be flattened to be serialized 







