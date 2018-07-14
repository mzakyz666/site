+++
author = "kernel-panic"
categories = ["Security"]
date = "2018-07-15T04:00:00+07:00"
description = "Do you believe your IoT device is secure?"
featured = "Internet%20of%20Hackable%20Things.jpg"
featuredalt = "Internet of Hackable Things"
featuredpath = "https://github.com/zakybstrd21215/site/raw/master/static/uploads/2018/07/14"
linktitle = ""
title = "The Internet of Hackable Things"
type = "post"

+++
Internet of Things, atau dikenal juga dengan singkatan IoT, merupakan sebuah konsep yang bertujuan untuk memperluas manfaat dari konektivitas internet yang tersambung secara terus-menerus. Adapun kemampuan seperti berbagi data, remote control, dan sebagainya, termasuk juga pada benda di dunia nyata. Contohnya bahan pangan, elektronik, koleksi, peralatan apa saja, termasuk benda hidup yang semuanya tersambung ke jaringan lokal dan global melalui sensor yang tertanam dan selalu aktif.

Pada dasarnya, Internet of Things mengacu pada benda yang dapat diidentifikasikan secara unik sebagai representasi virtual dalam struktur berbasis Internet. Istilah Internet of Things awalnya disarankan oleh Kevin Ashton pada tahun 1999 dan mulai terkenal melalui Auto-ID Center di MIT.Dan kini IoT menjadi salah satu tugas bagi seorang mahasiswa di sebuah perguruan tinggi.

Cara Kerja Internet of Things yaitu dengan memanfaatkan sebuah argumentasi pemrograman yang dimana tiap-tiap perintah argumennya itu menghasilkan sebuah interaksi antara sesama mesin yang terhubung secara otomatis tanpa campur tangan manusia dan dalam jarak berapa pun.Internetlah yang menjadi penghubung di antara kedua interaksi mesin tersebut, sementara manusia hanya bertugas sebagai pengatur dan pengawas bekerjanya alat tersebut secara langsung.

Tantangan terbesar dalam mengkonfigurasi Internet of Things yaitu menyusun jaringan komunikasinya sendiri, yang dimana jaringan tersebut sangatlah kompleks, dan memerlukan sistem keamanan yang ketat. Selain itu biaya yang mahal sering menjadi penyebab kegagalan yang berujung pada gagalnya produksi.

Internet of Things (IoT) telah menjadi topik yang hangat untuk dibicarakan akhir-akhir ini. IoT tidak hanya menjadi suatu konsep yang mempengaruhi hidup manusia tetapi bagaimana IoT bisa membantu memudahkan kehidupan manusia.

## Examples of IoT Hacking and Vulnerabilities

Dengan hanya memanfaatkan ribuan perangkat IoT yang tidak aman, hacker dapat meluncurkan serangan DDoS yang dapat melumpuhkan infrastruktur, sistem, dsb. Atau, penyerang dapat secara langsung mengeksploitasi perangkat dan menggunakannya sebagai pintu gerbang menuju ke tingkat yang lebih dalam dari sebuah jaringan di mana mereka bisa mengumpulkan data pribadi yang sensitif dan berharga.

Dan ini bisa jadi memacu kejadian yang lebih buruk. Para peneliti memperkirakan nanti tahun 2025, akan ada lebih dari 80 miliar perangkat IoT di dunia ini. Sebagian besar firmware tertanam yang berjalan pada perangkat ini tidak aman dan sangat rentan.

Dampak dari kerentanan IoT ini mungkin sering dianggap sepele, tapi dampaknya bisa sampai melayangkan nyawa seseorang. Bisa melayangkan nyawa dan membunuh seseorang loh, ngeri kan?

Nah, ini beberapa contoh permasalahan terkait IoT yang terekam jejaknya:

#### Mirai Botnet

