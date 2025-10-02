# 1. Translating Characters
In this challenge, they they told that /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). We have to reverse the casing to get the flag.

## My Solve
Flag: pwn.college{I9U2f3HwOuOcHlHrmxJP8-TFlXV.01MxEzNxwiM1AzNzEzW}

I first connected the stdout of /challenge/run to the stdin of the tr command. I gave all capital letters and small letters as first argument and second argument respectively to change the casing of all the letters of the flag.

```
hacker@data~translating-characters:~$ /challenge/run | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
yOUR CASE-SWAPPED FLAG:
pwn.college{I9U2f3HwOuOcHlHrmxJP8-TFlXV.01MxEzNxwiM1AzNzEzW}
```

## What I Learnt
I learnt about the tr command, which translates characters it receives over standard input and prints them to standard output. One way we can use it is that it translates the character provided in its first argument to the character provided in its second argument. For example: "tr a b", will translate all a's to b's.

## References
The reference I used is the instructions provided by the pwn.college.

# 2. Deleting Characters
In this challenge, they they told that /challenge/run will print the flag but will intersperse some decoy characters (specifically: ^ and %) among the flag characters. They told us to use tr -d to remove them.

## My Solve
Flag: pwn.college{ITQb-BrHlUZxxr64pMpGRovom6-.0FNxEzNxwiM1AzNzEzW}

I first connected the stdout of /challenge/run to the stdin of the tr -d command. I gave "^%" as arguments, as we have to remove those characters from the output.

```
hacker@data~deleting-characters:~$ /challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{ITQb-BrHlUZxxr64pMpGRovom6-.0FNxEzNxwiM1AzNzEzW}
```

## What I Learnt
I learnt that tr can also translate characters to nothing (basically delete them). This is done via "-d" flag and an argument of what characters to delete. For example: "tr -d ab" will delete all a's and b's.

## References
The reference I used is the instructions provided by the pwn.college.

# 3. Deleting newlines
In this challenge, they told that /challenge/run has a bunch of newlines added into the flag. They told us to delete them using tr's -d flag and the escaped newline specification.

## My Solve
Flag: pwn.college{QpHeSuLfuWyWHUPCYUETJNixzh9.0VNxEzNxwiM1AzNzEzW}

I first connected the stdout of /challenge/run to the stdin of the tr -d command. I then gave \n (newline specification) as argument in double quotes ("\n") to delete all the newlines and get the flag.

```
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{QpHeSuLfuWyWHUPCYUETJNixzh9.0VNxEzNxwiM1AzNzEzW}
```

## What I Learnt
I learnt about the newline specification, which is "/n". We have to keep it in double quotes when we use it in tr command. Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input into the shell normally. Also, if you want to replace backslash (\) character, we have to use (\\).

## References
The reference I used is the instructions provided by the pwn.college.

# 4. Extracting the first lines with head
In this challenge, they told that /challenge/pwn outputs a bunch of data, and we need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give us the flag if we do this right.

## My Solve
Flag: pwn.college{EtJX3m9aKWQryDxcTDe4AjLAbbS.0lNxEzNxwiM1AzNzEzW}

I first connected the output of /challenge/pwn to the head command with -n 7 as argument to get the first 7 lines. I then connected this output to /challenge/college to get the flag.

```
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{EtJX3m9aKWQryDxcTDe4AjLAbbS.0lNxEzNxwiM1AzNzEzW}
```

## What I Learnt
I learnt about the head command, which can be used to display the first few lines of its input. By default, it shows the first 10 lines, but we can control this with the -n option. For example: cat /something | head -n 7, will print the first 7 lines of "something" file.

## References
The reference I used is the instructions provided by the pwn.college.

# 5. Extracting specfic sections of the text
In this challenge, they told that /challenge/run program will give a bunch of lines with random numbers and single characters (characters of the flag) as columns. They asked us to use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line to get the flag.

## My Solve
Flag: pwn.college{M-XzHmZ0ci3-bQfzKVt2fg29XRC.01NxEzNxwiM1AzNzEzW}

I first ran the /challenge/run program to see the output. The 2nd coloumn had the flag. I then connected the output of the program to the input of cut command (-d " " -f 2) as argument to get the 6th coloumn. I then connected that output with the input of tr command with -d "\n" as argument to remove all the newlines and get the flag in 1 line.

