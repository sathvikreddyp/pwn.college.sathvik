# 1. Listing Processes
In this challenge, they told that they renamed challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory. But they also launched it, so we can find it in the running process list, figure out the filename, and relaunch it directly for the flag. 

## My Solve
Flag: pwn.college{wCkbOG0pKYhquaAxm3RP9BlVXze.QX4MDO0wiM1AzNzEzW}

First I used ps -efww and directed the output of it to grep challenge command to list out the processes of those which contains only challenge word. Then I launched it to get the flag.

```
hacker@processes~listing-processes:~$ ps -efww | grep challenge
root         132       1  0 05:15 ?        00:00:00 /challenge/13180-run-10777
hacker       167     155  0 05:18 pts/0    00:00:00 grep --color=auto challenge
hacker@processes~listing-processes:~$ /challenge/13180-run-10777
Yahaha, you found me! Here is your flag:
pwn.college{wCkbOG0pKYhquaAxm3RP9BlVXze.QX4MDO0wiM1AzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

## What I Learnt
I learnt about the ps command, which lists processes. By default, ps just lists the processes running in your terminal. However to make it useful (only processes running in your terminal isn't that useful), we can use either the -ef command or aux command. There are 2 syntax:
1)Standard Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.
2) BSD Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux
These two methods, ps -ef and ps aux, result in slightly different, but cross-recognizable output.

## References
The references I used are the instructions provided by the pwn.college. 

# 2. Killing Processes
In this challenge, they they told that /challenge/run will refuse to run while /challenge/dont_run is running. We must find the dont_run process and kill it, then run /challenge/run to get the flag. 

## My Solve
Flag: pwn.college{sygP8--5Y9Dw0v8zEEh29ONPSA5.QXyQDO0wiM1AzNzEzW}

I first used the ps command with -ef argument, then connected that output with "grep dont_run" command, to find the /challenge/dont_run process. I found out the PID of that process, then I used the kill command to terminate the process. I then ran /challenge/run to get the flag. 

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

## What I Learnt
I learnt about the kill command, which will terminate a process when we pass the PID of the process as the argument. 

## References
The references I used are the instructions provided by the pwn.college. 

# 3. Interrupting Processes
In this challenge, they they told that /challenge/run will refuse to give the flag until we interrupt it.  

## My Solve
Flag: pwn.college{spaedAQgp8mPRZQJFZjdu0fL87a.QXzQDO0wiM1AzNzEzW}

I ran /challenge/run and then after clicking enter, I used ctrl-c, with which i got the flag.  

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{spaedAQgp8mPRZQJFZjdu0fL87a.QXzQDO0wiM1AzNzEzW}
```

## What I Learnt
I learnt about how we can interrupt a process using ctrl-c. Ctrl-c sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

## References
The references I used are the instructions provided by the pwn.college. 

# 4. Killing Misbehaving Processes
In this challenge, they they told that there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which /challenge/run wants to write your flag. We need to kill this process, then run /challenge/run to get the flag without being overwhelmed by decoys (we don't need to redirect its output; it'll write to the FIFO on its own).

## My Solve
Flag: pwn.college{MWCo5ciAtEuvhlp_b5jdwCR0U6O.0FNzMDOxwiM1AzNzEzW}

I firts ran the ps -ef command to list out all the processes. Then I found the /challenge/decoy process and killed it using kill comand. Then I ran /challenge/run, which sent the flag to /tmp/flag_fifo. Then i read the /tmp/flag_fifo file to get the flag.  

