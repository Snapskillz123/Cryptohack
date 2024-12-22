# Proofs of knowledge
if first send an a that's generated randomly using a random r. `( a = g^r mod p)`
`{"a":8732263466296466977302693947124189507126731040098098868381909913072966925455934247273836367520574319467274755254009151702877494171513020839416221648000716}`
The script then sends me a random e. `(self.e = random.randint(0,2**511))`
I have to then calculate a random z where `z = r + e*w mod q`.
`{"z":7570655933448811369040408480087090188506766121513514344075408979112600092124981871087836230429719492265530694769076885467452066264312290245555723579812623}
{"flag": "crypto{sigma_protocol_complete!}", "message": "You convinced me you know an w such that g^w = y mod p!"}`

```python3
import random

# Constants
p = 0x1ed344181da88cae8dc37a08feae447ba3da7f788d271953299e5f093df7aaca987c9f653ed7e43bad576cc5d22290f61f32680736be4144642f8bea6f5bf55ef
q = 0xf69a20c0ed4465746e1bd047f57223dd1ed3fbc46938ca994cf2f849efbd5654c3e4fb29f6bf21dd6abb662e911487b0f9934039b5f20a23217c5f537adfaaf7
g = 2
w = 0x5a0f15a6a725003c3f65238d5f8ae4641f6bf07ebf349705b7f1feda2c2b051475e33f6747f4c8dc13cd63b9dd9f0d0dd87e27307ef262ba68d21a238be00e83

# Step 1: Generate random r and compute a
r = random.randint(0, q - 1)
a = pow(g, r, p)
print(f"Computed a: {a}")

# Step 2: Input the value of e
e = int(input("Enter the value of e: "))

# Step 3: Compute z = (r + e * w) % q
z = (r + e * w) % q
print(f"Computed z: {z}")
```