Tentang mirai bisa baca-baca di: [https://errorcybernews.com/2016/12/23/mirai-iot-botnet-dan-mitigasi-ddos-attack/](https://errorcybernews.com/2016/12/23/mirai-iot-botnet-dan-mitigasi-ddos-attack/ "https://errorcybernews.com/2016/12/23/mirai-iot-botnet-dan-mitigasi-ddos-attack/")

Source code Mirai: [https://github.com/zakybstrd21215/Mirai-Source-Code](https://github.com/zakybstrd21215/Mirai-Source-Code "https://github.com/zakybstrd21215/Mirai-Source-Code")

#### Perangkat Medis

Nah karena kerentanan perangkat IoT yang digunakan dalam dunia medis, kerentanan ini bisa sampai mengancam nyawa seseorang melayang. Beberapa kasus kerentanan IoT dalam perangkat medis bisa baca-baca dulu di:

* [https://errorcybernews.com/2017/06/06/kerentanan-dalam-pacemakers/](https://errorcybernews.com/2017/06/06/kerentanan-dalam-pacemakers/ "https://errorcybernews.com/2017/06/06/kerentanan-dalam-pacemakers/")
* [https://errorcybernews.com/2017/03/29/washer-disinfector-hacked/](https://errorcybernews.com/2017/03/29/washer-disinfector-hacked/ "https://errorcybernews.com/2017/03/29/washer-disinfector-hacked/")
* [https://errorcybernews.com/2017/09/13/kerentanan-dalam-pompa-infus/](https://errorcybernews.com/2017/09/13/kerentanan-dalam-pompa-infus/ "https://errorcybernews.com/2017/09/13/kerentanan-dalam-pompa-infus/")

Saya hanya mengambil 2 contoh kasus, tapi jika bicara tentang IoT ini masih banyak cakupannya jika dieksplorasi. Seperti: Thingbots, RFID, Home Automation, Connected Doorbell, Hub, Smart Coffee, Wearable, Smart Plug, Kamera, Lampu Lalu Lintas, Otomotif (seperti mobil otomatis), Pesawat, Lampu, Smart Lock, Smart Scale, Smart Meter, Termostat, Fridge, Media Player & TV, Senjata, Toilet, Mainan, dll.

Dari beberapa kasus yang terjadi, saya meringkas beberapa permasalahan inti yang bisa memicu kerentanan akan perangkat IoT ini:

#### 1. Hardware Hacking

* Port sensitif yang terekspos
* Akses ke konsol root/informasi sensitif melalui port debugging
* Mengganti firmware asli dengan firmware berbahaya (contoh: firmware yang sudah disisipi malware)
* Sniffing/Tapping untuk menemukan informasi sensitif dari komunikasi

#### 2. Komponen Web, Mobile dan Jaringan

* Otentikasi/otorisasi tidak aman
* Kerentanan dalam API
* Layanan jaringan yang tidak aman berjalan di perangkat
* Informasi sensitif dalam aplikasi seluler tidak dienkripsi
* Kerentanan di dasbor web

#### 3. Kerentanan dalam Firmware

* Kredensial akun/sertifikat key/sertifikat API dan informasi sensitif lainnya dalam firmware tidak dienkripsi
* Bisa mengekstrak sistem file dari firmware
* Mengsimulasikan/menduplikat firmware dan debugging binari untuk menemukan kerentanan (contoh: overflow)

#### 4. Radio

* Sniffing komunikasi sensitif dalam berbagai protokol komunikasi radio seperti BLE, ZigBee, raw radio, dll.
* Mengubah dan memutar ulang lalu lintas yang ditangkap untuk mengambil alih perangkat target
* Meretas saluran komunikasi dan mengambil alih perangkat target
* Membingungkan protokol komunikasi untuk menemukan bug dan menyebabkan crash

#### 5. Human Error

* Mengkonfigurasi perangkat dengan tidak benar/tidak aman
* Kredensial akun default

Berikut beberapa tips/langkah awal untuk menghindari terjadinya peretasan perangkat IoT:

1. Pelajari cara menjaga keamanan perangkat IoT. Pengguna harus melindungi perangkat IoT dengan cara yang sama seperti smartphone, tablet, dan komputer rumah. Cari cara untuk mengatur kata sandi yang kuat, membaca manual untuk instruksi tentang cara bagaimana mengunci perangkat agar terjaga dengan aman.
2. Bersihkan aplikasi yang memang sudah tidak digunakan. Banyak dari kita cenderung menyimpan aplikasi tanpa batas, bahkan jika kita tidak menggunakannya. Periksa perangkat secara berkala dan hapus aplikasi yang tidak lagi digunakan.
3. Pahami informasi apa saja yang dikumpulkan perangkat dan bagaimana cara perangkat itu mengelola dan menyimpannya.
4. Lakukan penelitian. Sebelum membeli perangkat IoT, lakukan pencarian untuk mengetahui apakah ada masalah keamanan dengannya dan apakah dapat diretas dengan mudah.
5. Ubah pengaturan kredensial akun default pada perangkat.
6. Jika bisa, gunakan aplikasi/alat untuk keamanan perangkat IoT atau gunakan layanan penyedia jasa solusi keamanan IoT.