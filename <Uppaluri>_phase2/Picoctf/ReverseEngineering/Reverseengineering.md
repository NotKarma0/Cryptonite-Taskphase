# 1. Vault Door-3
> This vault uses for-loops and byte arrays. The source code for this vault is here: VaultDoor3.java

## Solution:

- So when i opened the code in VS code, i observed that there was a flag at the bottom. So i tried simply using that it didnt work.
- When i observed the code which is being manipulated to give something else, i understood that the actual password is getting shuffled to give the return value. 
- So i figured i had to backtrack the given code, but after a lot of thought process it turns out inversing the actual code gives the code itself.
- So i wrote the code in c, then i put the return flag inside as the str and got the final flag as the answer


```
#include <stdio.h>
void main(){
    int i;
    char str[100],pass[100];
    fgets(str,sizeof(str),stdin);
    for (i=0; i<8; i++) {
        pass[i] = str[i];
    }
    for (; i<16; i++) {
        pass[i] = str[23-i];
    }
    for (; i<32; i+=2) {
        pass[i] = str[46-i];
    }
    for (i=31; i>=17; i-=2) {
        pass[i] = str[i];
    }
puts(pass);
}

```

## Flag:

```
picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_c79a21}
```

## Concepts learnt:

- None
- 

## Notes:

- None

## Resources:

- None

***

# 2. GDB baby step 1

> Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.

## Solution:
- So when i opened the file it said permission denied. So i used chmod to change permissions to open that file. I first checked the file type, which turned out to be a ELF File. Now it didnt give me anything and since the description for me to check the main function. 
- Since GDB can be used to analyze the ELF file, i used it. And in this process i checked out the different functions listed in that program file and saw that there a main function in there.
- I converted the AT&T text to intel as it shows Like eax instead of Mov. And then i disassembled the main function to convert it into lower level but human readable language. 
- I saw that there was a number beside the hex registry so i printed that number. And the flag was hidden in that.
- And i got the flag.

```
./debugger0_a
chmod 744 debugger0_a
file debugger0_a
gdb debugger0_a
info functions
set disassembly-flavor intel
disassemble main
print 0x86342
```
## Flag:
```
picoCTF{549698}
```
## Concepts learnt:
- I learned what gdb does. And i learned how to analyze the text written in gdb. And still have a lot left to learn.
- I have also learnt what disassembling does which basically converts binary code to lower level human readable language
- Need to understand gdb a lot more though.

## Notes:
- Use gdb to analyze parts of an executable file if its a ELF file or an exe file.
- Use language change commands such as set disassembly-flavour intel. 

## Resources:
https://medium.com/@Oscar404/cracking-picoctf-challenge-gdb-baby-step-1-2d77e8eab818

***
