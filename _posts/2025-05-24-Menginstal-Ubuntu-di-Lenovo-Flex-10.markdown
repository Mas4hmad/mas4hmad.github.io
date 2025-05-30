---
layout: post
title: "Menginstal Ubuntu di Lenovo Flex 10"
date: 2025-01-20 00:00:00 +0000
tags: [linux,operating system,experiment]
---

### Pengantar

Ubuntu merupakan Sistem Operasi sumber terbuka terbesar kedelapan saat ini (24 April 2025) menurut distrowatch. Dengan menggunakan GNOME sebagai Desktop Environment yang telah dimodifikasi, memudahkan pengguna dalam berinteraksi dengan perangkat mereka. Ubuntu menawarkan simplisitas/kesederhanaan dalam menambah pengalaman pengguna, sangat berbeda dengan Windows, namun hampir mirip dengan MacOS. Beberapa elemen seperti panel atas, Dock, jendela untuk satu aplikasi menambah kesederhanaan tanpa mengorbankan kemewahan yang dimiliki oleh Ubuntu.

Saat ini kita akan menginstal Ubuntu di Lenovo Flex 10. butuh pengaturan khusus dengan UEFI agar booting ke sistem operasi Ubuntu tidak bermasalah. Maksud saya, Ubuntu tidak mendukung UEFI 32 bit yang dibutuhkan Lenovo Flex 10. Jika anda tetap ingin menginstalnya, simak langkah-langkah berikut ini.

### Penginstalan

1. Siapkan Ubuntu ISO file [(unduh di sini)](https://ubuntu.com/download/desktop), dan flash drive USB sekitar 8 GB dan jadikan USB bootable, yakni menginstal ventoy [(unduh di sini)](https://www.ventoy.net/en/download.html). Sisipkan ubuntu pada USB tersebut.
2. boot dengan menekan <kbd>F12</kbd>, pilih Ubuntu. Selesaikan instalasi Ubuntu. Pada tahap ini UEFI boot belum tersedia. namun, kamu bisa mencopot USB drive dan memulai ulang laptopnya.
3. ketika telah mencapai shell UEFI, ketik ```linux (hd*,msdos*)/boot/vmlinuz* root=/dev/sd**``` yang merupakan path dari file vmlinuz. ganti angka bintang sesuai dengan path yang kalian temukan pada vmlinuz.
4. selanjutnya, ketik ```initrd (hd*,msdos*)/boot/initrd*``` yang merupakan path dari file initrd. ganti angka bintang sesuai dengan path yang kalian temukan pada initrd.
5. selanjutnya, ketik ```boot``` untuk memulai Ubuntu dan membuka terminal/command prompt linux.
6. ketika terminal telah terbuka, ketik ```sudo apt-get update && sudo apt-get install git bison libopts25 libselinux1-dev autogen m4 autoconf help2man libopts25-dev flex libfont-freetype-perl automake autotools-dev libfreetype6-dev texinfo``` untuk menginstal dependensi yang dibutuhkan.
7. ketik ```git clone git://git.savannah.gnu.org/grub.git``` untuk mengunduh bootloader GRUB.
8. selanjutnya, ketik ```cd grub``` untuk mengubah direktori ke grub.
9. kemudian ketik perintah di bawah untuk eksekusinya, seperti ini:
```shell
./autogen.sh
./configure --with-platform=efi --target=i386 --program-prefix=""
make
cd grub-core
sudo ../grub-install -d . --efi-directory /boot/efi/ --target=i386
cd /boot/efi/EFI
sudo cp grub/grubia32.efi ubuntu/grubx64.efi
sudo update-grub
```
<b>Ingat!</b> ketik perintah di atas dengan hati-hati, kalau bisa satu baris untuk satu perintah.karena ini akan mengubah bootloader GRUB yang sudah ada dan akan terjadi kesalahan jika perintah tidak sesuai.

### Kesimpulan

Ubuntu merupakan sistem operasi yang sangat mudah digunakan, namun tidak mendukung UEFI 32 bit yang dibutuhkan Lenovo Flex 10. Jika anda ingin menginstal Ubuntu di Lenovo Flex 10, maka anda harus menggunakan UEFI 64 bit.

<i>*Selain di halaman ini, kalian juga bisa lihat di https://rkblog.dev/posts/pc-hardware/how-cool-lenovo-flex-10-netbook-and-how-install-linux-32-bit-uefi-system/</i>