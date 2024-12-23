# Honest Verifier Zero Knowledge

So we get `e` and `y` and we're supposed to calculate `a` and `z`

![image](https://github.com/user-attachments/assets/942d8df0-35fc-456b-9da0-628b05024c8b)

We generate a random `z` for `z between 0 and q`

Then wee calculate `a` and send it back

`Send me a transcript for my given e proving that you know the flag w such that y = g^w mod p
{"e": 3035019235718855203812037500815164110977975704742795567412948145005829824561091218224992954928930567649073221201817082381456116043162481666979272083677349, "y": 3792106750752071791066403170883649881532513375474559961423290777562432307042030694291496361790139332159200706989105885833178774638065672111176488079340319, "message": "send me your transcript"}
{"a": 22040703333838511293735638621410469551399350788490390306564721407191635983971925055687977144675038324884004032931958140714636797772633604018861544487797707, "z": 10893039014917422186373600860851161806577141700996268332566664957352676353896050996586857664134284420566006190851711960107217800658992826153339631501102320}
{"flag": "crypto{so_honest_very_zero_knowledge}", "message": "You convinced me you know an w such that g^w = y mod p!"`

Script for calculating `a` and `z`:

```python3
from Crypto.Util.number import inverse
import random

# Constants
p = 0x1ed344181da88cae8dc37a08feae447ba3da7f788d271953299e5f093df7aaca987c9f653ed7e43bad576cc5d22290f61f32680736be4144642f8bea6f5bf55ef
q = 0xf69a20c0ed4465746e1bd047f57223dd1ed3fbc46938ca994cf2f849efbd5654c3e4fb29f6bf21dd6abb662e911487b0f9934039b5f20a23217c5f537adfaaf7
g = 2

# Given values
e=int(input("Enter e: "))
y=int(input("Enter y: " ))

# Step 1: Generate a random z in range [0, q-1]
z = random.randint(0, q - 1)

# Step 2: Calculate y^e mod p
y_e = pow(y, e, p)

# Step 3: Calculate modular inverse of y^e mod p
y_e_inv = inverse(y_e, p)

# Step 4: Calculate a = (g^z * y^e_inv) % p
a = (pow(g, z, p) * y_e_inv) % p

# Output the results
print("a =", a)
print("z =", z)
```
