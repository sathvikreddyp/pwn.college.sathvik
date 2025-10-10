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
Flag: 
