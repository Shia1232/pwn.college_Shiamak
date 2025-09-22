# Pondering Paths  
## The Root  
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files,  
programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you  
the flag. All you need to do for this level is to invoke this program!  
  
You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path,  
starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to  
as an "absolute path".  
  
Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!  
## Solve

**Flag:** `pwn.college{kGdnVCr8JTlDNyIhsQEtoG3meLd.QX4cTO0wCN1kjNzEzW}`  
```
hacker@paths~the-root:~$ /pwn  
BOOM!!!  
Here is your flag:  
pwn.college{kGdnVCr8JTlDNyIhsQEtoG3meLd.QX4cTO0wCN1kjNzEzW}  
```
### New Learnings  
I learnt the meaning of an absolute path and how basic directories work and about the root directory  
and learnt how to invoke a program by providing its path  
### Resources  

## Program and absolute paths  
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in  
the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the  
challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /  
challenge directory. Thus, the path to the run challenge program is /challenge/run.  

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file  
that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give  
you the flag. Good luck!  
### Solve
**Flag:** `pwn.college{Q6gLCwUaXSh2qYy98tS2B0zX3Xz.QX1QTN0wCN1kjNzEzW}`  
The thought proccess was to not run the directories one by one and then go to the run directory as that is using relative path but rather to use the concept of absolute path to directly run   the executable 'run' program  
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run   
Correct!!!  
/challenge/run is an absolute path! Here is your flag:  
pwn.college{Q6gLCwUaXSh2qYy98tS2B0zX3Xz.QX1QTN0wCN1kjNzEzW}   
```
### New Learnings
I learnt a little bit more complex application of an absolute path and how it is really used.  
### Resources  

## Position thy self 
 The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the  
 cd (change directory) command and passing a path to it as an argument, as so:  
 ```
hacker@dojo:~$ cd /some/new/directory  
hacker@dojo:/some/new/directory$
```
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a  
directory in which it's currently hanging out. The reasons for this will become clear later in the module.  
As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.  

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you).  
You'll need to cd to that directory before rerunning the challenge program. Good luck!  
### Solve
**Flag:** `pwn.college{oI44ihFnd90_dkLPb-Esdx4qz1s.QX2QTN0wCN1kjNzEzW}`  
Here, first I used pwd to check which directory I am in to give me a clue as to what I am supposed to do next.  
On showing it was in /home/hacker, I changed the directory to the root directory as I can access any sub-directories from there.  
I went to challenge using 'cd' and then tried to execute run directly.Upon trying, it told me i am not in the '/sys' directory.  
So I went to the '/sys' directory and executed /challenge/run to get the flag. At first I was very confused on what to do but then upon watching the video in the pondering paths  
module and also chatgpting i figured out that run is an executable and not a directory itself helping me massively in completing the issue.  
```
hacker@paths~position-thy-self:~$ pwd
/home/hacker
hacker@paths~position-thy-self:~$ cd /
hacker@paths~position-thy-self:/$ cd challenge
hacker@paths~position-thy-self:/challenge$ /challenge/run
Incorrect...
You are not currently in the /sys directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:/challenge$ cd /sys
hacker@paths~position-thy-self:/sys$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{oI44ihFnd90_dkLPb-Esdx4qz1s.QX2QTN0wCN1kjNzEzW}
```
### New Learnings
I learnt the difference between an executable and an directory(also an executable directory) and  
I learnt the usage of the 'cd' command and how to traverse through directories relatively.  
### Resources  
The File system video present in the module, askubuntu and chatgpt.  
## Position elsewhere  





