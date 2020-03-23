# How to flush DNS cache of networker

Networker is caching DNS entries which might lead to undesirable results when you are debugging connectivity issues and you need to update DNS entries. Networker would continue to use the cached entries. But you can clear the cached entries during runtime.

Below you see and example for

## Windows

First you need to get the process ID (PID) of the networker server daemon

```
C:\Users\Administrator>tasklist -fi "imagename eq nsrd.*"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
nsrd.exe                       920 Services                   0     23'724 K
```
now you can send this process a signal to flush the DNS

```
C:\Users\Administrator>C:\Program Files\EMC NetWorker\nsr\bin>dbgcommand.exe -p 920 FlushDnsCache
```
