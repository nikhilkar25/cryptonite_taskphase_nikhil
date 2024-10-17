# Listing Processes

## code

```bash
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   640 ?        Ss   20:39   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2560 ?        S    20:39   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    20:39   0:00 /challenge/13989-run-13593
root          72  0.0  0.0   2744  1280 ?        S    20:39   0:00 sleep 6h
hacker        73  0.5  0.0   5360  3840 pts/0    Ss   20:40   0:00 /run/dojo/bin/ssh-entrypoint
hacker        90  0.0  0.0   7868  3200 pts/0    R+   20:40   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/13989-run-13593
Yahaha, you found me! Here is your flag:
pwn.college{w0mmFG6nyOhPEftGYkRk1VM7Dvw.dhzM4QDLzkjN0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

## learnings

Used ps aux command to view all the processes even the ones not running in the terminal (like the one containing the flag).

# Killing Processes

## code

```bash
hacker@processes~killing-processes:~$ ps aux | grep /challenge/dont_run
hacker        73  0.0  0.0   4976  3200 ?        Ss   20:50   0:00 /challenge/dont_run
hacker        93  0.0  0.0   4140  2240 pts/0    S+   20:50   0:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{gUL_nlJWb1Xxbbgd1mC81dHMXgm.dJDN4QDLzkjN0czW}
```

## learnings

First we list all the processes which might or might not be running. Then grep for the /challenge/dont_run process. After terminating it using kill command we can access the flag.

# Interrupting Processes

## code

```bash
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{crDSJU1-ifEUAnkwb8ePSrOre4E.dNDN4QDLzkjN0czW}
```

## learnings

Learnt to interrupt a process using ^C

# Suspending Processes

## code

```bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         150     133  0 21:46 pts/1    00:00:00 bash /challenge/run
root         152     150  0 21:46 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$  bash /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
hacker       133       0  0 21:12 pts/1    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker       157     133  0 21:47 pts/1    00:00:00 bash /challenge/run
hacker       159     157  0 21:47 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
cat: /flag: Permission denied
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         150     133  0 21:46 pts/1    00:00:00 bash /challenge/run
root         165     133  0 21:47 pts/1    00:00:00 bash /challenge/run
root         167     165  0 21:47 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{0RoTwCyuzjVPwVHWSun4mFtRzS-.dVDN4QDLzkjN0czW}
```

## learnings

First i tried to access /challenge/run . Then i suspended its running by using ^Z. Then i obtained the copy of the file which i ran in order to get access to the original file.

# Resuming Processes

## code

```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{8NCddFogFB-uHlxIb7yuCgxafqS.dZDN4QDLzkjN0czW}
Don't forget to press Enter to quit me!
```

## learnings

Learnt to suspend then resume processes.

# Backgrounding Processes

## code

```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          84 S+   bash /challenge/run
root          86 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &

Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          84 S    bash /challenge/run
root          94 S    sleep 6h
root          95 S+   bash /challenge/run
root          97 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{cGUCy-mSRzJtklE5CYkVkBE437O.ddDN4QDLzkjN0czW}
```

## learnings

Learnt to suspend a process then run it in the background.

# Foregrounding Processes

## code

```bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &

hacker@processes~foregrounding-processes:~$ Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{IfBAKApGz8i4WZQtF_0bBwWInN4.dhDN4QDLzkjN0czW}
```

## learnings

Learnt to foreground a backgrounding process

# Starting Backgrounded Processes

## code

```bash
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82

Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
hacker@processes~starting-backgrounded-processes:~$ pwn.college{c_APHzutiQ3DtTkedlSmfpEELzH.dlDN4QDLzkjN0czW}
```

## learnings

Learnt how to run a process in the background without having to suspend it first.

# Process exit codes

## code

```bash
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
81
hacker@processes~process-exit-codes:~$ /challenge/submit-code 81
CORRECT! Here is your flag:
pwn.college{8Sb4EyUtxNkFnz41Xh8-qA5YATP.dljN4UDLzkjN0czW}
```

## learnings

I ran the file then echoed for its exit code. Then i ran the submit code file along with the exit code as argument
