+++
author = "kernel-panic"
categories = ["Security", "Nebula"]
date = "2018-01-08T00:00:00Z"
description = "Security Wargames"
featured = "m46370318112.jpg"
featuredalt = "Nebula Level00"
featuredpath = "https://beeimg.com/images"
linktitle = ""
title = "Exploit Exercises - Nebula Level00"
type = "post"

+++
Nah, inilah salah satu cara saya menghabiskan waktu sambil belajar, yaitu mengambil beberapa tantangan dan praktik pengkodean. Dimulai dengan Nebula, saya akan menjelaskan beberapa panduan solusi _level-by-level_ (00-19). Sebenarnya dulu saya sempat memainkan _Security Wargames_ Nebula ini, namun dulu saya tidak sempat menuntaskannya sampai level terakhir.

Disini saya akan membagi setiap level menjadi sebuah posting terpisah agar memudahkan bagi seseorang yang hanya mencari petunjuk pada satu level saja.

Di {{< url-link "level00" "https://exploit-exercises.com/nebula/level00/" "target">}} mengharuskan kamu untuk menemukan program Set User ID yang akan dijalankan sebagai akun "flag00". Petunjuk dalam bagian "About" menyuruh kita untuk memeriksa halaman man perintah find.

Saya sangat akrab dengan perintah find dari tugas SysAdmin saya di tempat kerja, jadi satu liner cepat harus bisa melakukan triknya.

Perintah di bawah ini akan mencari seluruh filesystem untuk file apapun dengan izin SUID yang dimiliki oleh pengguna flag00. Bagian terakhir dari perintah '2>/dev/null' mengirimkan error standar ke /dev/null untuk menghindari membanjiri layar dengan pesan izin yang ditolak.

    level00@nebula:~$ find / -perm -4000 -user flag00 2>/dev/null
    /bin/.../flag00

Outputnya mengidentifikasi program SUID dalam direktori "hidden" yang memenuhi spesifikasi perintah find. Saya merujuk ke direktori "hidden" karena jika kamu menjalankan perintah ls di direktori itu (tanpa bendera tambahan), direktori tidak akan muncul dalam output.

Mari menjalankan program SetUID:

    level00@nebula:~$ /bin/.../flag00
    Congrats, now run getflag to get your flag!
    flag00@nebula:~$ getflag
    You have successfully executed getflag on a target account
    flag00@nebula:~$ id
    uid=999(flag00) gid=1001(level00) groups=999(flag00),1001(level00)

Dan sukses! Menjalankan program SetUID meningkatkan hak akses menjadi pengguna flag00.

Tingkat pertama ini nampak sederhana namun mengajarkan konsep yang sangat penting dalam keamanan Linux. SetUID adalah jenis hak akses file khusus yang diberikan ke file. Ketika sebuah program memiliki bit SUID (-rwsr-x---), file tersebut berjalan sebagai pemilik file sebagai ganti mewarisi hak akses pengguna yang masuk.

Program ini memerlukan izin root untuk melakukan tugas tertentu dan mengubah file tertentu pada sistem. Administrator sistem harus sangat berhati-hati saat menyetel setuid dan setguid karena penggunaan mode akses ini tidak semestinya dapat menyebabkan kompromi sistem.

<div class="videoyoutube">
<div class="video-responsive">
<iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/MXUJFTnAY1E?rel=0"></iframe>
</div>
</div>