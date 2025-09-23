# Comprehending Commands  
## cat:not the pet,but the command!  
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






