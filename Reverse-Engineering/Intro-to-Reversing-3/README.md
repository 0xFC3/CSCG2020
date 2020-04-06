# Write Up

ltrace to find encrypted password.
```
strcmp("ivfi", "lp`7a<qLw\036kHopt(f-f*,o}V\017\025J")
```

Python Script to solve the challenge: 
```python
crypt_pass = 'lp`7a<qLw\036kHopt(f-f*,o}V\017\025J'

real_pass = ''
x = 0
for i in crypt_pass:
    real_pass += hex((int('0x' + i.encode('hex'), 16)+ 0x2)^(x + 0xa))[2:].decode('hex')
    x += 1    
print(real_pass)
```

Connect to server and enter password to retrieve flag.
