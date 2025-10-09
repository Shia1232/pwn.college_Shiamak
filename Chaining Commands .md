# Chaining Commands  
## Chaining with Semicolons  
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter  
separates lines. So, this:  
```
hacker@dojo:~$ echo COLLEGE > pwn
hacker@dojo:~$ cat pwn
COLLEGE
hacker@dojo:~$

```
Is roughly the same as this:
```
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$

```
Basically, when you hit Enter, your shell executes your typed command and, after that command terminates, gives  
you the prompt to input another command. The semicolon is analogous, just without the prompt and with you  
entering both commands before anything is executed.  

Give it a try now! In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a  
semicolon.  
### Solve
**Flag:** `pwn.college{sT1Wwe1tnn-m5-xhaAaLXXGNiPd.QX1UDO0wCN1kjNzEzW}`  
I ran /challenge/pwn chained with /challenge/college to get the flag.  
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{sT1Wwe1tnn-m5-xhaAaLXXGNiPd.QX1UDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to chain two commands.  
### Resources  
## Building On Success
You learned about exit codes in the Processes module. Now let's use them to chain commands together!  

The && operator allows you to run a second command only if the first command succeeds (in Linux convention, this  
means it exited with code 0). This is called the "AND" operator because both conditions must be true: the first  
command must succeed AND then the second command will run. That's super useful for complex commandline  
workflows where certain actions depend on the success of other actions.  

Here's the syntax:  
```
hacker@dojo:~$ command1 && command2
```
This means: "Run command1, and IF it succeeds, then run command2."  

Some examples:  
```
hacker@dojo:~$ touch /home/hacker/file && echo "this will run"
success
this will run
hacker@dojo:~$ touch /file && echo "this will NOT run"
touch: cannot touch '/file': Permission denied
hacker@dojo:~$
```
That second invocation of touch failed because the hacker user does not have write access to /file, so the echo  
did not run.  

In this challenge, you need to chain the programs /challenge/first-success and /challenge/second using the &&  
operator. Try running each command separately first to see what happens (which is that you will not get the flag).  
But if you chain them with &&, the flag will appear!  
### Solve  
**Flag:** `pwn.college{QWofvIUTAEKSPqkHEWr5EJYxD-e.0lM0MDOxwCN1kjNzEzW}`  
I used the && operator to run the two commands at the same time. 
```
hacker@chaining~building-on-success:~$ /challenge/first-success 
hacker@chaining~building-on-success:~$ /challenge/second
Error: /challenge/first-success must be successfully chained with 
/challenge/second using &&
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{QWofvIUTAEKSPqkHEWr5EJYxD-e.0lM0MDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to chain use the &&(And) command.  
### Resources  
## Handling Failure  
You just learned about the && operator, which runs the second command only if the first succeeds. Now let's  
learn about its opposite: the || operator allows you to run a second command only if the first command fails (exits  
with a non-zero code). This is called the "OR" operator because either the first command succeeds OR the second  
command will run.  

Here's the syntax:  
```
hacker@dojo:~$ command1 || command2
```
This means: "Run command1, and IF it fails, then run command2."  
  
Some examples:
```
hacker@dojo:~$ touch /file || echo "touch failed, so this runs"
touch: cannot touch '/file': Permission denied
touch failed, so this runs
hacker@dojo:~$ touch /home/hacker/file || echo "this will NOT run"
hacker@dojo:~$
```
The || operator is super useful for providing fallback commands or error handling!  
  
In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator. Go for  
it!  
### Solve
**Flag:** `pwn.college{In-kAXG4uCCoFKg8dh5A4RRnstM.01M0MDOxwCN1kjNzEzW}`  
I used the || command becuause /challenge/first-failure would fail and thus with this condition /challenge/second would run giving me the  
flag.  
```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{In-kAXG4uCCoFKg8dh5A4RRnstM.01M0MDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt the usage of the || command.
### Resources  
## Your First Shell Script  
As you combine more and more commands to achieve complex effects, the length of the combined prompt  
quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell  
script, and run them by executing the file! For example, consider our semicolon technique:  
```
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
```
We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix):  
```
echo COLLEGE > pwn
cat pwn
```
And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked  
like this, rather than taking commands from the user, it reads commands from the file.  
```
hacker@dojo:~$ ls
hacker@dojo:~$ bash pwn.sh
COLLEGE
hacker@dojo:~$ ls
pwn
hacker@dojo:~$
```
You can see that the shell script executed both commands, creating and printing the pwn file.  

Now, it's your turn! Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell  
script called x.sh, then run it with bash!  

-------------------------------------------------------------------------------------------------------------------------------  
NOTE: We haven't yet talked about Linux's amazing array of competent command line file editors. For now, feel free  
to use the Text Editor application in Desktop mode (Applications->Accessories->Text Editor) or the default  
editor in the VSCode Workspace!  
### Solve
**Flag:** `pwn.college{o5TAEtlZFYdNKf6CjPoofZtLaEe.QXxcDO0wCN1kjNzEzW}`
I wrote the commands /challenge/pwn and /challenge/college onto the shell script x.sh and then ran it using ``bash`` command to get the flag.  
```
hacker@chaining~your-first-shell-script:~$ echo '/challenge/pwn' > x.sh
hacker@chaining~your-first-shell-script:~$ echo '/challenge/college' >> x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{o5TAEtlZFYdNKf6CjPoofZtLaEe.QXxcDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to make a shell script.  
### Resources  
## Redirecting Script Output  
Let's try something a bit trickier! You've piped output between programs with |, but so far, this has just been  
between one command's output and a different command's input. But what if you wanted to send the output of  
several programs to one command? There are a few ways to do this, and we'll explore a simple one here: redirecting  
output from your script!  

As far as the shell is concerned, your script is just another command. That means you can redirect its input and  
output just like you did for commands in the Piping module! For example, you can write it to a file:  
```
hacker@dojo:~$ cat script.sh
echo PWN
echo COLLEGE
hacker@dojo:~$ bash script.sh > output
hacker@dojo:~$ cat output
PWN
COLLEGE
hacker@dojo:~$
```
All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode  
redirection, >& for redirecting to other file descriptors, and | for piping to another command.  

In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script  
that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the  
script into a single invocation of the /challenge/solve command!  
### Solve  
**Flag:** `pwn.college{4TKGvK05x1ySDMuYubK8_FzK8M1.QX4ETO0wCN1kjNzEzW}`  
```
hacker@chaining~redirecting-script-output:~$ echo '/challenge/pwn' > x.sh
hacker@chaining~redirecting-script-output:~$ echo '/challenge/college' >> x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve 
Correct! Here is your flag:
pwn.college{4TKGvK05x1ySDMuYubK8_FzK8M1.QX4ETO0wCN1kjNzEzW}
```
### New Learnings  
Learnt how to pipe a shell script's output into a command.  
### Resources  
## Executable Shell Scripts  
You have written your first shell script, but calling it via bash script.sh is a pain. Why do you need that bash?  

When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument.  
This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is  
executed.  

It turns out that you can avoid the need to manually invoke bash. If your shell script file is executable (recall File  
Permissions), you can simply invoke it via its relative or absolute path! For example, if you create script.sh in your  
home directory and make it executable, you can invoke it via /home/hacker/script.sh or ~/script.sh or (if your  
working directory is /home/hacker) ./script.sh.  

Try that here! Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly  
invoking bash!  
### Solve  
**Flag:** `pwn.college{UV8e6IBgvxj9NQZOBPo2EF_BkSV.QX0cjM1wCN1kjNzEzW}`  
```
hacker@chaining~executable-shell-scripts:~$ echo '/challenge/solve' > x.sh
hacker@chaining~executable-shell-scripts:~$ ls -l x.sh
-rw-r--r-- 1 hacker hacker 17 Sep 28 10:52 x.sh
hacker@chaining~executable-shell-scripts:~$ chmod ugo+x x.sh
hacker@chaining~executable-shell-scripts:~$ /x.sh
bash: /x.sh: No such file or directory
hacker@chaining~executable-shell-scripts:~$ x.sh
bash: x.sh: command not found
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{UV8e6IBgvxj9NQZOBPo2EF_BkSV.QX0cjM1wCN1kjNzEzW}
```
### New Learnings  
I learnt how to redirect execute a shell script without invoking bash
### Resources  
## Understanding Shebangs  
You're well on your way to your new life as a shell scripter! However, so far, your shellscripts can only be  
launched from the shell. Things worked great in the previous level (because you were invoking your script from the  
bash shell), but they won't work if your script was being invoked by, say, a program written in Python (or any other  
language).  

When a program is invoked in Linux, the Linux kernel first inspects the file to determine how it should be run. This  
does NOT use the extension (which is why you don't have to name your shell scripts with a .sh extension, or your  
Python scripts with a .py extension, or so on). Rather, Linux looks at the first few bytes of the file for this  
information.  

There are a bunch of different types of programs, but if the program file starts with the characters #! (often  
termed a "shebang"), Linux treats the file as an interpreted program, and the contents of the rest of the line as the  
path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument.  
  

Consider this shell script:
```
#!/bin/bash

echo "Hello Hackers!"
```
This can be executed as:
```
hacker@dojo:~$ chmod a+x script.sh
hacker@dojo:~$ ./script.sh
Hello Hackers!
hacker@dojo:~$
```
When ./script.sh was executed, Linux opened the file, read the first line, extracted /bin/bash as the interpreter,  
and executed /bin/bash ./script.sh to launch the script!  

Note, the shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it!  

For this challenge, create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the  
planet". Remember to make it executable, then run /challenge/run to verify your script works correctly!  

--------------------------------------------------------------------------------------------------------------------  
FUN FACT: Common shebangs you might see:
+ #!/bin/bash for bash scripts
+ #!/usr/bin/python3 for Python scripts
+ #!/bin/sh for POSIX shell scripts --- this is a more primitive predecessor to bash with fewer features, but more  
   compatibility to non-Linux systems!
  ### Solve
  **Flag:** `Flag: pwn.college{QtC7JReN2_OWoJPgmHDXFPG0DOU.0VOzMDOxwCN1kjNzEzW}`
  ```
  hacker@chaining~understanding-shebangs:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
  hacker@chaining~understanding-shebangs:~$ echo 'echo "hack the planet"' >> /home/hacker/solve.sh
  hacker@chaining~understanding-shebangs:~$ chmod u=rwx /home/hacker/solve.sh
  hacker@chaining~understanding-shebangs:~$ /challenge/run
  Testing your script...
  Perfect! Your flag:
  Flag: pwn.college{QtC7JReN2_OWoJPgmHDXFPG0DOU.0VOzMDOxwCN1kjNzEzW}
  ```
  ### New Learnings
  I learnt about shebangs.
  ### Resources
  ## Scripting with Arguments
  You've learned how to make shell scripts, but so far they've just been lists of commands. Scripts become much  
   more powerful when they can accept arguments! This might look like:
  ```
  hacker@dojo:~$ bash myscript.sh hello world
  ```
  The script can access these arguments using special variables:
  + $1 contains the first argument ("hello")
  + $2 contains the second argument ("world")
  + $3 would contain the third argument (if there had been one)
  + ...and so on
  Here's a simple example:
  ```
  hacker@dojo:~$ cat myscript.sh
  #!/bin/bash
  echo "First argument: $1"
  echo "Second argument: $2"
  hacker@dojo:~$ bash myscript.sh hello world
  First argument: hello
  Second argument: world
  hacker@dojo:~$
  ```
  For this challenge, you need to write a script at /home/hacker/solve.sh that:
  1. Takes two arguments
  2. Outputs them in REVERSE order (second argument first, then the first argument)
  For example:
```
hacker@dojo:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@dojo:~$
```
Once your script works correctly, run /challenge/run to get your flag!
### Solve 
**Flag:** `pwn.college{EQ122xGrLKM3tx0rqaQXi23kBX4.0VNzMDOxwCN1kjNzEzW}`
```
hacker@chaining~scripting-with-arguments:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ echo 'echo "$2 $1"' >> /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{EQ122xGrLKM3tx0rqaQXi23kBX4.0VNzMDOxwCN1kjNzEzW}
```
### New Learnings 
I learnt how to script with arguments.
### Resources  
## Scripting with Conditionals 
Now that you can use arguments in scripts, let's make them smarter with conditional logic!  
  
In bash, you can use if statements to make decisions:  
```
if [ "$1" == "ping" ]
then
    echo "pong"
fi
```
The above, in English, is if the first argument is "ping", print out "pong". The syntax is somewhat unforgiving  
for a few reasons. First, you must have spaces after if (if you're used to a language like C, this is different), after [,  
and before ]. Second, if, then, and fi must all be on different lines (or separated by semicolons); you can't lump  
them into the same statement. It's also a bit weird: instead of endif or end or something like that, the terminator of  
the if statement is fi (if backwards). Just something you have to remember.  

For this challenge, write a script at /home/hacker/solve.sh that:
+ Takes one argument
+ If the argument is "pwn", output "college"
+ For any other input, output nothing
Example :
```
hacker@dojo:~$ bash /home/hacker/solve.sh pwn
college
hacker@dojo:~$ bash /home/hacker/solve.sh foo
hacker@dojo:~$
```
Once your script works correctly, run /challenge/run to get your flag!  

--------------------------------------------------------------------------------------------------------------------------------------------------  
NOTE: Interested in what else you can check in a condition, other than string equality? Read all about it with help  
test!  
### Solve 
**Flag:** `pwn.college{Iu-bzsPAkQDP2xJ9NBf9e2kxCAa.0lNzMDOxwCN1kjNzEzW}`
```
hacker@chaining~scripting-with-conditionals:~$ echo '#!/bin/bash' > /home/hacker/solve.sh
echo 'if [ "$1" = "pwn" ]; then' >> /home/hacker/solve.sh
echo '  echo "college"' >> /home/hacker/solve.sh
echo 'fi' >> /home/hacker/solve.sh
chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{Iu-bzsPAkQDP2xJ9NBf9e2kxCAa.0lNzMDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt to script with conditionals.
### Resources
## Scripting with Default Cases 
Your if statements so far have handled specific cases, but what about everything else? That's where else  
comes in!  

The else clause executes when the if condition is false:  
```
if [ "$1" == "hello" ]
then
    echo "Hi there!"
else
    echo "I don't understand"
fi
```
Note that the else doesn't have a condition --- it catches everything that didn't match previously. It also doesn't  
have a then statement. Finally, the fi goes after the else block to denote the end of the whole complex statement!  
It is also optional: you didn't have it in the previous level, and you only need it if the logic you're trying to achieve  
demands it.  

Here's a practical example:  
```
if [ "$1" == "start" ]
then
    echo "Starting the service..."
else
    echo "Unknown command. Use 'start' to begin."
fi
```
For this challenge, write a script at /home/hacker/solve.sh that:  
+ Takes one argument
+ If the argument is "pwn", output "college"
+ For any other input, output "nope"

Example:  
```
hacker@dojo:~$ bash /home/hacker/solve.sh pwn
college
hacker@dojo:~$ bash /home/hacker/solve.sh hack
nope
hacker@dojo:~$ bash /home/hacker/solve.sh anything
nope
hacker@dojo:~$
```
Once your script works correctly, run /challenge/run to get your flag!  
### Solve  
**Flag:** `pwn.college{Q4032ZD7bBpwmv8jk4q6YJZsgIy.01NzMDOxwCN1kjNzEzW}`  
```
hacker@chaining~scripting-with-default-cases:~$ cat > /home/hacker/solve.sh <<'EOF'
#!/bin/bash

if [[ "$1" == "pwn" ]]; then
  echo "college"
else
  echo "nope"
fi
EOF

chmod +x /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{Q4032ZD7bBpwmv8jk4q6YJZsgIy.01NzMDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to use the else conditional.  
### Resources  
## Scripting with Multiple Conditions  
You've learned how to use a single if statement to check a condition. But what if you need to check multiple  
conditions? You can use elif (short for else if):  
```
if [ "$1" == "one" ]
then
    echo "1"
elif [ "$1" == "two" ]
then
    echo "2"
elif [ "$1" == "three" ]
then
    echo "3"
else
    echo "unknown"
fi
```
Note that you do need a then after the elif, just like the if. As before the else at the end catches everything that  
didn't match.   

For this challenge, write a script at /home/hacker/solve.sh that:  
+ Takes one argument
+ If the argument is "hack", output "the planet"
+ If the argument is "pwn", output "college"
+ If the argument is "learn", output "linux"
+ For any other input, output "unknown"
Example:
```
hacker@dojo:~$ bash /home/hacker/solve.sh hack
the planet
hacker@dojo:~$ bash /home/hacker/solve.sh pwn
college
hacker@dojo:~$ bash /home/hacker/solve.sh learn
linux
hacker@dojo:~$ bash /home/hacker/solve.sh foo
unknown
hacker@dojo:~$
```
Once your script works correctly, run /challenge/run to get your flag!  

---------------------------------------------------------------------------------------------------------------------------------   


NOTE: As you're creating your script, make sure to follow the spacing closely in the examples. Unlike many other  
languages, bash requires the [ and the ] to be separated from other characters by spaces, otherwise it cannot  
parse the condition.  
### Solve
**Flag:** `pwn.college{Yz0Fvk98obK7JrllaUjzxvRPnMK.0FOzMDOxwCN1kjNzEzW}`  
```
 cat > /home/hacker/solve.sh << 'EOF'                                                                                              #!/bin/bash                             

if [[ "$1" == "hack" ]]; then
  echo "the planet"
elif [[ "$1" == "pwn" ]]; then
  echo "college"
elif [[ "$1" == "learn" ]]; then
  echo "linux"
else
  echo "unknown"
fi
EOF

chmod +x /home/hacker/solve.sh
                                                                                                                                                                          
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{Yz0Fvk98obK7JrllaUjzxvRPnMK.0FOzMDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt about the elif command and it's usage.
### Resources  
## Reading Shell Scripts  
You're not the only one who writes shell scripts! They are very handy for doing simple "system-level" tasks, and  
are a common tool that developers and sysadmins reach for. In fact, a surprising fraction of the programs on a  
typical Linux machine are shell scripts.  
  
In this level, we will learn to read shell scripts. /challenge/run is a shell script that requires you to put in a secret  
password, but that password is hardcoded into the script iself! Read the script (using, say, cat), figure out the  
password, and get the flag!  

------------------------------------------------------------------------------------------------------------------------------------  
NOTE: Feel free to try to read the code of other challenges as well! Reading code is a critical strategy in learning  
new skills, because you can see how certain functionality was implemented and reuse those strategies in your  
own scripts. But watch out: some program files are machine code, and will not be readable to humans. You can use  
the file command to differentiate, but almost all the challenges in the Linux Luminarium are implemented as shell  
scripts and are safe to cat out.  
### Solve
**Flag:** `pwn.college{Ar9XFFRVyHMehbzpx1_jp2dCv5R.0lMwgDOxwCN1kjNzEzW}`  
I read /challenge/run to figure out the secret password and entered it to get the flag.  
```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
	echo "CORRECT! Your flag:"
	cat /flag
else
	echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{Ar9XFFRVyHMehbzpx1_jp2dCv5R.0lMwgDOxwCN1kjNzEzW}
```
### New Learnings
I learnt that executables can be shell scripts as well.  
### Resources  






 

  