```
hacker@processes~killing-misbehaving-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 14:44 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-i
root           7       1  0 14:44 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 14:44 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 14:44 ?        00:00:00 /bin/bash /challenge/.init
root         139       1  0 14:44 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140     138  0 14:44 ?        00:00:00 sleep 6h
root         141     137  0 14:44 ?        00:00:00 sleep 6h
hacker       142     139  0 14:44 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       144       0  0 14:45 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/
hacker       150     144  0 14:45 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       160     150  0 14:45 pts/0    00:00:00 ps -ef
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{.Wxyq-u4VUWMbyyGTIYNNWxkrKzJV9kDF76n.R4ZOed5.CB}
pwn.college{umHCQJAfOhRPLSizZxXEEP5ZYDAjAC.Nd5x3s.9wNzQre93}
pwn.college{kZU06tfjv43x2K9qMz-uiN76E07ntqC64H6A2qipHoOEgM2}
pwn.college{Cc0dpukntwFZbcCfsztiRK82gzFx4g3RLxleg74X0q2h7.s}
pwn.college{sRrpQZcst5d-rUMUxTunORUu41JPlTFO9PJjoDGH8CmEwdB}
pwn.college{kbVkdaLZUxrSSKUWAafGHNINN6Q-I9sy67Km3nzhZYdiZvL}
pwn.college{iZtBwNDcCnz13QIPRH97fh5TVD0EbKvngyKCG-ATK8BKltq}
pwn.college{DicXOWg2di56BO7DXGITqtvvNAqPKwtxcRj8ZG1GHmhY7H2}
pwn.college{8eSxhlSpRRohiR7haOgfMODqpIY5cOomR-8ryJLucCMmjeb}
pwn.college{QWlWuWsMmKi8.RgimCv8ZU7XmPzQk4UUBvsOFZ1CLZddnn5}
pwn.college{eXKkgKSdfCdD9qHF6zuIRcMslry3yhwRtAaf24PxDUKXPSJ}
pwn.college{c4vDl0Z4Y.3PahVZuXpsaQlV29ugfanZDXMkjLIDx-lErS.}
pwn.college{KXtIIrVODyyfIj3eMrxjG7lxJrFzkQ8.-.ocpGfHsIee75X}
pwn.college{rjcpG4Bmrsqq0wpu3l1RREHTHxOCL0eKsqwmNTqn8Sw6pO-}
pwn.college{g.CvxZUgd-6-4ZRHIc5cYiaFVA-8WMLwzLknFiS8jSAHUq6}
pwn.college{TCtcl1AJJ24S6Ygok4b-tJWKKeahW7EHj-hAiwcLGJ9ga3H}
pwn.college{FBVQtp4ku.L3FMxBmkQBlrDi0l4I0CfZVrlncOTt6kAPlVa}
pwn.college{a6IvgyAFXL8VbJ00N-js.oOO91q14JhAcTPZMrWBss1.lpo}
pwn.college{CZZDEJxgGCVTrMYNUVpETafSo0vVArA2l1q6yq7Cg1rBB7l}
pwn.college{x22KVfGfL.-D3ENKYUBWWo2VmWy8pnfE.MSA4HQiZHeaPph}
pwn.college{POl361NUNxsXKwCnv7U5rNQnMkWqvFJbSfZ2BXfWm9dW3zn}
pwn.college{To9ngE8Fb8ptmpj128.UybbeQBjHQjoiF6sZkV5y2362GZf}
pwn.college{JYtFG8ybNHdK6jYhxs53iOGvlffFNAztolw6yvdprdIxnaE}
pwn.college{jv4wozBwdDx.SUalR.GGAuzP6eZcQ6re9sVHR4e6BL9Zd80}
pwn.college{MGlhgq7Y2g9AOW.NAWf2MxkOr8TRg1sIxen2rQSeO9xCLzf}
pwn.college{opvjJ8Qf-0Nzt1esA6wZ6S7axg6KmMVhEo-A72Hol1-iCTN}
pwn.college{y.A8D1uvdrX-wVRrqexdzBzkbb-hr70NXSOFR.smj1WfVhJ}
pwn.college{Roc2Z-mYip7aM670jeIbSaZ7JSGdDwQ.TuzQu-1CBUG8qnE}
pwn.college{3vNg-6-0zKxXKfyHXwZWBQ7FBeCTVF8fQckgyIFu4l.kKHr}
pwn.college{zyLN.ohk5NgIlMOQaSz6CIuWGiDncAMiO2HaQLdYfIVxNEA}
pwn.college{7nK7YpW7pjO8ClZ2nCaIYohakveSaHtLJzEb-KUNYdqXacg}
pwn.college{ncLI8rF4p8J8nYkPbDVpcmonU6iCg6r4vbWXeW7WexK1vAs}
pwn.college{lrAf7NE5gg56pVMVu0cb-BY0v5zjohz.hUwZZ8TzTB4rs1f}
pwn.college{RzsDfqaSDlsMnw8HsmjYI8kbrd4QifZnSLJO1HTGDlsF7Q8}
pwn.college{TVzg.XP4mt0KJKEyBsmHtnVpoYFiXhoCKPfjBp2hu3xiroe}
pwn.college{q-tEGSASznwGZiiYv4JIzcVtfxWbqRcz1ExNQIKENyS0BB3}
pwn.college{eVTFzP81e-nVTZpCV9p.2luVIMfBD6CZ-LeGpAmwqb4fG6U}
pwn.college{0ClZm0dUpwZ4I4lP1xCGHJ03AQFDQLRa0Oh2DZlyCniGvWL}
pwn.college{EdEm2ZOECnb.CD9WtN.LI8O4mbStUwObLx38sf0sI27RhXr}
pwn.college{XvuiVcynHihGEHhnL69BpVPTsieaD4i-9vlkidgFgbaaZmn}
pwn.college{3AmMKwtrW-lJKpp-iOXk4NMYPPSnqNJTB7gMcoIftb.zfcX}
pwn.college{41iYSgn0fInZ1wgrqO4LbPzNURMdQRnzItuPMaAhVfwsu7L}
pwn.college{IPaVx9RGD1u.jWzguOvgJ.ltGzvftuzj1O38gv8A-7B0YnX}
pwn.college{.2BcOoOzoEaZvTr8Tdgii0S3OGnH0FBZiLw.V.5uAznAFl-}
pwn.college{fDabb8dTW5cUblZRuCA0ERTxU02H1xX6RgAXgLvwaKxyFuw}
pwn.college{HOm0Fb5UTlBJKuUYbae2DhZ65Z3KN1Rcc6MgEn1iz34bUU9}
pwn.college{sOWTZw6ICc4IfN2i7qr5btrBq1p7F.96zYR4kQQ20jyaEDK}
pwn.college{F9zMlnjFx3M-BEbRE3z3JfeaZQ-VBY37c3RV-n-u2Ddmf1f}
pwn.college{18FR50eCvVlosMOpU3KjBMd.xmYP43vRNeCLxazDG.XiIUG}
pwn.college{JLPQPdhmVDhp3ykPRhqsEIG9PAJYqkniju-hDybfxglDiXs}
pwn.college{fT0okfs5JZUZ2Ei9flNBd28O7w2zLh07Xfu4M4rDPLtLt-J}
pwn.college{5jQbwuG97ceLj2mpyh3Ec2mVXUTPZqw2fbL4ZdFduIjt8ua}
pwn.college{zlgxvPMWguH5hlnK-vwQIXATswXy12r5g551h7V3JDp3ARz}
pwn.college{G7Upft00vyQpH.wKrVqZyVJrESjW6yTon-FmzTn7bUiuRoa}
pwn.college{TpBD-LwqGfYtQcekhH8UN89xLv3xJdbuT4ucUwGiBjbhITw}
pwn.college{nrcT.t782UPkBKiTV1m3yl-ALjugodqjT8XS6wXFR5bv410}
pwn.college{maIWzkN3GOkWP4DK9yLJcDt4esEhDsOyCOLql7GVkRSe68K}
pwn.college{oAYYznXp6tk9uEWF.bkaGuaYbOI6HWvaIOnjUc2Xe29sqIX}
pwn.college{Ia9ioHcatjZxPek2jmJBsilcTTEyIocDhSmsMuS1Kx54RtD}
pwn.college{Y67ptKjH-Ot0lIbOACGSZT5E9pYoewCj80BxAReQy9-5dyU}
pwn.college{QIwVa7MR8oYCIPkNldsm5DEhmG70ZUMoYOoueRBEApMkEJu}
pwn.college{ryf770wIEf-dVxIRV8WY.nN2iwLkl1jCv3h.lGKwy34GHeh}
pwn.college{vEtmTuAON5U0PJpreOsJuvfQUElwJqrYNESTTD4d9JXcNXC}
pwn.college{1.Kjwigi0nM5XtAS0.SQKYB1fkX6XAAxjxUu8iq.cX2wcR.}
pwn.college{fXCkkkgy.rQUpDOa.DjmaB-OLq-3Lxwr3Yhsf4BAYZ1Slb1}
pwn.college{5supEX8zMUk9Z7rULx9U6cdYsw7CXzOIw2TUbMZ1Ujhe8oq}
pwn.college{0jp0o5wC.krirjaCRjTSe4g2F5F83gf0X.lCoDlJrS8CDeZ}
pwn.college{-TWG3XTXzjK.TgneVaGqtUAKi4AYCl7bAsY-JkTgtKM6e9M}
pwn.college{V0A4C9so6lEHOIeCQAQdqPtqawyskCRbwRK8RbHrW9RcD8-}
pwn.college{eB90eNgNsoRiHJacQtL9OIsbu-ifqBuN9W0AqMsnb7Bi7TR}
pwn.college{fSJYywilqEB6nvVXc-Kp4SMZ7VniArs0YpJjVhSJ61uw0G6}
pwn.college{MP-92Id5ZlZMLhv5TnuTUJcp.CyyKmRsCBTSD8fzYZgVal2}
pwn.college{0XLjxDT6XqNycC7W7s-vGqsT9tHNTVWxmPgf-Dt-eoov8O0}
pwn.college{fIbGaSixl6a37fSpdNJz35xRfmacNpjhRmeEDfko-GDBV4C}
pwn.college{QLa.XincuJ4wrz787R5R4nuVc8bp94i248ACUx9tzaQMvG3}
pwn.college{XzmkA0qcPaffc7C-JOyPYtb2LA3-PAQL8sUePu.p7VebTiu}
pwn.college{fDnIEYVo8FatKpTeatRzI4WE2vWjRUp0Ow9BcwnPUhS0-fx}
pwn.college{VAFP2JalTNhDW3WcjDZj2qrSLcqajbY6mZrebyfeccizpqo}
pwn.college{bhbf1PsZItH3-myrBzWKcb.YdwZquuhlO6Ap2KXYNUtTRx2}
pwn.college{gxGgNSyspGsIE7RiYdYQxlOEf9wcnJqIsT2TIDFIZuzByBW}
pwn.college{qWcvna4eAlfOzgNkauDPKzVtYGOe7t8GKYMXyeIS9DfWbBo}
pwn.college{.zyvWLJLuLHAr.AsL42l52b4HnHOB4ixhMhnaMEpCAw82Il}
pwn.college{PnJF8hQmkgZQ1JLPj72Qlzn6ypt3bAfKqBHHCPy-b.DFEsu}
pwn.college{N4SAuv5Yo0HUUOduWGEH-aYZ5rOd2RK3df1zwrLbkv.WKGN}
pwn.college{5uOg5DEuN8BnIR2vmXVQfRFrGY6QefgOK27yAb.o4-C3xeT}
pwn.college{l-jjAXwSqld.jj1j1zZxzbgYteIkDtou9U9FQC6yfE48W0D}
pwn.college{ZzVTQXh55rJXcDvWTGllEW7j-P.dBVoZuXPp5Ue2TSdwphU}
pwn.college{J.P4xbNInS1ucSfSGsQoUs6EdgAqTvUpbSTLZtJQDbphUVh}
pwn.college{v6sfzcJ5XotFUTtiWzPxyCqzt01ysBsiVJub54RRz9vFOtz}
pwn.college{Q3M09TuO9UvVxvP1IoHlQY6msNuY8p7xqzCMO7POLzog4.x}
pwn.college{TdRwAp9NN91tWzYXku4howCXdMpBw0fO-Ubh3ejYRkoHtKj}
pwn.college{jJz6Czc6owjX1RetCP6h2Ep.WKDQk.17rQg8rUU-yu3NNJO}
pwn.college{s7VFuAL3oQJ5PxD8gJJ5RoNfMSCxO-wsH8iAPL-zTa8RTDC}
pwn.college{47PWQeiRbpxEgYkyoZNRt64dCAKRpBZgvXs0UrP9NqpqBjd}
pwn.college{BJud8WDIwmeFUvqDcCdn4LKnZu2Bt06osTJ92u1uUoTHo4N}
pwn.college{BbNTe1JQHM5pW7GxGjc0gH4GVO2xBCIVwW.LCj.AvVaGeUW}
pwn.college{pMYa-aEKxa5GdGHQZLfv3SFacSAC2cl2VJK-m5x6TTubWka}
pwn.college{L95qYRaN7zqCRB2AW-vrXVskUVXC.EhbC.R7WUYW-vFAkjH}
pwn.college{eKLGHXcMVs0WQ.P-v8aZRTqm6vkDXb5mz5uWMD4Qa2b7GLK}
pwn.college{SPWjgjw03Cqx5LJtb0Lt2Jcpdp7HFrO4u749CEJI3Bd853X}
pwn.college{i7pIWUMKgcaqebxOfIO93o-NVcI4nJv32O7eKAqKzPCvIS2}
pwn.college{.S1AFiC8Wo5BV0K7oY3.9sVL4we6wW2jVCSZYwrjK1474Yc}
pwn.college{mp0-OVO4SApmengRUZ3LtIDVbOO66jl7lWmlP9qZ78MpMGI}
pwn.college{O6CSZy-2.D7c81vhiN3maYfCtlsgQt.Loor5FtinHBoT-yC}
pwn.college{EQJsnaRik8AuTeVhC2tzgOISU8RC18QR3RVkX.p15eMGuDd}
pwn.college{C7UqKx0mufb7a6ziOXotWTj.MZg5gDvthSg29yIfym9Tnd4}
pwn.college{zvC4WJOdDj3FRDrwMpDLwIMnujypQ0gN9AnnYcSYMebPdKE}
pwn.college{Mk7r6ZeeAxveT.ETCdqOl8uJ943saKqNsGczaKXKQpNweNP}
pwn.college{TToX2RGkgnyO55YQ6r-RPSh-GYFrM23iRZ6aM-4VTrZmIMy}
pwn.college{Pv5VkCJy-vJR5saa9fQ1DSrPOtx05zMIR3W6xXibe3A39Mk}
pwn.college{MCccl8WHOM9gB4LU0cveHZhy4K3BwM8szd-A60loObmwXkq}
pwn.college{t7TAQuoWMTfmNKyK6F7oFWQlgCL7ZA14Xrgh0UP4bzK7oNy}
pwn.college{z9X1MOa9NrmyJhjscLuqOc3DOd6BL1Qcqs.Dy-7Dl2d1...}
pwn.college{XLO6o7t44i5TkFGDow6fjhp15LM51pZQGyME25hogZNNjXP}
pwn.college{lh1T4DLcprWGWJfCpJpHoYh2IXISCRnBhoSw8hCS.2yLyv7}
pwn.college{Yx4Kc1v39aMnxKWjVvLkQrS28n6oh9rCIhfezOsYohPLhQp}
pwn.college{7kLFbzqbV8RtMswgNuFKJ4mHsHy32KpI0eaKfxYPSIycp-1}
pwn.college{yTMgStkW6J9RmrLfnwD86QZo1Z.rWvuX-kCw4C7rMI4oeBz}
pwn.college{rLEXw5BNE5JUXaDXRqinM9a70VSLP8QkKISQpTUGYNFDRbJ}
pwn.college{Pd.CNPKUU2Ezl4CRyyHjRll7ZokEN.nh-ZC3X.MJPnEhV8s}
pwn.college{W19EFA9ccPRcHJaUvqyMq.RqrLESgKt7sJ9qRg2TBibLInB}
pwn.college{s6HRXzu82vkswyIonuREszKmEcWeuim6VIdhEMpg.ZA6NCv}
pwn.college{zaF-dSXrjT53hZi0s.cGpJBSeIEKMGbVPeHM5150B7YaqOO}
pwn.college{LXWDjFaz3gBUenYlVHvKPICBC1Zw46JMjgsiMMig9vYG5bK}
pwn.college{uhhm8jNLpGaEEPWWEzcXnVLjMSK.oQyti-XuVe7cJAZF7EF}
pwn.college{FUpKgTkORPrUzN4OPy9BLb.wVN3O-Y8I3TJrTOVepfhqw8e}
pwn.college{CCmVicNd0J-Uhp.ofqbW4ogqH1lzTTHqi5-D6E3Fjm.9NaI}
pwn.college{yIQYf0tJtHW0TPmU-mtyAqg4dE4J6cHr5UZiNZ-PzJMnc4n}
pwn.college{lT5kWz3N5-pzTViAGRxPFQ9CANlxk4PTVRT2MZDBCkYBT7S}
pwn.college{jfudSUIfDtCzP.Bckbeu0JaRt21KjcDdWxOZFi9AI3idyFh}
pwn.college{2wXrTQpjFzcjULj2h-Ak590fLFOF6YGk8B9Ze7BdShg2oHW}
pwn.college{HOgKyPVixbw0XvzhlLGPP94dnhMVoMEmQbOU9boNWtxDzSG}
pwn.college{4QaQ2SalraijACf6DUdg27AEfFhssi8fHZFKCbHl9itkJ-8}
pwn.college{tn7DC38tVdHKOQMGVcTOM7kTGtzzrZS-zj4dE4O8ntn1e21}
pwn.college{MWCo5ciAtEuvhlp_b5jdwCR0U6O.0FNzMDOxwiM1AzNzEzW}
```

