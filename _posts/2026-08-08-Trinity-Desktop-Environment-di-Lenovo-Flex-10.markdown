---
layout: post
title: "Trinity Desktop Environment di Lenovo Flex 10"
date: 2026-08-08 08:00:00 +0700
tags: [linux,operating system,experiment]
---

Prologue
========

Trinity Desktop Environment (TDE) adalah kelanjutan dari KDE 3.5 yang ringan, klasik, dan stabil. Bagi pengguna yang ingin antarmuka desktop tradisional dengan konsumsi sumber daya rendah, Trinity bisa menjadi pilihan menarik. Pada sesi ini, saya mencoba Trinity di Lenovo Flex 10, laptop kecil dengan spesifikasi terbatas, untuk melihat apakah lingkungan desktop ini masih relevan di tahun 2026.

Installation
============

Untuk memasang Trinity pada ArtixLinux dengan init OpenRC, ada beberapa instruksi yang harus diperhatikan. Di lingkungan instalasi, saya menambahkan repositori Trinity dan Arch Linux, kemudian menginstal paket inti. Contoh perintah menambahkan repository archlinux:

- install `artix-archlinux-support`:
  ```bash
  sudo pacman -S artix-archlinux-support
  ```
- populasikan key pacman archlinux
  ```bash
  sudo pacman-key --populate archlinux
  ```
- sisipkan paket `extra` ke file `/etc/pacman.conf`:
  ```txt
  [extra]
  Include = /etc/pacman.d/mirrorlist-arch
  ```

- Tambahkan repositori Trinity ke file `/etc/pacman.conf`:
  ```txt
  [trinity]
  Server = https://mirror.ppa.trinitydesktop.org/trinity/archlinux/x86_64
  ```

- ambil kunci GPG dan sisipkan ke pacman seperti ini:
  ```bash
  # pacman-key --recv-key  D6D6FAA25E9A3E4ECD9FBDBEC93AF1698685AD8B
  # pacman-key --lsign-key D6D6FAA25E9A3E4ECD9FBDBEC93AF1698685AD8B
  ```

  
- Perbarui daftar paket:
  ```bash
  sudo pacman -Sy
  ```
- Instal paket Trinity desktop (pilih salah satu dari tiga di bawah):
  ```bash
  sudo pacman -S tde-core (inti, tanpa dukungan dasar)
  sudo pacman -S tde-base (dasar)
  sudo pacman -S tde-meta (dukungan penuh)
  ```

Jika menggunakan distribusi lain, seperti Fedora atau Arch, ikuti panduan paket masing-masing. Di Lenovo Flex 10, proses instalasi memerlukan ruang penyimpanan tambahan tetapi tidak memakan memori berlebih saat berjalan.

Post-installation
=================

Setelah instalasi selesai, ada beberapa layanan yang belum diinstal seperti tdm karena paket tde semua dibuat khusus untuk arch linux. maka dari itu diperlukan penyesuaian. Beberapa langkah yang saya lakukan pasca-installasi:

- buat file `/etc/init.d/tdm` dan sisipkan baris di bawah melalui editor teks kesukaan kalian seperti ini:
  ```txt
  #!/sbin/openrc-run

  description="Trinity Desktop Manager (TDM)"
  command=/opt/trinity/bin/tdm
  command_background=true
  pidfile=/var/run/tdm.pid

  depend() {
      need localmount xdmcp
      after dbus
  }
  ```
- jadikan file tadi bisa-dieksekusi seperti ini:
  ```bash
  sudo chmod +x /etc/init.d/tdm
  ```
- Tambahkan layanan dan jadikan startup, jadi otomatis berjalan setelah boot:
  ```bash
  sudo rc-update add tdm default
  ```
- Opsional, perintah ini dibuat agar bisa berjalan secara langsung:
  ```bash
  sudo rc-service tdm start
  ```
- tanpa perintah tadi, tdm bisa dimulai ketika restart.

Trinity menyediakan konfigurasi berbasis Control Center yang mudah dinavigasi. Saya menyesuaikan resolusi, tema klasik, dan shortcut keyboard. Penyesuaian ini membuat pengalaman kerja lebih cepat tanpa memakan banyak sumber daya.

Review
======

Kelebihan:
- Ringan dan cepat, cocok untuk hardware seperti Lenovo Flex 10.
- Tampilan klasik yang konsisten dan familiar bagi pengguna desktop lama.
- Kontrol penuh terhadap panel, menu, dan aplikasi bawaan.

Kekurangan:
- Tampilan terasa kurang modern dibandingkan lingkungan desktop baru.
- Beberapa aplikasi terbaru mungkin tidak terintegrasi sempurna.
- Dokumentasi penggunaannya tidak sekomprehensif desktop mainstream.

Secara keseluruhan, Trinity Desktop Environment adalah pilihan bagus untuk pengguna yang mencari lingkungan desktop stabil dan hemat sumber daya. Pada Lenovo Flex 10, Trinity berjalan lancar dan memberikan pengalaman kerja yang bersih serta responsif. Meski tidak cocok bagi mereka yang menginginkan tampilan modern, Trinity tetap relevan untuk pengguna dengan perangkat terbatas atau yang menyukai antarmuka desktop klasik.
