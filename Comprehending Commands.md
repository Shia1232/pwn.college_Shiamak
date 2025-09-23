# Comprehending Commands  
## cat: not the pet,but the command!  
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:  
```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md  
One of the most critical Linux commands is `cat`.  
`cat` is most often used for reading out files, like so:  
```
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:  
```
hacker@dojo:~$ cat myfile  
This is my file!  
hacker@dojo:~$ cat yourfile  
This is your file!  
hacker@dojo:~$ cat myfile yourfile  
This is my file!  
This is your file!  
hacker@dojo:~$ cat myfile yourfile myfile  
This is my file!  
This is your file!  
This is my file!  
```
Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later  
challenges...  
In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with  
cat!
### Solve  
**Flag:** `pwn.college{szCYs_QfN7rUgY2YIFRrP5ZWvWA.QXxcTN0wCN1kjNzEzW}`  
The usage of cat command is to read out the contents of a file. It was given the 'file' file had the flag so i used cat  
to read its contents and retrieve the flag.  
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag  
pwn.college{szCYs_QfN7rUgY2YIFRrP5ZWvWA.QXxcTN0wCN1kjNzEzW}
```
### New Learnings  
I learnt the usage of the cat command and its use-case.  
### Resources  
## catting absolute paths  
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's  
arguments as absolute paths:  
```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md  
In the last level, you did `cat flag` to read the flag out of your home directory!  
You can, of course, specify `cat`'s arguments as absolute paths:  
...  
```
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its  
absolute path: /flag.  

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access  
that file directly.  
### Solve  
**Flag:** `pwn.college{8hwjzzEDAEXjZb3_hp419wrxiTw.QX5ETO0wCN1kjNzEzW}`  
```
hacker@commands~catting-absolute-paths:~$ cat /flag  
pwn.college{8hwjzzEDAEXjZb3_hp419wrxiTw.QX5ETO0wCN1kjNzEzW}  
```
### New Learnings  
Learnt how to use cat command with an absolute path as the argument instead of a file  
### Resources  
## more catting practice  
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this  
level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag  
for you. You must retrieve the flag by absolute path, wherever it is.  
### Solve
**Flag:** `pwn.college{cPBpWmLsCqT67hBdjyZyTuA8MJB.QXwITO0wCN1kjNzEzW}`  
```
You cannot use the 'cd' command in this level, and must retrieve the flag by   
absolute path. Plus, I hid the flag in a different directory! You can find it   
in the file /usr/share/libc-bin/flag. Go cat it out **without** cding into that   
directory!  
hacker@commands~more-catting-practice:~$ ls  
a  
hacker@commands~more-catting-practice:~$ cat /usr/share/libc-bin/flag  
pwn.college{cPBpWmLsCqT67hBdjyZyTuA8MJB.QXwITO0wCN1kjNzEzW}  
```
### New Learnings  
I learnt how to cat into a file using an absolute path.  
### Resources  
## grepping for a needle in a haystack  
Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the  
contents we need! We'll learn it in this challenge.  
There are many ways to grep, and we'll learn one way here:  
```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```
nvoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.  

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!  

HINT: The flag always starts with the text pwn.college.  
### Solve  
**Flag:** `pwn.college{csgHD9DIaURGFIg6a6MC2H3_WF-.QX3EDO0wCN1kjNzEzW}`  
The general command syntax of grep was given so i replaced search_string with pwn.college so that only text with pwn.college  
shows up and the absolute path was given for me to cat the text out from.  
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt  
pwn.college{csgHD9DIaURGFIg6a6MC2H3_WF-.QX3EDO0wCN1kjNzEzW}  
```
### New Learnings  
I learnt the usage of the grep command and how to search for a string with a a certain key or keyword in it.  
### Resources  
## comparing files  
When looking for changes between similar files, eyeballing them might not be the most efficient approach! This  
is where the diff command becomes invaluable.  

diff compares two files line by line and shows you exactly what's different between them. For example:  
```
hacker@dojo:~$ cat file1  
hello  
world  
hacker@dojo:~$ cat file2  
hello  
universe  
hacker@dojo:~$ diff file1 file2  
2c2  
< world  
---  
> universe  
```
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the  
second file (>).  

Sometimes, when new lines are added, you'll see something like:  
```
hacker@dojo:~$ cat old  
pwn  
hacker@dojo:~$ cat new  
pwn  
college  
hacker@dojo:~$ diff old new  
1a2  
> college
```
This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add  
line 2 of file2").  
Now for your challenge! There are two files in /challenge:  
- /challenge/decoys_only.txt contains 100 fake flags  
+ /challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
    
