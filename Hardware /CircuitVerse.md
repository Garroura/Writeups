# CircuitVerse

**Task Description** :  
____________________________________________________________________________________________________________
Sometimes, you're asked to make a decision: either choose 0 (white) or 1 (black). Honestly, I might opt for something in between!\r\n\r\nWhat you have here is a simple binary conversion. Retrieve the flag!
____________________________________________________________________________________________________________

**Attachement** : [Circuit]() 
[Output]()

# Solution 
____________________________________________________________________________________________________________
Let's start with the challenge name which is "CircuitVerse" which is an online digital logic circuit simulator.
Players were provided with a .cv file and an output.txt , most of the players weren't able to know how to do open this file while the hint was in the task name. The website is online and free and doesn't require any registration so players can import the .cv file to see the circuit. 

![image](https://github.com/Garroura/Writeups/assets/164345052/66186f72-b18b-485a-9719-23086d495edf)



![image](https://github.com/Garroura/Writeups/assets/164345052/b24ecc63-e798-4c32-b518-6aba03902a27)


The second hint , is in the description , as it says it's a simple binary conversion , and it's between black and white ( which is the same name of the circuit ) . I was trying to hint players for the coulors "Grey" .

This circuit does a conversion from normal binary to Gray binary. 


![image](https://github.com/Garroura/Writeups/assets/164345052/62834648-9039-4c43-9a8c-7d5349af8b86)

Although not of the players made it to know exactly the conversion type , most of them tried to reverse the code ( the xor operation ) . Honestly it is not the intended way of solving the chall , i wanted to highlight the gray binary as it is commonly used in the embedded systems.

Now , all what you have to do is to move from gray code ( output) to the binary to get the flag.

![image](https://github.com/Garroura/Writeups/assets/164345052/1beddeb3-2407-4ea6-8abb-398c6ea6c7f1)

Here is a solver in python : 
