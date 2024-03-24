# PASSI

**Task Description** :  
____________________________________________________________________________________________________________

You are often prompted to create a strong password to secure your data. I developed a program to generate such passwords and used one to secure my files. However, I've forgotten the password! Can you assist me in retrieving it? 
____________________________________________________________________________________________________________

**Attachement** : [Binary](/Files/Binary) 

# Solution 
____________________________________________________________________________________________________________
The task revolves around exploiting  the `strcmp` vulnerability in the <string.h> library in C coding. 

Running the `file` command on the binary , it shows that it's not stripped allowing players can use any decompiler such as [Dogbolt](https://dogbolt.org) online or IDA. 

Analyzing the code , two functions which are `shuffleString` & `encrypt` are used to generate the password ( as mentioned in the challenge description ).

![image](https://github.com/Garroura/Writeups/assets/164345052/e97718d0-56fe-4d5d-ae94-dae43cd92122)


The code shows the `strcat` function to concatenate the string 'spark' 5 times.

The ``shuffleString`` function takes the string 'sparksparksparksparkspark', shuffles its characters based on a random value generated with a seed (42), and generates a new string.

![image](https://github.com/Garroura/Writeups/assets/164345052/dc2f65e6-f0a9-47de-9ba4-443fc3da7846)


Finally , the 'encrypt' function that encrypts each character of the text. It does an xor operation for each character with the corresponding character from the key 'spark'  takes modulo 26 to ensure the result is in the range of 0-25, and then adds 'A' (65 in ASCII to convert the result into an uppercase ASCII character.

![image](https://github.com/Garroura/Writeups/assets/164345052/0752591f-427b-41ec-b495-0c4d0d79ebcc)


In the main function, the user is prompted to input a password of length 25 for comparison with the generated password. Exploiting the vulnerability in strcmp function, which is well-documented [here](https://github.com/ariary/Hack-weak-strcmp-code), allows us to retrieve the password.

To exploit this vulnerabilty, we can use any debugger ( such as gdb ) to set a breakpoint at the strcmp function when debugging the binary.
We can also use ltrace which is debugging utility in Linux.

![image](https://github.com/Garroura/Writeups/assets/164345052/ff1a1bf8-3d77-4479-a1bd-30f233ea0008)


We can see the password used for the comparison in clear text. 

Despite the possibility of reversing the code in a Linux environment, this is not the intended method for solving the challenge. Most players who successfully completed this task employed a debugger to exploit the vulnerability.

The task was solved by 23 teams out of 119 teams registered in this online CTF.
 
    Spark{AAKZZBCRAKADSZKABRTZDRKTB}
