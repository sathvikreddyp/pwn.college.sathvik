# 1. Redirecting output
This challenge asked us to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase) using output redirection.

## My Solve
Flag: pwn.college{oc9O_TMS6729WPhOu56TxykOisd.QX0YTN0wiM1AzNzEzW}

I used the echo command with PWN as argument, then redirected the output to COLLEGE file using ">" to get the flag.

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{oc9O_TMS6729WPhOu56TxykOisd.QX0YTN0wiM1AzNzEzW}
```

## What I Learnt
I learned that every process in Linux has three initial, standard channels of communication: standard input (stdin), standard output (stdout), and standard error (stderr). These are the channels through which process takes input, processes output normal data, and processes output error details, respectively. We can redirect the standard output (stdout) to files using ">". For example, "echo hi > abcd" will redirect the output of echo hi (which will be hi) to the file abcd. We can then use a command like cat to read the file.

## References
The References I used was the problem statement provided by the pwn.college.

# 2. Redirecting more output
In this challenge, they asked us to redirect the output of /challenge/run to the "myflag" file, then the flag will be in that file.

## My Solve
Flag: pwn.college{EJ4bUQr1-dVYxdYtUOrsIAVLDcj.QX1YTN0wiM1AzNzEzW}

I first redirected the output of the /challenge/run program to the myflag file, then I read the file using cat command to get the flag.

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{EJ4bUQr1-dVYxdYtUOrsIAVLDcj.QX1YTN0wiM1AzNzEzW}
```

## What I Learnt
I learned that we can redirect the output of any command to a file, not only echo.

## References
The References I used was the problem statement provided by the pwn.college.

# 3. Apending output
In this challenge, they asked us to run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. This will write the first half of the flag to the file, and the second half to stdout. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag.

## My Solve
Flag: pwn.college{0FQhoSbgMi9bDNMpwwdAJUAPFRL.QX3ATO0wiM1AzNzEzW}

In this challenge, they asked us to run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. This will write the first half of the flag to the file, and the second half to stdout. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag.

```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{0FQhoSbgMi9bDNMpwwdAJUAPFRL.QX3ATO0wiM1AzNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

## What I Learnt
I learned that if we use ">" to redirect an output, then it will create a new output file every time, deleting the old contents. If we want to append the output, that is add the output to the file without deleting the existing contents, we have to use ">>" instead of ">".

## References
The References I used was the problem statement provided by the pwn.college.

# 4. Redirecting errors
In this challenge, they asked us to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in this case, the instructions) to instructions. Then they told we can find the instructions/feedback in instructions and the flag in myflag.

## My Solve
Flag: pwn.college{EJ4bUQr1-dVYxdYtUOrsIAVLDcj.QX1YTN0wiM1AzNzEzW}

I redirected the output of /challenge/run to myflag, as they told, by using ">", and redirected the errors to instructions by using "2>". I then read the myflag file using cat command to get the flag.

```
hacker@piping~redirecting-errors:~$ /challenge/run > my flag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   You have redirected the wrong file for stdout (/home/hacker/my instead of myflag).
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{EJ4bUQr1-dVYxdYtUOrsIAVLDcj.QX1YTN0wiM1AzNzEzW}
```

## What I Learnt
I learned about FD (file descriptor) number, it is a number that describes a communication channel in Linux. FD 0 is standard input, FD 1 is standard output, FD 2 is standard error. When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). If you want to redirect error, you have to use "2>", and similarly if you want to redirect output, you can use "1>" or ">". We can also redirect multiple file descriptors at the same time.

## References
The References I used was the problem statement provided by the pwn.college.

# 5. Redirecting output
In this challenge, they asked us to redirect the input of PWN file to challenge/run, but before that we should have the PWN file contain the value COLLEGE.

## My Solve
Flag: pwn.college{EaPlwiNsi6Wl7nldrQyzOgSNGl2.QXwcTN0wiM1AzNzEzW}

I first redirected the output of "echo COLLEGE" to PWN, as they told PWN file should have the value COLLEGE, then I redirected the input of PWN file to /challenge/run using (<) operator.

```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{EaPlwiNsi6Wl7nldrQyzOgSNGl2.QXwcTN0wiM1AzNzEzW}
```

## What I Learnt
I learned that just like how we can redirect output, we can also redirect inputs using (<).

## References
The References I used was the problem statement provided by the pwn.college.

# 6. Greping stored results
In this challenge, they asked us to first redirect the output of /challenge/run to /tmp/data.txt, which will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt. We then have to grep that for the flag.

## My Solve
Flag: pwn.college{o_v8h5AWoeh1oaN8kKN31KHmhso.QX4EDO0wiM1AzNzEzW}

I first redirected the output of /challenge/run to /tmp/data.txt, as they asked us to do it. I then used the grep command to find for "pwn.college" in /tmp/data.txt, since all flags over here start with pwn.college.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{o_v8h5AWoeh1oaN8kKN31KHmhso.QX4EDO0wiM1AzNzEzW}
```

