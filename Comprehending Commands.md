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
**Flag:** ``  






