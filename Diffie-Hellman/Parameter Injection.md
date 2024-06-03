# Parameter Injection

They've provided us with a netcat command and port.

The question tells us that we can avoid using discrete log function by a shortcut which is using a parameter to bypass it.

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/4091dec5-a8c0-4fac-8d20-e1440ec570f1)

WE first send bob random values of A,p and g. After Bob sends the interrupted value of B, we send Alice B,p and g where B is 0x01.

If B=1 then pow(B,a,p) is one which is our secret key.

Using they decryption code of DH Starter 5 question they flag comes 

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


shared_secret = 1
iv  = '5305d3b421b408fd787654d96602bfbc'
ciphertext = 'ab24b66bfd3d13e7f7ec13d751aa4605047488d502aa969c4e3db303e127e566'

print(decrypt_flag(shared_secret, iv, ciphertext))
```
  # Flag

  crypto{n1c3_0n3_m4ll0ry!!!!!!!!}
