# Writeup
As the password is in the binary as plaintext, it can be retrieved by the following command.
```
strings rev1
```
-->
```
[]A\A]A^A_
Give me your password: 
y0u_5h3ll_p455
Thats the right password!
Flag: %s
Thats not the password!
./flag
```

Connect to the server and enter the password to retrieve the flag.
# Prevention
The real password should be hashed and stored like that in the binary. The entered password should then be hashed with the same algorithm and compared to the real hash.
