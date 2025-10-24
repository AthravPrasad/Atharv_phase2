# ARMassembly 1
The Challenge Description is:
For what argument does this program print `win` with variables 79, 7 and 3?
File: chall_1.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

## Solution:
1) This file is not a PE executable file, so could'nt use IDA.
2) Went for multiple attempts to convert this file to a executable, however failed. All processes were either too lengthy and cumbersome.
3) Went for manual Analysis.
4) The main function sets up a small stack frame to store its variables and then reads the program’s input argument (from the command line).
   It converts the input from a string to an integer using atoi. Then it calls the func function with this integer.
   After func returns, main checks if the result is zero. If the result is zero, it prints "You win!"
   
5)The func function takes a number as input (let’s call it input_val) and performs some arithmetic with three fixed numbers: 79, 7, and 3.
  Step by step, it does:
  Saves the input and some temporary values on the stack.
  Calculates 7 << 79 (shifts 7 left by 79 bits) and stores the result.
  Divides that huge number by 3 and stores the result.
  Subtracts the original input from that result.
  Returns the final value.

6)Then, we compare, if x-3370 is zero then  we win. so x hould be 3370.
7)Finally, convert it to hexadecimal and add 32 bit padding.

*Flag*: picoCTF{00000d2a}

## Concepts Learnt:
Assembly level language.

## Notes:
I will try to find a way to make these files executable so i dont need to go through all this hassle.