## What I Learnt
I learnt how to use the ps and kill command effectively.

## References
The references I used are the instructions provided by the pwn.college. 

# 5. Suspending Processes
In this challenge, they told that this level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended.

## My Solve
Flag: pwn.college{kqdgceWyAzV7YtTL_dcDUwe6EqE.QX1QDO0wiM1AzNzEzW}

I first ran /challenge/run, then I clicked ctrl-z to suspend the process. Then I ran /challenge/run again to get the flag.

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         153     136  0 14:51 pts/0    00:00:00 bash /challenge/run
root         155     153  0 14:51 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ ^C
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         153     136  0 14:51 pts/0    00:00:00 bash /challenge/run
root         161     136  0 14:52 pts/0    00:00:00 bash /challenge/run
root         163     161  0 14:52 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{kqdgceWyAzV7YtTL_dcDUwe6EqE.QX1QDO0wiM1AzNzEzW}
```

## What I Learnt
I learned that we can suspend processes to the background using ctrl-z.

## References
The references I used are the instructions provided by the pwn.college. 

# 6. Resuming Processes
In this challenge, they told that this challenge's run needs you to suspend it, then resume it to get the flag.

## My Solve
Flag: pwn.college{UvaGxcaXDFyHO2PiAl0zpjNsGd7.QX2QDO0wiM1AzNzEzW}

I first ran /challenge/run process, then I suspended it with ctrl-z. I then resumed the process using fg command with the process as argument and got the flag.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{UvaGxcaXDFyHO2PiAl0zpjNsGd7.QX2QDO0wiM1AzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

## What I Learnt
I learned about the fg command, which is a builtin hat takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

## References
The references I used are the instructions provided by the pwn.college. 

# 7. Backgrounding Processes
In this challenge, they told that this challenge's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background.

## My Solve
Flag: pwn.college{YDnwe1YyaT5-xjuhMbzxzUTEU42.QX3QDO0wiM1AzNzEzW}

I first ran /challenge/run, then suspended the process with ctrl-z. Then I ran it in the background using the bg command and then ran the process again in the shell commandline to get the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S+   bash /challenge/run
root         140 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S    bash /challenge/run
root         148 S    sleep 6h
root         149 S+   bash /challenge/run
root         151 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{YDnwe1YyaT5-xjuhMbzxzUTEU42.QX3QDO0wiM1AzNzEzW}
```

