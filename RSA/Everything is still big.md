# Everything is still big

we've been given n e and c in hexadecimal, so we first convert it into decimal.

then we find the factors and all and put it in a program.

```
from Crypto.Util.number import inverse, long_to_bytes

# Given values
n = ...  
e = ...  
c = ...  
# p = ...
# q = ...
p = ...
q = ...

phi = (p - 1) * (q - 1)

d = inverse(e, phi)

m = pow(c, d, n)
message = long_to_bytes(m)

print("Decrypted message:", message)
```
