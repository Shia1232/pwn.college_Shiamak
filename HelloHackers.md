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
```
hacker@hello~intro-to-arguments:~$ hello hackers  
Success! Here is your flag:  
pwn.college{0FqCmq1N5N4HpVN_GdGfNp-CHty.QX4YjM1wCN1kjNzEzW}
```






