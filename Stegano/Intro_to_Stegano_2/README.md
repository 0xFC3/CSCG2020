# Write Up
When uploading the image to the website [https://tineye.com/](url), one can find the original image and compare it to the challenge file. It stands out, that the upper left corner of the tallest building is different from the original image. That hints, that the flag is hidden in that part of the image. Each window is either lit or not lit. Lit stands for 1 and not lit stands for 0. Combining all the windows spits out a binary string, which can be converted to ascii by a simple python script.
```python
bin_string = '01000011 01010011 01000011 01000111 01111011 01100001 01011111 01000110 01101100 00110100 01100111 01111101'
binary_values = bin_string.split()
print(binary_values)
flag = ''

for binary_value in binary_values:

    an_integer = int(binary_value, 2)


    ascii_character = chr(an_integer)

    flag += ascii_character

print(flag
```
