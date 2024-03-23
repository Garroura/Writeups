# PASSI

**Task Description** :  
____________________________________________________________________________________________________________

You are often prompted to create a strong password to secure your data. I developed a program to generate such passwords and used one to secure my files. However, I've forgotten the password! Can you assist me in retrieving it?
____________________________________________________________________________________________________________

**Attachement** : [Binary](WELCOME) 

# Solution 
____________________________________________________________________________________________________________
The task highlights the `strcmp` vulnerability in the <string.h> librairy in C coding. 

Running the `file` command on the binary , it shows that it's not stripped so players can use any decompiler such as https://dogbolt.org online or IDA. 

Going through the code , we can see that it uses two functions which are `shuffleString` & `encrypt` to generate the password ( as mentioned in the challenge description ).

![image](https://github.com/Garroura/Writeups/assets/164345052/e97718d0-56fe-4d5d-ae94-dae43cd92122)


The code shows the `strcat` function to concatenate the string 'spark' 5 times then the fucntion ``shuffleString`` which uses a random value generated with a seed (42) , to generate a new string by changing the order of the order of the caracters in the 'sparksparksparksparkspark' string.

![image](https://github.com/Garroura/Writeups/assets/164345052/dc2f65e6-f0a9-47de-9ba4-443fc3da7846)


Finally , using the 'encrypt' function that encrypts each character of the text. It does an xor operation for each character with the corresponding character from the key 'spark'  takes modulo 26 to ensure the result is in the range of 0-25, and then adds 'A' (65 in ASCII to convert the result into an uppercase ASCII character.

![image](https://github.com/Garroura/Writeups/assets/164345052/0752591f-427b-41ec-b495-0c4d0d79ebcc)


Finally in the main function , when running the bianry the user is asked to enter the password which should have a length of 25 in order to compare it with the password generated , doing some googling we can know that the strcmp fucntion is vulnerable and can be exploited. ( https://github.com/ariary/Hack-weak-strcmp-code ). [https://github.com/ariary/Hack-weak-strcmp-code].

To exploit this vulnerabilty we can use any debugger ( such as gdb ) to set a breakpoint at the strcmp function when debugging the binary.
We can also use ltrace which is debugging utility in Linux.

![image](https://github.com/Garroura/Writeups/assets/164345052/ff1a1bf8-3d77-4479-a1bd-30f233ea0008)


We can see the password used for the comparison in clear text. 

Although , reversing the code is possible in a linux environment but it is not the intended way of the challenge. Hopefully , most of the players who solved this task used a debugger to exploit the vulnerability.
The task was solved by 23 teams out of 119 teams registered in this online CTF.
 
    Spark{AAKZZBCRAKADSZKABRTZDRKTB}
