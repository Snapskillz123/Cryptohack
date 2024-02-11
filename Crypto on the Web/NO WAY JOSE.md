# NO WAY JOSE

Looking at the source code provided, the username needed to be admin butthe token needed to be found.
Suingt he header for the JOSE in the question, i put it in an online tool to geta JWT.
I then changed the value from false to true to change the data so we can get the flag because the flag would come if it was {admin: false}
In the question it told that JWTs can be exploited if algorithm is set to 'none'. so I put algotrithm to none and converted it into base64.

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/7390e715-175b-4277-9e2e-bc6c85243ddc)

I then replacedthe original header with this header(remove padding) and put it in the token entry box and i got a flag

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/341c1adf-3c47-4c68-af03-0385548f6ab1)

  # Flag

  crypto{The_Cryptographic_Doom_Principle}


