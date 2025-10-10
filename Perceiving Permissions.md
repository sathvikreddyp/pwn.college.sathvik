# 1. Changing File Ownership
In this challenge, they asked us to change the owner of /flag file to our username, that is hacker in pwn.college using chown command and then read the flag from that file. For this challenge only, they made it so that we can use chown to your heart's content as the hacker user (typically, this requires us to be root).

## My Solve
Flag: pwn.college{EIYR2hNGqpK_Oio2q7v9XiygVGF.QXxEjN0wiM1AzNzEzW}

I first used the chown command and changed the owner of /flag file to hacker from root. As I was now the owner of the file, I could read it using cat command and get the flag.

```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{EIYR2hNGqpK_Oio2q7v9XiygVGF.QXxEjN0wiM1AzNzEzW}
```

## What I Learnt
I learned about the chown command, which is used to change the ownership of a file from one user to another. Generally, we need to be root to use this command. We can also check the permissions of a file or directory using ls -l.

## References
The references I used are the instructions provided by the pwn.college.

# 2. Groups and Files
In this challenge, they asked us to change the group ownership of the /flag file to whatever group the user is in, and then read the file for the flag. They told that the flag is readable by whatever group owns it. They also told that it is possible in this challenge to invoke chgrp as the hacker user.

## My Solve
Flag: pwn.college{Q_zTN5pEgNWxKXZiEilMiMgiOvm.QXxcjM1wiM1AzNzEzW}

I first used the id command to see what groups im in. Then I used the chgrp command to change the group ownership of /flag file to hacker group from root. I then read the file using cat command to get the flag.

```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{Q_zTN5pEgNWxKXZiEilMiMgiOvm.QXxcjM1wiM1AzNzEzW}
```

## What I Learnt
I learned about the chgrp command, which is used to change the group ownership of a file. syntax: chgrp "group name" "file name". I also learned that we can check what groups you are part of with the id command.

## References
The references I used are the instructions provided by the pwn.college.

# 3. Fun With Group Names
In this challenge, they told that they have randomized the name of the group that your user is in. Like the previous level, we have to use the id command to figure that name out, then use chgrp and access /flag file.

## My Solve
Flag: pwn.college{g2jNC1WjlZZKuGqMij-IyDMqSNx.QXycjM1wiM1AzNzEzW}

I first used the id command to see what groups im in. Then i used the chgrp command to change the group ownership of /flag file to grp6233 group from root. I then read the file using cat command to get the flag.

```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp29315) groups=1000(grp29315)
hacker@permissions~fun-with-groups-names:~$ chgrp grp6233 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{g2jNC1WjlZZKuGqMij-IyDMqSNx.QXycjM1wiM1AzNzEzW}
```

## What I Learnt
I learned when to use the chgrp command.

## References
The references I used are the instructions provided by the pwn.college.

# 4. Changing Permissions
In this challenge, they told we have to change the permissions of the flag file and then read it to get the flag.

## My Solve
Flag: pwn.college{ET-MW1tCPrY0_lnjYAQ_leSEXBw.QXzcjM1wiM1AzNzEzW}

I used the chmod command with o+r as argument, so that other users will get access to read the flag file. I then read the flag file using cat command.

```
hacker@permissions~changing-permissions:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~changing-permissions:~$ ls -l
total 32
-rw-r--r-- 1 hacker hacker   4 Sep 30 08:47 COLLEGE
drwxr-xr-x 1 hacker hacker   0 Oct  1 13:44 Desktop
-rw-r--r-- 1 hacker hacker  77 Sep 30 16:50 PWN
-rw-r--r-- 1 hacker hacker   8 Sep 29 13:23 PWn
-rw-r--r-- 1 hacker hacker   0 Sep 26 14:35 college
-rw-r--r-- 1 root   hacker  60 Sep 23 17:24 h
-rw-r--r-- 1 hacker hacker 781 Sep 30 09:00 instructions
-rw-r--r-- 1 hacker hacker   0 Sep 30 09:00 my
-rw-r--r-- 1 hacker hacker  95 Sep 30 08:51 myflag
lrwxrwxrwx 1 hacker hacker   5 Sep 27 09:41 not-the-flag -> /flag
-rw-r--r-- 1 hacker hacker 437 Sep 30 08:55 the-flag
hacker@permissions~changing-permissions:~$ chmod o+r *
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{ET-MW1tCPrY0_lnjYAQ_leSEXBw.QXzcjM1wiM1AzNzEzW}
```

## What I Learnt
I learned how we can change permissions of a file using chmod command.

r - user/group/other can read the file (or list the directory)

w - user/group/other can modify the files (or create/delete files in the directory)

x - user/group/other can execute the file as a program (or can enter the directory, e.g., using cd)

"-" - nothing

## References
The references I used are the instructions provided by the pwn.college.

# 5. Executable Files
In this challenge, they told that we first have to make /challenge/run executable, then execute it to get the flag.

