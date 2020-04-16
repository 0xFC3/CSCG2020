# Writeup
When looking at the different channels of the picture with Stegsolve for example, one can find a password: 
```
s33_m3_1f_y0u_c4n
```
Binwalk is always a great tool, to look if the image file has more files hidden in it. And in this case, it does spit out the zip archive 4903C.zip.  This file can be unzipped with 7zip.
```
7z e 4903C.zip
```
But it asks for a password, which we have :) --> enter password --> flag is extracted.
