# 1. Chaining with Semicolons
In this challenge, they asked us to run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

## My Solve
Flag: pwn.college{oSPf3a3MZ50taqL4xsikAOgqANO.QX1UDO0wiM1AzNzEzW}

I ran /challenge/pwn and /challenge/college programs chained with a semicolon (;) to get the flag.

```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oSPf3a3MZ50taqL4xsikAOgqANO.QX1UDO0wiM1AzNzEzW}
```

## What I Learnt
I learned that we can chain commands with a semicolon (;). In most contexts, ; separates commands in a similar way to how Enter separates lines.

## References
The references I used were the instructions provided by the pwn.college.

# 2. Building on Success
In this challenge, they asked us to chain the programs /challenge/first-success and /challenge/second using the "&&" operator.

## My Solve
Flag:  pwn.college{gqcCulzcxnjtI-Q5g6ZCaOe_Yny.0lM0MDOxwiM1AzNzEzW}

I ran /challenge/first-success along with the AND operator (&&) and /challenge/second (/challenge/first-success && /challenge/second) to get the flag.

```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{gqcCulzcxnjtI-Q5g6ZCaOe_Yny.0lM0MDOxwiM1AzNzEzW}
```

## What I Learnt
I learned about the "&&" operator. It allows us to run a second command only if the first command succeeds (in Linux convention, this means it exited with code 0). syntax: "command1 && command2", this means run command1, and if it succeeds then run command2.

## References
The references I used were the instructions provided by the pwn.college.

# 3. Handling Failure
In this challenge, they asked us to chain the programs /challenge/first-failure and /challenge/second using the OR operator (||).

## My Solve
Flag:  pwn.college{AIFvEMpjHF_M0dCYcXOdB_LnstI.01M0MDOxwiM1AzNzEzW}

I ran /challenge/first-failure along with the OR operator (||) and /challenge/second (/challenge/first-failure || /challenge/second) to get the flag.

```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{AIFvEMpjHF_M0dCYcXOdB_LnstI.01M0MDOxwiM1AzNzEzW}
```

## What I Learnt
I learned about the OR (||) operator. It allows us to run a second command only if the first command fails (in Linux convention, this means it exited with a non zero code ). syntax: "command1 || command2", this means run command1, and if it fails then run command2.

## References
The references I used were the instructions provided by the pwn.college.

# 4. Your First Shell Script
In this challenge, they told us to run /challenge/pwn and then /challenge/college, but in a shell script, and then run it with bash to get the flag.

## My Solve
Flag: pwn.college{4VXjEfe-HprlJZ3ZDwUtfbzoon4.QXxcDO0wiM1AzNzEzW}

I used nano command to create a shell script named pwn.sh, and inside nano I typed /challenge/pwn && /challenge/college. Then I launched pwn.ch using bash command in the main terminal and got the flag.

```
hacker@chaining~your-first-shell-script:~$ nano pwn.sh
hacker@chaining~your-first-shell-script:~$ bash pwn.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{4VXjEfe-HprlJZ3ZDwUtfbzoon4.QXxcDO0wiM1AzNzEzW}
```

## What I Learnt
I learned how to make a shell script. They generally end with .sh and Linux has nano, which is a commandline text editor which we can use to make or edit shell scripts. To open a shell script in nano, we have to type "nano FILENAME" on the commandline. We have to use bash command to execute the file. When we use bash command, the shell reads commands from the file rather than the user.

## References
The references I used were the instructions provided by the pwn.college.

# 5. Redirecting Script Output
In this challenge, they told us create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command.

## My Solve
Flag: pwn.college{0qfxnTen9HD2FXTz5Emtte1jvjw.QX4ETO0wiM1AzNzEzW}

I used nano command to create a shell script named pwn.sh, and inside nano I typed /challenge/pwn and /challenge/college, on two different lines. Then I connected the output of the shell script using bash (bash pwn.sh) to the input of /challenge/solve using pipe (|) operator and got the flag.

```
hacker@chaining~redirecting-script-output:~$ nano pwn.sh
hacker@chaining~redirecting-script-output:~$ bash pwn.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{0qfxnTen9HD2FXTz5Emtte1jvjw.QX4ETO0wiM1AzNzEzW}
```

## What I Learnt
I learned that for the shell, the shell script is just like another command. So we can redirect its input and output with various methods we learned in previus modules like >,|.2>,<,>>,etc.

## References
The references I used were the instructions provided by the pwn.college.

# 6. Executable Shell Scripts
In this challenge, they told us to create a script that will invoke the /challenge/solve, make it executable, and then run it without invoking bash to get the flag.

## My Solve
Flag: pwn.college{Ir5HghBc7Lr-JK53mFKTrk8aK0_.QX0cjM1wiM1AzNzEzW}

I used nano command to create a shell script named pwn.sh, and inside nano I typed /challenge/solve. I then changed the permissions of the file to allow the user (that is me) to execute the file using chmod u+x. Then I executed the pwn.sh file to get the flag.

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

## What I Learnt
I learned that we can directly execute the shell script files, if we have executable (x) permissions for that.

## References
The references I used were the instructions provided by the pwn.college.

# 7. Understanding Shebangs
In this challenge, they asked us to create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". We had to make it executable, then run /challenge/run to verify your script works correctly to get the flag.

## My Solve
Flag:  pwn.college{cbSHXgjW3dhnfHi8acWCennivDT.0VOzMDOxwiM1AzNzEzW}

