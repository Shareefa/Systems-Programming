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

