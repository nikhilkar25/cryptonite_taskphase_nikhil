# Learning from Documentation

## code

```bash
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{onlwF2XdC4bfDZSpIbUlJZw2Vnv.dRjM5QDLzkjN0czW}
```

## learnings

learnt how to use  arguments  to obtain flag

# Learning complex usage

## code

```bash
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{I8Q8ZxZ-nlW4C1sROud5AJFepmZ.dVjM5QDLzkjN0czW}
```

## learning

Learnt to use the —printfile argument to print the description of files. In this case the /flag file.

# Reading Manuals

## code

```bash
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --kraqlp NUM
              print the flag if NUM is 322

AUTHOR
       Written by Zardus.The Description clearlys

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                            May 2024   

hacker@man~reading-manuals:~$ /challenge/challenge --kraqlp 322
Correct usage! Your flag: pwn.college{kZI3CZP2rJ2KaqlCp5ndj2jvF5p.dRTM4QDLzkjN0czW}                                       CHALLENGE(1)
```

## learnings

First i used the manual command on challenge. The description clearly states that on using the argument —kraqlp NUM where NUM is 322, the flag will be printed. Hence by documentation this flag can be obtained.

# Searching Manuals

```bash

hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge  --vaqumx
Initializing...
Correct usage! Your flag: pwn.college{QaLDzJbCw4dD27vg9nIsEDdmtae.dVTM4QDLzkjN0czW}

```

## learnings

First i opened the manual for challenge command. There were a plethora of arguments tho only one was correct . Using /flag to search for “flag” i obtained the right argument

# Searching for Manuals

## code

```bash
hacker@man~searching-for-manuals:~$ man man
MAN(1)                                            Manual pager utils                                           MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is the system's manual pager.  Each page argument given to man is normally the name of a program, utility
       or function.  The manual page associated with each of these arguments is then found and displayed.  A section,
       if  provided,  will direct man to look only in that section of the manual.  The default action is to search in
       all of the available sections following a pre-defined order (see DEFAULTS), and to show only  the  first  page
       found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.

       Conventional  section  names  include  NAME,  SYNOPSIS,  CONFIGURATION, DESCRIPTION, OPTIONS, EXIT STATUS, RE‐
       TURN VALUE, ERRORS, ENVIRONMENT, FILES, VERSIONS, CONFORMING TO, NOTES, BUGS, EXAMPLE, AUTHORS, and SEE ALSO.

       The following conventions apply to the SYNOPSIS section and can be used as a guide in other sections.

       bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
       [expression] ...   entire expression within [ ] is repeatable.

       Exact rendering may vary depending on the output device.  For instance, man will usually not be able to render
       italics when running in a terminal, and will typically use underlined or coloured text instead.

       The  command  or function illustration is a pattern that should match all possible invocations.  In some cases
       it is advisable to illustrate several exclusive invocations as is shown in the SYNOPSIS section of this manual
       page.

EXAMPLES
       man ls
           Display the manual page for the item (program) ls.

       man man.7
           Display  the manual page for macro package man from section 7.  (This is an alternative spelling of "man 7
           man".)

       man 'man(7)'
           Display the manual page for macro package man from section 7.  (This is another  alternative  spelling  of
           "man  7  man".  It may be more convenient when copying and pasting cross-references to manual pages.  Note
           that the parentheses must normally be quoted to protect them from the shell.)

       man -a intro
           Display, in succession, all of the available intro manual pages contained within the manual.  It is possi‐
           ble to quit between successive displays or skip any of them.

       man -t bash | lpr -Pps
           Format  the  manual  page for bash into the default troff or groff format and pipe it to the printer named
           ps.  The default output for groff is usually PostScript.  man --help should advise as to  which  processor
           is bound to the -t option.

       man -l -Tdvi ./foo.1x.gz > ./foo.1x.dvi
           This command will decompress and format the nroff source manual page ./foo.1x.gz into a device independent
           (dvi) file.  The redirection is necessary as the -T flag causes output to be directed to  stdout  with  no
           pager.   The output could be viewed with a program such as xdvi or further processed into PostScript using
           a program such as dvips.

       man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular  expression.   Print
           out any matches.  Equivalent to apropos printf.

       man -f smail
           Lookup the manual pages referenced by smail and print out the short descriptions of any found.  Equivalent
--More--
Most commands optionally preceded by integer argument k.  Defaults in brackets.
Star (*) indicates argument becomes new default.
-------------------------------------------------------------------------------
<space>                 Display next k lines of text [current screen size]
z                       Display next k lines of text [current screen size]*
<return>                Display next k lines of text [1]*
d or ctrl-D             Scroll k lines [current scroll size, initially 11]*
q or Q or <interrupt>   Exit from more
s                       Skip forward k lines of text [1]
f                       Skip forward k screenfuls of text [1]
b or ctrl-B             Skip backwards k screenfuls of text [1]
'                       Go to place where previous search started
=                       Display current line number
/<regular expression>   Search for kth occurrence of regular expression [1]
n                       Search for kth occurrence of last r.e [1]
!<cmd> or :!<cmd>       Execute <cmd> in a subshell
v                       Start up /usr/bin/vi at current line
ctrl-L                  Redraw screen
:n                      Go to kth next file [1]
:p                      Go to kth previous file [1]
:f                      Display current file name and line number
.                       Repeat previous command
-------------------------------------------------------------------------------
hacker@man~searching-for-manuals:~$ man -k challenge
rumhmyevaw (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man rumhmyevaw

CHALLENGE(1)                             Challenge Commands                            CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --rumhmy NUM
              print the flag if NUM is 854

AUTHOR
       Written by Zardus.

hacker@man~searching-for-manuals:~$ /challenge/challenge --rumhmy 854
Correct usage! Your flag: pwn.college{A85rQum-W4hmMTyeJDvLAa6F-Tw.dZTM4QDLzkjN0czW}
```

## learnings

First using man man i obtained the manual for the man [command.](http://command.In) In the description i discovered that using man -k challenge would provide me the hidden challenge man page. Upon obtaining the hidden man challenge page (”rumhmyevaw”) .I then used man rumhmyevaw to obtain the description for this where it showed ne that using the —rumhmy argument along with NUM=854 i would obtain the flag.

# Helpful Programs

## code

```bash
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
The secret value is: 571
hacker@man~helpful-programs:~$ /challenge/challenge 571
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: unrecognized arguments: 571
hacker@man~helpful-programs:~$ /challenge/challenge -g 571
Correct usage! Your flag: pwn.college{ITNuH57pHslDqePIpMzvyf1aNWG.ddjM4QDLzkjN0czW}
```

## learnings

First i used the —help argument as specified. The programs documentation here states that the argument -g will only give the flag when given the correct vakue. Hence we use the -p argument to print the value which comes out to be 571. On using the argument -g with this secret number we obtain the flag.

# Help for Builtins

## code

```bash
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "AulvxYct".
hacker@man~help-for-builtins:~$ challenge --secret AulvxYct
Correct! Here is your flag!
pwn.college{AulvxYctL59nzrItlemZfDzuxJu.dRTM5QDLzkjN0czW}
```

## learnings

Using the help of argument help we find that —secret argument used with a secret value which has been provided as "AulvxYct", will give us the flag.
