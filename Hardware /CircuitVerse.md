# CircuitVerse

**Task Description** :  
____________________________________________________________________________________________________________
Sometimes, you're asked to make a decision: either choose 0 (white) or 1 (black). Honestly, I might opt for something in between!

What you have here is a simple binary conversion. Retrieve the flag!
____________________________________________________________________________________________________________

**Attachement** : [Circuit](/Files/SPARKYSPARKYY.cv) 
[Output](/Files/Output.txt)

# Solution 
____________________________________________________________________________________________________________
Let's start with the challenge name, "CircuitVerse", which is an online digital logic circuit simulator.
Players were provided with a .cv file and an output.txt. Most of the players weren't able to  open this file while the hint was in the task name. The website is online, free and doesn't require any registration so players can import the .cv file to see the circuit. 

![image](https://github.com/Garroura/Writeups/assets/164345052/66186f72-b18b-485a-9719-23086d495edf)



![image](https://github.com/Garroura/Writeups/assets/164345052/b24ecc63-e798-4c32-b518-6aba03902a27)


The second hint , is in the description , as it says it's a simple binary conversion , and it's between black and white ( which is the same name as the circuit ) .  I was hinting to players about the colors "Grey".

This circuit does a conversion from normal binary to Gray binary. 


![image](https://github.com/Garroura/Writeups/assets/164345052/62834648-9039-4c43-9a8c-7d5349af8b86)

Although not all players managed to determine the exact conversion type, most of them tried to reverse the code (the XOR operation). Honestly, it is not the intended way of solving the challenge; I wanted to highlight the Gray binary as it is commonly used in embedded systems.

Now, all you have to do is to move from Gray code (output) to binary to get the flag.

![image](https://github.com/Garroura/Writeups/assets/164345052/1beddeb3-2407-4ea6-8abb-398c6ea6c7f1)

Here is a solver in python : 
````
def gray_to_binary(gray):
    binary = gray[0]
    for i in range(1, len(gray)):
        binary += str(int(binary[i-1]) ^ int(gray[i]))
    return binary
gray_sequence = "0111101011001000010100011100101101011110110001101110101000101000001011010110110111100010101011100110101001110000111001001010111001111110001010101111101011110000111111100010111001101110101010101111000011111010101010000111000011101011111111111110001011101100011100001111111000101000011100001111111111101001011001100010101011111011001011111111111000101110011010010110011001000011"
binary_code = gray_to_binary(gray_sequence)
print("Binary:", binary_code)
flag = ""
for i in range(0, len(binary_code), 8):
    byte = binary_code[i:i+8]
    flag += chr(int(byte, 2))

print("Flag : ", flag)

````
         Binary: 0101001101110000011000010111001001101011011110110100110000110000001101100100100101000011001101000100110001011111010001110011010001010100001100110101001101011111010101000011010001001011001100110101111101010011001100000101111101001101010101010100001101001000010111110101010000110000010111110101010101001110010001000011001101010010001101010101010000110100010011100100010001111101
         Flag :  Spark{L06IC4L_G4T3S_T4K3_S0_MUCH_T0_UND3R5T4ND}

