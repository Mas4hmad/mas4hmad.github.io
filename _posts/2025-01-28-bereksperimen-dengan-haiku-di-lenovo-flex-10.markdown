---
layout: post
Title: "Bereksperimen dengan Haiku di Lenovo Flex 10"
date:   2025-01-28 15:20:21 +0700
tags: [haikuOS,general,experiment]
---

### Pendahuluan

Haiku, sistem operasi sumber terbuka yang terinspirasi oleh BeOS yang legendaris, menawarkan pengalaman komputasi yang unik dan ringan yang menonjol dalam lanskap perangkat lunak saat ini. Dalam artikel ini, saya akan membahas perjalanan saya dalam menginstal dan menggunakan Haiku pada Lenovo Flex 10, perangkat 2-in-1 yang ringkas yang berfungsi sebagai tempat uji coba yang menarik untuk sistem operasi alternatif.

Sebagai penggemar teknologi yang selalu mencari solusi komputasi yang inovatif, saya tertarik dengan janji Haiku akan OS yang responsif, efisien, dan modern yang tidak sesuai dengan arus utama. Lenovo Flex 10, dengan spesifikasi perangkat kerasnya yang sederhana, menghadirkan kanvas yang ideal untuk memamerkan potensi Haiku dalam memberikan kehidupan baru pada perangkat lama atau yang memiliki keterbatasan sumber daya.

Eksperimen ini bukan hanya tentang menguji sistem operasi; ini tentang menjelajahi batasan-batasan dari apa yang mungkin dalam komputasi personal. Dapatkah Haiku, dengan arsitektur mikrokernel dan atribut uniknya, menawarkan alternatif yang layak untuk sistem operasi yang dominan? Bagaimana kinerjanya pada perangkat yang dirancang untuk Windows? Dan yang terpenting, dapatkah ia memberikan pengalaman pengguna yang terasa seperti sekilas masa depan komputasi?

Bergabunglah dengan saya saat kita memulai petualangan teknologi ini, mendorong batas-batas perangkat lunak dan perangkat keras. Apakah Anda seorang pengembang berpengalaman, penggemar teknologi yang ingin tahu, atau sekadar seseorang yang mencari alternatif di dunia komputasi, penelaahan mendalam tentang Haiku pada Lenovo Flex 10 ini menjanjikan wawasan tentang sistem operasi sumber terbuka yang canggih dan aplikasi dunia nyata mereka.

### Persiapan

hal yang perlu disiapkan untuk melakukan instalasi Haiku di Lenovo Flex 10 adalah:

- Lenovo Flex 10.
- USB flash drive
- Haiku ISO image berupa x86_gcc, pilih yang paling atas/terbaru (hrev*) [di sini](https://download.haiku-os.org/nightly-images/x86_gcc2h/).

### Proses Instalasi

- buat USB bootable dari Haiku ISO image yang sudah di unduh sebelumnya. bisa dari rufus, balena etcher, dd, atau cara lainnya. (ventoy saat ini belum didukung).
- pasang USB ke Lenovo Flex 10, lalu booting dari USB melalui <kbd>fn</kbd> + <kbd>F12</kbd>.
- spam <kbd>spasi</kbd> hingga muncul menu boot dari Haiku, pilih *select safe mode options*, pilih *enable safe mode*, lalu keluar dari menu dengan memilih *continue booting.*
- tunggu proses booting selesai, biasanya menunggu sekitar 20 menit (saya belum tahu apa yang menyebabkan lamanya proses booting. Ketika booting menggunakan alpine linux juga menunggu sekian menit).
- ketika muncul dialog selamat datang dari haikuOS, pilih *Try Haiku*, atau *Install Haiku*. (ketika anda telah mendapatkan beberapa pengalaman lebih, beritahu saya :)).

### Pengalaman Pengguna

- Dengan konfigurasi yang telah ditentukan, haiku dapat berjalan dengan semestinya, kecuali wlan/wi-fi tidak terkoneksi.
- Kecepatan mengelola aplikasi atau memuat ram sangat memuaskan. tidak perlu memakai ram yang besar, bahkan 2 gb ram sudah bisa menjalankan banyak aplikasi dengan lancar.
- Karena ini menggunakan pilihan safe mode saat booting, ada beberapa program penting yang tidak bisa berjalan di laptop ini.
- Hanya ini yang bisa saya sampaikan untuk saat ini. Penambahan akan dilakukan setelah mendapatkan beberapa pengalaman.

### Kesimpulan

Haiku, sistem operasi sumber terbuka yang menawarkan pengalaman komputasi yang unik dan inovatif, telah menjadi pilihan yang menarik bagi pengguna yang mencari alternatif di dunia komputasi. Dengan konfigurasi yang sederhana dan arsitektur unik, Haiku menawarkan potensi yang besar untuk memberikan pengalaman baru dan responsif pada perangkat yang dirancang untuk Windows.

Meskipun memiliki status beta (belum sepenuhnya matang/masih bersifat eksperimental), setidaknya fitur yang ditawarkan sama seperti yang diharapkan semua orang.