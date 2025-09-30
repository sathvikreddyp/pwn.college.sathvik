# 1. Printing variables
In this chsllenge, we are asked to print out the FLAG variable.

## My Solve
Flag: pwn.college{IDjU6vf4pL3yCw-uKaFLNgMBMe_.QX3UTN0wiM1AzNzEzW}

To solve this challenge, I executed the echo command followed by a $ sign with the variable "FLAG".

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{IDjU6vf4pL3yCw-uKaFLNgMBMe_.QX3UTN0wiM1AzNzEzW}
```

## WHat I Learnt
I have learnt how to print variables using the $ command and that many other commands can be used other than echo.

## References
The reference was the problem statement provided by the pwn.college.

# 2. Setting variables
In this challenge, we are asked to set the PWN variable to the value COLLEGE.

## My SOlve
Flag: pwn.college{sOG7BcnV98ND_I99mEz3KY91WC2.QX5UTN0wiM1AzNzEzW}

To solve this challenge, I used the = sign to assign the value of COLLEGE to PWN which led me to my flag.

```
hacker@variables~setting-variables:~$  PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sOG7BcnV98ND_I99mEz3KY91WC2.QX5UTN0wiM1AzNzEzW}
```

## What I Learnt
I have learnt how to assign values to variables using the = sign. Also, note that there are no spaces between the variable, equal to sign, and the value being assigned. They are ALL case sensitive.

## References
The reference was the problem statement provided by the pwn.college.

# 3. Multi-word variables
In this level, we have been asked to set the variable PWN to COLLEGE YEAH.

## My Solve
Flag: pwn.college{wIZBAIQd2qQ9gU2UjTvYSRf7GGC.QXwYTN0wiM1AzNzEzW}

To solve this challenge, I assigned the value "COLLEGE YEAH" to the variable PWN using double quotes since it was a 2 word assignment.

```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wIZBAIQd2qQ9gU2UjTvYSRf7GGC.QXwYTN0wiM1AzNzEzW}
```

## What I Learnt
I have learnt how to assign a multi word value to a variable using double quotes.

## References
The reference was the problem statement provided by the pwn.college.

# 4. Exporting Variables
In this challenge, we should invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported.

## My Solve
Flag: pwn.college{0cohSpWWSunD3CjoqgUUmT3-Gxm.QXyYTN0wiM1AzNzEzW}

To solve this challenge, I assigned the value COLLEGE to the variable PWN and exported it. I then assigned the value PWN to the variable COLLEGE without exporting it. I then ran /challenge/run to retrive the flag.

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{0cohSpWWSunD3CjoqgUUmT3-Gxm.QXyYTN0wiM1AzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```

## What I Learnt
I learnt how to export values assigned to variable if you want them to remain assigned through many programs using "export".

## References
The reference was the problem statement provided by the pwn.college.

# 5. Printing exported variables
In this challenge, we are asked to print out the exported vatiable (FLAG) into the shell to get the flag.

## My Solve
Flag: ‘pwn.college{cHc1QztgG4tcdf38dTWKiYfdkmE.QX4UTN0wiM1AzNzEzW}

I printed out the FLAG variable using env command instead of echo.

```
hacker@variables~printing-exported-variables:~$ env $FLAG
env: ‘pwn.college{cHc1QztgG4tcdf38dTWKiYfdkmE.QX4UTN0wiM1AzNzEzW}’: Permission denied
```

## What I Learnt
I learnt that we can even print the contents of the variable using env command other than echo command.

## References
The reference was the problem statement provided by the pwn.college.

# 6. Storing command output
