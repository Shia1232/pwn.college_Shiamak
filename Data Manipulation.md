# Data Manipulation 
## Translating characters  
One of the purposes of piping data is to modify it. Many Linux commands will help you modify data in really  
cool ways. One of these is tr, which translates characters it receives over standard input and prints them to  
standard output.  

In its most basic usage, tr translates the character provided in its first argument to the character provided in its  
second argument:  
```
hacker@dojo:~$ echo OWN | tr O P
PWN
hacker@dojo:~$
```
It can also handle multiple characters, with the characters in different positions of the first argument replaced  
with associated characters in the second argument.  
```
hacker@dojo:~$ echo PWM.COLLAGE | tr MA NE
PWN.COLLEGE
hacker@dojo:~$
```
Now, you try it! In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will  
become a and vice-versa). Can you undo it with tr and get the flag? 
### Solve  
**Flag:** `pwn.college{wmOggH75PzMDB94FtG8zeL6K0A6.01MxEzNxwCN1kjNzEzW}`
I ran /challenge/run and then swapped the cases using tr and all the upper-case and lower-case letters of the alphabet in opposite order.  
```
hacker@data~translating-characters:~$ /challenge/run
Your case-swapped flag:
PWN.COLLEGE{WMoGGh75pZmdb94fTg8ZEl6k0a6.01mXeZnXWcn1KJnZeZw}

hacker@data~translating-characters:~$ echo PWN.COLLEGE{WMoGGh75pZmdb94fTg8ZEl6k0a6.01mXeZnXWcn1KJnZeZw} | tr abcdefghijklmnopqrstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ
PWN.COLLEGE{WMOGGH75PZMDB94FTG8ZEL6K0A6.01MXEZNXWCN1KJNZEZW}
hacker@data~translating-characters:~$ echo PWN.COLLEGE{WMoGGh75pZmdb94fTg8ZEl6k0a6.01mXeZnXWcn1KJnZeZw} | tr abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz
pwn.college{wmOggH75PzMDB94FtG8zeL6K0A6.01MxEzNxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to swap characters in output in the shell.  
### Resources  
## Deleting characters  
tr can also translate characters to nothing (i.e., delete them). This is done via a -d flag and an argument of  
what characters to delete:  
```
hacker@dojo:~$ echo PAWN | tr -d A
PWN
hacker@dojo:~$
```
Pretty simple! Now you give it a try. I'll intersperse some decoy characters (specifically: ^ and %) among the flag  
characters. Use tr -d to remove them!  
### Solve  
**Flag:** `pwn.college{MK743Ei5qeSDDYnQN9nSsLWHjSI.0FNxEzNxwCN1kjNzEzW}`
I used the `` | tr -d ''`` to delete the decoy characters and retrieve the flags.  
```
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
pw%n^.%c^%o^%ll^%e^g^e^{^%M^K^%7^%43%E%i^5q^e^S^D%D^Y^nQN%9^%nS^s^L%W^%H%j%S^%I^.^%0^F^N%x%E^%z^N^%xw^%C^%N^1^%k^j^%N^z^%Ez^%W%}%^%
hacker@data~deleting-characters:~$ echo pw%n^.%c^%o^%ll^%e^g^e^{^%M^K^%7^%43%E%i^5q^e^S^D%D^Y^nQN%9^%nS^s^L%W^%H%j%S^%I^.^%0^F^N%x%E^%z^N^%xw^%C^%N^1^%k^j^%N^z^%Ez^%W%}%^%
| tr -d ^%
pw%n^.%c^%o^%ll^%e^g^e^{^%M^K^%7^%43%E%i^5q^e^S^D%D^Y^nQN%9^%nS^s^L%W^%H%j%S^%I^.^%0^F^N%x%E^%z^N^%xw^%C^%N^1^%k^j^%N^z^%Ez^%W%}%^%
bash: syntax error near unexpected token `|'
hacker@data~deleting-characters:~$ echo pw%n^.%c^%o^%ll^%e^g^e^{^%M^K^%7^%43%E%i^5q^e^S^D%D^Y^nQN%9^%nS^s^L%W^%H%j%S^%I^.^%0^F^N%x%E^%z^N^%xw^%C^%N^1^%k^j^%N^z^%Ez^%W%}%^% | tr -d ^%
pwn.college{MK743Ei5qeSDDYnQN9nSsLWHjSI.0FNxEzNxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to delete characters from a word in the shell.  
### Resources  
## Deleting newlines 
A common class of characters to remove is a line separator. This happens when you have a stream of data that  
you want to turn into a single line for further processing. You can specify newlines almost like any other character,  
by escaping them:  
```
hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!
hacker@dojo:~$
```
Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input  
into the shell normally. The newline, of course, is hard to input because when you typically hit Enter, you'll run the  
command itself. \n is a standin for this newline, and it must be in quotes to prevent the shell interpreter itself from  
trying to interpret it and pass it to tr instead.  

Now, let's combine this with deletion. In this challenge, we'll inject a bunch of newlines into the flag. Delete them  
with tr's -d flag and the escaped newline specification!  

-------------------------------------------------------------------------------------------------------------------------  
Fun fact! Want to actually replace a backslash (\) character? Because \ is the escape character, you gotta escape  
it! \\ will be treated as a backslash by tr. This isn't relevant to this challenge, but is a fun fact nonetheless!  
### Solve  
**Flag:** `pwn.college{MrlI6ofX7OUP3unJaJrS652QT7h.0VNxEzNxwCN1kjNzEzW}`
I deleted all the new lines in the flag to retrieve the flag efficiently.  
```
hacker@data~deleting-newlines:~$ /challenge/run
Your line-split flag: 
p
w
n.
co
l
l
e
g
e
{
M
r
l
I6
ofX
7O
U
P
3
un
J
a
Jr
S6
5
2
Q
T7h
.
0V
N
xE
z
Nxw
CN
1kj
N
zE
zW
}
hacker@data~deleting-newlines:~$ echo "p
w
n.
co
l
l
e
g
e
{
M
r
l
I6
ofX
7O
U
P
3
un
J
a
Jr
S6
5
2
Q
T7h
.
0V
N
xE
z
Nxw
CN
1kj
N
zE
zW
}"| tr -d "\n"
pwn.college{MrlI6ofX7OUP3unJaJrS652QT7h.0VNxEzNxwCN1kjNzEzW}hacker@data~deleting-newlines:~$ 

```
### New Learnings  
I learnt how to delete new-lines from a word or set of words in the shell.  
### Resources  
## Extracting the first lines with head 
In your Linux journey, you'll experience situations where you need to grab just the early output of very verbose  
programs. For this, you'll reach for head! The head command is used to display the first few lines of its input:  
```
hacker@dojo:~$ cat /something/very/long | head
this
is
just
the
first
ten
lines
of
the
file
hacker@dojo:~$
```
By default, it shows the first 10 lines, but you can control this with the -n option:
```
hacker@dojo:~$ cat /something/very/long | head -n 2
this
is
hacker@dojo:~$
```
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the  
first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right!  
Your solution will be a long composite command with two pipes connecting three commands. Good luck!  
### Solve  
**Flag:** ``

