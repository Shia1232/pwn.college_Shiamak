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
**Flag:** `pwn.college{IS8gCTvkSzfpt7ymCgx_8ZvRqqF.0lNxEzNxwCN1kjNzEzW}`
Here I basically piped /challenge/college by making its standard input the output of /challenge/pwn | head -n 7
```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/college < <( /challenge/pwn | head -n 7 )
Congratulations, you piped the right codes!
pwn.college{IS8gCTvkSzfpt7ymCgx_8ZvRqqF.0lNxEzNxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to extract the first lines of a program with head.  
### Resources  
## Extracting specific sections of text  
Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd  
column. For this, there's the cut command.  

For example, imagine that you have the following data file:
```
hacker@dojo:~$ cat scores.txt
hacker 78 99 67
root 92 43 89
hacker@dojo:~$
```
You could use cut to extract specific columns:
```
hacker@dojo:~$ cut -d " " -f 1 scores.txt
hacker
root
hacker@dojo:~$ cut -d " " -f 2 scores.txt
78
92
hacker@dojo:~$ cut -d " " -f 3 scores.txt
99
43
hacker@dojo:~$
```
The -d argument specifies the column delimiter (how columns are separated). In this case, it's a space character. Of  
course, it has to be in quotes here so that the shell knows that the space is an argument rather than a space  
separating other arguments! The -f argument specifies the field number (which column to extract).  

In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single  
characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d 
"\n" (like the previous level!) to join them together into a single line. Your solution will look something like /  
challenge/run | cut ??? | tr ???, with the ??? filled out.  
### Solve  
**Flag:** `pwn.college{MoIzSlGBe1wwT-TTaLy1twNngJ3.01NxEzNxwCN1kjNzEzW}`
I extracted the 2nd colum of data from /challenge/run and then just deleted the new lines from it using ``tr -d`` to get the flag.  
```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{MoIzSlGBe1wwT-TTaLy1twNngJ3.01NxEzNxwCN1kjNzEzW}hacker@data~extracting-specific-sections-of-text:~$ 

```
### New Learnings  
I learnt how to extract sections of data from a dataset(in this case how to extract one column out of many).  
### Resources  
## Sorting data
Files (or output lines of commands) aren't always in the order you need them! The sort command helps you  
organize data. It reads lines from input (or files) and outputs them in sorted order:  
```
hacker@dojo:~$ cat names.txt
  hack
  the
  planet
  with
  pwn
  college
hacker@dojo:~$ sort names.txt
  college
  hack
  planet
  pwn
  the
  with
