# DynamicLinkLib

**Task Description** :  
____________________________________________________________________________________________________________

I wrote some code to obfuscate my data, and instead of compiling it into a binary, I created this file!!! Can you help me retrieve my initial data?

____________________________________________________________________________________________________________

**Attachement** :
[Seek_Help.dll](/Files/Seek_help.dll) 
[Output](/Files/OutputDLL.txt)

# Solution 
____________________________________________________________________________________________________________

The task centres around decompiling .dll files. 
We can use DnsSpy , a debugger and .NET assembly editor , to open the file. 

![image](https://github.com/Garroura/Writeups/assets/164345052/941f6604-9186-423e-b7cc-7558aace0bbd)

 Examining the provided  C# code , we observe 2 functions , the `` main ``function and the `` jusdoit `` which stands for the encryption function.
For the ``main`` function , it encrypts the string ``s`` which represents  the flag and prints the encrypted string .
For the encryption , it's an easy one , xoring the flag with its length. 

Although the task may seem straightforward, it was solved by only 12 teams. This highlights the importance of exploring .dll files and understanding how to decompile them.

Here is the Solver in python :
````
String="Ol}nwgXPPOC(NYCRSHCOSCZIRREa"
Flag=""
for i in range(28):
    Flag+=chr(ord(String[i])^28)
print(Flag)
````

    Flag : Spark{DLLS_4RE_NOT_SO_FUNNY}
