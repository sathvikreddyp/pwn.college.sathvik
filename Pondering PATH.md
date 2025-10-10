# 1. The PATH Variable
## My Solve
Flag: pwn.college{8B55S-D0UP_CGfDp8XFdYydj32o.QX2cDM1wiM1AzNzEzW}

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

## References
The references I used were the instructions provided by the pwn.college.

# 2. Setting PATH
## My Solve
Flag: pwn.college{YLk49E0pykh4mGQwEsCXXrWmkFH.QX1cjM1wiM1AzNzEzW}

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

## References
The references I used were the instructions provided by the pwn.college.

# 3. Finding Commands
## My Solve 
Flag: pwn.college{0_EEmv2L5xXAD075vEok8wAaeBL.01NzEzNxwiM1AzNzEzW}

```
hacker@path~finding-commands:~$ which win
/challenge/paths/24578/win
hacker@path~finding-commands:~$ cat /challenge/paths/24578/flag
pwn.college{0_EEmv2L5xXAD075vEok8wAaeBL.01NzEzNxwiM1AzNzEzW}
```

# 4. Adding Commands
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

# 5. Hijacking Commands
## My Solve
Flag: pwn.college{0hL3IBr3r4An6XDm1iiju4vm-1v.QX3cjM1wiM1AzNzEzW}

```
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
