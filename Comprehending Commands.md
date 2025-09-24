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
**Flag:** `pwn.college{gKlGMx91P1D3d8t7chNae9VTFjB.01MwMDOxwCN1kjNzEzW}`  
Here the approach was very clear for me, I had to compare two files and the real flag would be the differentiating factor as the two files were identical in every other aspect.  
```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt  
3a4  
> pwn.college{gKlGMx91P1D3d8t7chNae9VTFjB.01MwMDOxwCN1kjNzEzW}  
```
### New Learnings  
I learnt the usage of the diff command and how to use it in the terminal.  
### Resources  
## listing files  
So far, we've told you which files to interact with. But directories can have lots of files (and other directories)  
inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using  
the ls command!  
ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided.  
Observe:  
```
hacker@dojo:~$ ls /challenge  
run  
hacker@dojo:~$ ls  
Desktop    Downloads  Pictures  Templates  
Documents  Music      Public    Videos  
hacker@dojo:~$ ls /home/hacker  
Desktop    Downloads  Pictures  Templates  
Documents  Music      Public    Videos  
hacker@dojo:~$  
```
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.  
### Solve  
**Flag:** `pwn.college{IWceFKAFCyAosZShBHVmm_8iKgX.QX4IDO0wCN1kjNzEzW}`  
It was given the executable was in '/challenge' directory so upon using the ls command in the directory it showed a random file with run in it which had been renamed  
which gave me the flag.  
```
hacker@commands~listing-files:~$ cd /challenge  
hacker@commands~listing-files:/challenge$ ls  
31278-renamed-run-29495  DESCRIPTION.md  
hacker@commands~listing-files:/challenge$ ./31278-renamed-run-29495    
Yahaha, you found me! Here is your flag:  
pwn.college{IWceFKAFCyAosZShBHVmm_8iKgX.QX4IDO0wCN1kjNzEzW}  
```
### New Learnings  
Learnt the usage of ls and how to **actually** apply it in a terminal to find the flag.  
### Resources  
## touching files  
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here.  
You can create a new, blank file by touching it with the touch command:  
```
hacker@dojo:~$ cd /tmp  
hacker@dojo:/tmp$ ls  
hacker@dojo:/tmp$ touch pwnfile  
hacker@dojo:/tmp$ ls  
pwnfile  
hacker@dojo:/tmp$
```
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your  
flag!  
### Solve  
**Flag:** `pwn.college{Q8xcfKM0HlvRavmZMEP18p6dOVK.QXwMDO0wCN1kjNzEzW}`  
The first attempt of mine at this had me a bit confused as I thought I had to create a '/tmp/..' file in the home directory but after  
trying that, I noticed by using the ls command that only a directory is still being made which gave me the hint  
to touch a pwn and college file in the /tmp directory and then run /challenge/run  
```
hacker@commands~touching-files:~$ cd /tmp  
hacker@commands~touching-files:/tmp$ touch pwn  
hacker@commands~touching-files:/tmp$ touch college  
hacker@commands~touching-files:/tmp$ /challenge/run  
Success! Here is your flag:  
pwn.college{Q8xcfKM0HlvRavmZMEP18p6dOVK.QXwMDO0wCN1kjNzEzW}  
```
### New Learnings  
Learnt how to make new files in a directory directly using the terminal using the touch command.  
### Resources  
## removing files  
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to  
clean up!  

