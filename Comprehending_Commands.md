# Cat , not the pet but the command

## code

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{M98YPF-6LtOZ_MHXQHOKpDw7CTY.dFzN1QDLzkjN0czW}
```

## learnings

To learn how to use cat command , used to read out files

# catting absolute paths

## code

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{49XZlV2ANRUwwtngxnL3YtUt5JH.dlTM5QDLzkjN0czW}
```

## learnings

The file was to be read at its absolute path, residing in /flag

# More catting practice

## code

```bash
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/python3.8/ensurepip/flag. Go cat it out **without** cding into
that directory!
hacker@commands~more-catting-practice:~$ cat  /lib/python3.8/ensurepip/flag
pwn.college{Q5jvGMPOdRCCBaWV-TFkRF5KqtJ.dBjM5QDLzkjN0czW}
```

## learnings

Accessing the file using cd command was not permitted. Therefore the only way to get the flag was to read the directory provided  using cat command.

# grepping for a needle in a haystack

## code

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{UrHu6m6Au_7ySRd82cABL5bKmaS.ddTM4QDLzkjN0czW}
```

## learnings

Used grep command to search for [pwn.college](http://pwn.college) (The starting characters of every flag) in the /challenge/data.txt file.

# Listing files

## code

```bash
hacker@commands~listing-files:~$ ls /challenge
2617-renamed-run-20899  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/2617-renamed-run-20899
Yahaha, you found me! Here is your flag:
pwn.college{ogSU2dRWZkISZBWalrj6Rdd8GTk.dhjM4QDLzkjN0czW}
```

## learnings

We were asked to use the ls funcyion to list the dofferent files in the challenge directory

ls /challenge bejung the command

after obtaining the random name the /challenge/run was named by we run it thus obtaining the flag

# Touching Files

## code

```bash
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ ls
bin  hsperfdata_root  tmp.XvrUsDZh8M
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls /tmp
bin  college  hsperfdata_root  pwn  tmp.XvrUsDZh8M
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{0PDAoofJC4lTNkCnA9Hmp_7Z0e6.dBzM4QDLzkjN0czW}
hacker@commands~touching-files:/tmp$
```

## learning

Made the tmp as current directory using the cd command. used touch command to create new files pwn and college into the tmp directory. 

# Removing files

## code

```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{cRjXwISbUpUmNryJ3k3TiOivD1O.dZTOwUDLzkjN0czW}
```

## learnings

Deleted the delete_me file using the rm command and accessed the necessary file to obtain flag
# Hidden Files

## code

```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-16902933311274  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat .flag-16902933311274
pwn.college{EczuxRx72XO2csYER2BStW7R6Pd.dBTN4QDLzkjN0czW}
```

## learnings

I used cd command to make the root directory / as the current directory.. Then the ls -a command is used to list out all the files which start with a period (.). The file starting with .flag… must be the desired one. Using the cat command to read this file , the flag is obtained

# An Epic FileSystem Quest

## code

```bash
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  BRIEF       boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ cat BRIEF
Great sleuthing!
The next clue is in: /usr/lib/ruby/2.7.0/racc

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/lib/ruby/2.7.0/racc
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/2.7.0/racc$ ls -a
.          debugflags.rb         info.rb              parser.rb               sourcetext.rb
..         exception.rb          iset.rb              parserfilegenerator.rb  state.rb
.NUGGET    grammar.rb            logfilegenerator.rb  pre-setup               statetransitiontable.rb
compat.rb  grammarfileparser.rb  parser-text.rb       rdoc                    static.rb
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/2.7.0/racc$ cat .NUGGET
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/arch/x86/power
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/2.7.0/racc$ cd  /opt/linux/linux-5.4/arch/x86/power
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/x86/power$ ls
INFO      built-in.a  cpu.o        hibernate.o     hibernate_64.c  hibernate_asm_32.S  hibernate_asm_64.o
Makefile  cpu.c       hibernate.c  hibernate_32.c  hibernate_64.o  hibernate_asm_64.S
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/x86/power$ cat INFO
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/sage/schemes/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/x86/power$ cd  /usr/lib/python3/dist-packages/sage/schemes/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/schemes/__pycache__$ ls
DISPATCH  __init__.cpython-38.pyc  all.cpython-38.pyc  readme.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/schemes/__pycache__$ cat DISPATCH
Great sleuthing!
The next clue is in: /usr/share/X11/xkb/symbols/sony_vndr
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/schemes/__pycache__$ cd /usr/share/X11/xkb/symbols/sony_vndr
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ ls
GIST  us
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ cat GIST
Tubular find!
The next clue is in: /opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ ls -a //opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi
.                 emulation.c   mfi.h        mptsas.h        srp.h                viosrp.h
..                esp-pci.c     mpi.h        scsi-bus.c      trace-events         virtio-scsi-dataplane.c
EVIDENCE-TRAPPED  esp.c         mptconfig.c  scsi-disk.c     vhost-scsi-common.c  virtio-scsi.c
Kconfig           lsi53c895a.c  mptendian.c  scsi-generic.c  vhost-scsi.c         vmw_pvscsi.c
Makefile.objs     megasas.c     mptsas.c     spapr_vscsi.c   vhost-user-scsi.c    vmw_pvscsi.h
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ //opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi
ssh-entrypoint: //opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ cat /opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi
cat: /opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ cat /opt/aflplusplus/nyx_mode/QEMU-Nyx/hw/scsi/EVIDENCE-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Gyre-Termes/Fraktur

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ ls -a /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Gyre-Termes/Fraktur
.  ..  ALERT-TRAPPED  Regular
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ cat /usr/share/javascript/mathjax/unpacked/jax/output/HTML-CSS/fonts/Gyre-Termes/Fraktur/ALERT-TRAPPED
Great sleuthing!
The next clue is in: /usr/lib/debug/.build-id/02

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/xkb/symbols/sony_vndr$ cd /usr/lib/debug/.build-id/02
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/02$ ls -a
.  ..  3a31d37cc4198b620d57cf182e8e8a2a04e8f9.debug  97679affdb4bf4d38378c32ba0925475a61921.debug  MEMO
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/02$ cat MEMO
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/include/config/arch/has/membarrier/sync

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/02$ ls -a /opt/linux/linux-5.4/include/config/arch/has/membarrier/sync
.  ..  NOTE-TRAPPED  core.h
hacker@commands~an-epic-filesystem-quest:/usr/lib/debug/.build-id/02$ cat /opt/linux/linux-5.4/include/config/arch/has/membarrier/sync/NOTE-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{U6NzP_CXdApZSagZfLG_PATPvYQ.dljM4QDLzkjN0czW}
```

## learnings

I navigated to the root directory `/` and read a file named `BRIEF` which gave me the first clue. It told me to search for a hidden file in the `/usr/lib/ruby/2.7.0/racc` directory. I used the `ls -a` command to list all files, including hidden ones (those starting with a `.`). I found a file called `.NUGGET` and opened it to get the next clue.Each clue led me to a new directory, where I had to use commands like `ls -a` and `cat` to find the hidden or trapped files. Sometimes, I had to avoid using `cd` to prevent the clues from disappearing.Some clues were marked as "delayed" or "trapped," meaning I had to carefully follow the instructions. For delayed clues, I had to enter the directory before they became visible. For trapped clues, I couldn't `cd` into the directory but had to directly read the file.: After following multiple clues, I reached the final directory and read the last file, which revealed the flag: `pwn.college{U6NzP_CXdApZSagZfLG_PATPvYQ.dljM4QDLzkjN0czW}`.

# Making directories

## code

```bash
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  tmp.XvrUsDZh8M
hacker@commands~making-directories:/tmp$ mkdir /tmp/pwn
hacker@commands~making-directories:/tmp$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{AprvjXCzRIuuuINll-A2PsN6ECO.dFzM4QDLzkjN0czW}
hacker@commands~making-directories:/tmp/pwn$
```

## learnings

First i make tmp my current directory.

Using the mkdir command specified i create my own directory /tmp/pwn and then make /tmp/pwn my current directory.

Then I use the touch command to create files inside this directory. In this instance i created college. 

Lastly using /challenge/run i obtain flag

# Finding Files

## code

```bash

hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/opt/linux/linux-5.4/include/config/system/data/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$ cat /opt/linux/linux-5.4/include/config/system/data/flag
pwn.college{AyTsxMkP8oktUaq55LPzCoGYJKJ.dJzM4QDLzkjN0czW}hacker@commands~finding-files:~$
```

## learnings

First I used the find function to obtain various files named `flag` on the filesystem. Many of who’s access i was denied. Atleast one of files which did not show permission denied must have contained the flag. I used the cat command oin each one of them until i got the flag pwn.college{…}

## code

# Linking files

```bash
ln: failed to create symbolic link '/challenge/catflag': File exists
hacker@commands~linking-files:~$ ln -s /home/hacker/not-the-flag /challenge/catflag
ln: failed to create symbolic link '/challenge/catflag': File exists
hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{QeHL9yCBQrijAIX26MWXr0FQpN9.dlTM1UDLzkjN0czW}
hacker@commands~linking-files:~$

```

## learnings

When i tried to use ln -s command between /challenge/catflag and /home/hacker/not-the-flag it should that the file already existed. Hence i used the rm command to delete the content of /home/hacker/not-the-flag. Then i used the ln -s flag to create a symlink between /flag and /home/hacker/not-the-flag. Hence by using /challenge/flag i obtained the flag
