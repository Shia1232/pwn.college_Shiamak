# Terminal Multiplexing 
## Launching Screen 
Let's dive right in!  

screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser  
tabs, but for your command line!  

Starting screen is super simple:  
```
hacker@dojo:~$ screen
```
That's it! You're now inside a screen session. It looks exactly like a terminal, but there are new capabilities there,  
waiting to be discovered.  

For this challenge, we've hooked things up so that just launching screen will get you the flag. Easy!  

----------------------------------------------------------------------------------------------------------------------------  
NOTE: When you're done with your command line, type exit or press Ctrl-D to leave the screen session. Then  
screen will terminate and return you to your original shell.  
### Solve  
**Flag:** `pwn.college{sICufbpwJvvq34yOKAzCqZwbMuT.0VN4IDOxwCN1kjNzEzW}`
```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{sICufbpwJvvq34yOKAzCqZwbMuT.0VN4IDOxwCN1kjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$ 
```
### New Learnings  
I learnt how to launch a screen in the terminal.  
### Resources  
## Detaching and Attaching  
Now we'll start digging in with the magic of detaching!  

Imagine you're working on something important over a remote connection, and your connection drops. With a  
normal terminal (outside of this awesome dojo environment), everything's gone. With screen, your work keeps  
running, and you can reattach later!  

You can also detach on purpose, which we'll do in this challenge. You detach by pressing Ctrl-A, followed by d (for  
detach). This leaves your session running in the background while you return to your normal terminal.  
```
hacker@dojo:~$ screen
[doing some work...]
[Press Ctrl-A, then d]
[detached from 12345.pts-0.hostname]
hacker@dojo:~$
```
To reattach, you can use the -r argument to screen:
```
hacker@dojo:~$ screen -r
```
For this challenge, you'll need to:  
1. Launch screen
2. Detach from it.
3. Run /challenge/run (this will secretly send the flag to your detached session!)
4. Reattach to see your prize

------------------------------------------------------------------------------------------------------------------------------------------------  
FUN FACT: Ctrl-A is screen's activation key for all of its shortcuts in its default configuration. All screen  
functionality is activated by some command combination starting with Ctrl-A.  

HINT: Remember: Hold Ctrl and press A, then release both and press d.  

HINT: If you see [detached from...], you did it right!  
### Solve  
**Flag:** `pwn.college{gAh7P-0Jk4OSmVjW8ed-wPPfF91.0lN4IDOxwCN1kjNzEzW}`  
```
acker@terminal-multiplexing~detaching-and-attaching:~$ screen bash
[detached from 162.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 162.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -ls
There are screens on:
	174.pts-0.terminal-multiplexing~launching-screen	(Remote or dead)
	163.pts-0.terminal-multiplexing~detaching-and-attaching	(Dead ???)
	187.pts-3.terminal-multiplexing~detaching-and-attaching	(Dead ???)
	211.pts-5.terminal-multiplexing~detaching-and-attaching	(Dead ???)
	235.pts-7.terminal-multiplexing~detaching-and-attaching	(Dead ???)
	293.pts-1.terminal-multiplexing~detaching-and-attaching	(Dead ???)
	162.pts-0.terminal-multiplexing~detaching-and-attaching	(Detached)
Remove dead screens with 'screen -wipe'.
7 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r 162
[detached from 162.pts-0.terminal-multiplexing~detaching-and-attaching]

hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{gAh7P-0Jk4OSmVjW8ed-wPPfF91.0lN4IDOxwCN1kjNzEzW}
Yes! Flag is: pwn.college{gAh7P-0Jk4OSmVjW8ed-wPPfF91.0lN4IDOxwCN1kjNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching:~$
```
### New Learnings  
I learnt how to reattach and detach a screen.  
### Resources  
## Finding Sessions  
Time for some screen detective work!  

If you become an avid screen user, you will inevitably end up with multiple sessions running. How do you find the  
right one to reattach to?  

Well, we can list them:
```
hacker@dojo:~$ screen -ls
There are screens on:
        23847.mysession   (Detached)
        23851.goodwork    (Detached)
        23855.morework    (Detached)
3 Sockets in /run/screen/S-hacker.
```
The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen  
session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.  
```
hacker@dojo:~$ screen -r goodwork
```
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two  
are decoys!  

You'll need to check each one until you find it. Don't forget to detach (Ctrl-A d) before trying the next session!
### Solve
**Flag:** `pwn.college{ci1GLlU8ZUxJBF5-b21ez2JXVGu.01N4IDOxwCN1kjNzEzW}`  
```
hacker@terminal-multiplexing~finding-sessions:~$ screen bash
[detached from 203.pts-3.terminal-multiplexing~finding-sessions]
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
	174.pts-0.terminal-multiplexing~launching-screen	(Remote or dead)
	163.pts-0.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	187.pts-3.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	211.pts-5.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	235.pts-7.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	293.pts-1.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	162.pts-0.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	144.session_063bc156bfa94946	(Detached)
	147.session_83bc02137b3b8752	(Detached)
	150.session_4708586a96e2440a	(Detached)
	203.pts-3.terminal-multiplexing~finding-sessions	(Detached)
11 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
[detached from 144.session_063bc156bfa94946]

hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{ci1GLlU8ZUxJBF5-b21ez2JXVGu.01N4IDOxwCN1kjNzEzW}
pwn.college{ci1GLlU8ZUxJBF5-b21ez2JXVGu.01N4IDOxwCN1kjNzEzW}
```
### New Learnings 
I learnt Reattaching to a screen using PID.  
### Resources  
## Switching Windows  
Okay, so far, screen is just a weird sort of terminal-with-a-terminal. But it can be much more!  
  
Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. This can be super handy for organizing different tasks!  
  
