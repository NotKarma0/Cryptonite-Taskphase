# 1. miniRSA
> What happens if you have a small exponent? There is a twist though, we padded the plaintext so that (M ** e) is just barely larger than N. Let's decrypt this: ciphertext

## Solution: 
- I just went into RSA cipher decryption. and decrypted it using the given values.

## flag: 
```
picoCTF{n33d_a_lArg3r_e_ccaa7776}
```

## Resources: 
- This is what i used to decrypt. https://www.dcode.fr/rsa-cipher

***

## 2. Custom encryption
> Can you get sense of this code file and write the function that will decode the given encrypted file content.
Find the encrypted file here flag_info and code file might be good to analyze and get the flag.

## Solution:
-  In the challenge, we are given a encrypted file and python code. 
-  Generator establishes a shared numeric key via modular exponentiation.

def generator(g, x, p):  
	return pow(g, x) % p  

 dynamic_xor_encrypt takes your plaintext, reverses it, and XORs it with a repeating text_key.

def dynamic_xor_encrypt(plaintext, text_key):  
	cipher_text = ""  
	key_length = len(text_key)  
	for i, char in enumerate(plaintext[::-1]):  
		key_char = text_key[i % key_length]  
		encrypted_char = chr(ord(char) ^ ord(key_char))  
		cipher_text += encrypted_char  
	return cipher_text  

 encrypt takes the result of the XOR step, converts each character to ASCII, and multiplies by (shared_key * 311) to produce a list of large numbers.

def encrypt(plaintext, key):
	cipher = []  
	for char in plaintext:  
		cipher.append(((ord(char) * key*311)))  
	return cipher 

-  Going through the python code, I was able to understand that the encryption takes the plaintext, reverses it, XORs each character with a repeating key string (trudeau), then converts the result to numbers by multiplying each character’s ASCII code by a shared key (derived by modular exponentiation) × 311.

- Now, we know that how to encrypt it, we just need to undo it to decrypt it.
- To create a decryption function, I make the following changes :
-  First I derive the shared key using leak_shared_key.
```
def generator(g, x, p):
    return pow(g, x) % p

def decrypt(cipher, key):
    plaintext = ""
    for num in cipher:
        plaintext +=  chr(num// (key*311))
    return plaintext

def dynamic_xor_decrypt(plaintext, text_key):
    orig = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext) :
        key_char = text_key[i % key_length]
        
        decrypted_char = chr(ord(char) ^ ord(key_char))
        orig += decrypted_char
    return orig
p = 97
g = 31

cipher = [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]
a = 88
b = 26
u = generator(g, a, p)
v = generator(g, b, p)
key = generator(v, a, p)
print(dynamic_xor_decrypt(decrypt(cipher,key), "trudeau"))
```
This was output: }c138c910_d6tp0rc2d_motsuc{FTCocip

## Flag:
```
picoctf{custom_d2cr0pt6d_019c831c}
```

## Resources:
- I used chatgpt to perfect the code honestly which was used to decrypt.

## Concepts learnt:
- How to decrypt a cipher manually.

***

