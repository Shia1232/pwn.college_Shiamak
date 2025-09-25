# Digesting Documentations 
## Learning From Documentation  
The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a  
specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig  
into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module,  
you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the  
concept of reading documentation.  

The correct usage of programs depends, in a large part, on the proper specification of arguments to them. Recall
the ``-a`` of ``ls -a`` in the hidden files challenge of the Basic Commands module: that ``-a`` was an argument that told ``ls``
to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ``ls`` with the -   
a argument was the correct way to use it in our scenario.  

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give  
you the flag. Let's pretend that this is its documentation:  
> Welcome to the documentation for ``/challenge/challenge``!
>  To properly run this program, you will need to pass it the argument of ``--giveflag``.
>  Good luck!
Given that knowledge, go get the flag!
### Solve  
**Flag:** `pwn.college{MuQYrr6Fj_ebZQHHUTzxG7HI0IJ.QX0ITO0wCN1kjNzEzW}`  
I had to use the ``--giveflag`` argument here to get the flag while running the program while usually we just  
run ``/challenge/challenge``  
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{MuQYrr6Fj_ebZQHHUTzxG7HI0IJ.QX0ITO0wCN1kjNzEzW}
```
### New Learnings  
I learnt that sometimes you need to correctly use a program(for example, ``ls -a`` instead of ``ls``) to get the desired result  
we want.  
### Resources  
## Learning Complex Usage  
While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you’ve already encountered this with the `find` level in Basic Commands. `find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level’s documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`!  
> This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument.  
> The argument to the `--printfile` argument is the path of the flag to read.  
> For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!  
### Solve  
**Flag:** `pwn.college{QWL6xQmHxeTHtYefsa4xIYmRXLR.QX1ITO0wCN1kjNzEzW}`
When I was first solving, I was stuck on the argument part.  
I realized I was overcomplicating it and just tried ``/flag`` which worked.  
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](/linux-luminarium/commands).
`find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/challenge
Correct argument! Here is the /challenge/challenge file:
#!/opt/pwn.college/bash

if [ "$#" -eq 0 ]
then
	fold -s <<< "Incorrect usage! You must pass an argument to me (read the challenge description for details)."
	exit 1
fi

if [ "$1" != "--printfile" ]
then
	fold -s <<< "Incorrect usage! You passed the wrong argument (read the challenge description for details)."
	exit 2
fi

if [ "$#" -eq 1 ]
then
	fold -s <<< "You must pass a file for --printfile to read!"
	exit 3
fi

echo "Correct argument! Here is the $2 file:"
cat "$2"
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{QWL6xQmHxeTHtYefsa4xIYmRXLR.QX1ITO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to use the --printfile argument and how some arguments to a command have their own commands  
such as ``-name`` and ``--printfile``  
### Resources  

## Reading Manuals  
This level introduces the man command. man is short for manual, and will display (if available) the manual of the  
command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is  
a real command):
```
hacker@dojo:~$ man yes
```
This will display the manual page for yes, which will look something like this:  
```
YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)
```
The important sections are:  
```
NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE                          NAME(1)
```
You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage,  
you can hit q to quit.  

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man
directory, but you never need to interact with it directly: you just query it using the man command. The arguments  
to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up  
the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would  
result in man displaying garbage).  

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You  
must learn this option through the man page for challenge!  
### Solve  
**Flag:** `pwn.college{Ivr_K2a_suiJmlI8vqJ0naLHSEJ.QX0EDO0wCN1kjNzEzW}`
I used the ``man challenge`` command to find out the argument which prints the flag  
and the actual command of challenge itself.  
```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ challenge --vrasui 280
bash: challenge: command not found
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$ /challenge/challenge --vrasui 280
Correct usage! Your flag: pwn.college{Ivr_K2a_suiJmlI8vqJ0naLHSEJ.QX0EDO0wCN1kjNzEzW}
```
### New Learnings 
I learnt how to use the ``man`` command and it's usage and wide use-cases in learning more about a command's  
arguments which gives it special usages.  
### Resources  
## Searching Manuals  
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n  
to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!  

