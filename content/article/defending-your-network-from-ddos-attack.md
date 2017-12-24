+++
author = "kernel-panic"
categories = ["Security"]
date = "2017-12-24"
description = "What should I do?"
featured = "images/w63205709011.jpg"
featuredalt = "DDoS Attack"
featuredpath = "https://beeimg.com"
linktitle = ""
title = "Defending Your Network From DDoS Attack"
type = "post"
+++

Serangan ini - yang disebut serangan "*Distributed Denial of Service*" atau serangan "*DDoS*" - seringkali bisa menjadi intens, melibatkan ratusan ribu komputer di seluruh dunia dan sejumlah besar trafik. Mereka dapat berlangsung berjam-jam atau berhari-hari tergantung pada maksud dari penyerang, membuat situs web, server atau seluruh jaringan menjadi tidak berfungsi selama serangan berlangsung.

Bagi lembaga keuangan mereka bisa sangat bermasalah karena dapat mencegah nasabah menyelesaikan transaksi, atau bahkan berdampak pada transaksi bank-ke-bank.

Memang, "*Laporan Investigasi Pelanggaran Data Verizon 2015 (DBIR) menunjukkan bahwa serangan DDoS adalah bentuk serangan yang paling umum terhadap bisnis jasa keuangan, menyumbang 32% dari semua serangan yang dianalisis dalam laporan tersebut*". Serangan semacam ini telah tumbuh secara eksponensial di 2015, dan masih berlanjut menjadi ancaman berbahaya sampai hari ini.

Saya menggambarkan serangan DDoS di bawah ini dan membahas solusi perangkat keras serta cloud yang bisa membantu mengatasi dan mengurangi dampak serangan DDoS sebelum mereka dapat membahayakan perusahaan atau membuat frustrasi pelanggannya.

## Apa itu serangan DDoS?

Secara umum, serangan DDoS adalah jenis serangan cyber yang menggunakan sejumlah besar komputer dan sejumlah besar traifk untuk menguasai server atau jaringan, memperlambat atau membuatnya sama sekali tidak responsif.

Serangan DDoS pada umumnya mengharuskan penyerang mengendalikan ribuan, puluhan ribu atau ratusan ribu komputer - biasanya dari perangkat yang dimiliki oleh pengguna normal di seluruh dunia - dan membuat mereka menjadi milik penyerang sendiri, atau yang biasa disebut "komputer zombie".

Jaringan komputer yang besar ini kemudian digunakan untuk memusatkan trafik, seperti permintaan sederhana untuk melihat halaman web atau sesuatu yang lebih berbahaya, pada satu target atau kelompok sasaran. Server atau jaringan yang ditargetkan, yang tidak dirancang untuk menangani permintaan simultan dari sejumlah besar sistem, sering macet atau berhenti merespons sepenuhnya.

Jumlah lalu lintas yang dihasilkan oleh serangan ini sangat besar.

Meskipun ada beberapa varian serangan DDoS, empat varian "utama" adalah sebagai berikut:

### Serangan Flooding atau Volumetric

Serangan Flooding mengirimkan sejumlah besar trafik ke jaringan korban untuk mengesampingkan jaringan dengan trafik. Dengan trafik yang cukup (yang hari ini, jauh lebih mudah melalui penggunaan botnet dan alat serangan DDoS lainnya), trafik menabrak jaringan korban sehingga pengguna yang sah tidak dapat mengakses akun mereka atau melakukan akses secara online.

### Serangan Amplification

Serangan DDoS berbeda yang "memanipulasi sistem nama domain yang dapat diakses publik, membuat mereka membanjiri target dengan paket UDP (*user datagram protocol*) dalam jumlah banyak. Dengan menggunakan berbagai teknik Amplification, pelaku dapat 'mengembangkan' ukuran paket UDP ini, sehingga membuat serangan begitu kuat hingga menjatuhkan infrastruktur Internet yang paling kuat sekalipun."

Seringkali paket penyerangan dipalsukan untuk menyembunyikan asal-usulnya, baik dari serangannya atau untuk mengalahkan pertahanan firewall potensialnya.

### Serangan Resource Depletion

Serupa dengan serangan Amplification, serangan Resource Depletion membanjiri server korban dengan paket informasi palsu untuk merebut server, sehingga tidak dapat merespon permintaan informasi yang sah.

