# Chaining with semicolons

## code

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oy8XmWE65kCVOLVc3sfLdkBvdV9.dVTN4QDLzkjN0czW}
```

## learnings

Learnt to chain commands using ;

# Your first shell script

## code

```
hacker@chaining~your-first-shell-script:~$ touch x.sh
hacker@chaining~your-first-shell-script:~$ chmod +x x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{YcMfSay0j6lJ1b0aPUlHTCUtT9J.dFzN4QDLzkjN0czW}
```

## learnings

I used the touch command to create a shell script.Then i used chmod to provide executionary acess to all. Then i added commands /challenge/pwn and /challenge/college to it and directly ran it using bash.

# Redirecting Script Output

## code

```
hacker@chaining~redirecting-script-output:~$ chmod +x x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{QLCtwpb3kori7tFMtejAMg6fDN-.dhTM5QDLzkjN0czW}
```

## learnings

By writing a script that runs both `/challenge/pwn` and `/challenge/college`, I can consolidate their outputs. Then pipe this output into /challenge/solve to run it.

# Executable shell scripts

## code

```
hacker@chaining~executable-shell-scripts:~$ touch xy.sh
hacker@chaining~executable-shell-scripts:~$ chmod a+x xy.sh
hacker@chaining~executable-shell-scripts:~$ ./xy.sh
Congratulations on your shell script execution! Your flag:
pwn.college{sU4cbkG6jE3rNy-mzL5QVyMvfU6.dRzNyUDLzkjN0czW}
```

## learnings

First i created a  shell script file then i provided executable access to it. Then i went to text editor and typed out /challenge/solve to it. Then i executed this shell script explicitly .
