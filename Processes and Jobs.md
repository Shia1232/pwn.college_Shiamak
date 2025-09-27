# Processes and Jobs  
## Listing Processes  
First, we will learn to list running processes using the ps command. Depending on whom you ask, ps either  
stands for "process snapshot" or "process status", and it lists processes. By default, ps just lists the processes  
running in your terminal, which honestly isn't very useful:  
```
hacker@dojo:~$ ps
    PID TTY          TIME CMD
    329 pts/0    00:00:00 bash
    349 pts/0    00:00:00 ps
hacker@dojo:~$
```
In the above example, we have the shell (bash) and the ps process itself, and that's all that's running on that  
specific terminal. We also see that each process has a numerical identifier (the Process ID, or PID), which is a  
number that uniquely identifies every running process in a Linux environment. We also see the terminal on which  
the commands are running (in this case, the designation pts/0), and the total amount of cpu time that the process  
has eaten up so far (since these processes are very undemanding, they have yet to eat up even 1 second!).  

In the majority of cases, this is all that you'll see with a default ps. To make it useful, we need to pass a few  
arguments.  

As ps is a very old utility, its usage is a bit of a mess. There are two ways to specify arguments.  

"Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including  
arguments. These can be combined into a single argument -ef.  

"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a  
terminal, and u for a "user-readable" output. These can be combined into a single argument aux.  

These two methods, ps -ef and ps aux, result in slightly different, but cross-recognizable output.  

Let's try it in the dojo:  
```
hacker@dojo:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
hacker         1       0  0 05:34 ?        00:00:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7       1  0 05:34 ?        00:00:00 /bin/sleep 6h
hacker       102       1  1 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server --auth=none -
hacker       138     102 11 05:34 ?        00:00:07 /usr/lib/code-server/lib/node /usr/lib/code-server/out/node/entr
hacker       287     138  0 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server/lib/vscode/ou
hacker       318     138  6 05:34 ?        00:00:03 /usr/lib/code-server/lib/node --dns-result-order=ipv4first /usr/
hacker       554     138  3 05:35 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server/lib/vscode/ou
hacker       571     554  0 05:35 pts/0    00:00:00 /usr/bin/bash --init-file /usr/lib/code-server/lib/vscode/out/vs
hacker       695     571  0 05:35 pts/0    00:00:00 ps -ef
hacker@dojo:~$
```
You can see here that there are processes running for the initialization of the challenge environment (docker-init),  
a timeout before the challenge is automatically terminated to preserve computing resources (sleep 6h to timeout  
after 6 hours), the VSCode environment (several code-server helper processes), the shell (bash), and my ps -ef  
command. It's basically the same thing with ps aux:  
```
hacker@dojo:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
hacker         1  0.0  0.0   1128     4 ?        Ss   05:34   0:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7  0.0  0.0   2736   580 ?        S    05:34   0:00 /bin/sleep 6h
hacker       102  0.4  0.0 723944 64660 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       138  3.3  0.0 968792 106272 ?       Sl   05:34   0:07 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       287  0.0  0.0 717648 53136 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       318  3.3  0.0 977472 98256 ?        Sl   05:34   0:06 /usr/lib/code-server/lib/node --dns-result-order=
hacker       554  0.4  0.0 650560 55360 ?        Rl   05:35   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       571  0.0  0.0   4600  4032 pts/0    Ss   05:35   0:00 /usr/bin/bash --init-file /usr/lib/code-server/li
hacker      1172  0.0  0.0   5892  2924 pts/0    R+   05:38   0:00 ps aux
hacker@dojo:~$
```
There are many commonalities between ps -ef and ps aux: both display the user (USER column), the PID, the TTY,  
the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND). ps -  
ef additionally outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in  
question, while ps aux outputs the percentage of total system CPU and Memory that the process is utilizing. Plus,  
there's a bunch of other stuff we won't get into right now.  

Anyways! Let's practice. In this level, I have once again renamed /challenge/run to a random filename, and this time  
made it so that you cannot ls the /challenge directory! But I also launched it, so you can find it in the running  
process list, figure out the filename, and relaunch it directly for the flag! Good luck!  

