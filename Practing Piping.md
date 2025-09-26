# Practing Piping
## Redirecting output  


First, let's look at redirecting stdout to files. You can accomplish this with the > character, as so:  
```
hacker@dojo:~$ echo hi > asdf
```
This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to  
output this file:  
```
hacker@dojo:~$ cat asdf
hi
```
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename  
COLLEGE (all uppercase).  
### Solve  
**Flag:** `pwn.college{MkHyfnMqetoaGrHf2o2pfX_7ONO.QX0YTN0wCN1kjNzEzW}`  
I echoed the word PWN to the file COLLEGE using the ``>`` command to redirect the output and get the flag.  
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{MkHyfnMqetoaGrHf2o2pfX_7ONO.QX0YTN0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to redirect output using the ``>`` command.  
### Resources  
## Redirecting more output  
Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this  
level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag  
will, of course, end up in the myflag file!  

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's  
because it communicates its instructions and feedback over standard  
error, and only prints the flag over standard out!  
### Solve  
**Flag:** `pwn.college{8i_ol2NxQ8IhfO5vgLqCJT0PCFv.QX1YTN0wCN1kjNzEzW}`  
I first redirected the output from stdout to the myflag file.  
Then I just read the myflag file using the ``cat`` command to get the flag.  
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{8i_ol2NxQ8IhfO5vgLqCJT0PCFv.QX1YTN0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to redirect output using other commands other than echo.  
### Resources  
## Appending output  
A common use-case of output redirection is to save off some command results for later analysis. Often times,  
you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this  
case, you might want all that output to keep appending to the same file, but > will create a new output file every  
time, deleting the old contents.  

You can redirect input in append mode using >> instead of >, as so:  
```
hacker@dojo:~$ echo pwn > outfile
hacker@dojo:~$ echo college >> outfile
hacker@dojo:~$ cat outfile
pwn
college
hacker@dojo:$
```
To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The  
practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the 
file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in  
truncation mode (>), the second half will overwrite the first and you won't get the flag!  

Go for it now!  
### Solve  
**Flag:** `pwn.college{oCUTVzcg1fCHMtjp4hQoeG52PoS.QX3ATO0wCN1kjNzEzW}`
I used the redirecting of output mode to not overwrite the first part of the flag already present in /home/hacker/the-flag.  
```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{oCUTVzcg1fCHMtjp4hQoeG52PoS.QX3ATO0wCN1kjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```
### New Learnings  
I learnt how to appedn the redirected using the ``>>`` command so that the output already written there is  
not over-written.  
### Resources  
## Redirecting errors  
Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File  
Descriptor numbers. A File Descriptor (FD) is a number that describes a communication channel in Linux. You've  
already been using them, even though you didn't realize it. We're already familiar with three:  
+ FD 0: Standard Input
+ FD 1: Standard Output
+ FD 2: Standard Error
When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). Thus, the following two commands are equivalent:

