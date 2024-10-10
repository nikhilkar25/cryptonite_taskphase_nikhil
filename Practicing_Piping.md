# Redirecting Output

## code

```bash
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{ovFehC9l1xkueAd_FI2dZsomIbY.dRjN1QDLzkjN0czW}
```

## learnings

 By echo command we copy “PWN” into the file COLLEGE.

# Redirecting more Output

## code

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{0zs8h97g_NJsUQ1LTGJ8occHCVT.dVjN1QDLzkjN0czW}
```

## learning

I copied the output of /challenge/run to the file myflag . Then catting this file i got the desired output

# Appending output

## code

```bash
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat  /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{cNjFXofQ3902VisGGYCzGQTjE04.ddDM5QDLzkjN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

## learnings

When you use the `>>` operator, output is appended to the file, preserving its existing content. In this case, the program writes the flag in two parts: the first part is written directly to the file, while the second part is sent to `stdout`. If you redirect `stdout` in append mode, both parts will be saved to the file without overwriting. If you use `>`, it truncates the file and only the second part remains.

# Redirecting errors

## code

```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{wkcVS3khs_GtvqNg8XfdhvVsJEH.ddjN1QDLzkjN0czW}
```

## learnings

I redirected the output of /challenge/run to myflag and catted it.

# Redirecting Input

## code

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{AgqV6VhNRw_yiaMkm6XxGfAneGP.dBzN1QDLzkjN0czW}
```

## learnings

I directed output of echo COLLEGE into PWN file using > , then redirected input into /challenge/run

# Grepping stored results

## code

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{A-Cv1yBqGtbebmJlMjq6OLNWpFW.dhTM4QDLzkjN0czW}
```

## learnings

I directed the output of /challenge/run into /tmp/data.txt and then grepped for the flag by searching for pwn.college

# Grepping live output

## code

```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{seAn48ke7Ic3SynusMjHM3Vi8-m.dlTM4QDLzkjN0czW}
```

## learnings

In this challenge, I was tasked with redirecting the output of  /challenge/run into another process, specifically grep, to search for the string  pwn.college. I began by executing /challenge/run, which outputs several informational messages. I used a pipe to redirect its output into grep, filtering the result to find the required flag, `pwn.college`.

# Grepping errors

## code

```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep "pwn.college"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{4D6EkDMafJ6hslRfGhIt865cbtq.dVDM5QDLzkjN0czW}
```

## learnings

used 2>&1 to combine both the standard error (stderr) and standard output (stdout) into a single stream. Then used grep to search for flag.

# Duplicating piped data with tee

## code

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee intercepted_output | /challenge/college
Processing...
WARNING: you are overwriting file intercepted_output with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee intercepted_output | /challenge/college
Processing...
WARNING: you are overwriting file intercepted_output with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat intercepted_output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "QSKROPgy"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret QSKROPgy | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{QSKROPgyYmbKKTyBfTItGDrFp7b.dFjM5QDLzkjN0czW}

```

## learnings

  I pipe the output of /challenge/pwn into /challenge/college and use tee command to obtain output of /challenge/pwn. Then i cat the file where the output is stored and obtain the secret command which eventually gives flag.

# Writing to multiple programs

## code

```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
1414513723269814753
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{0fKb7u1fXE8Pf-dN9f9RwkBGZo8.dBDO0UDLzkjN0czW}
```

## learnings

I piped the data of /challenge/hack into /challenge/the and /challenge/world and got desired flag

# Split piping stderr and stdout

## code

```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{MjltudGzXbKdh7SdreblO5thuA1.dFDNwYDLzkjN0czW}
```

## learnings

You can separate stdout and stderr by redirecting them to different programs. Use > >(/challenge/world) for stdout and 2> >(/challenge/the) for stderr. This keeps them apart while sending each to its own command.
