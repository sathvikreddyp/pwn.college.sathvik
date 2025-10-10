# 1. Chaining with Semicolons
## My Solve
Flag: pwn.college{oSPf3a3MZ50taqL4xsikAOgqANO.QX1UDO0wiM1AzNzEzW}

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oSPf3a3MZ50taqL4xsikAOgqANO.QX1UDO0wiM1AzNzEzW}
```

# 2. Building on Success
## My Solve
Flag:  pwn.college{gqcCulzcxnjtI-Q5g6ZCaOe_Yny.0lM0MDOxwiM1AzNzEzW}

```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{gqcCulzcxnjtI-Q5g6ZCaOe_Yny.0lM0MDOxwiM1AzNzEzW}
```

# 3. Handling Failure
## My Solve
Flag:  pwn.college{AIFvEMpjHF_M0dCYcXOdB_LnstI.01M0MDOxwiM1AzNzEzW}

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{AIFvEMpjHF_M0dCYcXOdB_LnstI.01M0MDOxwiM1AzNzEzW}
```

# 4. Your First Shell Script
## My Solve
Flag: pwn.college{4VXjEfe-HprlJZ3ZDwUtfbzoon4.QXxcDO0wiM1AzNzEzW}

```
hacker@chaining~your-first-shell-script:~$ nano pwn.sh
hacker@chaining~your-first-shell-script:~$ bash pwn.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{4VXjEfe-HprlJZ3ZDwUtfbzoon4.QXxcDO0wiM1AzNzEzW}
```

# 5. Redirecting Script Output
## My Solve
Flag: pwn.college{0qfxnTen9HD2FXTz5Emtte1jvjw.QX4ETO0wiM1AzNzEzW}

```
hacker@chaining~redirecting-script-output:~$ nano pwn.sh
hacker@chaining~redirecting-script-output:~$ bash pwn.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{0qfxnTen9HD2FXTz5Emtte1jvjw.QX4ETO0wiM1AzNzEzW}
```

# 6. Executable Shell Scripts
## My Solve
Flag: pwn.college{Ir5HghBc7Lr-JK53mFKTrk8aK0_.QX0cjM1wiM1AzNzEzW}

```
hacker@chaining~executable-shell-scripts:~$ nano pwn.sh
hacker@chaining~executable-shell-scripts:~$ pwn.sh
bash: pwn.sh: command not found
hacker@chaining~executable-shell-scripts:~$ ls
COLLEGE  Desktop  PWN  PWn  college  h  instructions  my  myflag  not-the-flag  pwn.sh  the-flag
hacker@chaining~executable-shell-scripts:~$ /home/hacker/pwn.sh
bash: /home/hacker/pwn.sh: Permission denied
hacker@chaining~executable-shell-scripts:~$ nano pwn.sh
hacker@chaining~executable-shell-scripts:~$ ls -l
total 36
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
-rw-r--r-- 1 hacker hacker  17 Oct 10 19:19 pwn.sh
-rw-r----x 1 hacker hacker 437 Sep 30 08:55 the-flag
hacker@chaining~executable-shell-scripts:~$ chmod u+x pwn.sh
hacker@chaining~executable-shell-scripts:~$ ./pwn.sh
Congratulations on your shell script execution! Your flag:
pwn.college{Ir5HghBc7Lr-JK53mFKTrk8aK0_.QX0cjM1wiM1AzNzEzW}
```

# 7. Understanding Shebangs
## My Solve
Flag:  pwn.college{cbSHXgjW3dhnfHi8acWCennivDT.0VOzMDOxwiM1AzNzEzW}

```
hacker@chaining~understanding-shebangs:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ ls -l
total 40
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
-rwxr--r-- 1 hacker hacker  17 Oct 10 19:19 pwn.sh
-rw-r--r-- 1 hacker hacker  28 Oct 10 19:29 solve.sh
-rw-r----x 1 hacker hacker 437 Sep 30 08:55 the-flag
hacker@chaining~understanding-shebangs:~$ chmod u+x solve.sh
hacker@chaining~understanding-shebangs:~$  /challenge/run
Testing your script...
Your script did not give the expected output.
Expected: hack the planet
Got:
hacker@chaining~understanding-shebangs:~$ nano solve.sh
hacker@chaining~understanding-shebangs:~$ ls -l
total 40
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
-rwxr--r-- 1 hacker hacker  17 Oct 10 19:19 pwn.sh
-rwxr--r-- 1 hacker hacker  33 Oct 10 19:30 solve.sh
-rw-r----x 1 hacker hacker 437 Sep 30 08:55 the-flag
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{cbSHXgjW3dhnfHi8acWCennivDT.0VOzMDOxwiM1AzNzEzW}
```

# 8. Scripting with Arguments
## My Solve
Flag: pwn.college{AT86Unh63zn5NGlqpYosA-pL8TG.0VNzMDOxwiM1AzNzEzW}

```
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{AT86Unh63zn5NGlqpYosA-pL8TG.0VNzMDOxwiM1AzNzEzW}
```

# 9. Scripting with Conditionals
## My Solve
Flag: pwn.college{EWEqNjqr_0IpAi3cMW4_6m-myhX.0lNzMDOxwiM1AzNzEzW}

```
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$  bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{EWEqNjqr_0IpAi3cMW4_6m-myhX.0lNzMDOxwiM1AzNzEzW}
```

# 10. Scripting with Default Cases
## My Solve
Flag: pwn.college{YQ5sCfCBAwX_0PamA9zYxv2a36l.01NzMDOxwiM1AzNzEzW}

```
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$  /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{YQ5sCfCBAwX_0PamA9zYxv2a36l.01NzMDOxwiM1AzNzEzW}
```

# 11. Scripting with Multiple Conditions
## My Solve
Flag: pwn.college{EALyi5sr5MU4ApH7v0trrCBY6Vr.0FOzMDOxwiM1AzNzEzW}

```
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$  bash /home/hacker/solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Test failed for input 'hack'
Expected: 'the planet'
Got: 'planet'
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh hack
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh foo
unknown
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{EALyi5sr5MU4ApH7v0trrCBY6Vr.0FOzMDOxwiM1AzNzEzW}
```

# 12. Reading Shell Scripts
## My Solve
Flag: pwn.college{oqvrNvyeD0Cjf8mWC2KQsFP055w.0lMwgDOxwiM1AzNzEzW}

```
hacker@chaining~reading-shell-scripts:~$ read -p "INPUT" GUESS
INPUThack the PLANET
hacker@chaining~reading-shell-scripts:~$ cat /flag
cat: /flag: Permission denied
hacker@chaining~reading-shell-scripts:~$ cat $GUESS
cat: hack: No such file or directory
cat: the: No such file or directory
cat: PLANET: No such file or directory
hacker@chaining~reading-shell-scripts:~$ /challenge/run

Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{oqvrNvyeD0Cjf8mWC2KQsFP055w.0lMwgDOxwiM1AzNzEzW}
```