I used nano command to create a shell script named solve.sh. Inside the shell script, I kept the shebang as #!/bin/bash as its a bash script and typed echo "hack the planet". I then made it executable using chmod command and then ran /challenge/run to get the flag.


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
-rwxr--r-- 1 hacker hacker  33 Oct 10 19:30 solve.sh
-rw-r----x 1 hacker hacker 437 Sep 30 08:55 the-flag
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{cbSHXgjW3dhnfHi8acWCennivDT.0VOzMDOxwiM1AzNzEzW}
```

## What I Learnt
I learned about shebangs. They start with #!. There are a bunch of different types of programs, but if the program file starts with the characters #!, Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument. The shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it. Common shebangs:

#!/bin/bash for bash scripts

#!/usr/bin/python3 for Python scripts

#!/bin/sh for POSIX shell scripts, this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems.

## References
The references I used were the instructions provided by the pwn.college.

# 8. Scripting with Arguments
In this challenge, they told us to make a script such that it takes 2 arguments and outputs them in reverse order. After the script is ready, they told us to run /challenge/run to get the flag.

## My Solve
Flag: pwn.college{AT86Unh63zn5NGlqpYosA-pL8TG.0VNzMDOxwiM1AzNzEzW}

I used nano command to create a shell script named solve.sh, and inside nano I typed echo "$2 $1". After that I invoked /challenge/run to get the flag.

```
hacker@chaining~scripting-with-arguments:~$ nano solve.sh
hacker@chaining~scripting-with-arguments:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{AT86Unh63zn5NGlqpYosA-pL8TG.0VNzMDOxwiM1AzNzEzW}
```

## What I Learnt
I learned that scripts can accept arguments. For example: bash script.sh argument1 argument2, $1 contains argument1 and $2 contains argument2, and so on.

## References
The references I used were the instructions provided by the pwn.college.

# 9. Scripting with Conditionals
In this challenge, they told us to make a script such that it takes 1 argument, and if the argument is pwn, then it outputs college, and for any other input it outputs nothing. Once the script is done they asked us to run /challenge/run to get the flag.

## My Solve
Flag: pwn.college{EWEqNjqr_0IpAi3cMW4_6m-myhX.0lNzMDOxwiM1AzNzEzW}

I used nano command to create a shell script named solve.sh, and inside nano I typed the script for outputting college if the argument is pwn. Then I ran /challenge/run to get the flag.

```
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh
hacker@chaining~scripting-with-conditionals:~$  bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{EWEqNjqr_0IpAi3cMW4_6m-myhX.0lNzMDOxwiM1AzNzEzW}

nano:
#!/bin/bash

if [ "$1" == "pwn" ]
then 
    echo "college" 
fi
```

## What I Learnt
I learned that we can also use conditional statements with arguments in the script. We should be careful with the syntax here as its a little weird.

## References
The references I used were the instructions provided by the pwn.college.

# 10. Scripting with Default Cases
In this challenge, they told us to make a script such that it takes 1 argument, and if the argument is pwn, then it outputs college, and for any other input it outputs nope. Once the script is done they asked us to run /challenge/run to get the flag.

## My Solve
Flag: pwn.college{YQ5sCfCBAwX_0PamA9zYxv2a36l.01NzMDOxwiM1AzNzEzW}

I used nano command to create a shell script named solve.sh, and inside nano I typed the script for outputting college if the argument is pwn, and nope for any other argument. Then I ran /challenge/run to get the flag.

```
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$  /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{YQ5sCfCBAwX_0PamA9zYxv2a36l.01NzMDOxwiM1AzNzEzW}

nano:
#!/bin/bash

if [ "$1" == "pwn" ]
then 
    echo "college"
else
    echo "nope" 
fi
```

## What I Learnt
I learned that we can also use else along with if in bash script. Else does not need then unlike if.

## References
The references I used were the instructions provided by the pwn.college.

# 11. Scripting with Multiple Conditions
In this challenge, they told us to make a script such that it takes 1 argument, if the argument is pwn, then it outputs college, if the argument is "hack", then it outputs "the planet", if the argument is learn, then it outputs linux and for any other input it outputs unknown. Once the script is done they asked us to run /challenge/run to get the flag.

## My Solve
Flag: pwn.college{EALyi5sr5MU4ApH7v0trrCBY6Vr.0FOzMDOxwiM1AzNzEzW}

I used nano command to create a shell script named solve.sh, and inside nano I typed the script for the given conditions. Then I ran /challenge/run to get the flag.

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

nano:
#!/bin/bash

if [ "$1" == "pwn" ]
then 
    echo "college"
elif [ "$1" == "hack" ]
then 
    echo "the planet"
elif [ "$1" == "learn" ] 
then 
    echo "linux"
else 
    echo "unknown"
fi 
```

## What I Learnt
I learned that we can also use elif (else if) in bash script. Syntax is same as if. We need to keep then over here also.

## References
The references I used were the instructions provided by the pwn.college.

# 12. Reading Shell Scripts
In this challenge, they told us that /challenge/run is a shell script, that requires you to put in a secret password, but that password is hardcoded into the script iself. They asked us to read the script, find the password and then get the flag.

## My Solve
Flag: pwn.college{oqvrNvyeD0Cjf8mWC2KQsFP055w.0lMwgDOxwiM1AzNzEzW}

I first tries to assign GUESS variable as hack the PLANET and read it but it did not work. I then read the script of /challenge/run using cat command. Then I found the password, which was hack the PLANET. I ran /challenge/run, entered the password, and got the flag.

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

## What I Learnt
I learned how we can read scripts, like by using cat command.

## References
The references I used were the instructions provided by the pwn.college.
