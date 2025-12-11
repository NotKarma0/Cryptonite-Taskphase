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


# 5. spAES Oddity

DESCRIPTION:
First `cd` into the `src` directory. Then run:

```bash
docker-compose up --build -d
```

You can then connect with:

```bash
nc localhost 4590
```

After solving locally, connect to the challenge with:
```
nc spaesoddity.nitephase.live 45673
```

## Solution:
- This problem took me more than 3 days to solve.
- The idea beheind it is: The program takes an odd-input and encrypts it with a random key generated everytime u connect to the server.
- Now, to get the flag. We fist input a 15 byte input. The first byte of the flag is padded to the input, and then its encrypted.
- Then we input a 17 byte input, Now there are two blocks each block gets encrypted seperately. The 17 byte input is basically 15 byte previous input + testing char+ random 
- We then brute force and try every character in place of testing char until the first half of the 17 byte encrypted output matches the 15 byte padded and encrypted input
- Then we do the same for 13 byte, 11 byte, 9 byte so on giving us two bytes per progress made.
- At the end we get the final flag.
  
```
from pwn import *
import string

# ----------------------------
# Server config
# ----------------------------
HOST = "spaesoddity.nitephase.live"
PORT = 45673

# Allowed characters likely inside the flag
POOL = string.ascii_lowercase + string.digits + "-_ABCD{}"


# ===========================================================
# 1. Communication wrappers (renamed + disguised)
# ===========================================================

def open_portal():
    """Connect to remote oracle."""
    return remote(HOST, PORT)

def wait_prompt(conn):
    """Wait until the oracle asks for hex input."""
    conn.recvuntil(b"input in hex:")

def drop(conn, data: bytes):
    """Send a hex string."""
    conn.sendline(data)

def fetch_line(conn):
    """Read single output line."""
    return conn.recvline().strip()


# ===========================================================
# 2. Oracle interaction (renamed + disguised)
# ===========================================================

def cipher_door(conn, msg_hex: str):
    """
    Sends a hex payload and retrieves ciphertext.
    Returns None if the oracle refuses input.
    """
    wait_prompt(conn)
    drop(conn, msg_hex.encode())

    out = fetch_line(conn).decode()
    if "Major Tom" in out:
        return None
    return out  # hex ciphertext


# ===========================================================
# 3. Attack logic (cleaned + disguised)
# ===========================================================

def mission_start():
    conn = open_portal()
    result = ""

    # ------------------------------------
    # FIRST CHARACTER ONLY (special case)
    # ------------------------------------
    print("[*] Starting extraction...")

    pad = b"A" * 15
    base_hex = cipher_door(conn, pad.hex())

    if base_hex is None:
        print("[-] Oracle rejected initial probe.")
        conn.close()
        return

    target_block = base_hex[:32]  # first AES block

    found_first = False
    for ch in POOL:
        crafted = pad + ch.encode() + (b"A" * 15)
        test = cipher_door(conn, crafted.hex())
        if test and test[:32] == target_block:
            result += ch
            print(f"[Part 1] {result}")
            found_first = True
            break

    if not found_first:
        print("[-] Failed to extract first byte.")
        conn.close()
        return

    # ------------------------------------
    # MAIN LOOP (2 bytes at a time)
    # ------------------------------------
    while len(result) < 49:
        next_total = len(result) + 2
        left_pad_len = (16 - (next_total % 16)) % 16
        block_index = (left_pad_len + next_total) // 16 - 1

        left_pad = b"A" * left_pad_len

        base = cipher_door(conn, left_pad.hex())
        if base is None:
            print("[-] Oracle refused base query.")
            break

        ref_block = base[block_index * 32 : block_index * 32 + 32]

        solved_pair = False

        for a in POOL:
            for b in POOL:
                guess = (result + a + b).encode()
                crafted = left_pad + guess + (b"A" * 15)

                attempt = cipher_door(conn, crafted.hex())
                if attempt and attempt[block_index * 32 : block_index * 32 + 32] == ref_block:
                    result += a + b
                    print(f"[Part {len(result)}] {result}")
                    solved_pair = True
                    break
            if solved_pair:
                break

        if not solved_pair:
            print("[-] Could not match any pair.")
            break

    print("\n[Final Flag]", result)
    conn.close()


# ===========================================================
# Entry
# ===========================================================
if __name__ == "__main__":
    mission_start()

```

## Flag:
```
nite{D4v1d_B0w13-s_0dds_w3r3_n3v3r_1n_y0ur_f4v0r}
```

## Concepts learnt:

- AES encryption.
- How to get the hidden padded value which is added to the input without the requiement of knowing the key  <   >

## Resouces:

- https://www.youtube.com/watch?v=C4ATDMIz5wc&t=2s
- https://www.youtube.com/watch?v=SLeTFY40PZQ&t=443s
- https://aes.cryptohack.org/ecb_oracle/
- https://www.ctfrecipes.com/cryptography/symmetric-cryptography/aes/mode-of-operation/ecb/ecb-oracle
- Chatgpt helped me completely to build the code.
- Chatgpt to help me build the code.

