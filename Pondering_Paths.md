# The Root

## code

```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{89ysyQgxFG_iASz-7-T4_rGBioG.dhzN5QDLzkjN0czW}

```

## learnings

To invoke a program by providing its path on the command line.Path starts with root directory.The pwn refers to the print working directory command

# Program and absolute paths

## code

```bash
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{A0Dw8byxngk7Nx4DhEMKwJnDvXU.dVDN1QDLzkjN0czW}

```

## learnings

Executing challenge by invoking its absolute path. To execute run file  the challenge directory which is in the / directory.

# Position thy self

## code

```bash
hacker@paths~position-thy-self:~$ cd /sys
hacker@paths~position-thy-self:/sys$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QXObztX9v29NWk3SZvVIcVpHBCG.dZDN1QDLzkjN0czW}

```

## learnings

When you attempt to run the program, it will likely give you an error if you're in the wrong directory, and it should also tell you which path you need to be in.
To navigate around directories by using the cd change directory command and passing a path to it as an argument.Then we execute the /challenge/run program from a specific path

# Position elsewhere

## code

```bash
hacker@paths~position-elsewhere:~$ cd /sys
hacker@paths~position-elsewhere:/sys$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:/sys$ cd /
hacker@paths~position-elsewhere:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4MmiTSawIZK3y6jWDAdKpX-cVCP.ddDN1QDLzkjN0czW}

```

## learning

When you attempt to run the program, it will likely give you an error if you're in the wrong directory, and it should also tell you which path you need to be in.
To navigate around directories by using the cd change directory command and passing a path to it as an argument.Then we execute the /challenge/run program from a specific path

# Position yet elsewhere

## code

```bash
hacker@paths~position-yet-elsewhere:~$ cd /sys
hacker@paths~position-yet-elsewhere:/sys$ /challenge/run
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:/sys$ cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-yet-elsewhere:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8l2q0W-1aXgioF_dVP88N4HByBX.dhDN1QDLzkjN0czW}

```

## learning

When you attempt to run the program, it will likely give you an error if you're in the wrong directory, and it should also tell you which path you need to be in.
To navigate around directories by using the cd change directory command and passing a path to it as an argument.Then we execute the /challenge/run program from a specific path

# implicit relative paths using /

## code

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{kyehkixcFO5nT1Api37n0maPjI5.dlDN1QDLzkjN0czW}

```

## learning

To access a file using current working directory cwd and relative path.
As the cwd was / it would only mean that to run /challenge/run we would need to use a relative path excluding the /.
Hence, we use challenge/run instead.

# explicit relative paths using /

## code

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{44Cz0OkaiwXyclaxYV6BtPa5dOe.dBTN1QDLzkjN0czW}
hacker@paths~explicit-relative-paths-from-:/$

```

## learning

Here we have been specified to use a '.' before the relative path. Assuming cwd to be / the relative path must be an altercation of
the absolute path. We must use ./challenge/run as relative path

# implicit relative path

## code

```bash
hacker@paths~implicit-relative-path:/$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
ssh-entrypoint: run: command not found
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wyhoLIaG9i974Dvct8B7DYgwZaY.dFTN1QDLzkjN0czW}

```

# learning

Here we have been specified to run the path from /challenge directory.

I used relative paths to launch run.
The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using .

# Home sweet Home

## code
```bash
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{ICd0BrI-mXdn9JWLQPWb0ql1qxy.dNzM4QDLzkjN0czW}
```

## learning

 Here `~` expands to `/home/hacker`, so `~/a` becomes `/home/hacker/a`.
also the argument `~/a` is only 3 characters ~/a

This command should successfully write the flag to /home/hacker/a