```
hacker@data~deleting-newlines:~$ ls /challenge/run
/challenge/run
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{QpHeSuLfuWyWHUPCYUETJNixzh9.0VNxEzNxwiM1AzNzEzW}hacker@data~deleting-newlines:~$  /chahacker@data~deleting-newlines:~$  /challenge/run
/challenge/run
Your line-split flag:
p
w
n
.col
l
ege
{
Q
pH
e
Su
L
fu
W
y
W
H
U
P
CYUET
J
Nix
z
h
9.
0
V
N
xEzNxw
iM
1
AzN
z
E
zW
}
Your line-split flag:
pw
n.
c
olleg
e{Q
pHeSuLf
uW
yW
H
U
PC
YUE
T
J
N
i
xzh9
.
0V
Nx
EzNx
wi
M
1A
z
NzE
z
W
}

hacker@data~deleting-newlines:~$
Connected!
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{EtJX3m9aKWQryDxcTDe4AjLAbbS.0lNxEzNxwiM1AzNzEzW}
hacker@data~extracting-the-first-lines-with-head:~$
Connected!
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
1002 p
2533 w
16287 n
6642 .
217 c
13971 o
7019 l
5403 l
14435 e
1793 g
2012 e
13386 {
32479 M
2536 -
1204 X
29322 z
24670 H
19140 m
18951 Z
14534 0
20380 c
15342 i
13170 3
13478 -
3994 b
29462 Q
16752 f
10987 z
12034 K
18434 V
4554 t
30248 2
24568 f
15574 g
8279 2
19024 9
22112 X
17419 R
20183 C
2869 .
26350 0
11398 1
17185 N
18059 x
32355 E
7210 z
5079 N
12100 x
17567 w
23179 i
28399 M
7710 1
18713 A
5086 z
32063 N
20776 z
13545 E
13767 z
23175 W
275 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{M-XzHmZ0ci3-bQfzKVt2fg29XRC.01NxEzNxwiM1AzNzEzW}
```

## What I Learnt
I learnt about the cut command, which can be used to extract a specific coloumn. The -d argument specifies the column delimiter (how columns are separated). The -f argument specifies which coloumn should be extracted.

## References
The reference I used is the instructions provided by the pwn.college.

# 6. Sorting data
In this challenge, they told that /challenge/flags.txt has 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end.

## My Solve
Flag: pwn.college{gRWQCddh5Kdvp1CUQz6tlfikLE4.0FM0MDOxwiM1AzNzEzW}

I used the sort command on /challenge/flags.txt, which will sort the file alphabetically, then the flag was at the last.

