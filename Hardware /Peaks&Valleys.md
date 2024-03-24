# Peaks&Valleys

**Task Description** :   
____________________________________________________________________________________________________________
My friend `R[u]DY` believes someone is listening to us! He used that blue card and a LED to send me a message, but I couldn't understand what he wanted to say.

[Click Here](https://wokwi.com/projects/392659621191772161)

____________________________________________________________________________________________________________
# Solution 
____________________________________________________________________________________________________________
Starting with the task name "Peaks&Valleys" , which means highs and lows ( in our case 1 and 0 ).
Players are provided with a Wokwi simualtion circuit , an Arduino card with a led . 
Looking at the task description , it says that we are trying to send a mesasge in a hidden way. 
Analyzing the code in teh ``sketch.ino`` we can see 'HIGH' and 'LOW' states of the led with the same delay ( so it can not be a Morse code as many players thought).

![image](https://github.com/Garroura/Writeups/assets/164345052/9c431643-54f0-4228-a061-b098716b9c12)

Where High represents 1 and Low represents 0, we can write a solver using Python to extract the binary and the flag:
````

binary=""
with open("Loop.txt", "r") as file:
    for line in file:
       if "HIGH" in line:
          binary+="1"
       elif "LOW" in line:
          binary+="0"
print ("Binary: " , binary)
flag =""
for i in range(0, len(binary), 8):
    byte = binary[i:i+8
    flag += chr(int(byte, 2))

print("Flag : ", flag)
````
The loop.txt file contains the code from the void loop() function from the sketch.ino code.


            Binary:  01010011011100000110000101110010011010110111101101001001010111110100010000110000011011100111010001010100010111110111011100110100011011100101010001011111001101000110111001111001001100000110111000110011010111110101010000110000010111110100100000110011011000010111001001011111010101010111001101111101
       Flag :  Spark{I_D0ntT_w4nT_4ny0n3_T0_H3ar_Us}

