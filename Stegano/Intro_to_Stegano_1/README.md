#Write Up

When executing the ***file*** command on the challenge file, one notices the comment ```alm1ghty_st3g4n0_pls_g1v_fl4g```. Combining that comment with the steghide tool, the flag is retrieved. 
```
steghide extract -sf chall1.jpg -xf output.txt
```
The passphrase is the comment. The flag is then exported into the ```output.txt``` file.
