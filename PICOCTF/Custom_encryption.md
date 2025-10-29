# Custom encryption
Can you get sense of this code file and write the function that will decode the given encrypted file content.
Find the encrypted file here flag_info and code file might be good to analyze and get the flag.

## Solution:
1) The code first makes a small “shared key” using Diffie–Hellman math — both sides use p = 97, g = 31, and their numbers a and b.
2) That math gives both sides the same secret number called key.
3) The plaintext message (the flag) is then reversed.
4) Each reversed letter is XORed with letters of the word "trudeau" that repeat again and again.
5) Each byte of that is turned into a big integer by multiplying it with key * 311.
6) To decode, I just reversed these steps: divide by key * 311 to get the semi-cipher bytes back.
7) Then I XORed them again with "trudeau" and flipped the result backward.
8) That revealed the hidden flag.

*Flag:* picoCTF{custom_d2cr0pt6d_e4530597}.

## Concepts Learnt:
How Diffie Hellman ciphers work and combination of different ciphers.

## Notes:
Ciphers are so hard to crack.