## My Solve
Flag: pwn.college{cH3fSLbulk5iKgCMDsqGi9uu3QZ.QXyEjN0wiM1AzNzEzW}

I used chmod a+x /challenge/run, ran the program and got the flag.

```
hacker@permissions~executable-files:~$ chmod a+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{cH3fSLbulk5iKgCMDsqGi9uu3QZ.QXyEjN0wiM1AzNzEzW}
```

## What I Learnt
I learned that we can also change the executable permissions of a program with chmod.

## References
The references I used are the instructions provided by the pwn.college.

# 6. Permission Tweaking Practice
In this challenge, they told that this challenge will ask us to change the permissions of the /challenge/pwn file in specific ways a few times in a row. If we get the permissions wrong, the game will reset and we can try again. If we get the permissions right eight times in a row, the challenge will let us chmod /flag to make it readable for ourselves. They told us to launch /challenge/run to start the challenge.

## My Solve
Flag: pwn.college{YmFttSgj41Y_PXCQRyZ0pMrUVgo.QXwEjN0wiM1AzNzEzW}

I first launched /challenge/run to begin the 8 rounds. I used the chmod command for all the 8 rounds according to what they gave. After that when I got the permission to chmod /flag, I made it readable, writeable, and executable to everyone by using "chmod a+rwx /flag". I then read the flag using cat command.

```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod o-r /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxr-x---
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ug+x /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": rwxr-x---
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrwxrw-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod go+rw /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": rwxrwxrw-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w--w-rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod ug-rx /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": -w--w-rw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ----w----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$  chmod uo-rw /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": ----w----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ----wx---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+x /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": ----wx---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---rwx---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+r /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": ---rwx---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ----w----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g-rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+r /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~permission-tweaking-practice:~$ chmod /flag
chmod: missing operand after ‘/flag’
Try 'chmod --help' for more information.
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

hacker@permissions~permission-tweaking-practice:~$  chmod a+rwx /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{YmFttSgj41Y_PXCQRyZ0pMrUVgo.QXwEjN0wiM1AzNzEzW}
```

## What I Learnt
I learned how to use the chmod command properly.

## References
The references I used were the instructions provided by the pwn.college.

# 7. Permissions Setting Practice 
In this challenge, they told it is like the previous challenge, but it will request more radical permission changes, which we will need "=" and "," "-" chaining to achieve.

## My Solve
Flag: pwn.college{0GJftLNr4ZZf2SFBa-_vbWK3Tbu.QXzETO0wiM1AzNzEzW}

Like the previous challenge, I first ran /challenge/run to start the rounds. I then used chmod to solve the rounds but this time with "=" and "," to completely overwrite the old permissions with the new ones. After the 8 rounds were done, I changed the permissions of the flag file to let anyone read, write, or execute it. I then read the /flag file using cat command.

```
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-x-wxr-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=rx,g=wx,o=rx /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": r-x-wxr-x
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r---wx-wx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$  chmod u=r,o=wx /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": r---wx-wx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--r-xrw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod g=rx,o=rw /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": r--r-xrw-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx-wxr-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rxw,g=wx,o=rx /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": rwx-wxr-x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwxr----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod g=r,o=x /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": rwxr----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-r-xrwx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rx,o=rwx /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": -w-r-xrwx
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ----w-rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=-,g=w,o=rwx /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": ----w-rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r---wxr-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=wx,o=rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod a=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{0GJftLNr4ZZf2SFBa-_vbWK3Tbu.QXzETO0wiM1AzNzEzW}
```

## What I Learnt
I learned that with chmod, we can also overwrite the old permissions with the new ones by using "=" and ",". For example: "chmod u=rw,g=r FILENAME" will set the user permissions to read and write, and the group permissions to read-only. We can also remove all the permissions by keeping "-" after "=". For example: "chmod u=rw,g=r,o=- FILENAME" will set the user permissions to read and write, the group permissions to read-only, and the world permissions to nothing at all.

## References
The references I used were the instructions provided by the pwn.college.

# 8. The SUID Bit
In this challenge, they told we have to add the SUID bit to the /challenge/getroot program. If we do this, root shell will spawn and we can read the flag directly using cat command.

## My Solve
Flag: pwn.college{ogpWKxitXd1BB5RSqkESMcyPvHO.QXzEjN0wiM1AzNzEzW}

I used the chmod command and "u+s" to add the SUID bit to /challenge/getroot, then I ran /challenge/getroot. After the root shell opened, I read the flag file using cat command.

```
hacker@permissions~the-suid-bit:~$ chmod u+s  /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{ogpWKxitXd1BB5RSqkESMcyPvHO.QXzEjN0wiM1AzNzEzW}
```

## What I Learnt
I learned that with set user id (SUID), a user can run a program as the owner of that program's file. As the owner of a file, you can set a file's SUID bit by using chmod: "chmod u+s FILENAME".

## References
The references I used were the instructions provided by the pwn.college.
