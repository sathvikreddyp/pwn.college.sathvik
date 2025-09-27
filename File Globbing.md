# 1. Matching With *
In this challenge, it was given to change your directory to '/challenge', but use globbing to keep the argument you pass to cd to at most four characters. After that it told to run '/challenge/run' to get the flag.

## My Solve
Flag: pwn.college{42CY1f3-GzVfyGHtNV3JHONrdy3.QXxIDO0wiM1AzNzEzW}

I changed my cwd to '/challenge' and kept it within 4 characters by using '*' glob. After the cwd changed, I ran the program to get the flag.

```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{42CY1f3-GzVfyGHtNV3JHONrdy3.QXxIDO0wiM1AzNzEzW}
```

## What I Learnt
I first learned about globbing. Globbing lets you reference files without typing out their full paths. Before executing commands that you enter, the shell first performs expansions on them, and one of these expansions is globbing. In this challenge, I learned about the "star" glob, When it encounters a "star" character in any argument, the shell will treat it as a wildcard and try to replace that argument with any files that match the pattern. It can match multiple files or single files also if only 1 file is there with that pattern. When zero files are matched,the shell leaves the glob unchanged. The "star" matches any part of the filename except for "/" or a leading ".".

## References
The reference I used is the challenge statement in pwn.college.

# 2. Matching With ?
In this challenge, it was given to change your directory to '/challenge' from home directory using the '?' glob instead of c and l. After that it was given to run '/challenge/run' to get the flag.

## My Solve
Flag: pwn.college{YidouVnI-l81zrkyv8QvyqX-cDw.QXyIDO0wiM1AzNzEzW}

I first used the cd command along with '/?ha??enge' command, as they told to replace c and l with glob. Then I ran the program to get the flag.  

```
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{YidouVnI-l81zrkyv8QvyqX-cDw.QXyIDO0wiM1AzNzEzW}
```
## What I Learnt 
I learned about the '?' glob. It is similar to the star glob but it only matches one character. The shell basically treats it like a single character wildcard.

## References
The reference I used is the challenge statement in pwn.college.

# 3. Matching with []
In this challenge, it asked us to first Change our working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h.

## My Solve
Flag: pwn.college{AmQayEOYcf2sIferfvc4gSC48lu.QXzIDO0wiM1AzNzEzW}

I first used the cd command to change the cwd to /challenge/files. Then i used the square bracket glob with letters b,a,s,h inside (like bash) as the argument for /challenge/run to get the flag. 

```
hacker@globbing~matching-with-:/challenge/files$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{AmQayEOYcf2sIferfvc4gSC48lu.QXzIDO0wiM1AzNzEzW}
```

## What I Learnt
I learned about the square bracket glob. The square brackets are, essentially, a limited form of "?", in that instead of matching any character, square bracket is a wildcard for some subset of potential characters, specified within the brackets. For example, "[pwn]" will match the character p, w, or n.

## References
The reference I used is the challenge statement in pwn.college.

# 4. Mathcing paths with []
This challenge was similar to the previous challenge, Just that we have to start from our home directory and we have to run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files.

## My Solve
Flag: pwn.college{spAhF2veekgyHs19cWTCUgnsAEB.QX0IDO0wiM1AzNzEzW}

