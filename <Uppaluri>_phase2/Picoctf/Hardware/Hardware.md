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
