+++
author = "kernel-panic"
categories = ["Security"]
date = "2018-05-17T03:55:42+07:00"
description = "Security is a very important topic and has gained a lot of prominence in recent years."
featured = "Website%20Security.png"
featuredalt = "Website Application Security"
featuredpath = "https://github.com/zakybstrd21215/site/raw/master/static/uploads/2018/05/17"
linktitle = ""
title = "Website Security, is it important?"
type = "post"

+++
Halo, pada kesempatan kali ini saya akan membahas sedikit mengenai _Website Security_. Oh iya, mohon maaf, sesi Nebula belum saya lanjut dan untuk saat ini saya tunda dulu.

_Let's back to topic.._

Keamanan adalah topik yang sangat penting dan telah mendapatkan banyak perhatian dalam beberapa tahun terakhir.

Mengembangkan aplikasi Web yang aman adalah tugas yang sangat sulit saat ini, karena ada beberapa teknologi yang terlibat dan akibatnya beberapa jenis serangan yang dapat dilakukan terhadap aplikasi Web, dengan kerentanan baru dan serangan yang datang dari waktu ke waktu.

Di  perusahaan, secara _general_, adalah umum untuk menemukan beberapa lingkungan infrastruktur dengan perangkat lunak yang ketinggalan jaman seperti sistem operasi, DBMS, server aplikasi, dan _library_ pada umumnya.

Tetapi sebagian besar serangan terjadi karena kerentanan hadir dalam aplikasi itu sendiri. Pengembang perangkat lunak memiliki peran yang sangat penting untuk mengkodifikasi algoritma terbaik dan memiliki pengetahuan tentang berbagai teknologi dan standar untuk pengembangan Web dan administrator sistem untuk  merancang dan memelihara lingkungan infrastruktur yang baik.

Dalam skenario ini peran profesional keamanan sangat dibutuhkan untuk membuat analisis dan tes keamanan bersama dengan tim pengembangan sistem dan _sysadmin_. Oleh karena itu, sangat penting bahwa perusahaan cukup berinvestasi dalam keamanan informasi, agar tidak kehilangan kepercayaan klien mereka dan menghindari kemungkinan kerugian.

#### Mari bahas beberapa kerentanan yang umumnya ditemukan di aplikasi Web

* **SQL Injection**

Hal yang unik dari serangan ini adalah perintahnya yang sederhana, tetapi serangan ini dapat menyebabkan kerusakan besar. Contoh ilustratif dari serangan ini yaitu mencoba memasukkan pernyataan SQL yang berfungsi untuk menghapus semua rekaman dari tabel aplikasi pengguna. 

Selain memasukkan perintah SQL untuk menghapus informasi aplikasi, dapat juga memasukkan perintah untuk mendapatkan informasi pengguna yang sensitif. Seperti halnya kejadian yang menimpa perusahaan besar seperti Yahoo, eBay di masa lalu.

_Sample Case:_

Nama pengguna: \[‘or 1 or‘ a ’=‘ a\]  
Kata Sandi: \[\* \* \* \* \* \* \* \* \*\]

Dalam  contoh lain ini, kita menguji kemungkinan menggabungkan parameter login dan kata sandi secara langsung dalam _String_ yang merakit perintah SQL.

Jika terdapat kerentanan dalam sebuah form login aplikasi, maka akan menghasilkan pernyataan SQL:

**select \* from users where login = ” or 1 or ‘a’ = ‘a’ and password = ‘12345678’**

**Final result: FALSE or TRUE OR True AND false**

Dan operasi logis ini akan menghasilkan _true_, seolah-olah permintaan telah menyampaikan registri pengguna yang valid dari database, sehingga menyebabkan masuk ke dalam aplikasi secara normal.

* **Cross-site Scripting**

Saya belajar tentang kerentanan ini beberapa tahun yang lalu, ketika saya menyelidiki serangan oleh Samy Kamkar, seorang ahli keamanan yang menulis kode JavaScript berbahaya. Serangan itu dilakukan di situs Myspace, yang pada masanya dianggap sebagai jaringan sosial terbesar di internet. (Untuk cerita Samy Kamkar ini bisa kalian akses informasi lebih lanjutnya di: [https://samy.pl/myspace/](https://samy.pl/myspace/ "https://samy.pl/myspace/"))

Dalam kasus MySpace, risiko terjadi karena aplikasi menerima kode JavaScript yang diinjeksikan ke bidang formulir web, karena kurangnya perlakuan yang memadai atas informasi yang dimasukkan oleh pengguna.

Dalam serangan ini, tujuannya adalah mengirim perintah JavaScript yang akan dieksekusi oleh browser korban, untuk mengelabuinya. Perusahaan-perusahaan besar seperti Twitter dan Orkut telah memperkenalkan kerentanan pada pertengahan tahun 2005.

* **Cross-Site Request Forgery**

Serangan ini lebih rumit karena kita perlu mengetahui teknologi yang akan kita serang, serta mengetahui dengan baik model otentikasi dan penggunaan cookie dan sesi. Saya tidak akan menjelaskan lebih lanjut mengenai CSRF ini, karena jika dibahas, artikel ini akan terlalu panjang.

Untuk mempelajari lebih lanjut tentang serangan ini dan hal lainnya, serta cara mencegahnya dalam aplikasi Web, saya sarankan Anda mengikuti project **OWASP** ([https://owasp.org](https://owasp.org "https://owasp.org")), komunitas/organisasi terbuka terkemuka yang berfokus pada keamanan aplikasi.

Bagi kalian yang bekerja atau sedang belajar tentang bidang keamanan informasi, saya sangat menyarankan untuk menganalisa dan menguji aplikasi OWASP Juice Shop Project: [https://www.owasp.org/index.php/OWASP_Juice_Shop_Project](https://www.owasp.org/index.php/OWASP_Juice_Shop_Project "https://www.owasp.org/index.php/OWASP_Juice_Shop_Project").

Project tersebut berfokus pada praktik CTF. CTF adalah singkatan dari Capture the Flag. Untuk CTF ini pernah saya bahas sebelumnya di: [https://muhammadzakyzulfiqor.xyz/article/ctf-what-they-mean-for-security/](https://muhammadzakyzulfiqor.xyz/article/ctf-what-they-mean-for-security/ "https://muhammadzakyzulfiqor.xyz/article/ctf-what-they-mean-for-security/")

<div class="videoyoutube"> <div class="video-responsive"> <iframe allowfullscreen="1" class="embedded-video-large" src="https://www.youtube.com/embed/62Mj0ZgZvXc?rel=0"></iframe> </div> </div>

Saya ingin berbagi lebih banyak di waktu luang saya. Saya harap Anda menemukan sesuatu yang mendatangkan nilai bermanfaat bagi Anda. _See you next time.._