Find the option that will give you the flag by reading the challenge man page.  
### Solve
**Flag:** `pwn.college{gh4kJ0EKHsJ1tERGSWb732CCJWa.QX1EDO0wCN1kjNzEzW}`  
I used man challenge and used /flag to search for the keyword flag to find the right argument to the ``challenge`` command.  
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --wht
Initializing...
Correct usage! Your flag: pwn.college{gh4kJ0EKHsJ1tERGSWb732CCJWa.QX1EDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt how to navigate the manual or ``man`` command better using searching and n.  
### Resources  
## Searching For Manuals  
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered  
in a searchable database, so you'll be able to search the man page database to find the hidden  
challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man  
man!  

-------------------------------------------------------------------------------------------------------------------------------  
HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure  
out how to search for the hidden manpage that will tell you how to use /challenge/challenge	  

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!  
### Solve  
**Flag:** `pwn.college{Q2ESPr6xV9JqVw6FNlJbiUj1HzM.QX2EDO0wCN1kjNzEzW}`
I was on the right track on this program but I got stuck as I didn't read the manpage fully.  
Upon finally reading the manpage using ``-K`` argument I got the solution.  
```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k /challenge/challenge flag
rxqwlbijzw (1)       - print the flag!
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environmen...
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environmen...
linux64 (1)          - change reported architecture in new program environmen...
pcap-config (1)      - write libpcap compiler and linker flags to standard ou...
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the ...
set_matchpathcon_flags (3) - set flags controlling the operation of matchpath...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matc...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpat...
setarch (1)          - change reported architecture in new program environmen...
setarch (8)          - change reported architecture in new program environmen...
x86_64 (8)           - change reported architecture in new program environmen...
hacker@man~searching-for-manuals:~$ /challenge/challenge rxqwlbijzw
Incorrect usage! Please read the hidden challenge man page!
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k /challenge/challenge print
rxqwlbijzw (1)       - print the flag!
aarch64-linux-gnu-strings (1) - print the sequences of printable characters i...
arch (1)             - print machine hardware name (same as uname -m)
asprintf (3)         - print to allocated string
base32 (1)           - base32 encode/decode data and print to standard output
base64 (1)           - base64 encode/decode data and print to standard output
blkid (8)            - locate/print block device attributes
bsd-from (1)         - print names of those who have sent mail
cat (1)              - concatenate files and print on the standard output
date (1)             - print or set the system date and time
dbus-monitor (1)     - debug probe to print message bus messages
dmesg (1)            - print or control the kernel ring buffer
dprintf (3)          - formatted output conversion
egrep (1)            - print lines that match patterns
error_print_progname (3) - glibc error reporting functions
fgrep (1)            - print lines that match patterns
fixpspps (1)         - filter to fix PSPrint PostScript so PSUtils work
fmtcheck (3bsd)      - sanitizes user-supplied printf(3)-style format string
fmtmsg (3)           - print formatted error messages
fortune (6)          - print a random, hopefully interesting, adage
fprintf (3)          - formatted output conversion
from (1)             - print names of those who have sent mail
fwprintf (3)         - formatted wide-character output conversion
git-grep (1)         - Print lines matching a pattern
grep (1)             - print lines that match patterns
groups (1)           - print the groups a user is in
hostid (1)           - print the numeric identifier for the current host
id (1)               - print real and effective user and group IDs
Image::ExifTool::PrintIM (3pm) - Read PrintIM meta information
infocmp (1)          - compare or print out terminfo descriptions
isprint (3)          - character classification functions
isprint_l (3)        - character classification functions
iswprint (3)         - test for printing wide character
jfr (1)              - parse and print Flight Recorder files
jmap (1)             - print details of a specified process
jshell (1)           - interactively evaluate declarations, statements, and e...
jstack (1)           - print Java stack traces of Java threads for a specifie...
ldd (1)              - print shared object dependencies
logname (1)          - print user's login name
lp (4)               - line printer devices
lsb_release (1)      - print distribution-specific information
malloc_stats (3)     - print memory allocation statistics
mode_to_security_class (3) - convert between SELinux class and permission val...
ms_print (1)         - post-processing tool for Massif
my_print_defaults (1) - display options from option files
netstat (8)          - Print network connections, routing tables, interface s...
nfnl_osf (8)         - OS fingerprint loader utility
nproc (1)            - print the number of processing units available
openssl-spkac (1ssl) - SPKAC printing and generating utility
openssl-version (1ssl) - print OpenSSL version information
pahole (1)           - Shows, manipulates data structure layout and pretty pr...
pam_echo (8)         - PAM module for printing text messages
paperconf (1)        - print paper configuration information
pcap_geterr (3pcap)  - get or print libpcap error message text
pcap_perror (3pcap)  - get or print libpcap error message text
perror (3)           - print a system error message
pod2usage (1)        - print usage messages from embedded pod docs in files
podselect (1)        - print selected sections of pod documentation on standa...
pr (1)               - convert text files for printing
print (1)            - execute programs via entries in the mailcap file
print_access_vector (3) - convert between SELinux class and permission values...
printenv (1)         - print all or part of environment
printerbanner (1)    - print large banner on printer
printf (1)           - format and print data
printf (3)           - formatted output conversion
prtstat (1)          - print statistics of a process
psiginfo (3)         - print signal message
psignal (3)          - print signal message
pwd (1)              - print name of current/working directory
py3versions (1)      - print python3 version information
readlink (1)         - print resolved symbolic links or canonical file names
realpath (1)         - print the resolved path
rgrep (1)            - print lines that match patterns
runlevel (8)         - Print previous and current SysV runlevel
security_av_perm_to_string (3) - convert between SELinux class and permission...
security_av_string (3) - convert between SELinux class and permission values ...
security_class_to_string (3) - convert between SELinux class and permission v...
seq (1)              - print a sequence of numbers
set_matchpathcon_printf (3) - set flags controlling the operation of matchpat...
shasum (1)           - Print or Check SHA Checksums
showfigfonts (6)     - prints a list of available figlet fonts
snprintf (3)         - formatted output conversion
spkac (1ssl)         - SPKAC printing and generating utility
sprintf (3)          - formatted output conversion
string_to_av_perm (3) - convert between SELinux class and permission values a...
string_to_security_class (3) - convert between SELinux class and permission v...
strings (1)          - print the sequences of printable characters in files
stty (1)             - change and print terminal line settings
swaplabel (8)        - print or change the label or UUID of a swap area
swprintf (3)         - formatted wide-character output conversion
sys_errlist (3)      - print a system error message
sys_nerr (3)         - print a system error message
systemd-id128 (1)    - Generate and print sd-128 identifiers
tac (1)              - concatenate and print files in reverse
tex2mail (1)         - TeX to ascii math prettyprinter
tty (1)              - print the file name of the terminal connected to stand...
uname (1)            - print system information
users (1)            - print the user names of users currently logged in to t...
vasprintf (3)        - print to allocated string
vdprintf (3)         - formatted output conversion
version (1ssl)       - print OpenSSL version information
vfprintf (3)         - formatted output conversion
vfwprintf (3)        - formatted wide-character output conversion
vprintf (3)          - formatted output conversion
vsnprintf (3)        - formatted output conversion
vsprintf (3)         - formatted output conversion
vswprintf (3)        - formatted wide-character output conversion
vwprintf (3)         - formatted wide-character output conversion
watchgnupg (1)       - Read and print logs from a socket
wc (1)               - print newline, word, and byte counts for each file
whoami (1)           - print effective userid
wprintf (3)          - formatted wide-character output conversion
x86_64-linux-gnu-strings (1) - print the sequences of printable characters in...
hacker@man~searching-for-manuals:~$ man -K /challenge/challenge flag
man         
--Man-- next: curl-config(1) [ view (return) | skip (Ctrl-D) | quit (Ctrl-C) ]
--Man-- next: ncursesw6-config(1) [ view (return) | skip (Ctrl-D) | quit (Ctrl-C) ]
^C         
hacker@man~searching-for-manuals:~$ ^C
hacker@man~searching-for-manuals:~$ ^C
hacker@man~searching-for-manuals:~$ ^C
hacker@man~searching-for-manuals:~$ ^C
hacker@man~searching-for-manuals:~$ /challenge/challenge --rxqwlb 269
Correct usage! Your flag: pwn.college{Q2ESPr6xV9JqVw6FNlJbiUj1HzM.QX2EDO0wCN1kjNzEzW}
```
### New Learnings
Learnt how to access the manual page for the ``man`` command and also how to navigate  
it properly.  
### Resources  
## Helpful Programs  
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument.  
Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /?  
(though that latter is more frequently encountered on Windows).  

In this level, you will practice reading a program's documentation with --help. Try it out!  
### Solve  
**Flag:** `pwn.college{k0OtJacHzLIyTNp4nLEm4LfbPil.QX3IDO0wCN1kjNzEzW}`  
Here I saw -p which would print the correct argument for the ``-g`` argument and I used that first  
to get the secret value and then used ``-g`` with the secret value to get the flag.  
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 44
hacker@man~helpful-programs:~$ /challenge/challenge -g 44
Correct usage! Your flag: pwn.college{k0OtJacHzLIyTNp4nLEm4LfbPil.QX3IDO0wCN1kjNzEzW}
```
### New Learnings  
I learnt the usage of the ``--help`` command as an alternative to the ``man`` command.  
### Resources  

  