### Serangan Diversion atau Ransom

Terakhir, pada vektor serangan ini, penyerang memulai tindakan DDoS terhadap server korban untuk mengalihkan perhatian tim keamanan dan responden insiden sementara penyerang menggunakan metode yang berbeda untuk menembus jaringan. Salah satu varian populer dari serangan ini adalah membanjiri server korban terus-menerus sampai mereka membayar uang tebusan (biasanya dengan Bitcoin).

Varian kedua dari serangan ini adalah untuk mengalihkan tim responden insiden dengan serangan DDoS skala besar sambil menanamkan malware atau trojan di jaringan yang dirancang untuk mencuri data, informasi, atau PII, atau memanfaatkan kerentanan yang diketahui.

## Pertahanan untuk serangan DDoS

Meskipun tidak selalu mungkin untuk mempertahankan diri dari serangan DDoS yang besar dan terorganisir tanpa ada dampak pada jaringan yang ditargetkan, ada beberapa strategi yang dapat membantu mengurangi dampak serangan DDoS yang paling berbahaya.

1. **Kenali tanda-tanda serangan DDoS**: pertahanan pertama dan terbaik melawan serangan DDoS adalah kemampuan untuk mengenalinya lebih awal. Sayangnya, tidak semua serangan DDoS mudah dibedakan dari lonjakan normal trafik jaringan atau web, atau penurunan kinerja jaringan secara mendadak. Berinvestasi dalam teknologi, diperlukan keahlian dan pelatihan yang tepat untuk membantu kamu membedakannya, atau menggunakan layanan anti-DDoS seperti yang dibahas di bawah ini.

2. **Perencanaan respon insiden**: Bersiaplah dengan program respon insiden yang hebat dan sertakan rencana mitigasi DDoS.

3. **Hubungi penyedia ISP**: Jika perusahaan kamu merasakan efek dari serangan DDoS, kemungkinan juga akan mempengaruhi penyedia ISP. Hubungi penyedia ISP untuk mengetahui apakah mereka dapat mendeteksi serangan DDoS dan mengarahkan ulang lalu lintas jika terjadi serangan daripada meminta dukungan. Saat memilih ISP, tanyakan apakah ada layanan perlindungan DDoS yang tersedia, dan pertimbangkan apakah kamu ingin melibatkan ISP cadangan jika terjadi serangan agar bisnis bisa tetap berjalan.

4. **Mempunyai intel ancaman yang berguna**: Setengah dari pertempuran di lingkungan saat ini adalah mengetahui apa yang harus dicari. Apa saja indikator potensial dari kompromi bahwa sebuah serangan sedang berlangsung? Apa ancaman vektor yang paling populer? Dan bagaimana rekan-rekan kamu menanggapi serangan tersebut? Bergabunglah dengan ISAC lokal, gunakan penyedia layanan intel atau jaringan ancaman dengan rekan kamu untuk memahami sumber ancaman dan serangan.

5. **Alat pertahanan dan mitigasi**: Ada dua alat yang harus dipertimbangkan oleh perusahaan selain firewall berbasis tanda tangan standar dan router (untuk menolak trafik berbahaya yang diketahui) saat memikirkan strategi mitigasi: (1) *Load balancers* untuk menyeimbangkan trafik di beberapa server dalam jaringan yang didefinisikan dengan tujuan menciptakan ketersediaan jaringan tambahan, dan (2) solusi anti-DDoS berbasis cloud untuk menyaring atau mengalihkan trafik berbahaya DDoS.

Saat ini, dengan komodifikasi dan distribusi besar alat serangan cyber yang canggih, semakin banyak orang memiliki akses ke malware canggih yang memfasilitasi serangan DDoS. Dengan peningkatan yang masif ini, organisasi/instansi saat ini perlu dipersiapkan untuk mempertahankan diri dari serangan DDoS atau menimbulkan risiko pemadaman dan kerusakan lainnya.

Pertimbangkan saran untuk mencegah penyerang men-*takedown*-kan jaringan dengan membanjiri trafik yang tidak diinginkan. Miliki rencana respon insiden dan bicarakan tindakan pencegahan DDoS terlebih dahulu dengan ISP dan vendor keamanan yang mengkhususkan diri dalam mengurangi jenis serangan ini.