These windows are handled with different keyboard shortcuts, all starting with Ctrl-A:  
+ Ctrl-A c - Create a new window
+ Ctrl-A n - Next window
+ Ctrl-A p - Previous window
+ Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
+ Ctrl-A " - bring up a selection menu of all of the windows
For this challenge, we've set up a screen session with two windows:
+ Window 0 has... well, you'll have to switch there to find out!
+ Window 1 has a welcome message

Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get  
that flag!  
### Solve
**Flag:** `pwn.college{M7Yz0HuWaq9T_XEBHAzqiJixUYg.0FO4IDOxwCN1kjNzEzW}`  
```


hacker@terminal-multiplexing~switching-windows:~$ screen -ls
There are screens on:
	174.pts-0.terminal-multiplexing~launching-screen	(Remote or dead)
	163.pts-0.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	187.pts-3.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	211.pts-5.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	235.pts-7.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	293.pts-1.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	162.pts-0.terminal-multiplexing~detaching-and-attaching	(Remote or dead)
	144.session_063bc156bfa94946	(Remote or dead)
	147.session_83bc02137b3b8752	(Remote or dead)
	150.session_4708586a96e2440a	(Remote or dead)
	203.pts-3.terminal-multiplexing~finding-sessions	(Remote or dead)
	186.pts-2.terminal-multiplexing~switching-windows	(Dead ???)
	135.challenge_session	(Detached)
Remove dead screens with 'screen -wipe'.
13 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~switching-windows:~$ screen -r 135
[detached from 135.challenge_session]



cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows:~$ Use Ctrl-A 0 to switch to window 0!

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{M7Yz0HuWaq9T_XEBHAzqiJixUYg.0FO4IDOxwCN1kjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{M7Yz0HuWaq9T_XEBHAzqiJixUYg.0FO4IDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to navigate a screen's windows.
### Resources  
## Detaching and Attaching(tmux)
Let's try the same thing with tmux!  

tmux (terminal multiplexer) is screen's younger, more modern cousin. It does all the same things but with some  
different key bindings. The biggest difference? Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.  

So to detach from tmux, you press Ctrl-B followed by d.  
```
hacker@dojo:~$ tmux
[doing some work...]
[Press Ctrl-B, then d]
[detached (from session 0)]
hacker@dojo:~$
```
The commands also differ:
+ tmux ls - List sessions
+ tmux attach or tmux a - Reattach to session
For this challenge:
1. Launch tmux
2. Detach from it.
3. Run /challenge/run (this will send the flag to your detached session!)
4. Reattach to see your prize
### Solve  
**Flag:** `pwn.college{k_ZluU6npIkedGJrPYC5Ux56Wj8.0VO4IDOxwCN1kjNzEzW}`  
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach
[exited]



hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{k_ZluU6npIkedGJrPYC5Ux56Wj8.0VO4IDOxwCN1kjNzEzW}
Congratulations, here is your flag: pwn.college{k_ZluU6npIkedGJrPYC5Ux56Wj8.0VO4IDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt the usage of tmux and how to reattach and detach using tmux.
### Resources 
## Switching Windows  
Let's learn to navigate windows in tmux!  

Just like screen, tmux has windows. The key combos are different, but the concept is the same:  
+ Ctrl-B c - Create a new window
+ Ctrl-B n - Next window
+ Ctrl-B p - Previous window
+ Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
+ Ctrl-B w - See a nice window picker
Tmux shows your windows at the bottom in a status bar that looks like:
```
[0] 0:bash* 1:bash
```
The * shows your current window, and each entry also shows the process that the window was created to run.  

We've created a tmux session with two windows:
+ Window 0 has the flag!
+ Window 1 has your warm welcome.
Go get that flag!
### Solve
**Flag:** `pwn.college{gm7haL86KKC5Ilh3DUmBZGOMesB.0FM5IDOxwCN1kjNzEzW}`
```
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux -ls
tmux: unknown option -- s
usage: tmux [-2CDlNuVv] [-c shell-command] [-f file] [-L socket-name]
            [-S socket-path] [-T features] [command [flags]]
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux attach
[detached (from session challenge_session)]

 cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows-tmux:~$ echo $TMUX
/tmp/tmux-1000/default,136,0
hacker@terminal-multiplexing~switching-windows-tmux:~$ 
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux list-windows
0: bash- (1 panes) [80x24] [layout b25d,80x24,0,0,0] @0
1: bash* (1 panes) [184x44] [layout be7e,184x44,0,0,1] @1 (active)
hacker@terminal-multiplexing~switching-windows-tmux:~$ 
hacker@terminal-multiplexing~switching-windows-tmux:~$ Here is your flag: pwn.college{gm7haL86KKC5Ilh3DUmBZGOMesB.0FM5IDOxwCN1kjNzEzW}
```
### New Learnings  
I learnt how to navigate tmux.  






