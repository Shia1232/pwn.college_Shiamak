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
**Flag:** ` `

