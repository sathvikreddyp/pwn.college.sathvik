# 1. Cat: not the pet, but the command!
This challenge requires us to read the flag from flag file from gome directroy using cat command.

## My Solve
Flag: pwn.college{Q2DPiwChjruOMbeQrtm_3LQUe7e.QXxcTN0wiM1AzNzEzW}

Cat is used to read out the files. I used "cat flag" to read out the flag from flag file.

hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{Q2DPiwChjruOMbeQrtm_3LQUe7e.QXxcTN0wiM1AzNzEzW}

## What I learnt
I learnt the usage of cat command in the linux terminal.

## References
The references were the instructions provided by the pwn.college.

# 2. Cattling absolute paths
This challenge also deals with the cat command. In this case, the flag is not copied directly onto my home directory. We are to first change directory to the root directory and then execute cat flag. 

## My Solve
Flag: pwn.college{AaOtCDn5hfV6-l2SFjp9yRMY8Xf.QX5ETO0wiM1AzNzEzW}

It was mentioned that this time, the flag wasn't directly copied onto my home directory. So, in order to read the flag folder, cat /flag(absolute path) was used.

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{AaOtCDn5hfV6-l2SFjp9yRMY8Xf.QX5ETO0wiM1AzNzEzW}
```

## What I learnt 
I learnt how to use the cat command and the absolute path combined.

## References
The references were the instructions provided by the pwn.college.

# 3. More cattling practice
In this challenge, the flag is to be retrieved from a directory which isn't the home directory or a directory which is not given directly. Absolute paths are to be used and we need to find out that directory.

## My Solve
Flag: pwn.college{AgC45NW8lftplR8BbB7Es898iLz.QXwITO0wiM1AzNzEzW}

The twist in this challenge is that the directory in which the flag file is stored wasn't directly mentioned. After few tries to retrive the flag, I realized that the path was mentioned in the instructions in the terminal. Then I used cat with absolute path given to retrieve the flag.

```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/lib/sympow/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /usr/lib/sympow/flag
pwn.college{AgC45NW8lftplR8BbB7Es898iLz.QXwITO0wiM1AzNzEzW}
```

## What I learnt 
I have learnt how to retrieve a folder when the exact directory and location is not mentioned. I was to use an absolute path to find the solution.

## References
The references were the instructions provided by the pwn.college.

# 4. Grepping for a needle in a haystick
In this challenge, I learnt the use of grep command. It is used to find a specific line(whose text is known) , in a lot of lines of a file(haystack).

## My Solve
Flag: pwn.college{kLTBVJkdoqX0K1cEJfFeSScVqGH.QX3EDO0wiM1AzNzEzW}

I entered the grep command with the common text of the flag(pwn.college) followed by the path of the file in which the search is to be done to retrieve the flag.

## What I learnt 
I have now learnt how to find a specific line whose text we know among a bunch of lines in a given file. The grep command can be used to efficiently find the lines of need.

## References 
The references were the instructions provided by the pwn.college.


# 5. Comparing files
In this challenge, there are 2 files which contains 100 fake flags and 100 fake + 1 real flag respectively. We are asked to identify the real flag.

## My Solve
Flag; > pwn.college{sHpXWo3mJBDlSV1G2u6HohDs9ZT.01MwMDOxwiM1AzNzEzW}

I usdd diff command to obtain the real flag. I entered diff along with path of 2 files with space in between them so that we can identify the real flag which is the only differences between the contents of those 2 files.

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
8a9
> pwn.college{sHpXWo3mJBDlSV1G2u6HohDs9ZT.01MwMDOxwiM1AzNzEzW}
```

## What I Learnt 
I have learnt the working and application of the diff command and how to compare two files effciently. One more thing is that, the two files are to be separated by a space.

## References 
The references were the instructions provided by the pwn.college.


# 6. Listing files
