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
In this challenge, ls command was introduced. The '/challenge/run' was given a random name and kept in '/challenge' directory. We had to run the renamed program to get the flag.

## My Solve
Flag: pwn.college{8zEC0_bfYZD0rnj6WEAajAAgnj-.QX4IDO0wiM1AzNzEzW}

I first read all the components of the /challenge directory with the ls command. Once executed, I received two names, "4359-renamed-run-5690" "DESCRIPTION.md". Assuming that "4359-renamed-run-5690" is a file, I tried reading it with the cat command. I didn't recieve the flag, which means it is a program. I ran it as is and recieved the flag.

 ```
hacker@commands~listing-files:~$ ls /challenge
7703-renamed-run-1116  DESCRIPTION.md
hacker@commands~listing-files:~$ cat /challenge/7703-renamed-run-1116
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:~$ /challenge/7703-renamed-run-1116
Yahaha, you found me! Here is your flag:
pwn.college{8zEC0_bfYZD0rnj6WEAajAAgnj-.QX4IDO0wiM1AzNzEzW}
```
## What I learnt 
I have learnt the use and execution of the ls command. It is used to list all the components of a given directory to find their names.

## References
The references were the instructions provided by the pwn.college.

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
In this challenge, we are to retrieve the flag following a list of clues hidden in various files and directories using the cd, ls and cat commands.

## My Solve
Flag: pwn.college{AHW5jWIo_pQ5MusG7-fd6Hyh7T-.QX5IDO0wiM1AzNzEzW}

I have performed the following commands to retrieve the flag:

```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
TIP  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin  challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat TIP
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/drivers/gpu/drm/nouveau/nvkm/subdev

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ cd  /opt/linux/linux-5.4/drivers/gpu/drm/nouveau/nvkm/subdev
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/nouveau/nvkm/subdev$ ls
Kbuild  bios  clk      fault  fuse  gsp  ibus      instmem  mc   mxm  pmu      therm  top
bar     bus   devinit  fb     gpio  i2c  iccsense  ltc      mmu  pci  secboot  timer  volt
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/nouveau/nvkm/subdev$ ls -a
.   .NOTE   bar   bus  devinit  fb    gpio  i2c   iccsense  ltc  mmu  pci  secboot  timer  volt
..  Kbuild  bios  clk  fault    fuse  gsp   ibus  instmem   mc   mxm  pmu  therm    top
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/nouveau/nvkm/subdev$ cat  .NOTE
Tubular find!
The next clue is in: /usr/share/icons/Adwaita/512x512/mimetypes
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/nouveau/nvkm/subdev$ cd  /usr/share/icons/Adwaita/512x512/mimetypes
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ Adwaita/512x512/mimetypes
bash: Adwaita/512x512/mimetypes: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ cat Adwaita/512x512/mimetypes
cat: Adwaita/512x512/mimetypes: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ ls
ALERT  application-x-executable.png  text-x-preview.png  x-office-presentation.png
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ ALERT
bash: ALERT: command not found
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ cd ALERT
bash: cd: ALERT: Not a directory
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ cat ALERT
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/scipy/optimize/tests

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/icons/Adwaita/512x512/mimetypes$ cd  /usr/lib/python3/dist-packages/scipy/optimize/tests
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ ls
BLUEPRINT                        test_constraint_conversion.py     test_minpack.py
__init__.py                      test_constraints.py               test_nnls.py
__pycache__                      test_cython_optimize.py           test_nonlin.py
test__basinhopping.py            test_differentiable_functions.py  test_optimize.py
test__differential_evolution.py  test_hessian_update_strategy.py   test_regression.py
test__dual_annealing.py          test_hungarian.py                 test_slsqp.py
test__linprog_clean_inputs.py    test_lbfgsb_hessinv.py            test_tnc.py
test__numdiff.py                 test_least_squares.py             test_trustregion.py
test__remove_redundancy.py       test_linesearch.py                test_trustregion_exact.py
test__root.py                    test_linprog.py                   test_trustregion_krylov.py
test__shgo.py                    test_lsq_common.py                test_zeros.py
test__spectral.py                test_lsq_linear.py
test_cobyla.py                   test_minimize_constrained.py
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ cat BLUEPRINT
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/timer

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ ls  /opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/timer
LEAD-TRAPPED  stm32-lptimer-trigger.txt  stm32-timer-trigger.txt
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ cat  /opt/linux/linux-5.4/Documentation/devicetree/bindings/iio/timer/LEAD-TRAPPED
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/drivers/irqchip

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ ls  /opt/linux/linux-5.4/drivers/irqchip
Kconfig                     irq-digicolor.c                irq-ls1x.c                 irq-sa11x0.c
Makefile                    irq-dw-apb-ictl.c              irq-madera.c               irq-sifive-plic.c
NUGGET-TRAPPED              irq-eznps.c                    irq-mbigen.c               irq-sirfsoc.c
alphascale_asm9260-icoll.h  irq-ftintc010.c                irq-meson-gpio.c           irq-sni-exiu.c
built-in.a                  irq-gic-common.c               irq-mips-cpu.c             irq-st.c
exynos-combiner.c           irq-gic-common.h               irq-mips-gic.c             irq-stm32-exti.c
irq-al-fic.c                irq-gic-pm.c                   irq-mmp.c                  irq-sun4i.c
irq-alpine-msi.c            irq-gic-realview.c             irq-mscc-ocelot.c          irq-sunxi-nmi.c
irq-armada-370-xp.c         irq-gic-v2m.c                  irq-mtk-cirq.c             irq-tango.c
irq-aspeed-i2c-ic.c         irq-gic-v3-its-fsl-mc-msi.c    irq-mtk-sysirq.c           irq-tb10x.c
irq-aspeed-vic.c            irq-gic-v3-its-pci-msi.c       irq-mvebu-gicp.c           irq-tegra.c
irq-ath79-cpu.c             irq-gic-v3-its-platform-msi.c  irq-mvebu-icu.c            irq-ti-sci-inta.c
irq-ath79-misc.c            irq-gic-v3-its.c               irq-mvebu-odmi.c           irq-ti-sci-intr.c
irq-ativic32.c              irq-gic-v3-mbi.c               irq-mvebu-pic.c            irq-ts4800.c
irq-atmel-aic-common.c      irq-gic-v3.c                   irq-mvebu-sei.c            irq-uniphier-aidet.c
irq-atmel-aic-common.h      irq-gic-v4.c                   irq-mxs.c                  irq-versatile-fpga.c
irq-atmel-aic.c             irq-gic.c                      irq-nvic.c                 irq-vf610-mscm-ir.c
irq-atmel-aic5.c            irq-goldfish-pic.c             irq-omap-intc.c            irq-vic.c
irq-bcm2835.c               irq-hip04.c                    irq-ompic.c                irq-vt8500.c
irq-bcm2836.c               irq-i8259.c                    irq-or1k-pic.c             irq-xilinx-intc.c
irq-bcm6345-l1.c            irq-imgpdc.c                   irq-orion.c                irq-xtensa-mx.c
irq-bcm7038-l1.c            irq-imx-gpcv2.c                irq-partition-percpu.c     irq-xtensa-pic.c
irq-bcm7120-l2.c            irq-imx-irqsteer.c             irq-pic32-evic.c           irq-zevio.c
irq-brcmstb-l2.c            irq-ingenic-tcu.c              irq-rda-intc.c             irqchip.c
irq-clps711x.c              irq-ingenic.c                  irq-renesas-h8300h.c       qcom-irq-combiner.c
irq-crossbar.c              irq-ixp4xx.c                   irq-renesas-h8s.c          qcom-pdc.c
irq-csky-apb-intc.c         irq-jcore-aic.c                irq-renesas-intc-irqpin.c  spear-shirq.c
irq-csky-mpintc.c           irq-keystone.c                 irq-renesas-irqc.c
irq-davinci-aintc.c         irq-lpc32xx.c                  irq-renesas-rza1.c
irq-davinci-cp-intc.c       irq-ls-scfg-msi.c              irq-s3c24xx.c
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ cat /opt/linux/linux-5.4/drivers/irqchip/NUGGET-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/local/lib/python3.8/dist-packages/setuptools/_vendor/importlib_resources/tests/namespacedata01/subdirectory
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/scipy/optimize/tests$ cd  /usr/local/lib/python3.8/dist-packages/setuptools/_vendor/importlib_resources/tests/namespacedata01/subdirectory
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/_vendor/importlib_resources/tests/namespacedata01/subdirectory$ ls
DOSSIER  binary.file
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/_vendor/importlib_resources/tests/namespacedata01/subdirectory$ cat DOSSIER
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/arch/h8300/include/uapi/asm

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/setuptools/_vendor/importlib_resources/tests/namespacedata01/subdirectory$ cd  /opt/linux/linux-5.4/arch/h8300/include/uapi/asm
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi/asm$ ls
CLUE  Kbuild  bitsperlong.h  byteorder.h  ptrace.h  sigcontext.h  signal.h  unistd.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi/asm$ cat CLUE
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/arch/m68k/coldfire

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi/asm$ ls  /opt/linux/linux-5.4/arch/m68k/coldfire
Makefile            clk.c        entry.S    intc-2.c     intc-simr.c  m523x.c  m527x.c  m5407.c    nettel.c  sltimers.c
REVELATION-TRAPPED  device.c     firebee.c  intc-5249.c  intc.c       m5249.c  m528x.c  m5441x.c   pci.c     stmark2.c
amcore.c            dma.c        gpio.c     intc-525x.c  m5206.c      m525x.c  m5307.c  m54xx.c    pit.c     timers.c
cache.c             dma_timer.c  head.S     intc-5272.c  m520x.c      m5272.c  m53xx.c  mcf8390.c  reset.c   vectors.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/h8300/include/uapi/asm$ cat /opt/linux/linux-5.4/arch/m68k/coldfire/REVELATION-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{AHW5jWIo_pQ5MusG7-fd6Hyh7T-.QX5IDO0wiM1AzNzEzW}
```

## What I learnt
I have learnt how to efficiently use the cat ls and cd command to retrieve the flag. I followed the clues given by the pwn.college and the bash. One clue let to another and so on. I started off with cd'ing to the root directory, then listed all the files. I then kept reading the clues which led me to further directories to which I kept cd'ing to.

## References
The references were the instructions provided by the pwn.college.

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

# 14. Linking files
In this challenge, it is given that /flag file has the flag. and '/challenge/catflag' command reads out '/home/hacker/not-the-flag', and we have to use symlink and fool it to give the flag.

## My Solve
Flag: pwn.college{Mk64LQu8l21VSPRlhr_OuhoncJa.QX5ETN1wiM1AzNzEzW}

It is given that /challenge/catflag reads /home/hacker/not-the-flag, and /flag file has the flag. So we have to link /flag file with /home/hacker/not-the-flag using ln command with -s argument for symbolic/soft link. After that we have to run the /challenge/catflag command to get the flag, as it will read /home/hacker/not-the-flag, which is a symbolic link to /flag file.

```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{Mk64LQu8l21VSPRlhr_OuhoncJa.QX5ETN1wiM1AzNzEzW}
```
## What I Learnt 
I learned about links and about the different types of links: soft link and hard link. Soft links are mostly used. For soft links, we use ln command with -s argument, and for hard links we use ln command without any argument.

## References

The references were the instructions provided by the pwn.college.