In Linux, you remove files with the rm command, as so:  
```
hacker@dojo:~$ touch PWN  
hacker@dojo:~$ touch COLLEGE  
hacker@dojo:~$ ls  
COLLEGE     PWN  
hacker@dojo:~$ rm PWN  
hacker@dojo:~$ ls  
COLLEGE  
hacker@dojo:~$  
```
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/  
check, which will make sure you've deleted it and then give you the flag!  
### Solve  
**Flag:** `pwn.college{0RuRlHQXqNsfIkmRfSq1uw1U7Fm.QX2kDM1wCN1kjNzEzW}`  
```
hacker@commands~removing-files:~$ ls  
a  delete_me   
hacker@commands~removing-files:~$ rm delete_me  
hacker@commands~removing-files:~$ /challenge/check  
Excellent removal. Here is your reward:  
pwn.college{0RuRlHQXqNsfIkmRfSq1uw1U7Fm.QX2kDM1wCN1kjNzEzW}  
```
### New Learnings  
I learnt how to remove a file from a directory using the terminal.  
### Resources  
## moving files  
You can also move files around with the mv command. The usage is simple:  
```
hacker@dojo:~$ ls  
my-file  
hacker@dojo:~$ cat my-file  
PWN!  
hacker@dojo:~$ mv my-file your-file  
hacker@dojo:~$ ls  
your-file  
hacker@dojo:~$ cat your-file  
PWN!  
hacker@dojo:~$  
```
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /  
challenge/check, which will check things out and give the flag to you.  
### Solve  
**Flag:** `pwn.college{8RIwyvcJ8nT0_auSAmmSeajah7D.0VOxEzNxwCN1kjNzEzW}`  
```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet  
Correct! Performing 'mv /flag /tmp/hack-the-planet'.  
hacker@commands~moving-files:~$ /challenge/check  
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:  
pwn.college{8RIwyvcJ8nT0_auSAmmSeajah7D.0VOxEzNxwCN1kjNzEzW}  
```
### New Learnings  
I learnt how to move files from one directory to another using the mv command.  
### Resources  
## hidden files  
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't  
show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag,  
as so:  
```
hacker@dojo:~$ touch pwn  
hacker@dojo:~$ touch .college  
hacker@dojo:~$ ls  
pwn  
hacker@dojo:~$ ls -a  
.college	pwn  
hacker@dojo:~$
```
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.  
### Solve  
**Flag:** `pwn.college{A54VBM9Xs7GKJAB6Bq4e2_IPlVS.QXwUDO0wCN1kjNzEzW}`  
```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.                      bin        etc    lib64   nix   run   tmp
..                     boot       home   libx32  opt   sbin  usr
.dockerenv             challenge  lib    media   proc  srv   var
.flag-133072577915997  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cat .flag-133072577915997
```
### New Learnings  
I learnt how to expose hidden files with the ``ls -a`` command.  
### Resources  
## An Epic Filesystem Quest  
With your knowledge of cd, ls, and cat, we're ready to play a little game!  

