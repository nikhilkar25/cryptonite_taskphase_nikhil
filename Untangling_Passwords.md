# Becoming root with su

## code

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{oIq6gM2sf9Cs10NfgEBbN3ycqwz.dVTN0UDLzkjN0czW}
```

## learnings

```
I first used the su command to elevate privileges to the root. Then after entering the password and becoming the root I could read the flag file.
```

# Other users with su

## code

```bash

hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{EHfoH9x_6gFaljnfXIjWdsz0vlk.dZTN0UDLzkjN0czW}
```

## learnings

I used the su command to gain access to user zardus . By entering the given password i became zardus and could run the file.

# Cracking Passwords

## code

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:18 1% 2/3 0g/s 288.1p/s 288.1c/s 288.1C/s chacha..jazmin
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04948g/s 288.1p/s 288.1c/s 288.1C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{0cH6sGTTRJeB5T0ZijvfHg3Gx6p.ddTN0UDLzkjN0czW}
```

## learnings

First i used the john command on /challenge/shadow-leak. Then by pressing a key i got the password aardvark. Now su-ing into zardus and entering the password i brcame zardus. Then i ran /challenge/run as zardus for the flag.

# Using Sudo

## code

```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{o_owGUlXi63SQq96FydDcJXloH1.dhTN0UDLzkjN0czW}
```

## learnings

Using the sudo command i can run commands as the root user and get the flags easily.