Use diff to find what's different between these files and get your flag!  
### Solve
**Flag:** `pwn.college{gKlGMx91P1D3d8t7chNae9VTFjB.01MwMDOxwCN1kjNzEzW}`  
Here the approach was very clear for me, I had to compare two files and the real flag would be the differentiating factor as the two files were identical in every other aspect.  
```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt  
3a4  
> pwn.college{gKlGMx91P1D3d8t7chNae9VTFjB.01MwMDOxwCN1kjNzEzW}  
```
### New Learnings  
I learnt the usage of the diff command and how to use it in the terminal.  
### Resources  
## listing files  
So far, we've told you which files to interact with. But directories can have lots of files (and other directories)  
inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using  
the ls command!  
ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided.  
Observe:  
```
hacker@dojo:~$ ls /challenge  
run  
hacker@dojo:~$ ls  
Desktop    Downloads  Pictures  Templates  
Documents  Music      Public    Videos  
hacker@dojo:~$ ls /home/hacker  
Desktop    Downloads  Pictures  Templates  
Documents  Music      Public    Videos  
hacker@dojo:~$  
```
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.  
### Solve  
**Flag:** `pwn.college{IWceFKAFCyAosZShBHVmm_8iKgX.QX4IDO0wCN1kjNzEzW}`  
It was given the executable was in '/challenge' directory so upon using the ls command in the directory it showed a random file with run in it which had been renamed  
which gave me the flag.  
```
hacker@commands~listing-files:~$ cd /challenge  
hacker@commands~listing-files:/challenge$ ls  
31278-renamed-run-29495  DESCRIPTION.md  
hacker@commands~listing-files:/challenge$ ./31278-renamed-run-29495    
Yahaha, you found me! Here is your flag:  
pwn.college{IWceFKAFCyAosZShBHVmm_8iKgX.QX4IDO0wCN1kjNzEzW}  
```
### New Learnings  
Learnt the usage of ls and how to **actually** apply it in a terminal to find the flag.  
### Resources  
## touching files  
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here.  
You can create a new, blank file by touching it with the touch command:  
```
hacker@dojo:~$ cd /tmp  
hacker@dojo:/tmp$ ls  
hacker@dojo:/tmp$ touch pwnfile  
hacker@dojo:/tmp$ ls  
pwnfile  
hacker@dojo:/tmp$
```
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your  
flag!  
### Solve  
**Flag:** `pwn.college{Q8xcfKM0HlvRavmZMEP18p6dOVK.QXwMDO0wCN1kjNzEzW}`  
The first attempt of mine at this had me a bit confused as I thought I had to create a '/tmp/..' file in the home directory but after  
trying that, I noticed by using the ls command that only a directory is still being made which gave me the hint  
to touch a pwn and college file in the /tmp directory and then run /challenge/run  
```
hacker@commands~touching-files:~$ cd /tmp  
hacker@commands~touching-files:/tmp$ touch pwn  
hacker@commands~touching-files:/tmp$ touch college  
hacker@commands~touching-files:/tmp$ /challenge/run  
Success! Here is your flag:  
pwn.college{Q8xcfKM0HlvRavmZMEP18p6dOVK.QXwMDO0wCN1kjNzEzW}  
```
### New Learnings  
Learnt how to make new files in a directory directly using the terminal using the touch command.  
### Resources  
## removing files  
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to  
clean up!  

In Linux, you remove files with the rm command, as so:  
```
hacker@dojo:~$ touch PWN  
hacker@dojo:~$ touch COLLEGE  
hacker@dojo:~$ ls  
COLLEGE     PWN  
hacker@dojo:~$ rm PWN  
hacker@dojo:~$ ls  
COLLEGE  
hacker@dojo:~$  
```
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/  
check, which will make sure you've deleted it and then give you the flag!  
### Solve  
**Flag:** `pwn.college{0RuRlHQXqNsfIkmRfSq1uw1U7Fm.QX2kDM1wCN1kjNzEzW}`  
```
hacker@commands~removing-files:~$ ls  
a  delete_me   
hacker@commands~removing-files:~$ rm delete_me  
hacker@commands~removing-files:~$ /challenge/check  
Excellent removal. Here is your reward:  
pwn.college{0RuRlHQXqNsfIkmRfSq1uw1U7Fm.QX2kDM1wCN1kjNzEzW}  
```
### New Learnings  
I learnt how to remove a file from a directory using the terminal.  
### Resources  
## moving files  
You can also move files around with the mv command. The usage is simple:  
```
hacker@dojo:~$ ls  
my-file  
hacker@dojo:~$ cat my-file  
PWN!  
hacker@dojo:~$ mv my-file your-file  
hacker@dojo:~$ ls  
your-file  
hacker@dojo:~$ cat your-file  
PWN!  
hacker@dojo:~$  
```
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /  
challenge/check, which will check things out and give the flag to you.  
### Solve  
**Flag:** `pwn.college{8RIwyvcJ8nT0_auSAmmSeajah7D.0VOxEzNxwCN1kjNzEzW}`  
```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet  
Correct! Performing 'mv /flag /tmp/hack-the-planet'.  
hacker@commands~moving-files:~$ /challenge/check  
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:  
pwn.college{8RIwyvcJ8nT0_auSAmmSeajah7D.0VOxEzNxwCN1kjNzEzW}  
```
### New Learnings  
I learnt how to move files from one directory to another using the mv command.  
### Resources  
## hidden files  
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't  
show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag,  
as so:  
```
hacker@dojo:~$ touch pwn  
hacker@dojo:~$ touch .college  
hacker@dojo:~$ ls  
pwn  
hacker@dojo:~$ ls -a  
.college	pwn  
hacker@dojo:~$
```
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.  
### Solve  
**Flag:** ``












