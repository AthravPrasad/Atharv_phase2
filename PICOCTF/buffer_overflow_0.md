# Buffer Overflow 0
Let's start off simple, can you overflow the correct buffer? The program is available here. You can view source here.
Additional details will be available after launching your challenge instance.

## Solution:
1) The given challenge program uses strcpy to copy into a 16-byte buffer, so you can write past it.
2) Now, On stack it’s: buf2 (16 bytes) → saved EBP (4 bytes) → saved EIP (4 bytes).
3) When the function returns it uses saved EIP as the return address.
4) The vulnerability is, If we overwrite that with nonsense, the program will crash.
5) This challenge prints the flag when the program crashes (SIGSEGV), so causing a crash is the goal.
6) We make a Simple payload: fill buffer with 16 As, overwrite EBP with 4 Bs, then put 4 Cs for the return address: A*16 + B*4 + C*4.
7) We Run this, program crash and we get flag.


*Flag:* picoCTF{ov3rfl0ws_ar3nt_that_bad_9f2364bc}

## Concepts Learnt:
Finding vulnerabilites in programs.

## Notes:
Nothing as such
