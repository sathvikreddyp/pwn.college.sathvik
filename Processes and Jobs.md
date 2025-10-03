# 1. Listing Processes
## My Solve
Flag: pwn.college{wCkbOG0pKYhquaAxm3RP9BlVXze.QX4MDO0wiM1AzNzEzW}

```
hacker@processes~listing-processes:~$ ps -efww | grep challenge
root         132       1  0 05:15 ?        00:00:00 /challenge/13180-run-10777
hacker       167     155  0 05:18 pts/0    00:00:00 grep --color=auto challenge
hacker@processes~listing-processes:~$ /challenge/13180-run-10777
Yahaha, you found me! Here is your flag:
pwn.college{wCkbOG0pKYhquaAxm3RP9BlVXze.QX4MDO0wiM1AzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

# 2. Killing Processes
## My SOlve
Flag: pwn.college{sygP8--5Y9Dw0v8zEEh29ONPSA5.QXyQDO0wiM1AzNzEzW}

```
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker       136     135  0 05:22 ?        00:00:00 /challenge/dont_run
hacker       155     145  0 05:22 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$  ps -ef | grep dont_run
hacker       157     145  0 05:23 pts/0    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{sygP8--5Y9Dw0v8zEEh29ONPSA5.QXyQDO0wiM1AzNzEzW}
```

# 3. Interrupting Processes
## My Solve
Flag: pwn.college{spaedAQgp8mPRZQJFZjdu0fL87a.QXzQDO0wiM1AzNzEzW}

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{spaedAQgp8mPRZQJFZjdu0fL87a.QXzQDO0wiM1AzNzEzW}
```

# 4. Killing Misbehaving Processes
