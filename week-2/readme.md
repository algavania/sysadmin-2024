# Week 2

## Table of Contents

- [Week 2](#week-2)
  - [Table of Contents](#table-of-contents)
  - [Linux Directory](#linux-directory)
    - [Overview](#overview)
    - [Hirarki Struktur Direktori](#hirarki-struktur-direktori)
      - [/ (Root)](#-root)
      - [/boot](#boot)
      - [/sys](#sys)
      - [/sbin](#sbin)
      - [/bin](#bin)
      - [/lib](#lib)
      - [/dev](#dev)
      - [/etc](#etc)
      - [/home](#home)
      - [/media](#media)
      - [/mnt](#mnt)
      - [/usr](#usr)
      - [/usr/sbin](#usrsbin)
      - [/usr/bin](#usrbin)
      - [/usr/lib](#usrlib)
      - [/usr/share](#usrshare)
      - [/usr/local](#usrlocal)
      - [/var](#var)
      - [/tmp](#tmp)
  - [DHCP](#dhcp)
    - [Melakukan test ping](#melakukan-test-ping)


## Linux Directory
![](assets/directory.jpg)

Salah satu perbedaam yang paling mencolok dari Linux dan Windows terletak pada struktur direktorinya. Tidak hanya formatnya yang berbeda tetapi cara mengakses direktorinya.

Di dalam Windows, format yang digunakan untuk mengakses direktori adalah sebagai berikut:
D:\Folder\subfolder\file.txt
Sedangkan di dalam Linux, format yang digunakan adalah sebagai berikut:
/Folder/subfolder/file.txt

Yang pertama bisa kita lihat dari tanda slash keduanya. Linux menggunakan slash (/) dan Windows menggunakan backslask (\). Selain itu, di dalam Linux tidak ada drive C:, D:, dll seperti Windows.  Saat booting, partisi root pada Linux akan ter-mount pada /.. Semua file, folders, devices, dan drive, akan mounted /. Penting untuk dicatat bahwa penulisan file dan folder pada Linux sangat case sensitive.

Contoh :
/Folder/subfolder/file.txt tidak sama dengan /folder/subfolder/file.txt

### Overview

Struktur Direktori Unix dan Linux adalah satu kesatuan (unified) Sturuktur Direktori under / Root file system. 
Ketika file system mounted secara fisik, seluruh Direktori akan tersusun secara bertingkat di dalam Root file system.

Struktur direktori pada Linux mengacu pada Filesystem Hierarchy Structure (FHS) yang di maintain oleh Free Standards Group dan banyak distribusi yang cenderung menyimpang dari standar tersebut.

### Hirarki Struktur Direktori

#### / (Root)
Struktur Direktori dimulai dari Root File System "/". Partisi di dalam root akan diletakkan pada UNIX atau UNIX-Compatible System

#### /boot
Direktori ini berisi Boot loader files, meliputi :
GRUB, Lilo, kernel, initrd, system.map config

#### /sys
Direktori ini berisi kernal, firmware, dan file system.

#### /sbin
Direktori ini berisi Binaries System dan Administration System tool yang penting untuk sistem operasi dan performanya.

#### /bin
Direktori ini berisi binaries untuk user dan beberapa hal yang dibutuhkan di single user mode. Contohnya : cat, ls, cp, dll.

#### /lib
Direktori ini berisi file library untuk semua binaries dari /sbin dan /bin

#### /dev
Berisi file system dan drivers

#### /etc
Berisi sistem konfigurasi termasuk :
/etc/hosts, /etc/resolv.conf, nsswitch.conf, defaults, dan network configuration. Contoh di atas merupakan host specific system dan file configuration application.

#### /home
Semua direktori home milik user berada di direktori ini kecuali direktori root home. Direktori root home tetap berada di direktori /root.
Direktori ini berisi file milik user, personal setting seperti .profile, dan lain-lain.

#### /media
Direktori ini berisi mount point untuk removable media seperti CD-ROM, USB, floppies, dan lain-lain.

#### /mnt
Berisi mount point untuk file sytem sementara untuk mempermudah saat ada troubleshooting dengan CDROM misalnya, dimana kita bisa mount file sistem Root dan mengatur konfigurasinya,

#### /usr
Data direktori dari user yang merupakan sub hirarki dari root file system. Direktori ini berisi berbagi aplikasi dan keperluan user. Banyak hal penting bagi user di direktori ini namun tidak penting bagi sistem operasi secara keseluruhan. Di direktori ini akan ditemukan bin, sbin, lib, system binaries, share directory, dan include directory

#### /usr/sbin
Direktori ini berisi tentang system binaries yang tidak penting - tidak kritis (non-critical)  dan beberapa keperluan jaringan

#### /usr/bin
Berisi command binaries yang non-essential dan non-critical untuk user

#### /usr/lib
Direktori ini berisi file library untuk binaries pada /usr/bin dan /usr/sbin

#### /usr/share
Direktori shared data

#### /usr/local
Sub hirarki di bawah direktori /usr yang memiliki data spesifik Local System, termasuk user, system binaries, dan library

#### /var
Direktori ini biasanya mounted sebagai file system terpisah di bawah root, dimana semua variabel seperti logs, spoll files untuk printer, crontab, mail, running proccess, lock files, dll. File system dan maintenance harus diperhatikan karena filesystem cepat penuh. Jika filesytem cepat penuh, maka Operational System dan aplikasi di dalamnya akan bermasalah.

#### /tmp
Direktori ini menyimpan file sementara yang akan dibersihkan saat sistem melakukan reboot. Terdapat satu direktori yang menyimpan file secara sementara juga. Perbedaan keduanya terletak pada direktori /var/tmp yang menyimpan files yang terlindungi saat sytem reboot. Dalam kata lain, /var/tmp files tidak akan hilang saat reboot.

Kemudian ada /proc, sistem file virtual yang berada di dalam memory dan mounted di dalam Root. System file ini berisi kernel dan proses statistik dalam format text.

## DHCP
Pertama-tama, kita perlu menginstall net-tools terlebih dahulu. Package net-tools ini nantinya akan digunakan untuk menampilkan tabel routing dari kenrel. Untuk menginstallnya dapat menggunakan perintah
`sudo apt install net-tools`

Kemudian kita gunakan perintah:
`sudo dhclient -v`
Untuk mengakses alamat IP secara dinamis dari server DHCP untuk network interface yang tertentu menggunakan hak akses superuser. Penggunaan superuser ini nantinya akan dibutuhkan pada saat mengkonfigurasi network interface. Di sini dapat dilihat IP yang dikembalikan adalah 10.0.2.15 .
![](assets/sudodhclient-v.jpg)

Dengan menggunakan perintah:
`ip addr`
Kita dapat melihat informasi tentang konfigurasi network interface yang sudah diterapkan pada server.
![](assets/ipaddr.jpg)

Untuk mengubah konfigurasi IP koneksi secara manual, dapat diakses melalui pengaturan Wired Connections dan mengkonfigurasi secara manual pada tab IPv4. Pastikan IPv4 Method yang dipilih adalah yang **manual** dan bukan default. Kemudian kita dapat mengubah alamat IP-nya, misal menjadi 10.0.2.16 . Pastikan untuk mengatur subnet masknya dengan sesuai pula, disini berarti 255.255.255.0, dan untuk gateway kita atur menjadi 10.0.2.2 . Sedangkan untuk DNS nya kita atur menjadi 8.8.8.8, yakni DNS umum milik Google.
![](assets/wiredsetting1.png)
![](assets/wiredsetting2.png)
![](assets/wiredsetting3.jpg)

Setelah itu, klik apply dan matikan koneksi wired dan nyalakan kembali. Pada saat kita mengakses routing table menggunakan perintah 
`sudo route -n` 
Akan muncul routing table dari kernel dalam bentuk numerik seperti gambar di bawah.
![](assets/sudoroute-n.jpg)

Saat kita gunakan kembali perintah
`ip addr`
Kita dapat melihat bahwa alamat IP sudah berubah dari 10.0.2.15 menjadi 10.0.2.16, sesuai dnegan alamat yang kita ubah sebelumnya.
![](assets/ipaddr2.jpg)

### Melakukan test ping
Saat sudah berhasil mengkonfigurasi dhcp dengan benar, maka saat kita mencoba untuk melakukan ping, akan kembali dengan sukses. Di bawah ini dilakukan test ping pada alamat 8.8.8.8 dan website detik.com.
![](assets/testping1dhcp.jpg)
![](assets/testping2dhcp.jpg)