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
The File system video present in the module, [Askubuntu](https://askubuntu.com/questions/862289/difference-between-executable-directory-vs-executable-files) and Chatgpt.  
## Position elsewhere  
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
## Solve
**Flag:** `pwn.college{ItCoBlRsqU4yAl2KjGzBDIZ0Xfp.QX3QTN0wCN1kjNzEzW}`  
```
hacker@paths~position-elsewhere:~$ cd /  
hacker@paths~position-elsewhere:/$ cd challenge  
hacker@paths~position-elsewhere:/challenge$ /challenge/run  
Incorrect...  
You are not currently in the /usr/share/zoneinfo/posix/Asia directory.  
Please use the `cd` utility to change directory appropriately.  
hacker@paths~position-elsewhere:/challenge$ cd /  
hacker@paths~position-elsewhere:/$ cd usr  
hacker@paths~position-elsewhere:/usr$ cd share  
hacker@paths~position-elsewhere:/usr/share$ cd zoneinfo  
hacker@paths~position-elsewhere:/usr/share/zoneinfo$ cd posix  
hacker@paths~position-elsewhere:/usr/share/zoneinfo/posix$ cd Asia  
hacker@paths~position-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run  
Correct!!!  
/challenge/run is an absolute path, invoked from the right directory!  
Here is your flag:  
pwn.college{ItCoBlRsqU4yAl2KjGzBDIZ0Xfp.QX3QTN0wCN1kjNzEzW}  
```
### New Learnings
Learnt how to work with much more complex paths and executed two instances of this challenge once using the correct directory's absolute path and once using its relative path(shown in the solve).  
### Resources  
## Position yet elsewhere  
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
**Flag:** `pwn.college{sp76r5lt1mA6tz_MQ_FBi8FOgQy.QX4QTN0wCN1kjNzEzW}`  
```
hacker@paths~position-yet-elsewhere:~$ pwd  
/home/hacker  
hacker@paths~position-yet-elsewhere:~$ cd /  
hacker@paths~position-yet-elsewhere:/$ cd challenge  
hacker@paths~position-yet-elsewhere:/challenge$ /challenge/run  
Incorrect...  
You are not currently in the /var/log directory.  
Please use the `cd` utility to change directory appropriately.  
hacker@paths~position-yet-elsewhere:/challenge$ cd /var/log  
hacker@paths~position-yet-elsewhere:/var/log$ /challenge/run  
Correct!!!  
/challenge/run is an absolute path, invoked from the right directory!  
Here is your flag:  
pwn.college{sp76r5lt1mA6tz_MQ_FBi8FOgQy.QX4QTN0wCN1kjNzEzW}  
```
### New Learnings 
Learnt how to work with much more complex paths and executed two instances of this challenge once using the correct directory's absolute path(shown in the solve) and once using its relative path.  
### Resources  
## Implicit relative paths,from /
Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in  
absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the  
previous three challenges.  

However, the current working directory does matter for relative paths.  

- A relative path is any path that does not start at root (i.e., it does not start with /)
* A relative path is interpreted relative to your current working directory (cwd)
+ Your cwd is the directory that your prompt is currently located at

This means how you specify a particular file, depends on where the terminal prompt is located.  

Imagine we want to access some file located at /tmp/a/b/my_file.  

  - If my cwd is /, then a relative path to the file is tmp/a/b/my_file.  
  * If my cwd is /tmp, then a relative path to the file is a/b/my_file.  
  + If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.  

Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊   
### Solve  
**Flag:** `pwn.college{oGKnYygrHJpbrSrowxUsTXenEQF.QX5QTN0wCN1kjNzEzW}`  
While solving this i faced the dilemma of not understanding completly how to execute a executable using a relative path as I had used an absolute path before even when opening subdirectories of smaller directories.  
The hint of using the relative path starting with a c gave me the idea to run 'challenge/run' instead of '/challenge/run' which helped me solve it. I used the ls function whos functionality I learnt from Askubuntu to ensure the relative path wouldnt be any other directory.
```
hacker@paths~implicit-relative-paths-from-:~$ cd /  
hacker@paths~implicit-relative-paths-from-:/$ ls  
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr  
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var  
hacker@paths~implicit-relative-paths-from-:/$ challenge/run  
Correct!!!  
challenge/run is a relative path, invoked from the right directory!  
Here is your flag:  
pwn.college{oGKnYygrHJpbrSrowxUsTXenEQF.QX5QTN0wCN1kjNzEzW}
```
### New Learnings
Learnt how to execute a executable from a cwd in which the executable is not present.  
### Resources  
AskUbuntu(Used it for another challenge and indirectly used a command from an answer there)  
## explicit relative paths, from /  
Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory.  
In this level, we're going to explore more explicit relative paths.  

In most operating systems, including Linux, every directory has two implicit entries that you can reference in  
paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to  
each other:  

  - /challenge  
  * /challenge/.  
  + / challenge/./././././././././  
+ /./././challenge/././
    
  The following relative paths are also all identical to each other:  

- challenge
- ./challenge
- ./././challenge
- challenge/.
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute  
 paths.  

This challenge will get you using . in your relative paths. Get ready!  
### Solve
**Flag:** `pwn.college{8vgd9FZ5gzoNPfa_PewqByYObHn.QXwUTN0wCN1kjNzEzW}`  
I went wrong here a couple of times thinking I had to implement .. somehow but once i figured out that the only challenge was to show the usage of ., the challenge became the same as the previous one.

```

hacker@paths~explicit-relative-paths-from-:~$ cd /  
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run  
Correct!!!  
./challenge/run is a relative path, invoked from the right directory!  
Here is your flag:  
pwn.college{8vgd9FZ5gzoNPfa_PewqByYObHn.QXwUTN0wCN1kjNzEzW}  
```
### New Learnings  
I learnt the usage of the . in a relative path  

### Resources  
## implicit relative path 
In this level, we'll practice referring to paths using . a bit more. This challenge will need you to run it from the /  
challenge directory. Here, things get slightly tricky.  

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the  
following:  
```
hacker@dojo:~$ cd /challenge  
hacker@dojo:/challenge$ run  
```
This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for  
programs every time you entered a naked path, you could accidentally execute programs in your current directory  
that happened to have the same names as core system utilities! As a result, the above commands will yield the  
following error:  
```
bash: run: command not found
```
We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use  
relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a  
program in the current directory, using . like in the previous levels. Give it a try now!  
### Solve
**Flag:** `pwn.college{QveR6qNqVBnjAtLaOUCiydG4qih.QXxUTN0wCN1kjNzEzW}`  
Here I first thought we had to run challenge/run from the '/' directory. On testing, it told me that I needed to do so from the '/challenge' directory instead.  
Thus I realized we have to invoke run from the '/challenge' by implicitly invoking it to avoid the 2nd error given in the problem statement solving the problem.  
```
hacker@paths~implicit-relative-path:~$ pwd  
/home/hacker  
hacker@paths~implicit-relative-path:~$ cd /  
hacker@paths~implicit-relative-path:/$ ./challenge/run  
Incorrect...  
You are not currently in the /challenge directory.  
Please use the `cd` utility to change directory appropriately.  
hacker@paths~implicit-relative-path:/$ cd challenge  
hacker@paths~implicit-relative-path:/challenge$ ./run  
Correct!!!  
./run is a relative path, invoked from the right directory!  
Here is your flag:  
pwn.college{QveR6qNqVBnjAtLaOUCiydG4qih.QXxUTN0wCN1kjNzEzW}  
```
### New Learnings  
I learnt to use '.' implicitly to invoke a executable in the directory directly without having to go to the directory above it.  
### Resources  

## home sweet home  
Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user,  
and your home directory is /home/hacker. The home directory is typically where users store most of their personal  
files. As you make your way through pwn.college, this is where you'll store most of your solutions.  

Typically, your shell session will start with your home directory as your current working directory. Consider the  
initial prompt:
```
hacker@dojo:~$  
```
The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and  
uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash  
sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home  
directory. Consider:  
```
hacker@dojo:~$ echo LOOK: ~  
LOOK: /home/hacker  
hacker@dojo:~$ cd /  
hacker@dojo:/$ cd ~  
hacker@dojo:~$ cd ~/asdf  
hacker@dojo:~/asdf$ cd ~/asdf  
hacker@dojo:~/asdf$ cd ~  
hacker@dojo:~$ cd /home/hacker/asdf  
hacker@dojo:~/asdf$
```
Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that  
~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.  
Fun fact: cd will use your home directory as the default destination:  
```
hacker@dojo:~$ cd /tmp  
hacker@dojo:/tmp$ cd  
hacker@dojo:~$
```
Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as  
an argument on the commandline, with these constraints:  

1.Your argument must be an absolute path.  
2.The path must be inside your home directory.  
3.Before expansion, your argument must be three characters or less.  
Again, you must specify your path as an argument to /challenge/run as so:  
```
hacker@dojo:~$ /challenge/run YOUR_PATH_HERE
```
### Solve  
**Flag:** `pwn.college{4r7HjVJvvNlokmj9by0TSFKhugE.QXzMDO0wCN1kjNzEzW}`  
So while solving this I went for the ls to check for any small files that might be present.Then on that failing I used  
/challenge/run tmp because i thought i had to use a valid file but i made the mistake of not using an absolute path.  
On figuring that out , I just typed in a random file name 'a' after ~/ which worked as it was an absolute path.  
```
hacker@paths~home-sweet-home:~$ ls  
hacker@paths~home-sweet-home:~$ ls ~  
hacker@paths~home-sweet-home:~$ /challenge/run tmp  
The argument you provided is not an absolute path!  
hacker@paths~home-sweet-home:~$ /challenge/run ~/a  
Writing the file to /home/hacker/a!  
... and reading it back to you:  
pwn.college{4r7HjVJvvNlokmj9by0TSFKhugE.QXzMDO0wCN1kjNzEzW}  
```
### New Learnings  
I learnt what the '~' directory actually is and its usage in an absolute path.  
## Resources  

 
























