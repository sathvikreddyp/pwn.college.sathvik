# 1. Launching Screen
## My Solve
Flag: pwn.college{wKHuZGDQNTncxwnK1ziA_BHVXI2.0VN4IDOxwiM1AzNzEzW}

```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{wKHuZGDQNTncxwnK1ziA_BHVXI2.0VN4IDOxwiM1AzNzEzW}
```

# 2. Detaching and Attaching
## My Solve
Flag: pwn.college{wEkK4cnorq39hgMnfGEJV6Ww5Dr.0lN4IDOxwiM1AzNzEzW}

```
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 140.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 140.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r

hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{wEkK4cnorq39hgMnfGEJV6Ww5Dr.0lN4IDOxwiM1AzNzEzW}
```

# 3. FInding Sessions
## My Solve
Flag: pwn.college{slT1jPL0fTwkDA-nLNtqdybr2mV.01N4IDOxwiM1AzNzEzW}

```
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        150.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        144.session_edc2014ab521f798    (Remote or dead)
        147.session_2d6862d88f709511    (Remote or dead)
        150.session_9666ba6a58ceab03    (Remote or dead)
        144.session_973bde0d7fca4e06    (Detached)
        147.session_60969911bba210ae    (Detached)
        150.session_81bcd31248b544e9    (Detached)
7 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 150
Remove dead screens with 'screen -wipe'.
[screen is terminating]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
Remove dead screens with 'screen -wipe'.
[screen is terminating]
hacker@terminal-multiplexing~finding-sessions:~$  screen -r 147
Remove dead screens with 'screen -wipe'.
[screen is terminating]
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{slT1jPL0fTwkDA-nLNtqdybr2mV.01N4IDOxwiM1AzNzEzW}
```

# 4. Switching Windows
## My Solve
Flag: pwn.college{Iy8StbYCEDlQqWnCFMxM9XzVqav.0FO4IDOxwiM1AzNzEzW}

```
hacker@terminal-multiplexing~switching-windows:~$ screen -r
 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{Iy8StbYCEDlQqWnCFMxM9XzVqav.0FO4IDOxwiM1AzNzEzW}
> MSG
```

# 5. Detaching and Attaching (tmux)
## My Solve
Flag:  pwn.college{0GTqv451EQJ28qCx5mcx7czVvth.0VO4IDOxwiM1AzNzEzW}
 ```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 11;rgb:0c0c/0c0c/0c0c echo Congratulations, here is your flag: pwn.college{0GTqv451EQJ28qCx5mcx7czVvth.0VO4IDOxwiM1AzNzEzW}
```

# 6. Switching Windows (tmux)
## My Solve
FLag: pwn.college{Ilu-6Yr-D-GSWovvsWZRJtsFnMX.0FM5IDOxwiM1AzNzEzW}

```
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a
window 1:
 Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!

window 0: 
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{Ilu-6Yr-D-GSWovvsWZRJtsFnMX.0FM5IDOxwiM1AzNzEzW}
> MSG
```
