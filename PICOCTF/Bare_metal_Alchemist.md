# Bare Metal Alchemist
my friend recommended me this anime but i think i've heard a wrong name.

## My Solve:
To begin the analysis and confirm the type of challenge, the decompiled code is analyzed to locate the main processing loop where the data decryption occurs.
To locate the start of the encrypted data in memory, the instruction R15R14 = 0x68; is identified, which sets the data's starting memory address to $\mathbf{0x68}$.
To determine the secret constant used for the cipher, the instruction R11 = 0xa5; is located, establishing the XOR key as $\mathbf{0xa5}$.
To confirm the mathematical function of the cipher, the core loop instruction, Z._0_1_ = (byte)R25R24 ^ R11;, is examined, verifying the operation is a simple XOR cipher.
To know precisely when the encrypted string ends, the loop's termination conditions are defined by noting that the process stops if the raw byte read is either $\mathbf{0x00}$ (NULL) or $\mathbf{0xa5}$.
To access the physical bytes of the encrypted message, the Ghidra Byte Viewer is used to navigate directly to the starting memory address $\mathbf{0x68}$.
To prepare the exact sequence of bytes for calculation, the Raw Hex Sequence is extracted by copying all bytes starting at \mathbf{0x68} up to the first terminator (\mathbf{00} or \mathbf{A5}) encountered.
To reverse the cipher and retrieve the cleartext data, the XOR operation ($\oplus$) with the key $\mathbf{0xa5}$ is applied to every byte of the extracted hex sequence.
To make the resulting cleartext data readable, the decrypted hexadecimal bytes are converted into their corresponding ASCII characters.
To finalize the challenge solution, the resulting ASCII characters are concatenated to present the final flag string.



## Concepts leanrt:
Ghidra manipulation and using and figuring out raw hex bytes.

## Notes:
toughest challenge. stay away from hardware.
