# 1. All Signs Align

## Solution:

- Basically what happens is 
    if bit == '0':
        out.append(a*get_x() % p)
    else:
        out.append(a*get_y() % p)
- If the bit is 0, it prints a * get_x() mod p, If the bit is 1, it prints a * get_y() mod p
- I had to search up a lot on what these functions do, and with the help of chatgpt, I have understood that it classifies into quadrant residue and non-quadrant residue.
- pow(x, (p-1)//2, p) so when this function gives 1- it is QR which means bit is 0, if it gives p-1 it is NQR  which means bit is 1.
- Converting the final binary number to bytes gave me the actual flag.

```
import ast

p = 9129026491768303016811207218323770273047638648509577266210613478726929333106121387323539916009107476349319902011390210650434835260358014251332047605739279

# Load the output list
with open("out.txt") as f:
    out = ast.literal_eval(f.read())

bits = ""
for v in out:
    leg = pow(v, (p-1)//2, p)
    if leg == 1:
        bits += "0"
    else:
        bits += "1"

print(bits)
```

## Flag:
```
crypto{Legendre_Symbols_are_leaking_bits}
```

## Concepts learnt:

- What is QR and NQR.

## Resources:

- Chatgpt to help me build the code.

# 2. Residue Refinery

## Solution:

- So understanding the program took me a lot of time, basically the digits are taken as a group of 2.
- M=a+b⋅x the group is taken like this, x indicates x^2=3
- basically our M is gonna get multiplied by the key which is also in the format of c+d.x which finally gives us the encrypted text which is given as a comment.
-  First step is to find the key, since they gave the First plaintext block = [0x31, 0x6d] = "1m", this can be used to find the key.
- We bruteforce to find which matches to the first two pair of encrypted text which is 98 13.
- key = (60,6)
- now we find inverse of the key, which when multiplied to the encrypted text will give the decrypted text. 
- inverse_key = (174, 34)
- Now on multiplication we get the flag. 

```
# solve.py
# Reproduces the key-recovery and decryption for the CTF challenge.
# Usage: python3 solve.py

ct_hex = "9813d3838178abd17836f3e2e752a99d5cd3fba291205f90c1d0a78b6eca"
ct = bytes.fromhex(ct_hex)
known_first_hex = "316d"  # given: flag[:2].hex() = '316d'
known_first = bytes.fromhex(known_first_hex)

p = 257

class Num:
    def __init__(self, n):
        # accept tuple/list/bytes of length 2
        a = int(n[0]) % p
        b = int(n[1]) % p
        self.n = [a, b]
    def __mul__(self, other):
        a0, a1 = self.n
        b0, b1 = other.n
        prod0 = (a0 * b0) % p
        prod1 = (a0 * b1 + a1 * b0) % p
        prod2 = (a1 * b1) % p
        # reduction x^2 = 3 => contribute 3*prod2 to coefficient 0
        r0 = (prod0 + 3 * prod2) % p
        r1 = prod1 % p
        return Num((r0, r1))
    def to_bytes(self):
        # original used: bytes(self.n.tolist())[::-1]
        # i.e. output bytes [n1, n0]
        a, b = self.n[0], self.n[1]
        if not (0 <= a <= 255 and 0 <= b <= 255):
            # not representable as single bytes
            return None
        return bytes([b, a])
    def __eq__(self, other):
        return isinstance(other, Num) and self.n == other.n
    def __repr__(self):
        return f"Num({self.n})"

# Split ciphertext into 2-byte blocks
blocks = [ct[i:i+2] for i in range(0, len(ct), 2)]
print(f"Total blocks: {len(blocks)}")

# Find key ks such that ks * known_first = first ciphertext block
c0 = blocks[0]
found_keys = []
for k0 in range(256):
    for k1 in range(256):
        k = Num((k0, k1))
        pt = Num((known_first[0], known_first[1]))
        prod = k * pt
        tb = prod.to_bytes()
        if tb is not None and tb == c0:
            found_keys.append((k0, k1))

print("Found keys:", found_keys)
if not found_keys:
    raise SystemExit("No key found (unexpected)")

ks = found_keys[0]
print("Key (bytes):", tuple(hex(x) for x in ks))

# Find multiplicative inverse of ks (i such that ks * inv = (1,0))
k_num = Num(ks)
inv = None
for i0 in range(256):
    for i1 in range(256):
        cand = Num((i0, i1))
        prod = k_num * cand
        if prod.n == [1, 0]:
            inv = (i0, i1)
            break
    if inv is not None:
        break

if inv is None:
    raise SystemExit("Inverse not found (unexpected)")
print("Inverse (bytes):", tuple(hex(x) for x in inv))

# Decrypt all blocks
inv_num = Num(inv)
plain = bytearray()
for blk in blocks:
    # ciphertext block is bytes([prod.n[1], prod.n[0]])
    # so reconstruct Num(prod.n[0], prod.n[1]) with (blk[1], blk[0])
    ct_num = Num((blk[1], blk[0]))
    pt_num = inv_num * ct_num
    a, b = pt_num.n[0], pt_num.n[1]
    if not (0 <= a <= 255 and 0 <= b <= 255):
        raise SystemExit(f"Decrypted components are not bytes: {pt_num.n}")
    plain += bytes([a, b])

print("Decrypted bytes (hex):", plain.hex())
try:
    print("Decrypted ASCII:", plain.decode())
except Exception as e:
    print("Could not decode to ASCII:", e)

print("\nFinal flag (as shown in challenge):")
print("nite{" + plain.decode() + "}")

```

## Flag:
```
nite{1mp0r7_m0dul3?_1_4M_7h3_m0dul3}
```


## Resources:

- Chatgpt to help me build the code.

# 3. Quixorte

## Solution:

- Firstly on observing the program. The original text gets rotated by the number of position of the bit. So 1st position A0 is gonna be rotated by 0 bits, second position A1 is gonna be rotated by 1 and so on.
- And after this XOR is done with a key.
- We can see that the file given is an encrypted png file. And we know that every png file has the first 8 common bytes which are 89 50 4E 47 0D 0A 1A 0A
- Using this we can get the key, A XOR B = C here A is original text, B is key, C is encrypted text also means. C XOR A = B.
- We then find the key which is ec 95 e0 22 0a 3d 5a b7
- For undoing the XOR we use the rule A XOR B XOR B = A. So we run the XOR again with the given png file.
- And then we undo the rotation to get the original png file. 

```
def rotate_right(b, i):
    r = i % 8
    return ((b >> r) | (b << (8 - r))) & 0xFF

def rotate_left(b, i):
    r = i % 8
    return ((b << r) | (b >> (8 - r))) & 0xFF


# Read encrypted file
with open("quote.png.enc", "rb") as f:
    enc = bytearray(f.read())

# Known PNG header (first 8 bytes of every PNG)
png_header = b'\x89PNG\r\n\x1a\n'

# Step 1: Rotate the known header the same way encryption did
rotated_header = bytearray(
    rotate_right(png_header[i], i) for i in range(8)
)

# Step 2: Recover the key
key = bytearray(8)
prefix_xor = 0

for i in range(8):
    t = enc[i] ^ rotated_header[i]
    key[i] = t ^ prefix_xor
    prefix_xor ^= key[i]

print("Recovered key (hex):", key.hex())

# Step 3: Undo the sliding XOR
N = len(enc)
L = 8

for i in range(N - L + 1):
    for j in range(L):
        enc[i + j] ^= key[j]

# Step 4: Undo the bit rotation
for i in range(N):
    enc[i] = rotate_left(enc[i], i)

# Save the decrypted file
with open("quote_decrypted.png", "wb") as f:
    f.write(enc)

print("Decryption complete! Saved as quote_decrypted.png")
```


## Flag:
```
nite{t0_b3_X0R_n0t_t0_b3333}
```

## Concepts learned: 
- None

## Resources:
- Chatgpt for helping me with the python code.

# 4. Willy's Chocolate Experience

## Solution:

- Basically the original text gets converted into Ascii characters and then first letter's ascii value is multiplied with 256^k-1 and second gets multiplied with 256^k-2 where k is the length of the text. 
- Now what actually happens here is this number which is called ticket. 
- Now the encrypted function is f = 13^m+37^m (mod p).  Now f(ticket-1) and f(ticket) are given to us.
- Our job is to find the value of ticket. To find the original sentence.
- We write two equations as A= x+y, B= 13x+37y. Where x= 13^t-1 and y=37^t-1
- Upon solving for ticket, we get the final flag.
-
```
from Crypto.Util.number import long_to_bytes
from sympy import discrete_log

# Given prime p
p = 396430433566694153228963024068183195900644000015629930982017434859080008533624204265038366113052353086248115602503012179807206251960510130759852727353283868788493357310003786807

# Given leftover values (A = f(ticket-1), B = f(ticket))
A = 124499652441066069321544812234595327614165778598236394255418354986873240978090206863399216810942232360879573073405796848165530765886142184827326462551698684564407582751560255175
B = 208271276785711416565270003674719254652567820785459096303084135643866107254120926647956533028404502637100461134874329585833364948354858925270600245218260166855547105655294503224

# Step 1: solve the linear system for x = 13^(t-1), y = 37^(t-1)

inv24 = pow(24, -1, p)                # modular inverse of 24 modulo p
x = (37 * A - B) * inv24 % p          # x ≡ 13^(t-1) (mod p)
y = (A - x) % p                       # y ≡ 37^(t-1) (mod p)

# Step 2: form ratio r = y / x = (37/13)^(t-1) (mod p)

r = y * pow(x, -1, p) % p             # modular division y/x
g = 37 * pow(13, -1, p) % p           # g ≡ 37/13 (mod p)

# Step 3: solve discrete log g^k = r (mod p), k = t-1

k = discrete_log(p, r, g)             # find exponent k

# Step 4: recover ticket and flag

ticket = k + 1
flag = long_to_bytes(ticket)

print("k (ticket - 1):", k)
print("ticket:", ticket)
print("flag:", flag)

```

## Flag:
```
nite{g0ld3n_t1ck3t_t0_gl4sg0w}
```

## Concepts learnt:

- I have learnt how to solve complex functions which use the modular function.

## Resources:

- Chatgpt to help me build the code.

