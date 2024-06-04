# Export-grade

On using the netcat command given, it provides us with different types of Diffie-Hellman types with keys of different sizes

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/aac94ba4-ae7c-4377-aace-527bf1e3b7ae)

I picked DH64 so that the discrete log problem will be easier.

Using this site: https://www.alpertron.com.ar/DILOG.HTM 

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/23ee2e0e-55c3-4aa8-a4ad-287f457654fc)

It gives a discrete log equation where k is an integer, so ran a code to check for what value of k does the Diffie Hellman equation work.

```
def verify_solution(A, g, p, a):
    return pow(g, a, p) == A

# Example values
A = 1572012706310995543  # public value A
g = 2  # generator g
p = 16007670376277647657  # prime modulus p
a = 2372095968249888631

for k in range(0,100):
    a=a+(8003835188138823828*k)
    if verify_solution(A, g, p, a):
        print(f"The private key 'a' = {a} is valid.")
        break
    else:
        print(f"The private key 'a' = {a} is not valid.")
```
From the above code i get a.

Then i perform B^a mod p to get the secret key.

After that I used the decryption code given in a previous question to get the flag.

```
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
import hashlib


def is_pkcs7_padded(message):
    padding = message[-message[-1]:]
    return all(padding[i] == len(padding) for i in range(0, len(padding)))


def decrypt_flag(shared_secret: int, iv: str, ciphertext: str):
    # Derive AES key from shared secret
    sha1 = hashlib.sha1()
    sha1.update(str(shared_secret).encode('ascii'))
    key = sha1.digest()[:16]
    # Decrypt flag
    ciphertext = bytes.fromhex(ciphertext)
    iv = bytes.fromhex(iv)
    cipher = AES.new(key, AES.MODE_CBC, iv)
    plaintext = cipher.decrypt(ciphertext)

    if is_pkcs7_padded(plaintext):
        return unpad(plaintext, 16).decode('ascii')
    else:
        return plaintext.decode('ascii')


shared_secret = 4818617755394763736
iv  = 'b5c0d814df441d3b22d3bbb07f494c7e'
ciphertext = 'e65dfbb8b34afff63cc7b89d07fa18522f4342ce10ccec04d619c3fd7d92fe25'

print(decrypt_flag(shared_secret, iv, ciphertext))
```

  # Flag

  crypto{d0wn6r4d35_4r3_d4n63r0u5}

