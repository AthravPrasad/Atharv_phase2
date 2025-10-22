# GDB Baby step 1:
The Challenge Description is:                
Can you figure out what is in the eax register at the end of the main function?              
Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base.             
If the answer was 0x11 your flag would be picoCTF{17}.                                     
Along with this a code file was provided from which the information was to be extracted.                           

## Solution:
1) A random file with a code, so i installed IDA and used it decompiler to open the file.
2) this gave me a piece of reverse engineered code. This is what i got.

   ''' ; Attributes: bp-based frame

   ; int __fastcall main(int argc, const char **argv, const char **envp)
   public main
   main proc near

   var_10= qword ptr -10h
   var_4= dword ptr -4

   ; __unwind {
   endbr64
   push    rbp
   mov     rbp, rsp
   mov     [rbp+var_4], edi
   mov     [rbp+var_10], rsi
   mov     eax, 86342h
   pop     rbp
   retn
   ; } // starts at 1129
   main endp '''

3) The challenge asks us to get the eax register value: It is in plain sight *86342h* .

## FLag:
picoCTF{549698}

## Concepts Learnt:
Using IDA Decompiler and Deassembler.

## Notes:
While installing IDA administrative permissions like " sudo apt install ....." and " chmod +x /......" were required.                      
(Linux luminarium of pwn.college rocks!")
