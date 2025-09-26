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

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{kLTBVJkdoqX0K1cEJfFeSScVqGH.QX3EDO0wiM1AzNzEzW}
```

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


# 7. Touching files
In this challenge, we are to explore how to create new files by using the touch command.

## My Solve
Flag: pwn.college{MOgLfa4mDDmEE1yUj6lCa14YVOw.QXwMDO0wiM1AzNzEzW}

To solve this challenge, I first used the touch command to create two files /tmp/pwn and /tmp/college and then ran /challenge/run to retrieve the flag.

```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{MOgLfa4mDDmEE1yUj6lCa14YVOw.QXwMDO0wiM1AzNzEzW}
```
## What I Learnt
I learnt how to use the touch command to make new files.

## References
The references were the instructions provided by the pwn.college.

# 8. Removing files
In this challenge, we need to create a file and delete it using rm command.

## My SOlve
Flag: pwn.college{0Y7Sumeinx7EswMnS13HFQV-ih1.QX2kDM1wiM1AzNzEzW}

I firts created a file called delete_me using touch command and deleted it using rm command. Then I ran /challenge/check to retrieve the flag.

```
hacker@commands~removing-files:~$ touch delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{0Y7Sumeinx7EswMnS13HFQV-ih1.QX2kDM1wiM1AzNzEzW}
```

## What I Learnt
I have learnt how to use the rm command to remove unnecessary files in a directory.

## References
The references were the instructions provided by the pwn.college.

# 9. Moving files
In this challenge, we need move /flag file to /tmp/hack-the-planet file and retrieve the flag.

## My Solve
Flag: pwn.college{Q-F9KlqnTaDWk5v0WWF8Hg6LaTh.0VOxEzNxwiM1AzNzEzW}

To solve this challenge, I used the mv command to move /flag to /tmp/hack-the-planet separated by spaces. I then ran the /challenge/check to retrieve the flag.

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{Q-F9KlqnTaDWk5v0WWF8Hg6LaTh.0VOxEzNxwiM1AzNzEzW}
```
## What I Learnt 
I have learnt how to move a file by using the mv command.

## References 
The references were the instructions provided by the pwn.college.

# 10. Hidden files
In this challenge, we are asked to invoke the hidden flag file which is dot-prepended using ls -a command.

## My Solve
Flag: pwn.college{g6mguXnj9QZvD4sJzUAgVFlHVqW.QXwUDO0wiM1AzNzEzW}

To solve this challenge, I first executed the ls -a / command to list all the hidden files in the root directory. I then read the /.flag-109493272220765 to retrieve the flag.

```
hacker@commands~hidden-files:~$ ls -a /
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-109493272220765  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-109493272220765
pwn.college{g6mguXnj9QZvD4sJzUAgVFlHVqW.QXwUDO0wiM1AzNzEzW}
```
## What I learnt 
I have learnt how to list hidden files by using the ls -a command which may be hidden by the normal ls command.

## References
The references were the instructions provided by the pwn.college.

# 11. An epic file system quest

# 12. Making directories
In this challenge, we need to make a /tmp/pwn directory and make a college file in it and retrieve the flag.

## My Solve 
Flag: pwn.college{MgoypP4ctKUYlvTDhY167NLdkcn.QXxMDO0wiM1AzNzEzW}

First, I created /tmp/pwn directory and then I made a college file in it and ran /challenge/run to retrieve the flag.

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{MgoypP4ctKUYlvTDhY167NLdkcn.QXxMDO0wiM1AzNzEzW}
```

## What I Learnt 
I have learnt how to use the mkdir command to create new directories. I've also then learnt to first cd into the new directory to make a new file in it.

## References 
The references were the instructions provided by the pwn.college.

# 13. Finding files
In this challenge, we need to find the hidden nflag in a random directrory.

## My Solve
Flag: pwn.college{IDYTM-8CGpNvmpUvpOIsDGeAPVX.QXyMDO0wiM1AzNzEzW}

To solve this challenge I first used the find command (find / -name flag) to list all the files named flag. I then started reading the files to retrieve the flag, ignoring the ones saying "permission denied"

```
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/lib/python3/dist-packages/twisted/conch/ssh/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
cat: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
cat: /nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
cat: /nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
cat: /nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
cat: /nix/store/h88mxp2mbgyj06vypwmqpy05idhwimnp-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
cat: /nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/lib/python3/dist-packages/twisted/conch/ssh/flag
pwn.college{IDYTM-8CGpNvmpUvpOIsDGeAPVX.QXyMDO0wiM1AzNzEzW}
```

## What I Learnt 
I have learnt how to use the find command to find a given file in a directory.

## References
The references were the instructions provided by the pwn.college.


# 14. 
