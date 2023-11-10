Here as suggested in the problem the text file is archived multiple times using different algorithms. Recursively unzipping the archives using the respective tools we end up with a text file

```bash
PS C:\Users\Arnav\Documents\CTF> wsl
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ ls Flag.pdf
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ file Flag.pdf
Flag.pdf: shell archive text
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ sh Flag.pdf
x - created lock directory _sh00046.
x - extracting flag (text)
x - removed lock directory _sh00046.
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ ls
Flag.pdf  flag
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ binwalk flag

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
100           0x64            bzip2 compressed data, block size = 900k

arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ binwalk -e flag

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
100           0x64            bzip2 compressed data, block size = 900k

arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ ls
Flag.pdf  _flag.extracted  flag
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ cd *.ex*
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ ls
64
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: gzip compressed data, was "flag", last modified: Thu Mar 16 01:40:15 2023, from Unix, original size modulo 2^32 328
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.gz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ gunzip 64.gz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ ls
64
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: lzip compressed data, version: 1
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.lz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ lunzip 64.lz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ ls 64
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: LZ4 compressed data (v1.4+)
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.lz4
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ lz4 -d 64.lz4
Decoding file 64
64.lz4               : decoded 266 bytes
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ ls
64  64.lz4
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: LZMA compressed data, non-streamed, size 255
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.lzma
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ lzma -d 64.lzma
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ ls
64  64.lz4
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: lzop compressed data - version 1.040, LZO1X-1, os: Unix
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.lzo
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ lzop -d 64.lzo
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: lzip compressed data, version: 1
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.lz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ lunzip 64.lz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: XZ compressed data, checksum CRC64
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ mv 64 64.xz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ xz -d 64.xz
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ ls
64  64.lz4  64.lzo
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ file 64
64: ASCII text
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF/_flag.extracted$ cat 64
7069636f4354467b66316c656e406d335f6d406e3170756c407431306e5f
6630725f3062326375723137795f33633739633562617d0a
```

The text file is then converted to ASCII using an ASCII converter to give the flag

`picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_3c79c5ba}`