# File Globbing  
## Matching with *  
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a  
"wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than  
explain:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
```
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For  
example:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
```
When zero files are matched, by default, the shell leaves the glob unchanged:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```
The * matches any part of the filename except for / or a leading . character. For example:  
```
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use  
globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run  
for the flag!  
### Solve  
**Flag:** `pwn.college{srGvj2VaVTg3xBRGZqqtHRQh14t.QXxIDO0wCN1kjNzEzW}`
I ran into a confusion at the start as I was unsure of the argument to pass due to the  
restriction of the four characters and initially thought i had to use LOOK: due to only  
one variation of file globbing shown but after trying without using echo or look  
i got the flag.  
```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd echo look /ch***e***
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch***e***
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{srGvj2VaVTg3xBRGZqqtHRQh14t.QXxIDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt file globbing using the '*' character.  
### Resources  
## Matching with ? 
Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as a single-  
character wildcard. This works like *, but only matches one character. For example:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ?  
character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!  
### Solve  
**Flag:** `pwn.college{E3kkg59b8Ec2W_6QDouHVay1Ulz.QXyIDO0wCN1kjNzEzW}`  
I used the ? to find the flag while avoiding the 'c','l' and '*' characters.  
```
hacker@globbing~matching-with-:~$ cd /ch???????
You used either the 'c', 'l', or '*' characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??????
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{E3kkg59b8Ec2W_6QDouHVay1Ulz.QXyIDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to file glob with just a single character search with ? instead of *.  
### Resources  
## Matching with []  
Next, we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any  
character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example,  
[pwn] will match the character p, w, or n. For example:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files  
and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!  
### Solve  
**Flag:** `pwn.college{gboXZ7wyHLpjq2GT9sClvufmtFY.QXzIDO0wCN1kjNzEzW}`  
I used the file_[] with b,a,s,h to list all the files with one argument while running /challenge/run to get the flag.  
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{gboXZ7wyHLpjq2GT9sClvufmtFY.QXzIDO0wCN1kjNzEzW}
```
### New Learnings
Learnt how to glob using [] which shows u a potential subset of files w those characters unlike * and ? before.  
### Resources  
## Matching paths with []  
Globbing happens on a __path__ basis, so you can expand entire paths with your globbed arguments. For example:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home  
directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b ,  
file_a, file_s, and file_h files!  
### Solve  
**Flag:** `pwn.college{QOyKU3nEuehuELp8flwAVxhTQHp.QX0IDO0wCN1kjNzEzW}`  
I used the /challenge/files/file_[...]  while running /challenge/run to find the files needed to be found without changing my directory  
to thus gt the flag.  
```
hacker@globbing~matching-paths-with-:~$ /challenge/run  /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{QOyKU3nEuehuELp8flwAVxhTQHp.QX0IDO0wCN1kjNzEzW}
```
### New Learnings
I learnt that we can match using [] while providing full file paths.  
### Resources  
## Multiple Globs  
So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple  
globs in a single word. For example:  
```
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have  
an f and an l, and end in anything (including ag, which makes flag).  

Now you try it. We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge  
/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers  
every word that contains the letter p.  
### Solve
**Flag:** `pwn.college{k3dGxJ64Dnell_JipbkNPPILEx7.0lM3kjNxwCN1kjNzEzW}`  
I first ``cd``-ed into the /challenge/files directory and ran /challenge/run with *p* for any files that have p in it.  
```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{k3dGxJ64Dnell_JipbkNPPILEx7.0lM3kjNxwCN1kjNzEzW}
```
### New Learnings  
Learnt how to do multiple globs(here used *p* for any file that has p in it).  
### Resources  
## Mixing Globs  
Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files.    
Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when    
passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!  
### Solve  
**Flag:** `pwn.college{U_UBdXzQYJuC4BEit1S24xGPwdN.QX1IDO0wCN1kjNzEzW}`  
I used [...] to specify the starting letters of the files and then * for the rest of the file starting with the letters  
c,e and p.  
```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{U_UBdXzQYJuC4BEit1S24xGPwdN.QX1IDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt  how to mix two different globs to find files which are completely different.  
### Resources  
## Exclusionary globbing  
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in  
the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters  
that aren't listed. For example:  
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with  
p, w, or n!  

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep  
that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.  
### Solve  
**Flag:** `pwn.college{MJBMELP25KsJPhV5_P1URvDBMO5.QX2IDO0wCN1kjNzEzW}`
I used [!...] to specify the starting letters of the files and then * for the rest of the file to get the files that do not start with p,w or n.  
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{MJBMELP25KsJPhV5_P1URvDBMO5.QX2IDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to search for files without certain words/letters(excludsionary globbing).  
### Resources  
## Tab Completion 
As tempting as it might be, using * to shorten what must be typed on the commandline can lead to mistakes.  
Your glob might expand to unintended files, and you might not spot it until the rm command is already running! No  
one is safe from this style of error.  

A safer alternative when you are trying to specify a specific target is tab completion. If you hit tab in the shell, it'll  
try to figure out what you're going to type and automatically complete it. Auto-completion is super useful, and  
this challenge will explore its use in specifying files.  

This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type  
the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!  
```
hacker@dojo:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@dojo:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
hacker@dojo:~$ cat /challenge/pwn<TAB>
pwn.college{HECK YEAH}
hacker@dojo:~$
```
When you hit that tab key, the name will expand and you'll be able to read the file. Good luck!  
### Solve  
**Flag:** ``