```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
1002 p
2533 w
16287 n
6642 .
217 c
13971 o
7019 l
5403 l
14435 e
1793 g
2012 e
13386 {
32479 M
2536 -
1204 X
29322 z
24670 H
19140 m
18951 Z
14534 0
20380 c
15342 i
13170 3
13478 -
3994 b
29462 Q
16752 f
10987 z
12034 K
18434 V
4554 t
30248 2
24568 f
15574 g
8279 2
19024 9
22112 X
17419 R
20183 C
2869 .
26350 0
11398 1
17185 N
18059 x
32355 E
7210 z
5079 N
12100 x
17567 w
23179 i
28399 M
7710 1
18713 A
5086 z
32063 N
20776 z
13545 E
13767 z
23175 W
275 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{M-XzHmZ0ci3-bQfzKVt2fg29XRC.01NxEzNxwiM1AzNzEzW}hacker@data~extracting-specific-sections-of-text:~$
Connected!
hacker@data~sorting-data:~$ sort /challenge/flags.txt
ovm.colldge{fQWQCcch5Jdup0CUQz6tkfikLD4.0FL0MDOxwiM1AyMzEzW}
ovn.bnllege{gQWQBddh5Jdvp0CTQy6tlfhkKE4.0FM0LCOxvhL0AyNzEzW}
ovn.bolldgd{gRWQCddh4Kdup1CTQz5tlfijLE3.0FM0LDOwviM1AyMzDzW}
ovn.bollefe{fQVPBddh4Kdup1BTPz5tkfikLE4.0FM0LDNxwhM1AzMzDzV}
owm.bolldfd{fRWPCdcg5Jduo0BUQy6tleikLE3.0FM0MDOxwiL0AzMzDyW}
owm.cnklege{fRWPCdch5Jcvp1CUPz6tlfhkKE4.0FL0LDOxviM1AyMyEzV}
owm.cokkefd{fRWQCcch5Kdvp1CUQz5sleikLE4.0EL0LCOxwiM1AzNyEzW}
owm.colkege{fRWPCcch4Jcvp1BUQz6slfhkLE4.0FL0MCOxwiM0AzMzDzV}
own.bnllege{fRWPCccg5Kduo0BUQz5tkehkLE4.0FM0LDOxvhM0AzNzEzW}
own.boklegd{fQWPCddg5Kcvp1BUQz5tlfikLE4.0EM0MDOxwhM0AzNzEzV}
own.bollege{gRWQCddg5Kcup1BUQy5skeikLD4.0EM0MDOxwiL1AzNzEzW}
own.cnkkdfe{fQWQCddg5Jcup1CUPy6tkfijLD4.0EL0MDNxwiL0AzNzEzV}
own.cnklege{fRWQCddh5Kdup1BUQz6tleikLD4.0FL0MDOxwiM1AzNzEzW}
own.cnllege{fRVQCddh5Jdvo0BUQz6tlfikKD3.0FM0MDOwwiM0AzNzDyW}
own.colkdfd{fRWPBddh5Kcvo1CUPy6tleijKE4.0FM0MDNxwiM1AzMzDyW}
own.colldgd{fQVQBcdg5Kcvo1CUPz6slfikLD4.0FM0LDOxwhL0AyNyEzV}
own.collefd{gQWQCdch5Jdvp1BUPz5slfijKD4.0FM0LDOxwiL1AyNyEzV}
own.collefe{fQWPCdch5Kcvp1CUQz6tleijLE3.0FM0MDNxwhM0AzNyEzW}
own.collegd{gRWQCddh5Kdvo1CUQz6tlfikLD4.0FM0MDOxwiM1AzNzDzW}
own.college{gRWQCddh5Kdvp0CTQz6tlfikLE4.0FM0MDOxwiM0AyNzEzW}
pvm.boklegd{gRWQCddh4Kdup0CTQz6sleijKD4.0FL0MDOxwhM0AzNzDzW}
pvm.colkdfd{fRWQCddh5Kdvp1CUQy6tleikLE4.0EM0LDOxwhM0AzNzEzV}
pvm.colkdge{gRVQCdch5Kdup1BUPz6tkfijLE4.0FM0MDOwwiM0AzMzEyW}
pvm.collefe{gQWQCdch5Kdvp1CUQz6tlfhkLE4.0FM0MDOxwiM1AzNzEzW}
pvm.collefe{gRWQCcdh5Kdvo1BUQy6skfhjKD3.0FM0LDOwwiM0AyNzEyV}
pvn.bnlkegd{gRWQBcdh5Jdup1BUQz6tlfhjKD3.0FM0MDOxvhM1AyNzEzW}
pvn.bolldfe{gRWQCddh5Kdvp0CUQz6tlfhkLD3.0FM0LDOxwiM1AzNzEzW}
pvn.bolldge{fRVPCdch4Kdvo0BUQz6sleikKE4.0FM0LDNwwiM1AzNyEzW}
pvn.bollege{fRVQCdch5Kdvp0CUQz6slfhkKE3.0FM0MCNwviL1AzMzEzV}
pvn.cokkege{gRVPCddg4Kcup1CUQz6tkfijKE4.0EM0MDNxviM1AzNyEzV}
pvn.coklege{gRWQCddh5Kdvp0CUQz6tlfhkLE4.0FM0MDOxwiM1AzMzEzV}
pvn.colkdfe{gRWQCddg5Kduo0BTQy6slfhkLE4.0FL0MCOxwhM0AzMyEyW}
pvn.colldge{fRWQBcch4Kcvp0CUQz6tkfijLE4.0FL0MCOxviL0AyMzEyW}
pvn.collefd{gRVQCdch5Kcvp1CUPy5skehkKE3.0EM0MDNwviM1AzNyEzW}
pvn.collefe{gRVQCdcg5Kdvp1BTQz6tleikLE4.0FM0MDOxwiM1AzMyDzV}
pvn.college{fRWQCddg5Kdup1CUQz6tlfikLE4.0FM0MDOxwiM1AzNzEzW}
pvn.college{fRWQCddh5Kcvo1CUQy6tlfikLE3.0EM0LDOxwiM0AyNzEzW}
pvn.college{gRWQCccg5Kdvp1CTQz6skfikKE3.0FM0MCOwwiM1AyNzEzV}
pvn.college{gRWQCddh5Kdup1CUPz6slfikKE4.0FM0MDNwwiM1AzMyEzW}
pwm.bnllefe{gRWQCddh4Jdvp1CUQz6tlfijKE4.0EL0MDNxwiM0AzNzDzW}
pwm.bokkegd{gRWQBddh5Jdvp1CUQz6tlfikLE4.0FM0MDOxwiL1AzNyEzW}
pwm.bolldge{fQWPCcch4Jdvo1CUQz6tlfijLE4.0FL0LDOwwiM0AzNzEzV}
pwm.cnllefd{gRWQCcdg5Kcup0CTQz6skfikKE4.0FM0MDOxwiM0AyMzEyW}
pwm.cnllege{fRVQCddh5Kdvo0CUQz5tlfikLE4.0EL0MCOwviM1AzMzEzW}
pwm.cnllege{gRWPCddg5Kdvp1CUQz6tleikLE4.0FM0MDOxwhM0AyNzEzW}
pwm.colkegd{gQWQCddh4Kcvp1CTQz5tlfhkLE4.0FM0MDOxwiM1AzNzEzW}
pwm.colldfd{fRWQCddh5Jdvp1CUQy5slfhkLE3.0FM0MDNxwiM1AzNyDzV}
pwm.colldgd{fRWPCcdg4Kdup1CUPz5tlfhkLE4.0FM0MCOwwiM1AzNzEzW}
pwm.colldge{gRWQCddg5Kdvp1CUQz6tlfikLE4.0FM0MDOwwiM1AzNzEzW}
pwm.collefe{gRVPBddh5Kdvp1CUPz6tkfhjLE4.0FM0LCOxwiM1AzNzDzW}
pwm.collegd{gRWPBddh5Jcvp1CUPz5tlfikLE4.0EM0MDOxviL1AyNzEzW}
pwm.college{gRWQCddh5Jdvp1CUQz6tlfikKE4.0EM0MDOxwiM1AzNzEzW}
pwm.college{gRWQCddh5Kdvp1BUQz6tlfikLE4.0FM0MDOxwiM1AzNzEyW}
pwm.college{gRWQCddh5Kdvp1CUQz6tlfikLE4.0FM0LDOwwiM1AzNzEzW}
pwn.bnkldfe{gQWQCcch5Jduo1CUPz5tlfikLD4.0FM0LDOwwiL0AyMzDyW}
pwn.bolkdfe{gRWQCcdh4Jdup0CUQz5tleikLE3.0FM0MDOxwhM0AyNzDyV}
pwn.bollegd{gRVQCddg5Kdvp1CUQz6tkfikKD4.0FM0MCOxviM1AzNyDzV}
pwn.bollege{fRWQBddh5Kcuo1CUQy6tlehjKE3.0FL0MCOxwiM1AyNzEzW}
pwn.cnkkefd{fRWPCdch4Kdup1CUQy6tlfhjLD4.0FM0MDOwwiM1AzNzDzW}
pwn.cnkldfd{gRWQCddh5Kcvp1CUPz6tkfijLE4.0FM0MDOxwiM1AzNzEyV}
pwn.cnlkdfe{fRVPCcdg4Kdup1CUQy6tkehjLD3.0EM0LDOwwiM1AzMzDzW}
pwn.cnlkegd{gRWQBcdg5Kduo1BUPy5slfikKE4.0EM0LDNxviM0AzMzEzW}
pwn.cnlkege{gRWQCddh5Kdvp1CUQz5tlfikLE3.0FL0LDOwwiL1AzMzEyW}
pwn.cnlldfd{fRWQCcch5Jdup1BUQz6slfikLE4.0FL0MDNxwhM1AyNzEyW}
pwn.cnlldge{fRVQCddh5Jcup1BUQz6tlfikLE4.0FL0LDNxwiM1AzNzDzW}
pwn.cnllegd{gQVQCddh5Kdup1CUPz6skeikLE3.0EM0MDOxwhM1AzNzEzW}
pwn.cokldfe{gRVQCdch5Kcvp0BTPy6slfhkLE4.0EL0MDOxwiM0AzNzDzV}
pwn.coklefe{gRWQBddh5Kdup1CUQz6tkeijLE4.0FM0MCOwwiM1AzNyEzW}
pwn.coklege{gRWQBcdh5Kdup1BUQy6tkfikKE4.0FM0MDOxwiL1AzMzEzW}
pwn.colkdfe{gRWPCddh5Jdup1CUQz6slehjLD4.0FL0MDOxwiM1AzNyDyW}
pwn.colkdge{gRVQCddh5Kdvp1BTQz6tkfikLE4.0FL0LCNxwiM1AzNzEzW}
pwn.colkefe{gRWQBcdh5Kdup1CTQz6tlfijLE4.0FL0MDNxwiM1AyMyEzV}
pwn.colkegd{gQWQBddh5Jdup0CUQz5tkfhkLD4.0EM0MDOxwiM0AzNzEzV}
pwn.colkege{gRWQCcdh5Kduo1CUPz6tlfikLD4.0FM0MDOxviM0AyNzDzW}
pwn.colldge{fQWQBdch5Kdvp1BUQy6skfhkLE4.0FM0MCOxviM1AzNzEzW}
pwn.colldge{gRWQCdch5Kdvp1CUQz6tlfikLE4.0FM0MDOxwiM1AzNzEzW}
pwn.collefd{gRWQBdch4Jdvp1BTQy6tlfikLD4.0FM0MDOxwiM1AzNyEzW}
pwn.collefe{fRVQCcdh4Kdvo0CUQy6tleikKE4.0FM0MCOxwhL1AzNzEyV}
pwn.collefe{gRWPCddh4Kdvp1CUPz6tleijLE3.0FM0MDOxwiM1AzNzEzV}
pwn.collefe{gRWPCddh5Kdup0CUQz6tlfikLE4.0FM0MDOxwiM1AzNzEzV}
pwn.collefe{gRWQCddh5Jduo1CTPz5tlfijKE4.0FM0MCOwwiM1AzNzEzV}
pwn.collegd{gRWQCddg4Kdvp1CTQz6tlfikLE4.0FM0MDNxwiM1AzNzEyW}
pwn.college{gQWPCdcg5Jcvo1CTPz6tleikKD3.0EM0MDOxwiM1AyNzEzW}
pwn.college{gQWQCddh5Kdvp1CUQz6tlfikLE4.0FL0MDOxwiL1AzNzEzW}
pwn.college{gRVPBcdh5Jdvp1CUQz6tlfikLE3.0FM0MDOxwiM1AzNzEzW}
pwn.college{gRVQBddh4Kdvp0CUQz6tlfhkLD4.0FM0MDOxwhM1AzNyEzV}
pwn.college{gRVQCddh5Kdvp1CTQz6tlfikLE4.0FM0MDOxwiM1AzNzEzW}
pwn.college{gRWPCddh5Kdvp1BUQz6tlfikLE4.0FL0MDOxwiM1AzNzEzW}
pwn.college{gRWPCddh5Kdvp1BUQz6tlfikLE4.0FM0LDOxwiM1AyNzEzW}
pwn.college{gRWQBcdh5Kdvp1CUQz6tlfikKE4.0FM0MDOxwiM1AzNyDzW}
pwn.college{gRWQBddh5Kdvp1CUQz6tkeikLD4.0FM0MCOxwiM1AzNzDzW}
pwn.college{gRWQCcdh5Kdvp1CUQz6tlfikLE4.0FM0MDOxwiL1AzNzEzW}
pwn.college{gRWQCdch5Kdvp1CUQz6tlfhkLE4.0FM0MDOxwiM1AzNzEzW}
pwn.college{gRWQCddh5Kdup1CUQz6tlfikLE4.0FM0MDOxwiM1AzNyEzW}
pwn.college{gRWQCddh5Kdvo1CUQz5tlfikLE4.0FM0MDNxwiM1AzNzEzW}
pwn.college{gRWQCddh5Kdvp1BUQz6tlfijKE4.0FM0MDOxwiM1AzNyEzW}
pwn.college{gRWQCddh5Kdvp1CUQz6slfikLE4.0FM0MDOxwiM1AzNzEzW}
pwn.college{gRWQCddh5Kdvp1CUQz6tlfhkLE4.0FM0MDNxwiM1AzNzDzW}
pwn.college{gRWQCddh5Kdvp1CUQz6tlfikLE4.0FM0LDOxwiM1AzNzEzW}
pwn.college{gRWQCddh5Kdvp1CUQz6tlfikLE4.0FM0MDOxwiM1AzNzEyW}
pwn.college{gRWQCddh5Kdvp1CUQz6tlfikLE4.0FM0MDOxwiM1AzNzEzW}
```

## What I Learnt
I learnt about the sort command, which by it's name, sorts the data. By default, sort orders lines alphabetically. However, we can use arguments to change this like -r: reverse order (Z to A), -n: numeric sort (for numbers), -u: unique lines only (remove duplicates), -R: random order.

## References
The reference I used is the instructions provided by the pwn.college.
