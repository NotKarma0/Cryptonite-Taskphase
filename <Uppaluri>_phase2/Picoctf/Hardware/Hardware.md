# IQ test:
> let your input x = 30478191278.

wrap your answer with nite{ } for the flag.

As an example, entering x = 34359738368 gives (y0, ..., y11), so the flag would be nite{010000000011}.

## Solution: 
- I converted the given x value to binary which gives 011100011000101001000100101010101110
- And i did gates for a lot of time and got the flag.

## Flag: nite{100010011000}

## Concepts learned:
- Hardwork, patience.

# i_like_logic
> i like logic and i like files, apparently, they have something in common, what should my next step be.

## Solutions: 
- So, I ended up looking into what a .sal file was and found out it’s actually the format Saleae Logic 2 uses for digital signal captures. 
- Then, I took a peek at a digital.bin file using strings and saw a bit of SALAE in there, which basically confirmed it.
-  After that, I grabbed the Logic 2 analyzer software, fired it up, and loaded the file. 
- I ran the analyzer on channel 3 and, buried in all the extra text, managed to pull out some useful signal info. And the flag was sitting inside some text.

## Flag:
```
FCSC{b1dee4eeadf6c4e60aeb142b0b486344e64b12b40d1046de95c89ba5e23a9925}
```

## Concepts Learned:
- Everything still need to understand it a bit better
- Learned how to analyze .sal files
- And how to use logic 2 software

# Resources:
- https://file.org/extension/sal This helped me understand sal files
- Chatgpt helped me a bit on how to use the software.

***
# bare-metal-alchemist
> my friend recommended me this anime but i think i've heard a wrong name.

## Solution:
- At first i thought it had something to do with full metal alchemist. I was very wrong it had nothing to do with it.
- I analyze the type of file which is firmware.elf which is AVR microcontroller meaning we need to analyze or disassemble it.
- Upong loading it in ghidra this was the main function
```
void main(void)
{
  ...
  R11 = 0xa5;
  R12 = 0;
  R13 = '\0';
  do {
    ...
    R15R14 = (byte *)0x68;
    R16 = 0;
    while (true) {
      Z = R15R14;
      R25R24._0_1_ = *R15R14;
      if ((byte)R25R24 == 0) break;
      Z._1_1_ = (undefined1)((uint)R15R14 >> 8);
      Z._0_1_ = (byte)R25R24 ^ R11;
      if ((byte)R25R24 == 0xa5) break;
      ...
    }
  } while (true);
}
```
- Z._0_1_ = (byte)R25R24 ^ R11; this means each byte is getting XOR with 0xa5
- It took a lot of time to find the first file offset file_offset = (.text file offset) + (desired VMA - .text VMA) which is file_offset = 
file_offset = 0x94 + 0x68 = 0xFC

- The firmware XORs every byte with 0xA5, and stops when it hits a 0x00.
This was the code used to do this decoding.
```
from pathlib import Path
raw = Path('firmware.elf').read_bytes()
start = 0xFC   # file offset we calculated
out = []
for b in raw[start:]:
    if b == 0x00:    # stop at null terminator
        break
    out.append(b ^ 0xA5)
print(bytes(out).decode())
```

## Flag:
TFCCTF{Th1s_1s_som3_s1mpl3_4rdu1no_f1rmw4re}

## Resources: 
- https://www.varonis.com/blog/how-to-use-ghidra
- A lot of help from Chatgpt.

## Concepts learnt:
- How to use ghidra to disassemble the code.
- More knowledge on XOR decoding.
- How python can be used efficiently.

## Notes:
- Everything.

***