I ran the /challenge/run program with the absolute path of all the files globbed into a square bracket.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{spAhF2veekgyHs19cWTCUgnsAEB.QX0IDO0wiM1AzNzEzW}
```

## What I Learnt 
I learned that we can also expand entire paths with globbed arguments. I also learned that globbing happens on a path basis.

## References
The reference I used is the challenge statement in pwn.college.

# 5. Multiple globs
In this challenge, it asked us to change the working directory to /challenge/files, then run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

## My Solve
Flag: pwn.college{ciJMlRe7NqsVbXjiW5gaNM9TkZL.0lM3kjNxwiM1AzNzEzW}

I first used the cd command to change the cwd to /challenge/files. Then I used the /challenge/run with two star globs and p in between as arguments to get the flag.

```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{ciJMlRe7NqsVbXjiW5gaNM9TkZL.0lM3kjNxwiM1AzNzEzW}
```

## What I Learnt 
I learned that we can use multiple globs at a time that too in a single word also.

## References
The reference I used is the challenge statement in pwn.college.

# 6. Mixing globs
In this challenge, they asked us to cd to /challenge/files, then using the globbing we learned till now, we had to write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning".

## My Solve
Flag: pwn.college{odYPT3M9vzdJshDrAHzaIgxWj2K.QX1IDO0wiM1AzNzEzW}

I first used cd command to change the cwd to /challenge/files, then I ran the program with /challenge/run with c,e,p inside square brackets and 1 star as globs as the argument, this argument was exactly 6 characters, and i got the flag. This argument will match all the files that start with either c,p or e.

```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{odYPT3M9vzdJshDrAHzaIgxWj2K.QX1IDO0wiM1AzNzEzW}
```

## What I Learnt
I learned that we can use different types of globs into the same argument and the shell will expand it.

## References
The reference I used is the challenge statement in pwn.college.

# 7. Exclusionary globbing
In this challenge, they asked us to go to /challenge/files and then run /challenge/run with all files that don't start with p, w, or n as argument.

## My Solve
Flag: pwn.college{4t2Lp4tBiC8rnWeK8vUu57WW8jf.QX2IDO0wiM1AzNzEzW}

As they gave, I first changed the cwd to /challenge/files using cd command. Then I ran the program along with using the square brackets glob with (!pwn) inside to exclude those files which are starting with p,w, or n (exclusionary globbing), and I kept the star glob to include all files after that.

```
hacker@globbing~exclusionary-globbing:/challenge/files$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{4t2Lp4tBiC8rnWeK8vUu57WW8jf.QX2IDO0wiM1AzNzEzW}
```

## What I Learnt 
I learned that we can also exclude some characters while globbing using square bracket glob and starting either ! or ^ inside the bracket and then keeping the letters we want to exclude.

## References
The reference I used is the challenge statement in pwn.college.

# 8. Tab completion
In this challenge, they copied the flag into /challenge/pwncollege, and we can freely cat that file. But we can't type the filename. We have to tab-complete (click tab on your keyboard) to get the flag.

## My Solve
Flag: pwn.college{Yg-NXKpwazX9Okt-re25fNfxwiP.0FN0EzNxwiM1AzNzEzW}

I read /challenge/pwncollege using the cat command, but I clicked tab after typing till pwn, as they told we must use tab-key in the challenge to get the flag.

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{Yg-NXKpwazX9Okt-re25fNfxwiP.0FN0EzNxwiM1AzNzEzW}
```

## What I Learnt
I learned that instead of using the star glob, which is risky as it might expand to unintended files, we can click tab when we are writing the path of the file and the shell will try to figure out what you're going to type and automatically complete it. All we have to do is click tab.

## References
The reference I used is the challenge statement in pwn.college.

# 9. Multiple options for tab completion
In this challenge, there is a /challenge/files directory with a bunch of files starting with pwncollege. It was given we have to Tab-complete from /challenge/files/p or so, and make your way to the flag.

## My Solve
Flag: pwn.college{cnqKJ5whCooV7PVDrCL_-NXOa51.0lN0EzNxwiM1AzNzEzW}

I first typed till /challenge/files/pwncollege- then clicked tab, it then showed me a bunch of files starting with pwncollege-. I then tried reading a few with cat command, then when I went to /challenge/files/pwncollege-fl and clicked tab. Then I ran cat /challenge/files/pwncollege-flag to retrieve the flag.

```
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwncollege-
pwncollege-family      pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flamingo    pwncollege-hacking
pwn-college            pwncollege-family      pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:~$ /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flamingo    pwncollege-hacking
pwn-college            pwncollege-family      pwncollege-flyswatter
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-
pwncollege-family      pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{cnqKJ5whCooV7PVDrCL_-NXOa51.0lN0EzNxwiM1AzNzEzW}
```

## What I Learnt
I learned that if there are more than 1 options when u click tab, then the bash will auto expand till the point where there are multiple options, or till the last common point of the multiple options, then if u hit agin for a second time, some bashes will cycle through all the options and some will show all the options available.

## References
The reference I used is the challenge statement in pwn.college.

# 10. Tab completion on commands
In this challenge, it was given that there is a command that starts with pwncollege, and it'll give you the flag. It told us to type pwncollege and hit the tab key to auto-complete it.

## My Solve
Flag: pwn.college{oDL4Pk21LBz0vo2EEeLRoWYY6Vx.0VN0EzNxwiM1AzNzEzW}

As given in the challenge statement, i first typed pwncollege then clicked tab, it auto completed the command and i executed the command to get the flag.

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-2312
.bash_history  .config/       .lesshst       college        h              not-the-flag
hacker@globbing~tab-completion-on-commands:~$ pwncollege-2312
Correct! Here is your flag:
pwn.college{oDL4Pk21LBz0vo2EEeLRoWYY6Vx.0VN0EzNxwiM1AzNzEzW}
```

## What I Learnt
I learned that we can use the tab key for completing not only files, but we can use it for commands also. But we must be careful when we auto complete and check if the command is correct to prevent wrong commands with a similar name from being executed.

## References
The reference I used is the challenge statement in pwn.college.
