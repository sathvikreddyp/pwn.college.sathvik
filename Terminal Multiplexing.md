# 1. Launching Screen
In this challenge, they asked us launch screen to get the flag.

## My Solve
Flag: pwn.college{wKHuZGDQNTncxwnK1ziA_BHVXI2.0VN4IDOxwiM1AzNzEzW}

I launched a new screen session, using "screen" and got the flag.

```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{wKHuZGDQNTncxwnK1ziA_BHVXI2.0VN4IDOxwiM1AzNzEzW}
```

## What I Learnt
I learned about screen. Screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line. To start a screen, we just have to type "screen" on the commandline. When you're done with your command line, type exit or press Ctrl-D to leave the screen session. Then screen will terminate and return you to your original shell.

## References
The references I used were the instructions provided by the pwn.college.

# 2. Detaching and Attaching
In this challenge, they asked us to first launch a screen, then detach from it and run /challenge/run. This will send the flag to the detached screen/session. We have to reattach to the screen to get the flag.

## My Solve
Flag: pwn.college{wEkK4cnorq39hgMnfGEJV6Ww5Dr.0lN4IDOxwiM1AzNzEzW}

I first launched a new session using screen. After entering the session, I detached from it using ctrl-A and then pressing d (after releasing ctrl-A), and ran /challenge/run in the main terminal. I then again went back to the screen using "screen -r" and found the flag in the session.

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

screen: 
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{wEkK4cnorq39hgMnfGEJV6Ww5Dr.0lN4IDOxwiM1AzNzEzW}
```

## What I Learnt
I learned how we can come out (detach) and go back (attach) to the screen session. We can detach from a screen by first pressing ctrl-A, releasing it and then pressing d. This leaves your session running in the background while you return to your normal terminal. We can go back to the session (reattach) by typing "screen -r" on the commandline.

## References
The references I used were the instructions provided by the pwn.college.

# 3. FInding Sessions
In this challenge, they told that they created three different screens, of which 1 of them has the flag, and other 2 are decoys. We need to check each one until we find the flag.

## My Solve
Flag: pwn.college{slT1jPL0fTwkDA-nLNtqdybr2mV.01N4IDOxwiM1AzNzEzW}

In the main terminal, I first used screen -ls to list all the screens. I then used "screen -r PID" to go into different sessions. First session with PID 144 was a decoy. The session with PID 147 had the flag. I ignored the sessions which told remote or dead.

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

## What I Learnt
I learned that we can list sessions using "screen -ls". To go into a specific session, we have to keep the PID of the session at the end of session -r (session -r PID).

## References
The references I used were the instructions provided by the pwn.college.

# 4. Switching Windows
In this challenge, they told that they have created two windows in a sission. window 0 has the flag and window 1 has a welcome message. We have to go to window 0 to get the flag.

## My Solve
Flag: pwn.college{Iy8StbYCEDlQqWnCFMxM9XzVqav.0FO4IDOxwiM1AzNzEzW}

In the main terminal, I types screen -r to enter screens. I was in screen 1 at default. Then I used ctrl-A then 0 to enter screen 0 and found the flag there.
```
Main terminal:
hacker@terminal-multiplexing~switching-windows:~$ screen -r
 cat <<MSG

screen 1:
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!

screen 0: 
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{Iy8StbYCEDlQqWnCFMxM9XzVqav.0FO4IDOxwiM1AzNzEzW}
> MSG
```

## What I Learnt
I learned that a screen session can have multiple windows. To control through windows, we can use different keyboard shortcuts, all starting with Ctrl-A:

Ctrl-A c - Create a new window

Ctrl-A n - Next window

Ctrl-A p - Previous window

Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9

Ctrl-A " - bring up a selection menu of all of the windows

## References
The references I used were the instructions provided by the pwn.college.

# 5. Detaching and Attaching (tmux)
In this challenge, they asked us to first launch tmux, then detach from it, then run /challenge/run in the main terminal, which will send the flag to your detached session, then reattach to the session to get the flag.

## My Solve
Flag:  pwn.college{0GTqv451EQJ28qCx5mcx7czVvth.0VO4IDOxwiM1AzNzEzW}

I launched a new session using tmux, then I detached from the session using ctrl-B and then d (after releasing ctrl-B), and then ran /challenge/run in the main terminal. Then the flag was printed in the session, so I went back to the session using "tmux a" and got the flag.

 ```
Main terminal:
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach

tmux: 
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 11;rgb:0c0c/0c0c/0c0c echo Congratulations, here is your flag: pwn.college{0GTqv451EQJ28qCx5mcx7czVvth.0VO4IDOxwiM1AzNzEzW}
```

## What I Learnt
I learned about terminal multiplexer (tmux) which is similar to screen, but with different key bindings. The biggest difference between them is that tmux uses ctrl-B as its command prefix while screen uses ctrl-A.

To detach from tmux- ctrl-B followed by d.

tmux ls - List sessions

tmux attach or tmux a - Reattach to session

## References
The references I used were the instructions provided by the pwn.college.

# 6. Switching Windows (tmux)
In this challenge, they told that they created a tmux session with 2 windows, window 1 has a welcome message, and window 0 has the flag. We have to go to window 0 to get the flag.

## My Solve
FLag: pwn.college{Ilu-6Yr-D-GSWovvsWZRJtsFnMX.0FM5IDOxwiM1AzNzEzW}


```
Main terminal:
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

## What I Learnt
I learned how we can navigate windows in tmux:

Ctrl-B c - Create a new window

Ctrl-B n - Next window

Ctrl-B p - Previous window

Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9

Ctrl-B w - See a nice window picker

Tmux also shows your windows at the bottom in a status bar.

## References
The references I used were the instructions provided by the pwn.college.
