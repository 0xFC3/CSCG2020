# Writeup
The ltrace tool can be used to find the encrypted password.
```
strcmp("ivfi", "lp`7a<qLw\036kHopt(f-f*,o}V\017\025J")
```
Then you can use gdb to disassemble the main function. By understanding how the entered password is modified and then compared to the encrypted password in the binary, one can just write a simple python script to decrypt the encrypted password.

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
Connect to the server and enter the password to retrieve the flag.
# Prevention
The real password should be hashed and stored like that in the binary. The entered password should then be hashed with the same algorithm and compared to the real hash.
