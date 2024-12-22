# Special soundness
Since we get two values of a we also get two values of e and z, so we can create simultaneous equations:

![image](https://github.com/user-attachments/assets/5ac7fd55-acec-46ca-8573-3b53ea9c653b)

I send a random `e` to the challenge and it gives me a corresponding `z`

`{"e":115677824981197856990832244499884290782533184865234712278800388984391465891175638661968110321437743148043495463072207489096010036209331178131329795208996}
{"z": 12319415584678195349485912021932893524266688092075699420517681892384353066262631276836688830087493056832664596629598444365737781300608804667346356633292017, "message": "not convinced? I'll happily do it again!"}`

it again generates a an `a` and we give it a random `e` again and it generates a `z`
`{"e":4787839316360225534280846897867459449577351113438067013802169333486109399166993112826844508755986998397974735822631668166962741567504507709471154033054661}
{"z2": 2866721253366839115189629740268048253748386981463157934464079835174930908127388053109706457156161222589252237911573138926303496009595136490067486532815501, "message": "I hope you're convinced I know the flag now. Goodbye :)"}`

i then use this script to solve the equations:

```python3
from Crypto.Util.number import inverse

# Constants from the script
p = 0x1ed344181da88cae8dc37a08feae447ba3da7f788d271953299e5f093df7aaca987c9f653ed7e43bad576cc5d22290f61f32680736be4144642f8bea6f5bf55ef
q = 0xf69a20c0ed4465746e1bd047f57223dd1ed3fbc46938ca994cf2f849efbd5654c3e4fb29f6bf21dd6abb662e911487b0f9934039b5f20a23217c5f537adfaaf7

# Observed values from the script
z = int(input("Enter z (from first challenge): "))
e = int(input("Enter e (from first challenge): "))
z2 = int(input("Enter z2 (from second challenge): "))
e2 = int(input("Enter e2 (from second challenge): "))

# Calculate w
numerator = (z - z2) % q
denominator = (e - e2) % q
denominator_inv = inverse(denominator, q)
w = (numerator * denominator_inv) % q

print(f"Recovered flag (w): {w}")
```

Then i convert w to bytes: `b'crypto{specially_sound_sigmas}\xcb&\x00\xedV6&.\xb5Yfx\x7f\xb9q\x0eV\xe0Ju\xe7%\x88\xd00\xc1\xb1\xf1\xa1\x1e\xffb'`