We'll start it out in /. Normally:  
```
hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
```
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file  
and the challenge directory.  

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's  
how it'll work:  
0.Your first clue is in /. Head on over there.
1.Look around with ls. There'll be a file named HINT or CLUE or something along those lines!  
2.cat that file to read the clue!  
3.Depending on what the clue says, head on over to the next directory (or don't!).  
4.Follow the clues to the flag!  

Good Luck!  
### Solve 
**Flag:** `pwn.college{scGysvN9cF6r-pb_dp1A274OOIo.QX5IDO0wCN1kjNzEzW}`  
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
DISPATCH  challenge  flag  lib32   media  opt   run   sys  var
bin       dev        home  lib64   mnt    proc  sbin  tmp
boot      etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat DISPATCH
Great sleuthing!
The next clue is in: /usr/share/perl5/Debian/DebConf/Client

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/share/perl5/Debian/DebConf/Client
ConfModule.pm  TIP-TRAPPED
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/share/perl5/Debian/DebConf/Client/TIP-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/misc

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/misc
hacker@commands~an-epic-filesystem-quest:/usr/share/misc$ ls
TEASER  config.guess  config.sub  magic  magic.mgc
hacker@commands~an-epic-filesystem-quest:/usr/share/misc$ cat TEASER
Congratulations, you found the clue!
The next clue is in: /usr/lib/python3/dist-packages/sympy/simplify/tests

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/misc$ cd /usr/lib/python3/dist-packages/sympy/simplify/tests
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ ls
ALERT             test_epathtools.py   test_powsimp.py   test_sqrtdenest.py
__init__.py       test_fu.py           test_radsimp.py   test_traversaltools.py
__pycache__       test_function.py     test_ratsimp.py   test_trigsimp.py
test_combsimp.py  test_gammasimp.py    test_rewrite.py
test_cse.py       test_hyperexpand.py  test_simplify.py
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ cat ALERT
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/fs/xfs

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ ls /opt/linux/linux-5.4/fs/xfs
BLUEPRINT-TRAPPED    xfs_dquot_item.h    xfs_iomap.c        xfs_quotaops.c
Kconfig              xfs_error.c         xfs_iomap.h        xfs_refcount_item.c
Makefile             xfs_error.h         xfs_iops.c         xfs_refcount_item.h
kmem.c               xfs_export.c        xfs_iops.h         xfs_reflink.c
kmem.h               xfs_export.h        xfs_itable.c       xfs_reflink.h
libxfs               xfs_extent_busy.c   xfs_itable.h       xfs_rmap_item.c
mrlock.h             xfs_extent_busy.h   xfs_iwalk.c        xfs_rmap_item.h
scrub                xfs_extfree_item.c  xfs_iwalk.h        xfs_rtalloc.c
xfs.h                xfs_extfree_item.h  xfs_linux.h        xfs_rtalloc.h
xfs_acl.c            xfs_file.c          xfs_log.c          xfs_stats.c
xfs_acl.h            xfs_filestream.c    xfs_log.h          xfs_stats.h
xfs_aops.c           xfs_filestream.h    xfs_log_cil.c      xfs_super.c
xfs_aops.h           xfs_fsmap.c         xfs_log_priv.h     xfs_super.h
xfs_attr_inactive.c  xfs_fsmap.h         xfs_log_recover.c  xfs_symlink.c
xfs_attr_list.c      xfs_fsops.c         xfs_message.c      xfs_symlink.h
xfs_bio_io.c         xfs_fsops.h         xfs_message.h      xfs_sysctl.c
xfs_bmap_item.c      xfs_globals.c       xfs_mount.c        xfs_sysctl.h
xfs_bmap_item.h      xfs_health.c        xfs_mount.h        xfs_sysfs.c
xfs_bmap_util.c      xfs_icache.c        xfs_mru_cache.c    xfs_sysfs.h
xfs_bmap_util.h      xfs_icache.h        xfs_mru_cache.h    xfs_trace.c
xfs_buf.c            xfs_icreate_item.c  xfs_ondisk.h       xfs_trace.h
xfs_buf.h            xfs_icreate_item.h  xfs_pnfs.c         xfs_trans.c
xfs_buf_item.c       xfs_inode.c         xfs_pnfs.h         xfs_trans.h
xfs_buf_item.h       xfs_inode.h         xfs_pwork.c        xfs_trans_ail.c
xfs_dir2_readdir.c   xfs_inode_item.c    xfs_pwork.h        xfs_trans_buf.c
xfs_discard.c        xfs_inode_item.h    xfs_qm.c           xfs_trans_dquot.c
xfs_discard.h        xfs_ioctl.c         xfs_qm.h           xfs_trans_priv.h
xfs_dquot.c          xfs_ioctl.h         xfs_qm_bhv.c       xfs_xattr.c
xfs_dquot.h          xfs_ioctl32.c       xfs_qm_syscalls.c
xfs_dquot_item.c     xfs_ioctl32.h       xfs_quota.h
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ cat BLUEPRINT-TRAPPED 
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ cat BLUEPRINT-TRAPPED
cat: BLUEPRINT-TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ cat /opt/linux/linux-5.4/fs/xfs/BLUEPRINT-TRAPPED
Lucky listing!
The next clue is in: /usr/share/doc/libidn2-0

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sympy/simplify/tests$ cd /usr/share/doc/libidn2-0
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ ls
AUTHORS  BRIEF  NEWS.gz  README.md.gz  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ cat BRIEF
Congratulations, you found the clue!
The next clue is in: /usr/share/racket/pkgs/parser-tools-lib
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ ls /usr/share/racket/pkgs/parser-tools-lib
INFO  LICENSE.txt  info.rkt  parser-tools
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ cat /usr/share/racket/pkgs/parser-tools-lib/INFO
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/arch/arm/mach-efm32

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ ls /opt/linux/linux-5.4/arch/arm/mach-efm32
CLUE-TRAPPED  Makefile  Makefile.boot  dtmachine.c
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ cat /opt/linux/linux-5.4/arch/arm/mach-efm32/CLUE-TRAPPED
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/sound/core/seq/oss

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$  ls -a
.  ..  AUTHORS  BRIEF  NEWS.gz  README.md.gz  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libidn2-0$ cd /opt/linux/linux-5.4/sound/core/seq/oss
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/core/seq/oss$ ls -a
.   .NOTE     seq_oss.c         seq_oss_event.c  seq_oss_init.c   seq_oss_midi.c  seq_oss_readq.c  seq_oss_rw.c     seq_oss_synth.h  seq_oss_timer.h   seq_oss_writeq.h
..  Makefile  seq_oss_device.h  seq_oss_event.h  seq_oss_ioctl.c  seq_oss_midi.h  seq_oss_readq.h  seq_oss_synth.c  seq_oss_timer.c  seq_oss_writeq.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/sound/core/seq/oss$ cat .NOTE
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{scGysvN9cF6r-pb_dp1A274OOIo.QX5IDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt the applications of the ``ls``, ``cd``, ``ls -a`` and ``cat`` commands together and how to find the flag using them in synchronization.  
### Resources  
## making directories  
We can create files. How about directories? You make directories using the mkdir command. Then you can stick  
files in there!  
Watch:  
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will  
check your solution and give you the flag!  
### Solve
**Flag:**  `pwn.college{4H81GE8HNAvok8c7ZsilGWxjUj2.QXxMDO0wCN1kjNzEzW}`  
```
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd ./pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challege/run
bash: /challege/run: No such file or directory
hacker@commands~making-directories:/tmp/pwn$ ls
college
hacker@commands~making-directories:/tmp/pwn$ cd college
bash: cd: college: Not a directory
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{4H81GE8HNAvok8c7ZsilGWxjUj2.QXxMDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to make directories using the ``mkdir`` command.  
### Resources  
## finding files















