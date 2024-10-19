# The PATH Variable

## code

```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{UbLgGTDrsR9qBaVr3zS8RboZt-p.dZzNwUDLzkjN0czW}
```

## learnings

I first declared the PATH variable as blank which disrupts the operation of the /challenge/run program. The rm command doesn’t work and gives us the file

# Setting Paths

## code

```
hacker@path~setting-path:~$ PATH="/challenge/more_commands"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{k6-lNEAhVFwigK7JGKy-Hz8CAlb.dVzNyUDLzkjN0czW}
```

## learnings

We set path to the /challenge/more_commands directory and then run /challenge/run which invokes the win command and gives flag.

# Adding Commands

## code

```

nano /home/hacker/win
hacker@path~adding-commands:~$ which cat
/run/workspace/bin/cat
hacker@path~adding-commands:~$ chmod +x /home/hacker/win
hacker@path~adding-commands:~$ win
ssh-entrypoint: win: command not found
hacker@path~adding-commands:~$ /home/hacker/win
/bin/cat: /flag: Permission denied
hacker@path~adding-commands:~$ export PATH=/home/hacker/win:$PATH
hacker@path~adding-commands:~$ $PATH
ssh-entrypoint: /home/hacker/win:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker/scripts: No such file or directory
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~adding-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~adding-commands:~$ $PATH
ssh-entrypoint: /home/hacker:/home/hacker/win:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker/scripts: No such file or directory
hacker@path~adding-commands:~$ /home/hacker/win
/bin/cat: /flag: Permission denied
hacker@path~adding-commands:~$ ls -l /home/hacker/win
-rwxr-xr-x 1 hacker hacker 15 Oct 15 06:26 /home/hacker/win
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{Ig8gXyFj7tAM74dpQxtcPHPw4eZ.dZzNyUDLzkjN0czW}
```

## learnings

Almost gave up on this one but somehow got it. First  i used the which command to get the cat absolute path. Then i used  +x to make the win file accessible for execution. 

# Hijacking Commands

## code

```
hacker@path~hijacking-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod +x rm
hacker@path~hijacking-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{oXUI68uWd2NHcMIInToqurZJ4eT.ddzNyUDLzkjN0czW}
```

## learnings

Yet another tricky one. First i tried to modify the rm faux command to trick the system into thinking that my provided rm command is what it should execute , so that it does not remove the flag from /challenge/run. For this i set rm to execute cat flag except i had to use the absolute path of cat.
