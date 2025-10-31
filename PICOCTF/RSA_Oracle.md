# RSA Oracle
Can you abuse the oracle?
An attacker was able to intercept communications between a bank and a fintech company.
They managed to get the message (ciphertext) and the password that was used to encrypt the message.
After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can be found here nc titan.picoctf.net 56979.
Decrypt the password and use it to decrypt the message. The oracle can decrypt anything except the password.

## My Solve:
1) The primary objective of the challenge was to decrypt a secret message file.
2) The required encryption key, or password, had been intercepted but was locked using an RSA Oracle service.
3) Access to the Oracle's functions was established by connecting to the server using the Netcat tool.
4) It was immediately verified that the Oracle was programmed to explicitly refuse decryption of the specific, intercepted key ciphertext.
5) The number $2$ was chosen as a known value and was encrypted directly by the Oracle to obtain its ciphertext representation.
6) This resulting ciphertext for $2$ was then multiplied by the intercepted key's original ciphertext.
7) This mathematical multiplication generated a new, modified ciphertext value for submission.
8) Crucially, this modified ciphertext corresponded to the encryption of $2$ times the actual original password.
9) The disguised ciphertext was submitted to the Oracle, which proceeded to decrypt the value without identifying the trick.
10) This result was simply divided by $2$ to successfully recover the actual password, which was the hex string daa099.
11) The final step involved using the openssl command-line utility to decrypt the secret message file.
12) The recovered password, daa099, was correctly supplied as the required decryption key, yielding the final flag.

*Flag:* picoCTF{3ss_r0ckl1ng_r39_da099d93}

## Concepts Learnt:
Cracking ciphers.

## Notes:
Sometimes the solution is in the problem itself

