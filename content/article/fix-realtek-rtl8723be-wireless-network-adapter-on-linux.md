+++
author = "kernel-panic"
categories = ["Linux"]
date = "2018-01-03"
description = "How to fix Realtek RTL8723BE Wireless Network Adapter on your Linux machine."
featured = "s21458244892.png"
featuredalt = "Fix RTL8723BE Linux"
featuredpath = "https://beeimg.com/images"
linktitle = ""
title = "Fix Realtek RTL8723BE Wireless Network Adapter on Linux"
type = "post"
+++

Kali ini saya ingin berbagi cara memperbaiki Realtek RTL8723BE Wireless Network Adapter di Linux. Tutorial ini juga dapat digunakan untuk Realtek Wireless Network Adapter lainnya yang didukung oleh *rtlwifi_new*.

Dulu ketika saya mulai menggunakan Linux di laptop yang baru saya beli pada waktu itu yaitu HP 14-AC001TU, saya menghadapi masalah terkait sinyal Wi-Fi di OS Kali yang saya gunakan. Kali Linux gagal menemukan jaringan Wi-Fi yang bisa digunakan. Setelah cari solusi kesana-kemari, akhirnya saya menemukan solusi untuk masalah ini.

## Bahan yang dibutuhkan:

**rtlwifi_new**: {{< url-link "https://github.com/lwfinger/rtlwifi_new" "https://github.com/lwfinger/rtlwifi_new" "target">}}

## Steps by Steps

1. Download rtlwifi_new dari link di atas dan ekstrak ke direktori yang kamu inginkan (contohnya, saya dulu mengekstraknya di direktori /opt).

2. Buka Terminal dan masuk ke direktori dimana kamu mengekstrak rtlwifi_new (dalam kasus saya, /opt/rtlwifi_new-master) dengan menggunakan perintah cd. Lihat screenshot yang diberikan di bawah ini:

		cd /opt/rtlwifi_new-master 

	![](https://beeimg.com/images/e05271428911.png) 

3. Sekarang, jalankan perintah ini di Terminal seperti yang ditunjukkan pada Screenshot di bawah ini:

		make clean
		
	*Perintah make clean opsional untuk instalasi pertama kali, kamu bisa menggunakannya untuk pemasangan lebih lanjut*
	
	![](https://beeimg.com/images/g24109131372.png) 

		make
	
	![](https://beeimg.com/images/a70166279382.png) 

4. Setelah itu, jalankan perintah ini di Terminal seperti yang ditunjukkan pada screenshot di bawah ini:

		sudo make install

	![](https://beeimg.com/images/f14402084732.png) 

5. Jika semuanya baik-baik saja dan berhasil, kamu akan melihat pesan "Install rtlwifi SUCCESS". Ini berarti rtlwifi telah berhasil diinstal.

6. Sekarang, jalankan perintah ini seperti yang ditunjukkan pada screenshot di bawah:

		sudo modprobe rtl8723be
		
7. Sekarang, jalankan perintah ini seperti yang ditunjukkan pada screenshot di bawah:

		echo “options rtl8723be ant_sel=2” | sudo tee /etc/modprobe.d/rtl8723be.conf
		
8. Langkah ini bersifat opsional. Jika kamu ingin melihat bahwa konten teks berhasil ditulis ke /etc/modprobe.d/rtl8723be.conf, kamu dapat menggunakan perintah ini seperti yang ditunjukkan pada screenshot di bawah:

		cat /etc/modprobe.d/rtl8723be.conf
		
	![](https://beeimg.com/images/o17619625722.png) 

9. Jika semua perintah di atas berhasil dijalankan, maka semuanya sudah selesai. Sekarang, kamu perlu me-restart komputer dan kamu akan melihat Wi-Fi bekerja dengan baik juga komputer kamu akan menemukan jaringan Wi-Fi yang tersedia.

10. Setelah me-restart komputer kamu, coba koneksikan ke jaringan Wi-Fi untuk pengetesan.

Semoga postingan ini bermanfaat bagi banyak pengguna yang menggunakan Realtek Wireless Network Adapter dan menghadapi masalah terkait sinyal Wi-Fi di OS Kali/Linux nya.
