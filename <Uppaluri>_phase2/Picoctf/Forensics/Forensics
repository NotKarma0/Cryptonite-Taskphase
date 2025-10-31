# 1. Trivial Flag Transfer Protocol

> Figure out how they moved the flag.

## Solution: 
-  First, I open the tftp file in WIRESHARK. In there, I filter out the tftp data in the file and export it separately out.
-  About 7 files got exported as part of the above process. Mainly 2 txt files with some encryption on it.
-  Also, as .dev file got exported with steghide, which might have been used to hide the flag in the images given or something. ( initial assumption )
-  Bcz we have a encrypted message, I decided why not put it in the cipher identifier. 
-  On running it, I was able to identify it as ROT-13 encrytion 
-  The first part of the message: TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER
-  The sencond part of the message 
-  Then from the plan.txt file's message was also ROT-13 and it gave the key inorder to solve the challenge, ie KEY: DUEDILIGENCE - the password used for steghide.
-  Now, I ran steghide on all the 3 image files and the 3rd image, picture3.bmp had hidden the flag, which hid the data in it. On being invoked by steghide, it transferred the flag into flag.txt file. 

steghide extract -sf picture3.bmp -p DUEDILIGENCE
wrote extracted data to "flag.txt".

- On opening the opening flag.txt , the flag was revealed!!!


```
steghide extract -sf picture3.bmp -p DUEDILIGENCE
wrote extracted data to "flag.txt".
cat flag.txt
```
## Flag:
```
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```
## Concepts learnt:
- Most of it was known.

## Notes:
- None

## Resources:
- None

***
# 2.m00nwalk
> Decode this message from the moon.

## Solution: 
-  On opening the audio file given in the challenge, the audio file had some strange audio in it. 
-  Referring the hints and doing a bit research on it, I was able to understand that it was a SSTV signal. 
-  In order to convert the sstv signal to an image file, you can run this command found in google 

```
 qsstv -d (message.wav) -o result.png
```
The answer was shown in pic

## Flag:
```
picoCTF{beep_boop_im_in_space}
```
## Concepts learnt:
- Everything from start to end

## Notes:
- Need to get more clarity a lot honestly.
## Resources:
- https://github.com/Dvd848/CTFs/blob/master/2019_picoCTF/m00nwalk.md
***
# Tunnel vision 
> We found this file. Recover the flag.
## Solution: 

- First, I download the file that's given in the challenge. But, when I tried to open it, I wasn't able to do so.
-  I also noticed the file downloaded had no extension. So, I ran exiftool on it.
-  I found that the file in a bmp file. So, I added the bmp extension to it.
-  Now, I tried opening it. But on opening it, I wasn't able to see the content in it. So, its more than likely to be corrupted.
-  On doing some research, I understood that we can use a hex editor to examine what's corrupted in the file.
-  To uncorrupt the file, I compared it with a normal bmp file, on the hex editor.
-  On comparison, I found that the info header had characters like : BA D0, instead of numbers like a normal bmp file. So, I converted the characters to the nos given in the normal bmp file like : ` 36 00 00 00 28 00 `. 
-  On saving it, I got :
which had a fake flag in it.
-  Here, I came to a hault. So, I focused on the basics, ie, to look into what the challenge name is hinting at? Tunnel vision means to narrow down your vision on something. So like somehow the image which is corrupted might be a like a smaller part of a bigger image like the one in citadel.
- We can do this process in the hex-editor. So, referencing the website (that I mentioned in the resources), I did this.
-  The 2nd row is where the bytes of the height and the width are located, ie 4 byted for each height and width. 
-  I started with changing the height's value, bcz height's value was way less than width's value. I started with 1000's hex value, working my way down. Well, 1000 was wrong, so I couldn't see the content in the image file.
-  At a height of around 850, I was able to see the content in the file and the flag was revealed in the image



## Flag:
```
picoCTF{qu1t3_a_v13w_2020}
```

## Concepts learnt:
- Everything from start to end

## Notes:
- Need to get more clarity a lot honestly.

***