## What I Learnt
I learned how we can redirect an output to a file and then use grep command to find a paticular thing.

## References
The References I used was the problem statement provided by the pwn.college.

# 7. Grepping live output
In this challenge, they told that /challenge/run will output a hundred thousand lines of text, including the flag. We have to grep for the flag.

## My Solve
Flag: pwn.college{QLNioGCxf1X7aKEpihWHHMFaDfh.QX5EDO0wiM1AzNzEzW}

I used the pipe operator (|) to connect the standard output of /challenge/run to the input of "grep pwn.college".

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{QLNioGCxf1X7aKEpihWHHMFaDfh.QX5EDO0wiM1AzNzEzW}
```

## What I Learnt
I learned about the pipe operator, represented by "|". With this operator, Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example: echo "yes-yes | grep yes" will give "yes-yes" as final output and "echo no-no | grep yes" will not give any final output.

## References
The References I used was the problem statement provided by the pwn.college.

# 8. Grepping errors
This challenge is similar to the previous challenge, /challenge/run will overwhelm us with output, but this time on standard error. They asked us to grep through it to find the flag.

## My Solve
Flag: pwn.college{8tH-EC_TWccK0W8aZJq92rUh6it.QX1ATO0wiM1AzNzEzW}

I redirected the standard error of /challenge/run to standard output, by using "2>& 1", here ">&" is for redirecting a file descriptor to another file descriptor, then used the pipe operator to connect this output to the input of grep command to find the flag.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{8tH-EC_TWccK0W8aZJq92rUh6it.QX1ATO0wiM1AzNzEzW}
```

## What I Learnt
I learned about ">&" operator, which is used to redirect a file descriptor to another file descriptor. For example: "2>& 1" will redirect FD2 (standard error) to FD1 (standard output). I also learned that the "|" operator redirects only standard output to another program, and there is no 2| form of the operator, It can only redirect standard output.

## References
The References I used was the problem statement provided by the pwn.college.

# 9. Filtering with grep -v
In this challenge, /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags (containing the word DECOY somewhere in the flag) mixed in with the real flag. They told we need to filter out the decoys while keeping the real flag, using grep -v.

## My Solve
Flag: pwn.college{AM6-_eusRIfLU4rDVK9B9drtPBw.0FOxEzNxwiM1AzNzEzW}

