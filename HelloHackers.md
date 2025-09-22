  # Hello Hackers
  ## Intro To Commands
  In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:  
  ```
  hacker@dojo:~$ whoami  
hacker  
hacker@dojo:~$  
```
Here, the user executed the whoami command, which simply prints the username (hacker) to the terminal. When the command terminates, the shell once again displays the prompt, ready for the next command.  

In this level, invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.  
  ### Solve
  **Flag:** `pwn.college{kMfQW2NQqTTUJs7jaT6y-YgCUMd.QX3YjM1wCN1kjNzEzW}`  
```
hacker@hello~intro-to-commands:~$ hello  
Success! Here is your flag:  
pwn.college{kMfQW2NQqTTUJs7jaT6y-YgCUMd.QX3YjM1wCN1kjNzEzW}  
```


### New Learnings
I learnt how to properly connect to pwn.college using ssh and moreover how to get the flag and put it in pwn.college to get the key.  
### References  
  
## Intro To Arguments  
Let's try something more complicated: a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its   arguments. The first word is the command, and the subsequent words are arguments. Observe:  
```
hacker@dojo:~$ echo Hello  
Hello  
hacker@dojo:~$  
```
In this case, the command was echo, and the argument was Hello. echo is a simple command that "echoes" all of its arguments back out onto the terminal, like you see in the session above.  
Let's look at echo with multiple arguments:  
```
hacker@dojo:~$ echo Hello Hackers!  
Hello Hackers!  
hacker@dojo:~$
```
In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!  

In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers. Try it now!  
### Solve  
**Flag:** `pwn.college{0FqCmq1N5N4HpVN_GdGfNp-CHty.QX4YjM1wCN1kjNzEzW}`  
At first while solving this i was confused on what to do as i thought i had to repeat hello hackers without using echo.  
On rereading the problem, I understood it clearly that i was required to use hello as a command like the website used echo and substitute how it used Hello as an argument with Hackers.   
```
hacker@hello~intro-to-arguments:~$ hello hackers  
Success! Here is your flag:  
pwn.college{0FqCmq1N5N4HpVN_GdGfNp-CHty.QX4YjM1wCN1kjNzEzW}
```
### New Learnings  
I learnt on what commands are and the usage of the echo command from the example and that an argument is always preceded by  
a command like so:  
```
[command] argument(s)
```
### References  


## Command History  
You're going to type a lot of commands, and typing everything from scratch can be annoying.  
Luckily, the shell saves a history of every command you invoke.

You can scroll through those saved commands with the up/down arrow keys, and we'll practice that in this  
challenge. This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it! In  
other challenges, the history will contain the log of the commands you've run, so if you need to run a similar  
command again, you can use the arrow keys to scroll through and find it!  
### Solve
**Flag:** `pwn.college{sNbzY3dbQYnes_HM0r5rCaMQrN2.0lNzEzNxwCN1kjNzEzW}`  
I was confused on how to solve this, upon pressing the upward key  
i recieved messages such as 
```
hello
```
and   
```
hackers
```
However upon going up a bit further I saw the message the flag is " _____" which confirmed that I had gone the right way.  

```
hacker@hello~command-history:~$ the flag is pwn.college{sNbzY3dbQYnes_HM0r5rCaMQrN2.0lNzEzNxwCN1kjNzEzW}
```
### New Learnings  
I learnt the usefulness of the up arrow key which saved me time in writing the same long commands later on and  
which also helped me execute programs using the terminal much more smoothly making mistakes much more forgiving  
### References  


  




  








