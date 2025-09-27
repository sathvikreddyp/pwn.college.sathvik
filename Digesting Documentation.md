# 1. Learning From Documentation
In this challenge, a program was given to run with a specific argument to get the flag. The program was '/challenge/challenge' and the argument we have to use is '--giveflag'. The argument was given in the documentation of the program.

## My Solve
Flag: pwn.college{8aAXEuAfDLJDSryU1Ta3ISivo1j.QX0ITO0wiM1AzNzEzW}

I invoked the given program  in the terminal along with the argument they gave to get the flag.

```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{8aAXEuAfDLJDSryU1Ta3ISivo1j.QX0ITO0wiM1AzNzEzW}
```

## What I Learnt 
I learned how the correct usage of programs depends, in a large part, on the proper specification of arguments to them. I also learned one of the need of a documentation of a program is to figure out which argument to use on the command line. One of the main needs of a documentation is to figure out how to use programs correctly.

## References
The reference used was the challenge statement and docummentation given in pwn.college.

# 2. Learning Complex Usage
In this challenge, a documentation for '/challenge/challenge' program was given. This documentation provided that if we run the program, it will print arbitrary files to the terminal, when we give it the '--printfile argument'. It also told that we have to give the path of the file as the argument to '--printfile'.

## My Solve
Flag: pwn.college{A9nElVKknKBfOxa3uAtPNJRiwfz.QX1ITO0wiM1AzNzEzW}

I invoked the '/challenge/challenge' program with the '--printfile' argumant, along with the path to the flag (/flag) as the argument to '--printfile'. This entire command then printed the flag file and I got the flag.

```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{A9nElVKknKBfOxa3uAtPNJRiwfz.QX1ITO0wiM1AzNzEzW}
```
## What I Learnt
I learned that some commands take arguments to their arguments. For example, 'find' has a '-name' argument, and the '-name' argument itself takes an argument specifying the name to search for.

## References
The reference used was the challenge statement and docummentation given in pwn.college.

# 3. Reading Manuals
In this challenge, there was a secret option that, when you use it, will cause the challenge to print the flag. The 'man' command was introduced and we have to go through the manpage of 'challenge' to get the flag.

## My Solve
Flag: Correct usage! Your flag: pwn.college{os0gHqvVl2-YuOITHbw9ggisDpY.QX0EDO0wiM1AzNzEzW}

I first opened the manual page of 'challenge' by using the 'man' command with 'challenge' as the argument. In the manual, it was given that '/challenge/challenge' program prints the flag if the correct argument  --osgqvl 029 is given. So I ran the program with the argument they gave to print the flag.

```
hacker@man~reading-manuals:~$ man challenge
hacker@man~reading-manuals:~$
hacker@man~reading-manuals:~$ /challenge/challenge  --osgqvl 029
Correct usage! Your flag: pwn.college{os0gHqvVl2-YuOITHbw9ggisDpY.QX0EDO0wiM1AzNzEzW}
```

## What I Learnt
I learned about the man command. It will display (if available) the manual of the command you pass as an argument. For example: man challenge. Manpages are stored in a centralized database and that database lives in the /usr/share/man directory, but we dont need to interact with it directly, we can just use the man command.

## References
The reference used was the challenge statement and docummentation given in pwn.college.

# 4. Searching Manuals
In this challenge, it was similar to the previous challenge, where we had to read the manual page of 'challenge' to find the correct argument to get the flag. But over here we have to search in the manual as the manual was very big.

## My Solve
Flag:  pwn.college{kIykknYxksAysIELUU2T9xqsrDb.QX1EDO0wiM1AzNzEzW}

I first opened the manual page of challenge with the 'man' command, then I searched for all the 'flag' words using '/' and '?' and 'n' and 'N' to navigate around, until I found the correct argument to use to get the flag.

```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge  --mropgc
Initializing...
Correct usage! Your flag: pwn.college{kIykknYxksAysIELUU2T9xqsrDb.QX1EDO0wiM1AzNzEzW}
```

## What I Learnt
I learned how to search for keywords inside manual pages in linux. We have to use '/' to search or '?' to search backwards. After searching, we can click 'n' to go to the next result or 'N' to go to the previous result. We can even scroll man pages with the arrow keys.

## References
The reference used was the challenge statement and docummentation given in pwn.college. The inbuilt manpages was also used.

# 5. Searching For Manuals

# 6. Helpful Programs
This program told us to use the '--help' argument with /challenge/challenge program to get hints on how to get the flag.

## My Solve
Flag:  pwn.college{IBlKSe-XJffxqifHh8ytk1E86sk.QX3IDO0wiM1AzNzEzW}

I first executed the --help command which showed me a way to get the flag. I first found the secret value to retrieve the flag and used /challenge/challenge -p (secret value) to get the flag.

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
hacker@man~helpful-programs:~$ /challenge/challenge  -g GIVE_THE_FLAG
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge  --print-value
The secret value is: 818
hacker@man~helpful-programs:~$ /challenge/challenge  -g 818
Correct usage! Your flag: pwn.college{IBlKSe-XJffxqifHh8ytk1E86sk.QX3IDO0wiM1AzNzEzW}
```

## What I Learnt 
I learnt that not all programs will have a manpage. However, we can use the '--help- or sometimes '-h' argument along with the command to know how to use the command.

## References 
The reference used was the challenge statement and docummentation given in pwn.college. The inbuilt help page with the '--help' argument was also used.

# 7. Help For Builtins
In this challenge, the challenge command is a shell builtin, rather than a program. We need to look at its help to find the secret value and get the flag.

## My Solve
Flag: pwn.college{oQjo5OWB4eS81xS1nJmZxmo4i9_.QX0ETO0wiM1AzNzEzW}

I used the 'help' to lookup help for builtins. In that help page, the secret value and the argument to get the flag was given. I then ran the challenge command with the argument and the secret value given in help to get the flag.

```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "oQjo5OWB".
hacker@man~help-for-builtins:~$ challenge --secret oQjo5OWB
Correct! Here is your flag!
pwn.college{oQjo5OWB4eS81xS1nJmZxmo4i9_.QX0ETO0wiM1AzNzEzW}
```
## What I Learnt
I first learned about builtins, which are commands that are inbuilt into the shell itself, instead of being programs with man pages and help options. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. We can get a list of all shell builtins with the 'help' builtin. We can get help on a specific builtin by passing it to the help builtin, like 'help cd' (in place of cd you can put any builtin, and yes cd is a builtin).

## References 
The reference used was the challenge statement and docummentation given in pwn.college.
