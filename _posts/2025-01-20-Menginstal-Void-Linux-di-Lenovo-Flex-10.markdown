---
layout: post
title: "Menginstal Void Linux di Lenovo Flex 10"
date: 2025-01-20 00:00:00 +0000
tags: [linux,operating system,experiment]
---

### Pengantar

Sebenarnya untuk percobaan menginstal linux/sistem operasi alternatif di Lenovo Flex 10 sudah saya lakukan pada tahun 2023. Ketika itu saya merasa bahwa sistem operasi ketika itu (Windows) sudah termakan banyak sumber daya yang membuat sistem terlalu lambat dan tidak bisa diandalkan. Bahkan saat itu saya mengganti hard disk menjadi ssd belum berhasil untuk berjalan dengan semestinya.

Akhirnya saya putuskan untuk mencoba menginstal Void Linux dengan layanan live xfce terbaru yang tersedia di laman [void linux](https://voidlinux.org/) (pada saat itu tahun 2023).

### Proses instalasi

Saya mengunduh dan memasukkan image live xfce terbaru (ingat, flash drive harus di atas ukuran imagenya!) ke dalam flash drive dengan menjalankan program `dd`. Tanpa pengaturan tambahan saya menyalakan laptop dan masuk ke boot manager. Setelah itu saya memilih flash drive untuk memulai booting (alhamdulillah tersedia).

Saya menginstal Void Linux dengan menggunakan program `xbps-install` ketika membuka terminal. untuk pengaturannya seperti ini:

- pengaturan network dengan menggunakan wlan, pengaturan ssid dan password masing-masing punya preferensi sendiri.
- pengaturan keyboad menggunakan Indonesian.
- pengaturan zona waktu menggunakan Asia/Jakarta.
- pengaturan nama pengguna (ada dua: username dan fullname) dan password, yang masing-masing punya preferensi sendiri.
- pengaturan media boot ke sda (disk ssd)
- pengaturan disk partisi dengan sda1 menjadi fat32 berukuran 300MB (dan menandainya sebagai bootable/esp), sda2 menjadi swap berukuran 4GB, dan sda3 menjadi ext4 yang merupakan sisanya.

setelah semuanya dirasa beres saya memilih install dan menunggu proses instalasi selesai. setelah itu saya reboot dan laptop secara otomatis memilih Void Linux untuk booting.

### Proses paska instalasi

Saya menggunakan program `# xbps-install -Su` untuk memperbarui program yang telah terinstal. tetapi ada masalah muncul yakni harus menggunakan `# xbps-install -Su xbps` untuk memperbarui program xbps sebagai penginstal khas dari Void Linux.

Setelah itu dan mereboot laptop, saya menginstall program yang dibutuhkan dengan tampilan grafis yang memudahkan pengguna dengan menggunakan program `# xbps-install -S octo-xbps`. Octo-xbps adalah program yang memungkinkan pengguna untuk menginstal program dengan tampilan grafis. selain itu saya juga menginstal repo non-free dengan program `# xbps-install -S void-repo-nonfree git firefox libreoffice nano`.

Agar bisa mendapatkan mscorefonts, selain kita menginstall `void-repo-nonfree`, kita juga perlu membuat perintah terminal seperti ini:

```git
git clone https://github.com/void-linux/void-packages
cd void-packages
./xbps-src binary-bootstrap
echo "XBPS_ALLOW_RESTRICTED=yes" >> etc/conf
./xbps-src pkg -f msttcorefonts
xi msttcorefonts
```

Ingat! kita harus memasukkan satu baris untuk satu perintah. Agar tidak ada langkah yang terlewati.

### Pengalaman pengguna

Karena Void Linux menawarkan Sistem Operasi yang minimalis, saya berhasil dibuat takjub oleh kecepatan laptop saya ketika menjalankan beberapa program.

Saya hampir lupa, Void Linux juga menawarkan program steam bagi gamer yang ingin bermain game secara native selain di windows dan macos. Namun, bagi saya yang memiliki laptop yang memiliki spesifikasi bukan untuk gaming, saya hanya bisa melihat program ini cukup sebagai dekorasi (huhuhu).

Sebagai alternatif dari Microsoft Office, Void Linux menawarkan Libreoffice sebagai pemroses kata, pembuat tabel, presentasi dan lain sebagainya.

### Epilog

Saya menulis ini sebagai referensi untuk pengguna yang ingin menginstal Void Linux di Lenovo Flex 10. Sekian.