NOTE: Both ps -ef and ps aux truncate the command listing to the width of your terminal (which is why the  
examples above line up so nicely on the right side of the screen. If you can't read the whole path to the process,  
you might need to enlarge your terminal (or redirect the output somewhere to avoid this truncating behavior)!  
Alternatively, you can pass the w option twice (e.g., ps -efww or ps auxww) to disable the truncation.  
### Solve  
**Flag:** `pwn.college{4BYs7-QjdoUxS-oQ0sSG74Yq3h6.QX4MDO0wCN1kjNzEzW}`  
I listed all the processes and found the one which is in /challenge and re-ran it to get the flag
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 03:17 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 03:17 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 03:17 ?        00:00:00 /challenge/32511-run-17776
root         135     132  0 03:17 ?        00:00:00 sleep 6h
hacker       137       0  0 03:17 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       143     137  0 03:17 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       161       1  0 03:17 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disableLeaveAlert true
hacker       165     161  0 03:17 pts/1    00:00:00 /run/dojo/bin/bash --login
hacker       175     143  0 03:17 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   03:17   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7  0.1  0.0 231708  2560 ?        S    03:17   0:00 /run/dojo/bin/sleep 6h
root         132  0.0  0.0   4132  2560 ?        S    03:17   0:00 /challenge/32511-run-17776
root         135  0.0  0.0   2744  1280 ?        S    03:17   0:00 sleep 6h
hacker       137  0.1  0.0 231576  3520 pts/0    Ss   03:17   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       143  0.0  0.0 231940  4160 pts/0    S    03:17   0:00 /run/dojo/bin/bash --login
hacker       161  0.1  0.0  36972 21760 ?        Sl   03:17   0:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.0 --writable -t disable
hacker       165  0.0  0.0 231940  4160 pts/1    Ss+  03:17   0:00 /run/dojo/bin/bash --login
hacker       176  0.0  0.0 233600  3840 pts/0    R+   03:17   0:00 ps -aux
hacker@processes~listing-processes:~$ /challenge/32511-run-17776
Yahaha, you found me! Here is your flag:
pwn.college{4BYs7-QjdoUxS-oQ0sSG74Yq3h6.QX4MDO0wCN1kjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```
### New Learnings  
I learnt how to list processes using ``ps -ef`` and ``ps -aux``.
### Resources  
## Killing Processes  
You've launched processes, you've viewed processes, now you will learn to terminate processes! In Linux, this is  
done using the aggressively-named kill command. With default options (which is all we'll cover in this level), kill  
will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.  

Let's say you had a pesky sleep process (sleep is a program that simply hangs out for the number of second  
s specified on the commandline, in this case, 1337 seconds) that you launched in another terminal, like so:  
```
hacker@dojo:~$ sleep 1337
```
How do we get rid of it? You use kill to terminate it by passing the process identifier (the PID from ps) as an  
argument, like so:  
```
hacker@dojo:~$ ps -e | grep sleep
 342 pts/0    00:00:00 sleep
hacker@dojo:~$ kill 342
hacker@dojo:~$ ps -e | grep sleep
hacker@dojo:~$
```
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/  
dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all  
knowledge of your mission. Good luck.  
### Solve
**Flag:** `pwn.college{855haXXkj_Ug03oo_rj604aIUBY.QXyQDO0wCN1kjNzEzW}`
I listed the processes while grepping for dont_run and then just killed it using its PID.  
Then I ran /challenge/run to get the flag.  
```
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker       136     135  0 03:23 ?        00:00:00 /challenge/dont_run
hacker       178     145  0 03:23 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker       180     145  0 03:24 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{855haXXkj_Ug03oo_rj604aIUBY.QXyQDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to kill a program on the shell.  
### Resources  
## Interrupting Processes  
You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of  
the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down  
the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and,  
typically, this causes the application to cleanly exit.  

Try it here! /challenge/run will refuse to give you the flag until you interrupt it. Good luck!  

---------------------------------------------------------------------------------------------------------------------  
For the very interested, check out this article about terminals and "control codes" (such as Ctrl-C).  
### Solve  
**Flag:** `pwn.college{49VxKdOKPM9oUa2dAzOSbCxOk4H.QXzQDO0wCN1kjNzEzW}`
I ran /challenge/run and then interrupted it with CTRL + C to get the flag.  
```
hacker@processes~interrupting-processes:~$ /challenge/run 
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{49VxKdOKPM9oUa2dAzOSbCxOk4H.QXzQDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to interrupt a process.  
### Resources  
## Killing Misbehaving Processes  
Sometimes, misbehaving processes can interfere with your work. These processes might need to be killed...  

In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo  
into which (like in the Practicing Piping FIFO challenge) /challenge/run wants to write your flag. You need to kill  
this process.  

Your general workflow should be:
1. Check what processes are running.
2. Find /challenge/decoy in the list and figure out its process ID.
3. kill it.
4. Run /challenge/run to get the flag without being overwhelmed by decoys (you don't need to redirect its  
   output; it'll write to the FIFO on its own).
Good Luck!
---------------------------------------------------------------------------------------------------------------------------------  
NOTE: You might see a few decoy flags show up even after killing the decoy process. This happens because Linux  
pipes are buffered: conceptually, they have a sort of length through which data flows, and you might kill the decoy  
process while data is in the pipe. That data, having already entered the pipe, will proceed to the other end (your  
cat). If you wait a second, you'll see the decoys stop, and then you can /challenge/run and win!pwn.college{UXZtU11A3kpLrgus0jyXa0YyD0V.0FNzMDOxwCN1kjNzEzW}
### Solve 
**Flag:** `pwn.college{UXZtU11A3kpLrgus0jyXa0YyD0V.0FNzMDOxwCN1kjNzEzW}`
I killed the process and then ran /challenge/run to pipe to to the fifo and then opened another terminal and used ``cat`` to read it.  

<img width="1517" height="231" alt="image" src="https://github.com/user-attachments/assets/6d58565a-40cc-4d26-ac85-f8a588bc2b7c" />

```
hacker@processes~killing-misbehaving-processes:~$ ps -aux | grep decoy
root         139  0.0  0.0   5204  3520 ?        S    03:37   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       142  0.1  0.0  13516  9280 ?        Ss   03:37   0:00 /usr/bin/python /challenge/decoy
hacker       183  0.0  0.0 230696  2560 pts/0    S+   03:37   0:00 grep --color=auto decoy
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ kill 139
bash: kill: (139) - No such process
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
```

<img width="792" height="994" alt="image" src="https://github.com/user-attachments/assets/5fba1a02-217f-440b-800b-bb8afbc63c66" />

<img width="792" height="994" alt="image" src="https://github.com/user-attachments/assets/47d9c1c4-7b8f-425e-a077-d28eb6e2aae3" />

```
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{yYe2TiL8q5XFwe11tvbR9y60CRRxfrKfK4x3NOcZltIVZMz}
pwn.college{Quyf0BNciBTo5o6o4e7OezNrhCFH.zKRjtgCYm4A9b3n92Q}
pwn.college{tH-wa391LytwEk4B55B2hMjMRJlX-gHAMx.u3kL9DyW1zEI}
pwn.college{PFLISw9VYxXUvNLz7ECKo6kPhc2s8.fjaeee4MQKJkOHDFY}
pwn.college{TR-IO9cKF.-2DWhG6NszP8DvDgF8kRWiHYT7JUp56jOpZ9d}
pwn.college{PIiF.PavJ2CHTKcVt0vs7HGPAope3adjlOfbY.Tway1PXiV}
pwn.college{HkJnywTC284CrzrypJ-C92Md1KtCXC.DKNLgvsZXrtbwa8O}
pwn.college{aSgfNAH.JgNjG6b3sGtmtdvdS6aQL-1KhJZDqEQtPuBRRrv}
pwn.college{RvH8-utR1t4zWrkONeYl3y6C.eTQEq1Zw9ilxu-CtMT4HAm}
pwn.college{2bRtmdFr.Z8qchnrfUhNMgHA-V17u2SQwzpAWttUswhL3X.}
pwn.college{yuyKivj9SJY3ycaTqSZS3lvtChvMyelHTU59fvxlzwbhK6X}
pwn.college{Z2WUx4aAVhkzHk0jDN8IvId8bdJiHDfArHdsHG5EhbHaDYh}
pwn.college{3foYe93j3xankCWYoKMRE47DUyHh5UKdU8ybe7gVYCH1Avr}
pwn.college{npnrHg.dvZMSNr5JZQMLHrfn148Gg0z6v63a7OuYq20V9TT}
pwn.college{iXjUoNBpTyB3cZDQToNJTtwDkOX9PJtjxlMHUBAfkjHWQ3e}
pwn.college{rFlvm6FfXi6E4HaHw-XWEb3kGzYUbLAfC-CPzC9gF.lhTu6}
pwn.college{7itJweMBjXdVWp0VQQxvlb8taza9AhvcDiKiO3cXa9EFoWU}
pwn.college{JLq2wnUSCKX-KEv51fYNnSRdbj7VHez1NkNp0r2cqvWK0LX}
pwn.college{VPkFlkFds7URrE.98aq2yE0X3WeVtAcT6486uNoMf4xrC.6}
pwn.college{SLJ4vuI0Bgr-FGiJOOTbHiEXD-wnj3FfPWbaRtzyzmYYq7o}
pwn.college{3oQEba7MzSMzTxZEEB6Y0WKD3k4QNrqKZfAufMQqIg4HTaB}
pwn.college{RVtrQHgL4bNoXbrtCLYmo7JeHViPOU7OuMRFSpkVm9Av9NB}
pwn.college{.tr08jgcm32YO-ZfUV6HUNCMRt-UusKCoyYSRZIt4DisPFb}
pwn.college{3jS5QgpaV7xD3oN2Hbl4nLmfUDgpRU4efe.4qKTDJvEuewo}
pwn.college{HBmmOPFSEKtHhguZZcNfxh56xFJr4jeaahWK.YjPCky0mwP}
pwn.college{XKwR4Ol4SdWjD7AbKTwbHpPa-3IKy5DxBEi4l8te4ujQgJF}
pwn.college{he8OonwRSHwVXD6wZ0LUpQOCFLAdJthiFIqx3Tbf91ZzLhe}
pwn.college{cpq8BKRMowUoEZ3GXshU2TbMO6UE5icxJFg8A34JskmVNKY}
pwn.college{zjNeRsM7j6AZJb49.-edXpLuTiq-U5oG-4jgi5EbwFVnriV}
pwn.college{6LmVzQaWfFzpSz2xykI71jWlWMztp6mXlKPfG1CfjEKVfmF}
pwn.college{yY4-25myb7ioqYS0B3D5707Nz49FYWSbU0Fy-kBCnBkz8uu}
pwn.college{ipAqIKyE.s8iS6AYi-TgmzyPZn5GCXnffCippxbsD9OJx29}
pwn.college{dC9s2Js1TsFYm9iy-XDYr2lXivUdb3SQtfaFV2DwfNqMabC}
pwn.college{8eHbxXAkgNqhRsYREt-fbK2qQaUi.7ROQ0KIro08SVY3NiH}
pwn.college{qwUFt32V5DjnMKww9YOut06Z4gV.AmAn7MLK.wSUrvj-Tct}
pwn.college{sVG7eZJRaU7jLgl8Dog.vFnf7ILA8RsFapyi5VWqCb23w9x}
pwn.college{QFFhZ-ymZB8Z3LDZdVk7daPgwvqcCwDEHt59quV.qDFqT9q}
pwn.college{8wOEtucH3unKANEARUxOJLD643orWHzcn795AxKg6.pTYLl}
pwn.college{VqZixxxC1grmaelxWRTQ675J8GAz9IhDESfAIi0XP2TYUBh}
pwn.college{WUwU9UA6HM3ykIvTgwoP.tgJM1ucoXBd900OgJ9QboOOSdK}
pwn.college{LjElIQSXL.74w9Vr5pQ6KSg5R-arl0BJMW4EO3kH5ulnc5Z}
pwn.college{pCGk-zeWI7zOLwn4HxqX2Zyw5WcdNbdKpYDbdRKat1h0feb}
pwn.college{rA6l4kCoBqJvINUrGe8-ZdZekwMfWV1A9DJ4Wuk3.p2DYEW}
pwn.college{NDlKw9HXgH.T7pZL1SN.g5WRjaWAe6dSPFmi0VTMVTFpEir}
pwn.college{zRBVIef1Y48d9XFT24n5CnbG5JtwYGSnZt6b.HP49D1iFrv}
pwn.college{G-u9xu2gN-MW179BRhtda285VItC9O0bp84IqIWdCNcW5Y1}
pwn.college{NubUfBGiPOikeQe5ERd2pYbnp1E2WRZWt5r5-Vd5xb48n9L}
pwn.college{PXgQQlvgJMp8QzzeZWsFuEN1b9gJlxgQmQ.FuLpT5dO9usB}
pwn.college{HNK2E.hGUN9W01ldl1SO.47BmhOKyDBlM9.1SCMMJtOEpVL}
pwn.college{K7OJhiNAeZdw.T0imzV7GUPP1ZL59n1urK-jzFOCu-7OVbO}
pwn.college{a4MQ4My.Lf18x1b9iLmAd5bgLTlXjt0qLR97gTYj2cnWRz4}
pwn.college{AJK01KaVwDKABmo10NmvVhzTLAxu0B3D0MhWvGujjBTyDG5}
pwn.college{u-ISSXwmt8D7NPeehH4MC529Yf7.TgZInJNPs-OotT6zvQK}
pwn.college{KIj9Cc-mZ.vgwgeHJE6Nh62QD8F0jzd4bND33Xyzcfwlf03}
pwn.college{uRETKqxuxu9l-qdFB7bmgTM0jo1xDoq13UcSIW.axp0XrHJ}
pwn.college{dWtRH5DOtYyNxHI8YCN8OblnW9g6H3fYdqcsE2NGkBmFmN.}
pwn.college{b619hdKb4AeZZ8-nVkYoArIqye5YmUOAV4UzMpTweGUTkCk}
pwn.college{XnPwK6-rbXHPfTiT5dF936D1Ay33as9V8UJj9xuHOX6I-7d}
pwn.college{rhfd7guKoZEXFTLjDZCiAY6.rz6pNHhOob4e6oa4PMJE5jC}
pwn.college{ZQr60G3U5n1Tw6mYfgf084.WaTp8a6E3zok5t0hGoCNHM84}
pwn.college{tpou5VjVbZXYBlxX7otHgqmzVSKBbft5UZh.C84AKlJeCAH}
pwn.college{EmrZareN6QTQCFpnVYiBZH5AVRfrBi6hERibOIqHIbxNm2X}
pwn.college{xxQiyMEanNAJDgwKHk82AjVflpFlZLfDVJxrHg.18OnKG9A}
pwn.college{dIqwp9Lt1uqiXNZiEJXB4vu81THd54I3F4VG7WIXiBVWEP3}
pwn.college{JHfEadTayBtWBQ2AHYr1K-tuM6vI0QzwOqx5d9aqJmSek69}
pwn.college{NQ55PtsOg0wf6KtbdeDcuUn8EAtK8LA5QO0UAUcN3v43Ud2}
pwn.college{Dj8q39JD.BMGk17RyTtHYTwLCyEJ1eNEBDsIIaaIyiC3cX6}
pwn.college{yzi9KVuzmfo7Qvq.fEUDgjCSkid4bdpShZLmhjl7206bnp5}
pwn.college{GkdD.4fSM6Y.92jOSMNIQt9vhtdxVJ3To6BQ0h2l45v5Ope}
pwn.college{IHteIqNxC7Sh19W0lPXvhFJuFbh5.ZXgHHOjcUg1a5fFIf3}
pwn.college{QcxIo3Logjqsf3fV7c74rc4wXDTlIEGFAOZSLWRVVauJYO.}
pwn.college{2Bzsmf3gSu8wkX.HC8YrEe54zzUFrlSnR7Q1dEkn3a8Xlgb}
pwn.college{v5.Cz1Uw1jy62g4jQRUyBfqTT3VVnormNgGCzPa0irltFNR}
pwn.college{Gc8Xg3pcIoHmS7bjjb6VNgd.2jAoCq0fuHyo.fJTUEcmkZw}
pwn.college{5hwSrkpKT9YsEwIZPlHSHLzc5lAAdVsv1dtxNa2IelNsxnI}
pwn.college{fYKBdHm.ZLcICN8.6nJ7XUNg1rVIJsMcWp6F43hIYNv38K8}
pwn.college{APcmETr8S4KrqDw9cvFkOVzBf3cy7SbeMwXX2wVt8L9QlWF}
pwn.college{yu2SGGd2uDKVXHCeddpBzinroZwBY6Ab.nVk8hdR3rpwcjx}
pwn.college{yrGstSXAo1KF4HJw7ame3vJFHhb.KudQq8gr81tOX9GrpHM}
pwn.college{toLp0Bt1Yi2FBiDUhnKQ4oP3aiAKBHLWquDNJ6Tdmr1iRl5}
pwn.college{H51O0IGzjVfoHN0fdTmGhkJWbXsMUcFi.aD2GfSmaoljPGt}
pwn.college{9kG7nIqLqrwOwPZfcvhRwBRzpheyvcfr-8tMr8FzXR.Rv-L}
pwn.college{2Hp1IpQ.awlfAtMvoluRr3-JEF-cwIFTiLK555TImphI1zn}
pwn.college{mlhq5.wRT36HzhxGUMA8mLpBZ6kfAFOa5bJeVu-TEHUhWjO}
pwn.college{doSugDHW.szobLzJwj2jrDILRkn9OESHvTgzViv3MLo9.qA}
pwn.college{rx.xKfQZ6dajLXjiF.f1SDiYID3ENYYaaofZKlIp4hp4-oE}
pwn.college{DGjdB15GwMlRDauXXZDG9IIEJGSoQYWjIcTU2uGk4KW2C4T}
pwn.college{EYKJnzM5fI9ZnjBq-hS9BmPOdttt4YTshNmBZE2OxpduY1t}
pwn.college{q0-PjvAWoCZlkwU16JQu4OpQe987ANrwb.KJNg1IfC4wG-3}
pwn.college{jcA0YRtD4gAGtBM03W-SsOEvpe-q11fLbMxwG.DMbFipE-3}
pwn.college{GSgOACH39AJfJg1ZeRpt-LHtg3vo3h3uzXwJCyrT1m.weSZ}
pwn.college{mDNcDUZGAzIgfmJA6Hdhnt3SGElJFSh2a.XuaOLhQKQXfRk}
pwn.college{wm4RYYe5ZBw8t0K8Y2f6U8eif0M9zdzZAo0HcW3pRkBa-ft}
pwn.college{yD4WR6FKBpUeEndJoqv5vlmkVKkHvnjrzjWMvlpEExtMhG5}
pwn.college{kXF35SYod9mN.D7gf-EdtCsk9gB6zWTYELzTZAJ54fB3Ass}
pwn.college{5qes-QyKIQ7AoMzodw19rdAXaaE7B2Q6f0Pya4MuJ5nRWxV}
pwn.college{bBjgVEW0MuBD.EXOOTKI1cqXmeu7H0kX0c1HcTI4prXmukr}
pwn.college{3ZBZf.J-fGJpRO8GYRcCmZDyhkEX8TLjY5ItejX.DLG95z3}
pwn.college{.blc7T06iRZh6XiX5bUvoGZW-fIDF46.qt1DaLonsE0pA1M}
pwn.college{B2dT3-vhcbBLqqGJKoDK7zL677fyzt25S5AziP7TuwHHeK.}
pwn.college{qaNj.c3nrxHbBY3BiiN8nlnu3Jcvq1E.Z8la7mBbNtp5iCC}
pwn.college{G4YMEesDmawrnGG74WcDizribXSK7I2SYS5jDci20LFOU7T}
pwn.college{b0E4lotzOcowG8N.evm-8oTwWwaF1fNl20NfYcoDLWYH83U}
pwn.college{XphInCyWZcGAUTEXXp.72hPfpIZBBW-Kb1tQZTkEgrSaP.C}
pwn.college{PIelTI5VU5A9fAs-HIzfQUL1peHuV--NMGsI4d8KCaTJcqp}
pwn.college{6752AZWd2crYDPVJ5YHmFU7gMvtAGMbM6IwjWMrDi3NP2yp}
pwn.college{iuFPMuMl-GF9fFoYe0MeDV9tyiKKoilKDIzAVIjHntrl.rI}
pwn.college{iJ8QHSUkTgqVZmJA5VJ1cw-IR9NRNKLW7zGYKH2WojGBRhw}
pwn.college{no3P1q.gWghnkf.ll-QvWX2pDT5rsW6cYnZKJ61-7ZaJDiK}
pwn.college{DKwmoyM5BzggJwpHDNqKAXv05X6LaF4ef68Ts1ng7ZRcDUr}
pwn.college{Bf1wMTA06-QPARpt.0swX25qwDKPZMqharWWisU2YQWdtRQ}
pwn.college{-L7dXSOZHz-gU4JqWz3IPBzCfbyTNr48sZNd-OCbqCqyMo8}
pwn.college{5C5AdaaOZLkdW1D1V7Br0QREu6BKL1iAehs6B.tAPEkQrnt}
pwn.college{ZkvaslSEUzVumFimpNACFYwhOhH2BaepDq427AOpJoEl0EO}
pwn.college{wGn0XgKfAdA9Nh72v0BQ3fIieaYAebsIDGUiMwEsytTYM63}
pwn.college{pZQ5rmTV04p58xeU1z4xlHVvWsyT8C2NI0Av8Bw70W3e6Fj}
pwn.college{DtQbLmx9ZCReUN6RD0UM3L6wJZRHUUHmTYHFqyzZBLJNQNU}
pwn.college{DOgfYXCMLlkjdgtRY86-uweB5X4MRStpRFwdCJXGAPneUGq}
pwn.college{877bYU8ihByzB0dkAu-TY0VKMJY67Fo.SGGeh1f-U49sbYp}
pwn.college{po2sJrPEv4oFhuYmXvOYSworrGeYVEeuYCFvNm4Mjy94GHz}
pwn.college{cM6t1cgttnYb4BktYbvsXjSUnYB2U5ZwQuNGmJibxglrW57}
pwn.college{-e-vHF8H2Ojop5vq-48tgN.mnIxAkrKOSPajuNC4-m6Auiq}
pwn.college{8ZTj5oGiToRgBN3i2g-lMzIgyv01jMDDisXbISgjCMn5wJW}
pwn.college{4qpt8-bkCOGVQOw2ESBdLLRo74ZWl9UFUBK3YP664xouno0}
pwn.college{aDdWYK9dK0h1eHnTNV8a4qot2MpxGwOC4zk1PYsQBHv5hb6}
pwn.college{ToVOkB2uvQ-oGS8YqIPbuKk9ndKZepVJzVSwHVpa4u6sIZ0}
pwn.college{SGG8RzkbCQZt.A17h1rnszEB5u7iOBdbxvig0T6flX0B1Ow}
pwn.college{bK-tGOTZ.5WLBCKXnYsPdSQia0aKK2qZfU5yxdJp2xk2nvZ}
pwn.college{ySCHEBn8FHPha2THjUss9ItmYHh-ILBCIaVrsBq2l8rQRjQ}
pwn.college{bIJ-qOb5T-11plFeegMOuaW3HDTxyeC4dSmw1O5q.Ali5Dp}
pwn.college{YXACX20WiPlSb1divM2eYhn1tAmTCWkG47Cu0L7eSfw8XIV}
pwn.college{UxXTUVyKPbH4Fa9MJxJNpJPAtcEczzMVDvqB-010jxVwInd}
pwn.college{jf.w.Z39PA3IquDocbtmYP.8spRViQyZyfejoK8gCF.gJin}
pwn.college{b3gbLVDOb13XVH.PZG89oUnOmD3M6OxkI238USk.1AHQgdu}
pwn.college{UXZtU11A3kpLrgus0jyXa0YyD0V.0FNzMDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to kill misbehaving programs.  
### Resources  
## Suspending Processes  
You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get  
your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this  
works and, in the next level, we'll figure out how to resume those suspended processes!  

This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to  
launch it, then suspend it, then launch another copy while the first is suspended!  
### Solve  
**Flag:** `pwn.college{wWeh9A-_U8dXdXRWm6lCRMDO_XK.QX1QDO0wCN1kjNzEzW}`  
I suspended /challenge/run and then ran it again to get the flag.  
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         176     149  0 03:50 pts/1    00:00:00 bash /challenge/run
root         178     176  0 03:50 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         176     149  0 03:50 pts/1    00:00:00 bash /challenge/run
root         183     149  0 03:50 pts/1    00:00:00 bash /challenge/run
root         185     183  0 03:50 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{wWeh9A-_U8dXdXRWm6lCRMDO_XK.QX1QDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to suspend a process using CTRL + Z.  
### Resources  
## Resuming Processes  
Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just  
terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended  
process, resumes it, and puts it back in the foreground of your terminal.  

Go try it out! This challenge's run needs you to suspend it, then resume it. Good luck!  
### Solve  
**Flag:** `pwn.college{Yhet3HYeByzSA8dEBojcCbWXPUd.QX2QDO0wCN1kjNzEzW}`
I ran /challenge/run then suspended it with CTRL+Z and then foregrounded it with ``fg``.  
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{Yhet3HYeByzSA8dEBojcCbWXPUd.QX2QDO0wCN1kjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```
### New Learnings  
I learnt how to resuming a process after suspending it.  
### Resources  
## Backgrounding  Processes 
You've resumed processes in the foreground with the fg command. You can also resume processes in the  
background with the bg command! This will allow the process to keep running, while giving you your shell back to  
invoke more commands in the meantime.   

This level's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use  
the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is  
running in the background!  

-----------------------------------------------------------------------------------------------------------------------  
ARCANUM: If you're interested in some deeper details, check out how to view the differences between suspended  
and backgrounded properties! Allow me to demonstrate. First, let's suspend a sleep:  
```
hacker@dojo:~$ sleep 1337
^Z
[1]+  Stopped                 sleep 1337
hacker@dojo:~$
```
The sleep process is now suspended in the background. We can see this with ps by enabling the stat column  
output with the -o option:  
```
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 T    sleep 1337
hacker       782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```
See that T? That means that the process is suspended due to our Ctrl-Z. The S in bash's STAT column means that  
bash is sleeping while waiting for input. The R in ps's column means that it's actively running, and the + means that  
it's in the foreground!  

Watch what happens when we resume sleep in the background:
```
hacker@dojo:~$ bg
[1]+ sleep 1337 &
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 S    sleep 1337
hacker      1224 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$
```
Boom! The sleep now has an S. It's sleeping while, well, sleeping, but it's not suspended! It's also in the background  
and thus doesn't have the +.  
### Solve 
**Flag:** `pwn.college{gI4F2L5ix-LfIlk4_WWxj1HvQZz.QX3QDO0wCN1kjNzEzW}`  
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         161 S+   bash /challenge/run
root         163 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         161 S    bash /challenge/run
root         171 S    sleep 6h
root         172 S+   bash /challenge/run
root         174 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{gI4F2L5ix-LfIlk4_WWxj1HvQZz.QX3QDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to suspend a program and then resume it in the background.  
### Resources  
## Foregrounding Processes  
Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do?  
Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level  
will walk you through that!  
### Solve
**Flag:** `pwn.college{QtvVDFHS49NIAmz-bkoS36F4K42.QX4QDO0wCN1kjNzEzW}`
I suspended /challenge/run and then resumed in the background by using ``bg`` and then foregrounded it  
by using ``fg``.  
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{QtvVDFHS49NIAmz-bkoS36F4K42.QX4QDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to foreground a background process.  
### Resources  
## Starting Background Processes  
Of course, you don't have to suspend processes to background them: you can start them backgrounded right  
off the bat! It's easy; all you have to do is append a & to the command, like so:  
```
hacker@dojo:~$ sleep 1337 &
[1] 1771
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker      1709 Ss   bash
hacker      1771 S    sleep 1337
hacker      1782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$
```
Here, sleep is actively running in the background, not suspended. Now it's your turn to practice! Launch /
challenge/run backgrounded for the flag!  
### Solve
**Flag:** `pwn.college{MyzUaJj8Qqn5FPcF6qcWHAwPsAd.QX5QDO0wCN1kjNzEzW}`  
I directly backgrounded /challenge/run while entering on the command line by appending a & and then  
running it.  
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 162
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{MyzUaJj8Qqn5FPcF6qcWHAwPsAd.QX5QDO0wCN1kjNzEzW}

[1]+  Done                    /challenge/run
```
### New Learnings  
I learnt how to directly background a process without suspending it.  
### Resources  
## Process Exit Codes   
Every shell command, including every program and every builtin, exits with an exit code when it finishes  
running and terminates. This can be used by the shell, or the user of the shell (that's you!) to check if the process  
succeeded in its functionality (this determination, of course, depends on what the process is supposed to do in the  
first place).  

You can access the exit code of the most recently-terminated command using the special ? variable (don't forget  
to prepend it with $ to read its value!):  
```
hacker@dojo:~$ touch test-file
hacker@dojo:~$ echo $?
0
hacker@dojo:~$ touch /test-file
touch: cannot touch '/test-file': Permission denied
hacker@dojo:~$ echo $?
1
hacker@dojo:~$
``` 
As you can see, commands that succeed typically return 0 and commands that fail typically return a non-zero  
value, most commonly 1 but sometimes an error code that identifies a specific failure mode.  

In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/  
submit-code with that error code as an argument. Good luck!  
### Solve  
**Flag:** `pwn.college{UKXvEzEzltIssQLbuvaChXZzjQD.QX5YDO1wCN1kjNzEzW}`  
I first ran /challenge/get-code and then echoed the error code and ran it as an argument to /challenge/submit-code  
to get the flag.  
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
63
hacker@processes~process-exit-codes:~$ /challenge/submit-code 63
CORRECT! Here is your flag:
pwn.college{UKXvEzEzltIssQLbuvaChXZzjQD.QX5YDO1wCN1kjNzEzW}
```
### New Learnings  
I learnt about process exit codes and how to find it out for a process after running it.  
### Resources  








