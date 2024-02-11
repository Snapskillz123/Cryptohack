# JWD secrets

I analysed the source code provided and instead of the default key they used SECRET_KEY. I then made my own token by changing false to true and keeping the key as the default key-"secret".

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/139c6cd6-2f5e-4c51-ac8d-798272011f84)

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/ebc06f27-698c-4179-804e-e9c2eda060ff)

I used the token i made and put it in the entry box and got the required flag.

![image](https://github.com/Snapskillz123/Cryptohack/assets/149099858/6a49dacf-43f3-4c70-adaf-0c996ea6babf)

  # Flag

  crypto{jwt_secret_keys_must_be_protected}


