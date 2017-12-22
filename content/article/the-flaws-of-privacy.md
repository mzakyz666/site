+++
author = "kernel-panic"
categories = ["Security"]
date = "2017-12-21"
description = "Bagaimana kerentanan ini bisa dieksploitasi?"
featured = "enQpC6/Background_Privacy.jpg"
featuredalt = "Privacy"
featuredpath = "https://image.ibb.co"
linktitle = ""
title = "The Flaws of Privacy"
type = "post"
+++

"Privasi" adalah konsep yang menarik, dan sangat disalahpahami, dalam bidang TI. Banyak kekurangan keamanan online bisa berawal dari kesalahpahaman ini, maka relevansinya dengan jelas semua ini. Topik ini relevan untuk perspektif keamanan dan pemrograman.

Privasi untuk manusia adalah, (sebagian besar) sederhana. Ketika kita mengatakan kepada seseorang "ini pribadi", orang tersebut mengerti "jangan tunjukkan pada siapa pun", tapi hal tersebut adalah konsep manusia, bukan konsep mesin.

Privasi untuk mesin berarti sama tapi diterapkan secara berbeda. Saat kita menunjukkan "ini pribadi", mesin itu mengerti "jangan tunjukkan pada manusia lain". Inilah sebabnya mengapa penting untuk menguji pengaturan privasi saat meletakkan sesuatu secara online: hanya karena ada sesuatu yang mengatakan "pribadi", tidak berarti sebenarnya.....

## Bagaimana kesalahpahaman ini bisa berasal dari kerentanan?

Ketika sebuah situs web dirancang, perancang membuat menu "pengaturan privasi" dan menambahkan opsi untuk membuat sesuatu menjadi pribadi. Dia juga dapat meminta otentikasi, seperti login yang valid, atau meminta pembayaran (untuk membaca/melihat kekayaan intelektual atau menghindari pembajakan).

Masalahnya adalah ketika "privasi" ini tidak sepenuhnya diuji atau bahkan dipahami dari "sudut pandang" mesin. Hal ini memungkinkan orang untuk mengelabui website. Jika "_private_" berarti tidak dapat dibagi dengan manusia, setiap manusia yang mencoba mengakses file akan diminta untuk otentikasi atau diblokir.

Tapi bagaimana kalau mesin meminta mesin lain?

## Bagaimana kerentanan ini dieksploitasi?

Ini tidak terjadi di semua situs web, namun terjadi pada beberapa situs web. Beberapa situs web dapat memblokir salah satu kerentanan ini namun memungkinkan yang lain. Hacker dapat menggunakan "kesalahpahaman" ini untuk mengelabui beberapa situs web, melewati beberapa mekanisme ini, dengan menggunakan mesin untuk meminta mesin lain.

Berikut adalah beberapa contohnya:

* Contoh bagusnya adalah meminta Google untuk mencari beberapa file tertentu. Karena peretas tidak dapat mengakses situs web dan biasanya mendapatkan file tersebut, dia dapat meminta Google menggunakan operator "filetype:", jika Google bisa mendapatkan file tersebut. Di beberapa situs web, karena mesinnya meminta mesin lain, itu diperbolehkan.
* Contoh lainnya adalah ketika kita ingin melihat gambar di situs jejaring sosial. Jika kita "klik kiri" thumbnail, lalu meminta kita untuk memasukan akun atau login, (memaksa kita untuk menerima persyaratan layanan dan privasi untuk melihatnya), tapi jika kita "klik kanan" dan pilih "open in new tab", karena browser bertanya, alih-alih tombol yang dioperasikan secara manual (AKA = Human), itu akan memuat gambarnya.
* Contoh bagus lainnya adalah menggunakan cache Google untuk melihat profil terperinci di jejaring sosial (seperti contoh sebelumnya, kami tidak dapat melihatnya tanpa akun), atau topik yang ada, karena itu hanya untuk anggota saja, membutuhkan login yang valid.
* Contoh lainnya adalah menggunakan beberapa program untuk mengubah "_user agent_" dan menjadi sesuatu seperti "Google Bot", untuk memungkinkan melihat konten situs web tanpa diminta untuk membayar pembayaran atau otentikasi dan menipu pengaturan privasi situs web.

Semua contoh ini ada dan cukup umum. Saya telah menguji dan menemukan semuanya, terkadang dengan sedikit bahaya, dan kadang-kadang mengungkapkan informasi pribadi yang sensitif. "Private" hanya membuat filter, tapi ada banyak cara untuk memotong filter itu jika tidak dikonfigurasi dengan benar.

Google bukan satu-satunya mesin yang bisa kita coba "_trick to ask_" mesin lain. Mesin pencari hanya bisa mengindeks apa yang mereka diizinkan (dalam konfigurasi robots.txt), dan terkadang, mereka tidak diizinkan untuk melihat konten.

Ketika itu terjadi, peretas mencoba metode lain seperti "buka di tab baru" untuk menghindari tombol yang dioperasikan secara manual, atau hacking URL (mengubah URL secara langsung untuk menavigasi direktori di situs web). Semua itu dan lebih bisa digunakan, semua didasarkan pada kekurangan konsep "privacy".

_Harap diperhatikan: Saya menggunakan istilah "hacker" tapi tidak dengan makna negatif. "Hacker" disini digunakan sebagai seseorang yang mencoba untuk bend aturan privasi, terlepas dari niat._

