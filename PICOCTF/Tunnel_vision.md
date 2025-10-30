# Tunnel Vision
We found this file. Recover the flag.

## My Solve:
1) Firstly we have a BMP file, thats an image.
2) When we open the file, we find that it has no contents.
3) The file size is 2.8 MB. Where is the File contents?
4) This tells us that the file is corrupted.
5) So, we fix using hex editor.
6) Initial Fix: Checks the Pixel Array Offset (starting at offset 0x0A). The value is BA D0 00 00.
7) Reasoning: This converts to 53,434 bytes, which is far too large, as the pixel data should start immediately after the headers. The correct standard offset is 54 bytes.
8) Sets the value at offset 0x0A to 36 00 00 00 (36 hex = 54 decimal).
9) Reasoning: To set the pixel array address to the correct starting point (54 bytes) immediately after the mandatory headers.
10) Checks the DIB Header Size (starting at offset 0x0E). The value is BA D0 00 00.
11) Sets the value at offset 0x0E to 28 00 00 00.
12) Reasoning: To set the header size to the correct 40 bytes.
13) We save the file and try to open it again.	The image now opens, but it shows the decoy flag: "not a flag sorry."
14) We use exiftool to check the actual image size.
15) The dimensions are 1134 x 306 pixels.
16) Reasoning: Calculates the expected size for a 1134x306 image (Width x Height x 3 bytes per pixel) and finds it's ~1 MB. The full file size is ~2.8 MB.
17) This massive difference means we are only seeing a fragment of the actual image.
18) Using calculator, we find that The estimated new height is roughly 850 pixels.
19) We Choose a test height of 840 pixels and converts it to Little Endian hex: 48 03 00 00 (840 decimal = 0x348 hex).
20) We Replace the original value at offset 0x16.
21) Reasoning: To force the image viewer to draw more rows of pixels, thereby revealing the hidden data.
22) Finallly	we save the file and successfully open it.	The image is now much taller and reveals the true flag


*Flag:* picoCTF{qu1t3_a_v13w_2020}

## Concepts Learnt:
How image files get extensions, how to manipulate move about and edit the binary and hex code in a file.


## Notes:
This was very hard Took me a lot of time and help to get it done.



