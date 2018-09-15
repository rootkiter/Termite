---
name :  Termite
---

# Usage

1. Node in service mode.

> $ ./agent -l 8888

2. Use admin (client mode) to connect the node above.

> $ ./admin -c 127.0.0.1 -p 8888

3. You will get a built-in shell and get help through the help command.

>> help

4. View current node topology.

>> show 
 0M
 +-- 1M

* There is currently only one node.
* Its ID is 1.
* M --> MacOS, L --> Linux, W --> Windows

5. Add a new node ( client mode ).
> ./agent -c 127.0.0.1 -p 8888

6. View current node topology.
 0M
 +-- 1M
 |   +-- 2M

* Now there are two node, and the 2 node is located below the 1 node.

7. Binding a socks service for node 2 at the local port.
>> goto 2
    Switch 2 node.
>> socks 1080
    A 1080 port socks service will appear on the local machine, but the provider of the service is node 2.
    localhost:1080 -----> [@2-node] socks service.

8. Binding a shell services for node 1 at the local port.
>> goto 1
>> shell 7777
    nc 127.0.0.1 7777,  you will catch it. And the provider of the service is node 1.
    localhost:7777 -----> [@1-node] shell console.

9. Download file from remote node.
>> goto 1
>> downfile 1.txt 2.txt
    [@1-node] 1.txt ------> [@localhost] 2.txt

10. Upload file from local machine.
>> goto 2
>> upfile 2.txt 3.txt
    [@localhost]  2.txt ------> [@2-node] 3.txt

11. Port forward
>> goto 2 
>> lcxtran 3388 10.0.0.1 3389
    localhost:3388 -------> [@2-node] 10.0.0.1:3389


# Videos [Chinese...]
    http://rootkiter.com/toolvideo/toolmp4/1maintalk.mp4
    http://rootkiter.com/toolvideo/toolmp4/2socks.mp4
    http://rootkiter.com/toolvideo/toolmp4/3lcxtran.mp4
    http://rootkiter.com/toolvideo/toolmp4/4shell.mp4
    http://rootkiter.com/toolvideo/toolmp4/5file.mp4

# Author:
    rootkiter@rootkiter.com
