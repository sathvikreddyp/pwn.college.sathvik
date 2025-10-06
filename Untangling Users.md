# 2. Other users with su
## My Solve
Flag: pwn.college{oKVZwsqjazUItlizGYMEvAP3E-Y.QX2UDN1wiM1AzNzEzW}

```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{oKVZwsqjazUItlizGYMEvAP3E-Y.QX2UDN1wiM1AzNzEzW}
```

# 3. Cracking passwords
## My Solve
Flag: pwn.college{wdBSmKGtK2GZXDfhP0xF4I2B0Zi.QX3UDN1wiM1AzNzEzW}

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

# 4. Using sudo
## My Solve
Flag: 
