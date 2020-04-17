# Writeup
This challenge can be solved with the Chinese remainder theorem. A lot of things point to this solution. First, e is 3. So it is as small as it can be. Second, the challenge includes three pairs of keys, which all tell the same message. And lastly, the challenge description talks about China, which again points to the Chinese remainder theorem. 

To solve the challenge I used this tool: [https://github.com/JulesDT/RSA-Hastad](url)
The following command spits out the flag:
```
python rsaHastad.py <n0 File> <n1 File> <n2 File> <c0 File> <c1 File> <c2 File>
```
# Prevention
e should be a lot bigger than 3. e = 65537, would be a good public exponent.
