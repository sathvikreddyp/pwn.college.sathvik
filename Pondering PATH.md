# 1. The PATH Variable
In this challenge, they told that /challenge/run will delete the flag file using rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you. Thus, you must make it so that /challenge/run can't find the rm command.

## My Solve
Flag: pwn.college{8B55S-D0UP_CGfDp8XFdYydj32o.QX2cDM1wiM1AzNzEzW}

I first blanked out the PATH variable by typying PATH=" ". Then I ran /challenge/run, and since PATH variable is blanked out, it wont be able to find rm command and hence it wont be able to delete the flag file, so i got the flag.

```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ ls
bash: ls: No such file or directory
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{8B55S-D0UP_CGfDp8XFdYydj32o.QX2cDM1wiM1AzNzEzW}
```
## What I Learnt
I learned about the PATH variable, which is a special shell variable which stores a bunch of directory paths in which the shell will search for programs corresponding to commands. Without a PATH, bash cannot find commands like ls,rm,etc.

## References
The references I used were the instructions provided by the pwn.college.

# 2. Setting PATH
In this challenge, they told that /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory.

## My Solve
Flag: pwn.college{YLk49E0pykh4mGQwEsCXXrWmkFH.QX1cjM1wiM1AzNzEzW}

I overwrote PATH variable with /challenge/more_commands. Then I thought we could just run win command, but it didnt work, so I ran /challenge/run with win as argument and got the flag.

```
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ win
It looks like 'win' was improperly launched. Don't launch it directly; it MUST
be launched by /challenge/run!
hacker@path~setting-path:~$ /challenge/run win
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{YLk49E0pykh4mGQwEsCXXrWmkFH.QX1cjM1wiM1AzNzEzW}
```

## What I Learnt
I learned how we can overwrite the PATH variable with some directory, so we can run the programs inside the directory using their bare name. Basically, by adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name.

## References
The references I used were the instructions provided by the pwn.college.

# 3. Finding Commands
In this challenge, they told they they added a win command somewhere in the PATH variable, but it wont give us the flag. However, they told that the command is in the same directory as the flag file, and they made the flag file readable for us. We have to find the directory win command and then read the flag file from there.

## My Solve 
Flag: pwn.college{0_EEmv2L5xXAD075vEok8wAaeBL.01NzEzNxwiM1AzNzEzW}

I first located the directroy the win command is in by using the which command, and found the directory it is in ( /challenge/paths/10466). I then read the flag file using the cat command, as they told its in the same directory as the win command.

```
hacker@path~finding-commands:~$ which win
/challenge/paths/24578/win
hacker@path~finding-commands:~$ cat /challenge/paths/24578/flag
pwn.college{0_EEmv2L5xXAD075vEok8wAaeBL.01NzEzNxwiM1AzNzEzW}
```

## What I Learnt
I learned about the which command, which looks at each directory in PATH variable in order and prints the first file it finds whose name matches the argument you passed. When you type the name of a command, something inside one of the many directories listed in the PATH variable is what actually gets executed (unless the command is a builtin).

## References
The references I used were the instructions provided by the pwn.college.

# 4. Adding Commands
In this challenge, the win command does not exist. We have to make a shell script called win, add its location to the PATH, and enable /challenge/run to find the flag.

## My Solve
Flag: pwn.college{oSImB8eU6eK9IFF8e6zXcxCZPuo.QX2cjM1wiM1AzNzEzW}

```
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ ls -l
total 48
-rw-r----x 1 hacker hacker   4 Sep 30 08:47 COLLEGE
drwxr-x--x 1 hacker hacker   0 Oct  1 13:44 Desktop
-rw-r----x 1 hacker hacker  77 Sep 30 16:50 PWN
-rw-r----x 1 hacker hacker   8 Sep 29 13:23 PWn
-rw-r----x 1 hacker hacker   0 Sep 26 14:35 college
-rw-r--r-- 1 root   hacker  60 Sep 23 17:24 h
-rw-r----x 1 hacker hacker 781 Sep 30 09:00 instructions
-rw-r----x 1 hacker hacker   0 Sep 30 09:00 my
-rw-r----x 1 hacker hacker  95 Sep 30 08:51 myflag
lrwxrwxrwx 1 hacker hacker   5 Sep 27 09:41 not-the-flag -> /flag
-rwxr--r-- 1 hacker hacker  27 Oct 10 19:36 pwn.sh
-rwxr--r-- 1 hacker hacker 168 Oct 10 19:49 solve.sh
-rw-r----x 1 hacker hacker 437 Sep 30 08:55 the-flag
-rwxr-xr-x 1 hacker hacker  10 Oct 10 20:49 win
-rw-r--r-- 1 hacker hacker  18 Oct 10 20:28 win.sh
hacker@path~adding-commands:~$ PATH=/home/hacker:/run/dojo/bin
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{oSImB8eU6eK9IFF8e6zXcxCZPuo.QX2cjM1wiM1AzNzEzW}
```

## What I Learnt
I learnt how to use which command properly. I also learnt how to ass location of scripts to PATH variable.

## References
The references I used were the instructions provided by the pwn.college.

# 5. Hijacking Commands
In this challenge, it will delete the flag using rm command without printing anything to us. We have to find a way to retrieve the flag.

## My Solve
Flag: pwn.college{0hL3IBr3r4An6XDm1iiju4vm-1v.QX3cjM1wiM1AzNzEzW}


```
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ ls -l
total 52
-rw-r----x 1 hacker hacker   4 Sep 30 08:47 COLLEGE
drwxr-x--x 1 hacker hacker   0 Oct  1 13:44 Desktop
-rw-r----x 1 hacker hacker  77 Sep 30 16:50 PWN
-rw-r----x 1 hacker hacker   8 Sep 29 13:23 PWn
-rw-r----x 1 hacker hacker   0 Sep 26 14:35 college
-rw-r--r-- 1 root   hacker  60 Sep 23 17:24 h
-rw-r----x 1 hacker hacker 781 Sep 30 09:00 instructions
-rw-r----x 1 hacker hacker   0 Sep 30 09:00 my
-rw-r----x 1 hacker hacker  95 Sep 30 08:51 myflag
lrwxrwxrwx 1 hacker hacker   5 Sep 27 09:41 not-the-flag -> /flag
-rwxr--r-- 1 hacker hacker  27 Oct 10 19:36 pwn.sh
-rw-r--r-- 1 hacker hacker  10 Oct 10 21:14 rm
-rwxr--r-- 1 hacker hacker 168 Oct 10 19:49 solve.sh
-rw-r----x 1 hacker hacker 437 Sep 30 08:55 the-flag
-rwxr-xr-x 1 hacker hacker  17 Oct 10 21:07 win
-rw-r--r-- 1 hacker hacker  18 Oct 10 20:28 win.sh
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$  PATH="/home/hacker:/run/dojo/bin"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{0hL3IBr3r4An6XDm1iiju4vm-1v.QX3cjM1wiM1AzNzEzW}
```

## What I Learnt
I learnt how to write scriptsm making files executable assigning directories to PATH variable.

## References
The references I used were the instructions provided by the pwn.college.
