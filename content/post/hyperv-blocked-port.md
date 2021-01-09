---
title: "Hyper-V Blocked Port"
date: 2021-01-09T17:18:12+05:30
tags: [windows]
categories: [windows]

---


## Issue:
We noticed an issue following Windows 10 update 1809 where Windows would reserve a range of ports that included port 50,000. Sometimes even 1303 (node) or 2181 (zookeeper) or IntellijIDE default ports.

When you check which process is using the current port using the command

`netstat -an`

We find that the port is not being used. These ports are being reserved by docker or Hyper-V.


## To find ports reserved by docker/Hyper-V

`netsh interface ipv4 show excludedportrange protocol=tcp`


##Solution

### Solution 1

We need to reset the same. This can be done by

`netsh int ipv4 set dynamic tcp start=51001 num=5000`
and then restart.

### Solution 2
If the above approach does not work then the below script should be run from cmd as Administrator

```
rem Modify Dynamic Port Range for Development Users
dism /online /get-features | find /i "Microsoft-Hyper-V" && (
rem Modify Dynamic Port Range
start /wait "" netsh int ipv4 set dynamicport tcp start=20000 num=16384
start /wait "" netsh int ipv4 set dynamicport udp start=20000 num=16384
rem Add Registry Key
start /wait "" reg add HKLM\SYSTEM\CurrentControlSet\Services\hns\State /v EnableExcludedPortRange /d 0 /f
goto :eof
)
rem Set range to default
start /wait "" netsh int ipv4 set dynamicport tcp start=49152 num=16384
start /wait "" netsh int ipv4 set dynamicport udp start=49152 num=16384
rem Remove Registry Key
start /wait "" reg delete HKLM\SYSTEM\CurrentControlSet\Services\hns\State /v EnableExcludedPortRange /f
```