## What I Learnt
I learned about the bg command, which will basically resume the process like fg, but in the background, while fg will resume it in the foreground. This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

## References
The references I used are the instructions provided by the pwn.college. 

# 8. Foregrounding Processes
In this challenge, they told that this challenge's run process should first be suspended, then resumed in the background, then it has to be brought to the foreground without suspending it.

## My Solve
Flag: pwn.college{Qusz1PcTXOAXrikftrEU9y09Sjx.QX4QDO0wiM1AzNzEzW}

I first ran /challenge/run, it then showed me what I should do to get the flag. I first clicked ctrl-z to suspend the run process. Then I resumed it in the background using the bg command. I then brought it to the foreground using the fg command.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{Qusz1PcTXOAXrikftrEU9y09Sjx.QX4QDO0wiM1AzNzEzW}
```

## What I Learnt
I learned that we can foreground a backgrounded process with fg, just like how we foreground a suspended process.

## References
The references I used are the instructions provided by the pwn.college. 

# 9. Starting Background Processes
In this challenge, they told that this challenge's run process should be launched backgrounded to get the flag.

## My Solve
Flag: pwn.college{oGlYlmLEVRRCbXikZMwER5yxfYV.QX5QDO0wiM1AzNzEzW}

I ran /challenge/run process, appended with "&", so that it will be backgrounded.

```
hacker@processes~starting-backgrounded-processes:~$  /challenge/run &
[1] 141
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{oGlYlmLEVRRCbXikZMwER5yxfYV.QX5QDO0wiM1AzNzEzW}
```

## What I Learnt
I learned that we dont have to suspend a process to background them like previous challenges, we can start/launch them backgrounded by appending the command with "&".

## References
The references I used are the instructions provided by the pwn.college. 

# 10. Process Exit Codes
In this challenge, they told that we must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument to get the flag.

## My Solve
Flag: pwn.college{8qY8XTofkOH7rdxUFe6P7nL6cpK.QX5YDO1wiM1AzNzEzW}

I first ran /challenge/get-code. Then i read the exit code of the command using the "?" variable with echo command (echo $?). We have to use "$" because "?" is a variable. I then got the error code, which was 40, then i ran /challenge/submit-code with 40 as argument to get the flag.


```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
16
hacker@processes~process-exit-codes:~$ /challenge/submit-code 16
CORRECT! Here is your flag:
pwn.college{8qY8XTofkOH7rdxUFe6P7nL6cpK.QX5YDO1wiM1AzNzEzW}
```

## What I Learnt
I learned how we can access the error codes of of the most recently-terminated command using the special "?" variable (don't forget to prepend it with "$" to read its value).

## References
The references I used are the instructions provided by the pwn.college. 
