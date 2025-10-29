# Format String 0
Can you use your knowledge of format strings to make the customers happy?
Download the binary here.
Download the source here.
Additional details will be available after launching your challenge instance.

## Solution:
On launching the instance, we are asked few questions.
Answering them all correctly gets us the flag. 
A wrong answer prevents us from getting the flag and kicks us out of the program.
The first question: Gr%114d_Cheese — This is acceptedhen used as a format printf(choice1) prints a very long field (%114d), making count > 64 so the program calls serve_bob().
Cla%sic_Che%s%steak — this exact menu string is accepted for the second customer.
The program does printf(choice2) with no arguments, so the three %s cause printf to dereference bogus pointers from the stack.
That typically causes a crash (SIGSEGV).
This gives us our flag.

*Flag:* picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_ef312157}.

## Concepts Learnt:
how Stacks work and how thir overflow can be manipulated into tricking the program to give you the flag.

## Notes:
Nothing as such.
