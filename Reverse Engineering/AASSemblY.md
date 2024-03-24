# ASSemblY

**Task Description** :  
____________________________________________________________________________________________________________

You all now can admit that I forget a lot... For this one, I wanted to make a veryyyyyy simple program to hide my ID. Unfortunately, I erased all the files, the only one I got is this one. I don't even understand what is written here! For the last time, can you help me get back my ID before Rouissi gets mad at me ? (It is a long integer)

____________________________________________________________________________________________________________

**Attachement** : 
[ASS](/Files/ASS.s) 
[Output](/Files/output.txt)

# Solution 
____________________________________________________________________________________________________________
The description provides insights about the task. Players are provided with a simple assembly code . The task revolves around exploring assembly and its workings.

Analyzing the code, the main function moves the hidden ID "XXXXXXXXX" to a local varibale and calls the function ``func``.

![image](https://github.com/Garroura/Writeups/assets/164345052/651ec674-64e5-4b48-a891-d016cbe127ee)

![image](https://github.com/Garroura/Writeups/assets/164345052/601202a2-a6e4-4d95-aaab-322a0b407341)

The ``func`` performes the following operations:
* Moves the first argument ( which is the ID ) to DWORD PTR -20[rbp].
* Moves this value to the eax.
* Calls the ``cdqe`` which * stands for 'Convert Doubleword to Quadword Extended' (passing from eax to rax) .
* Shifts rax left by 3 bits (equivalent to multiplying rax by 8).
* Moves the rax content to the QWORD PTR -8[rbp].
* Performs an xor operation with 5 for the QWORD PTR -8[rbp].
* Compares its content with the constant value in the rax which is '5934314573'.
* Sets al to 1 if equal, 0 otherwise.
* stores the result of the function call in another local variable and prints it using ``printf``.
Analyzing the Output.txt file and the ``.rodata`` , we observe that the main function prints 1 as a result of the comparison. Players are tasked with retrieving the ID by reversing the code.

Here is a one-liner solution using Python:
``print(int((5934314573^5)/8))``

      Flag : Spark{741789321}