hacker@dojo:~$
```
By default, sort orders lines alphabetically. Arguments can change this:  
+ -r: reverse order (Z to A)
+ -n: numeric sort (for numbers)
+ -u: unique lines only (remove duplicates)
+ -R: random order!
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among  
them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake  
flags). Go get it!
### Solve 
**Flag:** `pwn.college{UsCUx9N_jjgBLBYv2e896D-Psyu.0FM0MDOxwCN1kjNzEzW}`  
I sorted the data from Z to A using the -r argument to put the first flag printed as the real one.  
```
hacker@data~sorting-data:~$ sort /challenge/flags.txt -r
pwn.college{UsCUx9N_jjgBLBYv2e896D-Psyu.0FM0MDOxwCN1kjNzEzW}
pwn.college{UsCUx9N_jjgBLBYv2e896D-Psyu.0FM0LDOxwCN1kjNzEzW}
pwn.college{UsCUx9N_jjgBLBYv2e895D-Psxu.0FM0MDOxwCN1kjNzEzW}
pwn.college{UsCUx9N_jjgBLBYu2e896D-Psyu.0FM0MDOxwCN1kjNzEzW}
pwn.college{UsCUx9M_jjgBLBYv2e896D-Psyu.0FM0MDOxwCN1kjNzEzW}
pwn.college{UsBUx9N_jjgBLBYv2e896D-Psxu.0FM0MDOxwCM1kjNzEzW}
pwn.college{UsBUx9N_jjgBLBYv2e796D-Psyu.0FM0MDOxwBN1kjNzEzW}
pwn.college{UsBUw9N_jjgBLBYv2d896D-Psyu.0FM0MCOxwCN1kjNzDzW}
pwn.college{UrCUx9N_jjgBLBYv2e896D-Psyu.0FM0MDOxwCM1kjNzEzW}
pwn.college{UrCUx9N_ijgBLBYv2d896D-Psyt.0FM0LDOwwCN1kjNyDzW}
pwn.college{TsCUx8N_jjgBKBXv2e796D-Psxu.0FM0MDOxwCN1kjNzDyW}
pwn.college{TrCUx9N_jjgBLBYv2e896C-Psyu.0FM0MCOxvBN1kiNzEzW}
pwn.collegd{UsCUx9M_jjgBLBYu2e895D-Pryt.0FM0MDOwwCN1kjNzEzW}
pwn.collegd{UsCUw9M_jjgALBXv2d796D-Psyt.0FL0MCOxvCN1kjMyEzW}
pwn.collegd{UsCTx9N_ijgBLAYv2d795D-Psyu.0FM0LDNxwCN1kjNzEzW}
pwn.collegd{TrCUx8N_jjgBLBYv2e786D-Psyu.0FM0MCOxwCN0kjNzDzW}
pwn.collefe{UsCUx9N_jjgBLBYv1e896D-Psyu.0FM0MDOxvCN1kjNzEzW}
pwn.collefe{UsCUx8N_jjgBLBYv2e896D-Psyu.0FM0MCOxwCN1kjNzEzW}
pwn.colldge{UsCUx9N_jjgBLBYv2e896D-Psyu.0FM0MDOwwCN1kjNzEzW}
pwn.colldge{UrCUx9N_jjgBLBXu2e896D-Osyu.0FL0MCOxwCN0kjNzDzW}
pwn.colldge{UrCUx9N_ijgBLBYv2e896D-Psyu.0FM0MDOxwCN1kjNzEzW}
pwn.colldgd{TsCTx9M_jjgBKAYv1e785D-Psyt.0FM0MDOwwCN1kjNzDzW}
pwn.colldfe{UsCUx8N_jjgBLBYv2e886D-Orxu.0FM0LDOxwCN1jjNzEzW}
pwn.colldfe{UsBTw9N_jjfAKAYv2e886C-Psyu.0FM0MDOwwCM0jjMzEzW}
pwn.colldfd{UsCUx9M_jifBLAYu2d896C-Osxu.0EM0LDOwwBM0kiNyEzV}
pwn.colkege{UsCUx9N_jjgBLBYv2e896D-Psyt.0FM0MDOwwCN1kjNzEzW}
pwn.colkege{UsCUx9M_jjgAKAXv2e896D-Psyu.0EM0LDOwvBM1jjNzEzW}
pwn.colkege{UsCTx9N_jigBLBYv2d896D-Psxu.0FM0LCOxwCN0kjNzEzW}
pwn.colkegd{UsCUx9N_jjgBKAYu2e796D-Osyt.0FL0MDOwwCM1kjNzDzW}
pwn.coklege{UsCUx9N_jjgBLBYv2e896D-Psxu.0EM0MDOwwCM1kjNzEzW}
pwn.coklege{UsCUx9N_jigBKBYv1d896D-Pryt.0FM0MDOxwCN1jjMzDzV}
pwn.coklege{UsCUw9N_ijgALBYv1e896D-Psyu.0FM0MDOxwCN1kjNzEzW}
pwn.coklefe{UsCUx9N_jjgBKBYv2d896D-Osyu.0FL0MDOxwCN0kjNzDzW}
pwn.cokkege{UsCTw9N_jjfBLBYu1e896D-Psyt.0FM0MDOxwCN1kjNzEzW}
pwn.cokkege{UsBUx8M_ijgAKAXv1e896D-Osyu.0EM0MCOwwBN1kjNzEyW}
pwn.cokkege{TrCTw9N_jjfAKBXv1e796D-Osxu.0EL0MDNxvCM1kjMzEzW}
pwn.cokkefe{UsBUx9M_jjgBLBXu1e886D-Prxu.0FM0MDNwwCN1jiNzEyW}
pwn.cnllege{UsCUx8N_jjgBLBYu2e796C-Orxu.0FL0MCOxvCM0kjNyEzW}
pwn.cnllege{UsCUx8M_jjgBLBYv2e896D-Psyu.0FM0MDOwwCN1kjNzDzW}
pwn.cnllege{TrBUx9N_jigBLBYv2e786D-Psyu.0FM0LDNwwBN0kjMzEzV}
pwn.cnllegd{UsCTx9N_jjgBKBYv2e896D-Psyu.0FM0MDOxwCN1kiNzEyW}
pwn.cnlldge{UsCTw9N_jjgBLBYu2d896D-Osyu.0FL0LDOxwCN1jjNzEzW}
pwn.cnlldge{TsCUx8M_ijgBKBYu2d786C-Psyu.0EL0MDNxwBM1kjNyEzV}
pwn.cnklege{UsBUx9M_ijgBLAYv2d896D-Osyu.0EL0LCNwvCN1jjMzEzW}
pwn.bollege{UsCTx9M_jjgBLBYv2d896D-Psyu.0FL0MCOxwCN0kjNzEzW}
pwn.bollefe{TrCTx9N_jigBLBYv2e885D-Psxu.0FM0MDOxwCN1kiNyEzW}
pwn.bokldgd{TsBUx9N_jifBLBYu2d895D-Pryt.0EM0LDOwvCN1jiNzEzV}
pwn.bokldfe{TsCTx8N_jifBKBYv1d796D-Psyu.0FM0LDNxwBN0jjNyEyV}
pwn.bnllegd{UsCUw9N_jjgBLBYv2e896C-Psyu.0FM0MDOxwCN1kjNzEzW}
pwn.bnlkege{UsCTx8N_ijfBLAXu2e895C-Osyu.0FM0MDOxvBN1kjNzEzW}
pwm.college{UsCUx9N_jjfBLBYv2e886D-Psyu.0FM0MDOxwCN1kjNyEzW}
pwm.college{UsCUw9N_ijgBLAYv2e896D-Osxt.0FM0MDOxwCN1kjNyEzW}
pwm.college{UsBUw9N_jjgALBYv2e896D-Pryu.0FL0MDOxwCN0kjNzDzV}
pwm.college{UrCUx9N_jifALBYv2d896D-Psyu.0FL0MCOxwCN1jjNzEzW}
pwm.college{TsCUw9N_jjgBLBYv1e896D-Osyu.0EM0MDOxwCN0jjNzEzW}
pwm.colldge{TrCUx9N_ijgBLAYv2e885D-Psyu.0FM0LDOxwBM0kjMyEzW}
pwm.colkege{UsCTw9N_jjgBLBYv2e896D-Psyu.0FM0LDOxvCN1kjMzEzW}
pwm.coklege{TrBTw8N_jigBLAXu2d886D-Pryt.0FM0LDNxwCN1kjNyDyW}
pwm.cokkdge{UsCUx9N_jjgALBYv1d796D-Psyu.0FM0MDOxvCM1kiNzEyV}
pwm.cnlkege{TsCUw9N_jjgALBYv2e896C-Psyu.0FM0MDOxwCN1kjNyEzW}
pwm.cnlkdfd{UsCUw8M_jifBKBYv1e885D-Osyu.0FL0MCNxwCM0kjNzEyW}
pwm.bollege{UrCTx9M_ijgALBYu1e896C-Prxu.0FM0MDOwvBM1kjNzEzV}
pwm.bnlkdge{TsCTx8M_jjgALAYv2e795C-Osyt.0FM0MDOxwBN1kjNyEzW}
pvn.college{UsCUx9N_jjgBLBYv2e895C-Psyu.0FM0MDOxwBN1kjNzEzW}
pvn.college{UsCUx9N_jjgBLBYv1e896D-Psyu.0FM0MDOxwCN1kjNzEzW}
pvn.college{UsCTx9N_jjfBLBYv1e896D-Psyu.0EM0MDNxvCN1kjNzEzW}
pvn.collegd{TrCTx8M_iigAKAYv2e895D-Psxt.0EM0MCOxvCN1kiMzDyV}
pvn.collefe{TsBUx9N_iigAKBYv1e896C-Psxu.0EM0MCOxwBN0jiNzEzW}
pvn.collefd{TsCUx9N_jjgBKBYv2d896D-Osyu.0EM0MCOwvBN1kjNzEzW}
pvn.colldge{UsCUx9N_jjgBLBXv2e896D-Psyu.0FM0MDNxvBN1kiNzEzW}
pvn.colldge{TsCUx8N_jigBLBYv2e896D-Psyu.0FM0LDOxwCN1kiNzEzW}
pvn.colldgd{UsBUx8N_jjfBLBXv2e896D-Psxt.0FM0LDOwwBM0kiNyEzV}
pvn.colkdge{UsCUw8N_jjgBLBYu2e895D-Psyu.0FM0LDOxwCN0kiNzEzV}
pvn.cokkefd{UsCUx9N_jjfBLBYu2d896C-Pryu.0FM0MDOxwCN0kiNzEzW}
pvn.bollege{UrCUw9N_iigBKBXv1e896D-Psyu.0FM0MDNwwCN0jjNyDyW}
pvn.bollege{UrBTx9N_jjfBLBYv1e896D-Psyu.0FM0MCOxwCM1kjNzDzV}
pvn.bollege{TsCUx9M_jigBKBYu2e896D-Pryu.0FM0MDNwwBN1jjNyDzW}
pvn.bolkdgd{TsCTw9M_ijfBLAYv2d896D-Psxu.0FL0LCOwwCN0kjMyDyV}
pvn.bokkegd{UsBUx8M_jjgBKBXu1e896D-Psxu.0FM0LDOwvCN0kjNyEzW}
pvm.college{TrCUx8M_jigAKBXv2d896D-Psyu.0FM0MCOxwCM0kjNzEyW}
pvm.collegd{TsCUx9N_jjfBKAYv1d895D-Oryu.0FM0LDOwwCM1kiNyEzW}
pvm.colldgd{UrCUw9N_jjgBLBYu2e796D-Osyu.0EL0LDOxwCN1kjMzEzW}
pvm.colldfe{UrBUx9M_ijgALAYu2e895D-Osxu.0EM0MDOxvCN0jjNyEzV}
pvm.cnlkege{UsCUw8M_jjgBKAXu2e886D-Psxu.0EM0MDOxwCN1kjNzEzW}
own.college{UsCUw9N_ijgBLBYv2e886D-Psyu.0FL0MDOxwCN1kjNyEzW}
own.college{UsCUw9M_jjgBLBYv2e896C-Psyu.0FL0MDOxvCN0kiNzEyV}
own.college{UsBUx9N_jjgBLBYu2e786C-Psyu.0EM0MDNxwBN1jjNzEzW}
own.college{UrCTw8N_jigBLAXu2e896D-Osyu.0FL0LDNwvCN1jjNzEzW}
own.collegd{UsCUw9M_jjgBLBYv2e896D-Psyu.0FM0LDOxvCM1jiNzEzW}
own.collefe{UsCUx9N_jjgBLBYv2d896D-Psyt.0EM0MDOwwBN0kjNzDzW}
own.colkefe{TrCTx8N_jigALBXv1e886D-Psyu.0FM0LDOwwCN1kjNzEzW}
own.colkefd{UsCUx9M_jjgBKBYv1e796D-Oryt.0FM0LCOxvCN1kiNyDyW}
own.cnklege{UsBUx9N_jjgBLBYv2e896D-Psyt.0FM0MDOxwCN1kjNzEzW}
own.bolkege{UsCUx8N_jigBLBYu2e896D-Psyu.0FM0LDOxvBN1kjNzEyW}
own.bolkdfd{TsCTx9M_jigBKBYv2d886D-Osxu.0EL0LCOxwBN1kiNzEzW}
own.bnlkege{UsBTx9M_jjgBLAYv2e896D-Psxu.0EM0LDOwwCN1kjNzEzV}
owm.colkdfe{TsCUx9N_jjfBLAXv2e795D-Prxu.0EM0MCNxvCN1kjNzEzW}
owm.bokldge{UsCTx9N_jjfBLAYv2e886D-Psxu.0FL0MDNwvCN1jjNyEzV}
ovn.cokldgd{UrCUx9N_ijgBLBYu2e796D-Psyu.0FM0MDOxwCN1jiNzEyW}
ovn.cnlkdge{UrCUx9N_jjgBLBYv2e795D-Psyu.0FL0MDOxwCN1kjNzEzW}
ovn.bolldge{UrCUx9N_jigBLBYv1d796D-Psyu.0EM0LDNwvCN1jiNzEzV}
````
### New Learnings  
I learnt how to sort data in a given file.  
### Resources  



