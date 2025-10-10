# 1. Becoming root with su
In this challenge, they asked us to become the root with su and then read the flag. The root password was given (hack-the-planet).

## My Solve
Flag: pwn.college{gQsgqsgDPral2d0RXZkqDkvxszQ.QX1UDN1wiM1AzNzEzW}

I first used su and then entered the password to become the root. I then read the flag file using cat command.

```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{gQsgqsgDPral2d0RXZkqDkvxszQ.QX1UDN1wiM1AzNzEzW}
```

## What I Learnt
I learned how we can become the root of the system using su command. su asks for a password before giving you root status. This check against the root password is what obsoletes su. Modern systems very rarely have root passwords, and different mechanisms (that we will learn later) are used to grant administrative access. su and sudo are the two utilities we can use to become the root.

## References
The references I used are the instructions provided by the pwn.college.

# 2. Other users with su
In this challenge, they asked us to switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

## My Solve
Flag: pwn.college{oKVZwsqjazUItlizGYMEvAP3E-Y.QX2UDN1wiM1AzNzEzW}

I first used su with zardus as argument and typed the password they gave to switch to zardus user. After switching, I ran /challenge/run to get the flag.

```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{oKVZwsqjazUItlizGYMEvAP3E-Y.QX2UDN1wiM1AzNzEzW}
```

## What I Learnt
I learned how we can switch users with su. We have to keep the username as the argument of the su command.

## References
The references I used are the instructions provided by the pwn.college.

# 3. Cracking passwords
In this challenge, they gave us a leak of /etc/shadow in /challenge/shadow-leak. They then asked us to crack the password of zardus, then su to zardus and then run /challenge/run to get the flag.

## My Solve
Flag: pwn.college{wdBSmKGtK2GZXDfhP0xF4I2B0Zi.QX3UDN1wiM1AzNzEzW}

I first used the famous John the ripper on /challenge/shadow-leak to crack passwords. I also used the --show argument later to arrange it properly and i found the password of zardus. I then switched the user to zardus using su and entering the password found and ran /challenge/run to get the flag.

```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:18 1% 2/3 0g/s 286.8p/s 286.8c/s 286.8C/s chacha..jazmin
0g 0:00:00:19 1% 2/3 0g/s 286.9p/s 286.9c/s 286.9C/s 10sne1..nermal
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04933g/s 287.2p/s 287.2c/s 287.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ john --show /challenge/shadow-leak
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20367:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wdBSmKGtK2GZXDfhP0xF4I2B0Zi.QX3UDN1wiM1AzNzEzW}
```

## What I Learnt
I learned how we can crack passwords using john. The passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow. The passwords in the file are generally encrypted.

## References
The references I used are the instructions provided by the pwn.college.

# 4. Using sudo
In this challenge, they told that we will have sudo access, and we have to use it to read the flag.

## My Solve
Flag: pwn.college{Qo5_eGSHVDsqd8QZuIOQPgtfl68.QX4UDN1wiM1AzNzEzW}

I used the cat command on /flag with sudo at the start to read the flag with root access.

```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{Qo5_eGSHVDsqd8QZuIOQPgtfl68.QX4UDN1wiM1AzNzEzW}
```

## What I Learnt
I learned that we can put sudo at the start of the command to run the command as a root. Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root. Unlike su, which relies on password authentication, sudo checks policies to determine whether the user is authorized to run commands as root. These policies are defined in /etc/sudoers.

## References
The references I used are the instructions provided by the pwn.college.
