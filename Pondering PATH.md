# Pondering PATH 
## The PATH Variable  
It turns out that the answer to "How does the shell find ls?" is fairly simple. There is a special shell variable,  
called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to  
commands. If you blank out the variable, things go badly:  
```
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory
hacker@dojo:~$
```
Without a PATH, bash cannot find the ls command.  

In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file  
using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will  
give it to you! Thus, you must make it so that /challenge/run also can't find the rm command!  

Keep in mind: /challenge/run will be a child process of your shell, so you must apply the concepts you learned in  
Shell Variables to mess with its PATH variable! If you don't succeed, and the flag gets deleted, you will need to  
restart the challenge to try again!  
### Solve
**Flag:** `pwn.college{EkXFWMFUdMRr-xmdj67WCx2cKBb.QX2cDM1wCN1kjNzEzW}`  
I set the PATH variable to blank so it couldn't find rm so that upon  
running /challenge/run the flag does not get deleted.  
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{EkXFWMFUdMRr-xmdj67WCx2cKBb.QX2cDM1wCN1kjNzEzW}
```
### New Learnings  
I learnt about the PATH variable and how to disable commands like rm and ls using PATH.  
### Resources  
## Setting PATH
Okay, so things break when you blank out PATH. But what about doing something useful with PATH?  
  
Let's explore how we would, for example, add a new directory of programs to our command repertoire. Recall that  
PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically  
execute them via their path:  
```
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ goodscript
bash: goodscript: command not found
hacker@dojo:~$ /home/hacker/scripts/goodscript
YEAH! This is the best script!
hacker@dojo:~$

```
If you maintain useful scripts that you want to be able to launch by bare name, this is annoying. However, by  
adding directories to or replacing directories in this list, you can expose these programs to be launched using their  
bare name! For example:  
```
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
Let's practice. This level's /challenge/run will run the win command via its bare name, but this command exists in  
the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that  
/challenge/run needs, so you can just overwrite PATH with that one directory. Good luck!  
### Solve  
**Flag:** `pwn.college{AKyX105vGxowBQ4Txe3lRn2BfZH.QX1cjM1wCN1kjNzEzW}`
I set the path to /challenge/more_commands as it had win in it to make win a executable command just by it's name.  
```
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{AKyX105vGxowBQ4Txe3lRn2BfZH.QX1cjM1wCN1kjNzEzW}

```
### New Learnings  
I learnt how to set the PATH to a directory that usually has to be invoked using its absolute or relative path.  
### Resources  
## Finding Commands 
When you type the name of a command, something inside one of the many directories listed in your $PATH  
variable is what actually gets executed (of course, unless the command is a builtin!). But which file, precisely? You  
can find out with the aptly-named which command:  
```
hacker@dojo:~$ which cat
/bin/cat
hacker@dojo:~$ /bin/cat /flag
YEAH
hacker@dojo:~$
```
Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and  
prints the first file it finds whose name matches the argument you passed.  

In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in  
the same directory as a flag file that we made readable by you! You must find win (with the which command), and  
cat the flag out of that directory!  
### Solve  
**Flag:** `pwn.college{sF2uQCCzXR0U50kPMvNQupxFdZO.01NzEzNxwCN1kjNzEzW}`  
I used which to find the directory of the win command which had the flag file in it and i cat flag from there to get the flag.
```
hacker@path~finding-commands:~$ which win
/challenge/paths/27143/win
hacker@path~finding-commands:~$ /challenge/paths/27143/flag
bash: /challenge/paths/27143/flag: Permission denied
hacker@path~finding-commands:~$ cat /challenge/paths/27143/flag
pwn.college{sF2uQCCzXR0U50kPMvNQupxFdZO.01NzEzNxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to find out the path of commands whose path's are present in the PATH variable by using the ``which`` command.
### Resources  
## Adding Commands  
Recall our example from the previous level:
```
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
What we see here, of course, is the hacker making the shell more useful for themselves by bringing their own  
commands to the party. Over time, you might amass your own elegant tools. Let's start with win!  

Previously, the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win  
does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to  
the PATH, and enable /challenge/run to find it!  

----------------------------------------------------------------------------------------------------------------------------------  
Hint: /challenge/run runs as root and will call win. Thus, win can simply cat the flag file. Again, the win command is  
the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. But remember, if  
you do that, your win command won't be able to find cat.  
  
You have three options to avoid that:  
1. Figure out where the cat program is on the filesystem. It must be in a directory that lives in the PATH variable,  
   so you can print the variable out (refer to Shell Variables to remember how!), and go through the directories in  
   it (recall that the different entries are separated by :), find which one has cat in it, and invoke cat by its  
   absolute path.
2. Set a PATH that has the old directories plus a new entry for wherever you create win.
3. Use read (again, refer to Shell Variables) to read /flag. Since read is a builtin functionality of bash, it is  
   unaffected by PATH shenanigans.
Now, go and win!
### Solve  
**Flag:**  `pwn.college{Il8rKqsTQ7CiETSfowWlU4y9gUv.QX2cjM1wCN1kjNzEzW}`
I added the win shell script to the PATH where cat already existed to invoke reading the flag.  
```
hacker@path~adding-commands:~$ echo 'cat /flag' > win
hacker@path~adding-commands:~$ PATH=".:$PATH"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: ./win: Permission denied
It looks like that did not work... Did you set PATH correctly?
hacker@path~adding-commands:~$ chmod ugo+x win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{Il8rKqsTQ7CiETSfowWlU4y9gUv.QX2cjM1wCN1kjNzEzW}
```
### New Learnings  
I learnt how to add a new command while maintaining the old set of commands present in PATH variable.  
### Resources  
askUbuntu  
## Hijacking Commands  
Armed with your knowledge, you can now carry out some shenanigans. This challenge is almost the same as  
the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before,  
it will not print anything out for you.  

How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have  
experience creating the win command when the previous challenge needed it. What else can you create?  
### Solve
**Flag:** `pwn.college{4Vy2A19DJkY4OesKU5rw48T6nBF.QX3cjM1wCN1kjNzEzW}`  
I created a fake /tmp/fakebin/rm, prepended it to PATH, and ran the challenge so the fake rm printed the flag and then delegated to /bin/rm, which deleted the file.  
```
hacker@path~hijacking-commands:~$ mkdir -p /tmp/fakebin
hacker@path~hijacking-commands:~$ 
cat > /tmp/fakebin/rm <<'EOF'
> #!/bin/bash
> cat -- "$@"
> /bin/rm "$@"
> EOF
hacker@path~hijacking-commands:~$ chmod +x /tmp/fakebin/rm
hacker@path~hijacking-commands:~$ export PATH="/tmp/fakebin:$PATH"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /tmp/fakebin/rm. Executing!
cat: -f: No such file or directory
pwn.college{4Vy2A19DJkY4OesKU5rw48T6nBF.QX3cjM1wCN1kjNzEzW}
Uh oh, looks like I successfully removed the flag! That means you did not 
properly set PATH to keep me from finding 'rm'. Since the flag is gone, you 
will need to re-launch the challenge from the module page! Better luck next 
time.
```
### New Learnings  
I learnt how to make a fake directory and make it run before the actual rm command to prevent unwanted possibilities.  
### Resources  

