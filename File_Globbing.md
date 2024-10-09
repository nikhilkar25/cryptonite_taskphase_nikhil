# Matching with *

## code

```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{wUPMK-F1KbQ21r9w7n906m8q29E.dFjM4QDLzkjN0czW}
```

## learnings

The challenge asks us to switch directory wo /challenge but we cannot use more than 3 characters. Thus by file globbing technique we can write /challenge as /ch* and get flag

# Matching with ?

## code

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{EOeNhcGvOz6sAFQEUGHGKrPr71k.dJjM4QDLzkjN0czW}
```

## learnings

The challenge asks you to replace the c and l of challenge with ? to switch directory and thus obtain file.

# Matching with []

## code

```bash
hacker@globbing~matching-with-:/challenge/files$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
```

## learnings

The challenge asks us to obtain flags by running files with name file_b files_ a files _ s

and files _ h. We can use globbing to obtain all files together and thus obtain flag.

# Matching paths with []

## code

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{MqIGtpoxvPS4VgESNi7vjX5uR8D.dRjM4QDLzkjN0czW}
```

## learnings

Learnt how to use absolute path to access files using globbing.

# Mixing globs

## code

```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{gr9z-d8BEtP3ZiIj3YhxbKAixGm.dVjM4QDLzkjN0czW}
```

## learnings

We first cd inro the /challenge/files directory. Then we use file globbing terchnique of * and [] and put the first chasracters of the required files to obtain them.

# Exclusionary Globbing

## code

```bash
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{M6FbfyDN3ZGZhYYFzdRxQX9G-WX.dZjM4QDLzkjN0czW}
```

## learnings

We first cd into the /challenge/files directory. Then by using globbing to obtain all files that do not start with p w or n we obtain flag.
