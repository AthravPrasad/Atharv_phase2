# Mini RSA
What happens if you have a small exponent? There is a twist though, we padded the plaintext so that (M ** e) is just barely larger than N.
Let's decrypt this: ciphertext

## My Solve:
The problem provided the ciphertext (C), a large modulus (N), and explicitly stated the exponent was E=3.
A key hint noted that the plaintext was padded so that $M^E$ was only slightly larger than N.
When the public exponent E is very small (like E=3), the resulting ciphertext C is calculated as C \equiv M^3 \pmod N; due to padding.
The value M^3 is not significantly larger than N, allowing an attacker to find the plaintext M by iterating through small multiples of N (i.e., calculating the cube root of C + i.N) until a valid message is found, a process performed efficiently using a Python script.
After a brief wait, the script successfully found a result whose cube root yielded plaintext containing the flag.
The recovered flag was then submitted, solving the challenge and getting the flag.

*Flag:* picoCTF{e_sh0u1d_b3_lArg3r_aef7377d}

## Concepts Learnt:
Using The RSA to cipher and understanding how cipher depend on e.

## Notes:
None as such.
