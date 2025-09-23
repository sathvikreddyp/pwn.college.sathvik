# 1. The Root
This challenge asks us to invoke a program by providing its path on the command line.

## My Solve
Flag: pwn.college{0foFaQD3aZPbuBdhlqV9QiZboUw.QX4cTO0wiM1AzNzEzW}

I invoked a program named "pwn" in root directory by typing "/pwn".

hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{0foFaQD3aZPbuBdhlqV9QiZboUw.QX4cTO0wiM1AzNzEzW}

## What I learnt 
I learnt about the Directories and the Root Directory. Then I learnt about the path of the Directories. I learnt how to navigate through the directroies in the linux terminal using commands.

## References
The references were the instructions and the video provided by the pwn.college.

# 2. Program and absolute paths
This challenge asks us to execute the run file in the challenge directroy which in turn is present in the root directory.

## My Solve
Flag: pwn.college{8OikyKwtKdpL8ASqxD7CDU7OpYD.QX1QTN0wiM1AzNzEzW}

I wrote "/challenge/run" in the linux terminal to invoke the path of the run file in challenge directory.

hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{8OikyKwtKdpL8ASqxD7CDU7OpYD.QX1QTN0wiM1AzNzEzW}

## What I learnt
I learnt about the paths of the directories and how to invoke them.

## References
The references were the instructions and the video provided by the pwn.college.

# 3. Position thy self
This challenge asks us to execute the /challenge/run program from a specific path which it will say.

## My Solve
Flag: pwn.college{gfXyzAj8TkyLbPO5JCRVHPBki8v.QX2QTN0wiM1AzNzEzW}

I first typed "/challenge/run" in the terminal. It showed I am in the wrong directory and it showed me to go to the correct directory. I then went to that directory and typed "/challenge/run" to invoke the run file in challenge directory.

hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-thy-self:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{gfXyzAj8TkyLbPO5JCRVHPBki8v.QX2QTN0wiM1AzNzEzW}

## What I learnt
I learnt to use the cd command in the terminal.

## References
The references were the instructions and the video provided by the pwn.college.


# 4. Position elsewhere
This challenge asks us to execute the /challenge/run program from a specific path which it will say.

## My Solve
Flag: pwn.college{QTYuN9pGf7-KP2SN2DL1vHWwkw4.QX3QTN0wiM1AzNzEzW}

I first typed "/challenge/run" in the terminal. It showed I am in the wrong directory and it showed me to go to the correct directory. I then went to that directory and typed "/challenge/run" to invoke the run file in challenge directory.

hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd  /usr/share/doc/fontconfig
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QTYuN9pGf7-KP2SN2DL1vHWwkw4.QX3QTN0wiM1AzNzEzW}

## What I learnt
I learnt to use the cd command in the terminal.

## References
The references were the instructions and the video provided by the pwn.college.

# 5. Position yet elsewhere
This challenge asks us to execute the /challenge/run program from a specific path which it will say.

## My Solve
Flag: pwn.college{8Gv8J2X86xe2hnxHk-vwQATD3k5.QX4QTN0wiM1AzNzEzW}

I first typed "/challenge/run" in the terminal. It showed I am in the wrong directory and it showed me to go to the correct directory. I then went to that directory and typed "/challenge/run" to invoke the run file in challenge directory.

hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd  /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-yet-elsewhere:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{8Gv8J2X86xe2hnxHk-vwQATD3k5.QX4QTN0wiM1AzNzEzW}

## What I learnt
I learnt to use the cd command in the terminal.

## References
The references were the instructions and the video provided by the pwn.college.

# 6. Implicit relative paths, from /
This challenge asks us to run /challenge/run using a relative path while having a current working directory of /.

## My Solve
Flag: pwn.college{AfaR53mEZAHoHokDE7EVvEjpiqW.QX5QTN0wiM1AzNzEzW}

I used cd / command to go to root directroy. From there, I used relative path to acces a run file from challenge.

hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{AfaR53mEZAHoHokDE7EVvEjpiqW.QX5QTN0wiM1AzNzEzW}

## What I learnt
I learnt to move from one director to another using cd command. I leanrt to use relative paths to access files from different directroies.

## References
The references were the instructions and the video provided by the pwn.college.

# 7. Explicit relative paths, from /
This challenge requires us to deal with ".". The "." refers to the same directory. Once we use cd for a new directory, "." is used to signify presence in the same directory.

## My Solve
Flag: pwn.college{UD1CnQ6zGc3FirbuLG0D2x6h3WU.QXwUTN0wiM1AzNzEzW}

I first used the cd command to enter into the root directory. I then ran the ./challenge/run within the root directory.

hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{UD1CnQ6zGc3FirbuLG0D2x6h3WU.QXwUTN0wiM1AzNzEzW}

## What I learnt
I have learnt the use and meaning of ".". The "." indicates the current working directory.

## References
The references were the instructions and the video provided by the pwn.college.

# 8. Implicit relative path
This challenge requires us to deal with ".". Once we are in a /challenge command, entering a "naked" /run shows an error. Using the ./ signifies its presence in the current working directory avoiding error.

## My Solve
Flag: pwn.college{4_w93uLZnSHS5EdQEr4YqM73X1y.QXxUTN0wiM1AzNzEzW}

First we use the cd /challenge to navigate into the directory. Next we enter ./run to execute the program. The ./ indicates its presence in the current working directory and avoids errors.

hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4_w93uLZnSHS5EdQEr4YqM73X1y.QXxUTN0wiM1AzNzEzW}

## What I learnt 
I've learnt that the ./ is mandatory to indicate that the prompt is present in the current working directory and without it an error is displayed.

## References
The references were the instructions and the video provided by the pwn.college.

# 9. Home sweet home
This challenge requires us to deal with the home directory. Bash uses ~ as the home directory as a default, expanding to /home/hacker.

## My Solve
Flag: pwn.college{oAzf--ynj2ado7L2pjx-NerzGsY.QXzMDO0wiM1AzNzEzW}

So, I first wrote the command in the prompt(/challenge/run) followed by a space and the argument of home(~) with a 3 letter or less of my choice(h) which copied the flag to the file of my choice.

hacker@paths~home-sweet-home:~$ /challenge/run ~/h
Writing the file to /home/hacker/h!
... and reading it back to you:
pwn.college{oAzf--ynj2ado7L2pjx-NerzGsY.QXzMDO0wiM1AzNzEzW}

## What I learnt
I have learnt how to properly use an argument along with a command and copy a flag to the file of my choice.

## References
The references were the instructions and the video provided by the pwn.college.
