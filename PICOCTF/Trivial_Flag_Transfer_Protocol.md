#  Trivial Flag Transfer Protocol
Figure out how they moved the flag.

## My Solve:
1) Firstly We have a file.Looking at its extension,  we come to understand that it is a tftp file.
2) This file is opened using Wireshark.
3) We extract files present inside: instructions.txt, plan, program.deb, and three .bmp image files.
4) We Proceed with instructions: The contents of the file was decrypted using the simple ROT13 cipher by using hit and trial method.
5) it Read:
Instructions.txt Decrypted: Stated the traffic wasn't encrypted and they needed to "DISGUISE OUR FLAG TRANSFER."
Plan Decrypted: Revealed the method: "I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE. CHECK OUT THE PHOTOS."

6) So there must be the flag hidden in the image files.
7) How is it hidden?
8) There is also a file called "Program" thats a installer for steghide.
9) The idea is now clear. Using Steghide, we analyse all the three files. The third File gets us the flag.


*Flag:* picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

## Concepts Learnt:
Learnt how to use steghide and Wireshark.

## NOtes:
Nothing as such.
