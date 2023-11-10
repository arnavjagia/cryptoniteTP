looking into the file using `cat` gave a bunch of random characters. So tried to search for `picoCTF` and used grep

```bash
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ strings ret | grep picoCTF
picoCTF{H
Password correct, please see flag: picoCTF{3lf_r3v3r5ing_succe55ful_9ae85289}
```

got the flag 

```
picoCTF{3lf_r3v3r5ing_succe55ful_9ae85289}
```