I connected the output of /challenge/run to grep command with -v and DECOY as arguments using the pipe operator (|).

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{AM6-_eusRIfLU4rDVK9B9drtPBw.0FOxEzNxwiM1AzNzEzW}
```

## WHat I Learnt
I learned 1 more use of grep, with the -v argument, the command shows lines which do not match a pattern. For example: if a file has "hello world" and "hello man" and we use "grep -v world" on this file, it will print "Hello man" on the terminal.

## References
The References I used was the problem statement provided by the pwn.college.

# 10. Duplicating piped data with tee
In this challenge, they told us that /challenge/pwn must be piped into /challenge/college, but we need to intercept the data to see what pwn needs from you, using the tee command.

## My SOlve
Flag: pwn.college{QhhWn2oGMicqD00Ka086T00EZx6.QXxITO0wiM1AzNzEzW}

I first used the ls command to list all the files in the home directory. I read cat file but nothing was there in that. Then I tried to pipe the /challenge/pwn to /challenge/college but the secret code was missing.  I then used the tee command to duplicate the output of /challenge/pwn to the PWN file, then I read the file to get the secret code and then I used that secret code as argument with /challenge/pwn and connected the output of that with /challenge/college using the pipe operator (|) to get the flag.

```
hacker@piping~duplicating-piped-data-with-tee:~$ ls
COLLEGE  PWN  PWn  college  h  instructions  my  myflag  not-the-flag  the-flag
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn
cat: pwn: No such file or directory
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee PWN | /challenge/college
Processing...
WARNING: you are overwriting file PWN with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn
cat: pwn: No such file or directory
hacker@piping~duplicating-piped-data-with-tee:~$ cat PWN
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "QhhWn2oG"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret QhhWn2oG
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret QhhWn2oG | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{QhhWn2oGMicqD00Ka086T00EZx6.QXxITO0wiM1AzNzEzW}
```

## What I Learnt
I learned about the tee command, which can be used to duplicate data flowing through your pipes to any number of files provided on the command line. For example: "echo hi | tee blah hello" will duplicate the output of "echo hi" which is hi to the files "blah" and "hello", along with the standard output. Basically we end up with three copies of the piped-in data: one to stdout, one to the blah file, and one to the hello file.

## References
The References I used was the problem statement provided by the pwn.college.

# 11. Process substitution for input
In this challenge, they told we have two sets of command outputs: /challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag. They asked us to use Use process substitution with diff to compare the outputs of these two programs and find the flag.

## My Solve
Flag: > pwn.college{0VaClsJ1-sMU8AH2hbQKPe2fJVw.0lNwMDOxwiM1AzNzEzW}

I used the diff command with input process substitution of /challenge/print_decoys and /challenge/print_decoys_and_flags as arguments (diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)) to get the real flag.

```
hacker@piping~process-substitution-for-input:~$  diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
13a14
> pwn.college{0VaClsJ1-sMU8AH2hbQKPe2fJVw.0lNwMDOxwiM1AzNzEzW}
```

## What I Learnt
I learned that Linux follows the philosophy that "everything is a file". That is, the system strives to provide file-like access to most resources, including the input and output of running programs! The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line and hook it up to the output of programs. I also learned about process substitition, where we can hook input and output of programs to arguments of commands. For reading from a command (input process substitution), we use <(command). When we write "<(command)", bash will run the command and hook up its output to a temporary file that it will create. This isn't a real file, it's called a named pipe, in that it has a file name.

## References
The References I used was the problem statement provided by the pwn.college.

# 12. Writing to multiple programs
In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. We have to run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands.

## My Solve
Flag: pwn.college{YKLRoveVOpo3A9895jBoysUmebg.QXwgDN1wiM1AzNzEzW}

I used tee command to duplicate the output of /challenge/hack to the input of both the /challenge/the and the /challenge/planet commands simultaneously to get the flag. 

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
24697130233145130299
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{YKLRoveVOpo3A9895jBoysUmebg.QXwgDN1wiM1AzNzEzW}
```

## What I Learnt

## References
The References I used was the problem statement provided by the pwn.college.

# 13. Split-piping stderr and stdout 
In this challenge, we are asked to get hack's stdout to go to /challenge/planet and stderr to go to /challenge/the — separately, not mixed.

## My Solve
Flag: pwn.college{IW_0lWlrE7v5acwBLku7q3TjQ7o.QXxQDM2wiM1AzNzEzW}

I wrote /challenge/hack 2> >( /challenge/the ) | /challenge/planet in the terminal because | /challenge/planet connects hack's stdout to planet's stdin, 2> >( /challenge/the ) redirects hack's stderr into a process substitution; the shell runs /challenge/the with its stdin coming from that redirection, so stderr goes into /challenge/the alone.

```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >( /challenge/the ) | /challenge/planet
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{IW_0lWlrE7v5acwBLku7q3TjQ7o.QXxQDM2wiM1AzNzEzW}
```

## What I Learnt
I learnt how to redirect stderr and stdout seperately, not mixed.

## References
The reference was the problem statement provided by the pwn.college.

# 14. Named pipes
