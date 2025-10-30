# Clutter Overflow
Clutter, clutter everywhere and not a byte to use.
nc mars.picoctf.net 31890

## My Solve
1) So basically, we have a program that gives you the flag only if it gets the specific input.
2) The objective is to make the program print the flag by successfully passing the conditional check: if (code == GOAL).
3) Target Value: The required value for the code variable is 0xdeadbeef.
4) The Vulnerability: The program uses the highly unsafe gets(clutter); function to read user input.
5) Since gets() has no way to check the size of the destination buffer (clutter), it will write data far past the 256-byte boundary of the clutter array.
6) The Exploit: Because the long code variable is stored immediately next to the clutter buffer on the program stack, sending more than 256 bytes of data will cause the excess bytes to overflow.
7) The clutter buffer will overwrite the value of the adjacent code variable.
8) Also, the value 0xdeadbeef must be written in Little Endian format (\xef\xbe\xad\xde\x00\x00\x00\x00).
9) Success: When gets() finishes, the stack-based code variable is overwritten with 0xdeadbeef.
10) We write a python script for it and pass it to the instance.

*Flag:* picoCTF{c0ntr0ll3d_clutt3r_1n_my_buff3r}

## Comcepts learnt:
Identifying vulnerabilites, and why VS code givesthe warning that gets() is unsafe.

## Notes:
Beware of gets().

