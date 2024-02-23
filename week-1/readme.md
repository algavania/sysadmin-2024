# Week 1

## Table of Contents

- [Week 1](#week-1)
  - [Table of Contents](#table-of-contents)
  - [Tugas 1 (Instalasi Debian)](#tugas-1-instalasi-debian)
  - [Perbedaan Debian 12 (bookworm) dengan Debian 11 (bullseye)](#perbedaan-debian-12-bookworm-dengan-debian-11-bullseye)
  - [Fungsi file "/etc/groups"](#fungsi-file-etcgroups)
  - [Perbedaan "su" dengan "su -"](#perbedaan-su-dengan-su--)
  - [Fungsi "sudo"](#fungsi-sudo)
  - [Penambahan User sebagai User Sudo](#penambahan-user-sebagai-user-sudo)



## Tugas 1 (Instalasi Debian)

1. Download [Virtual Box](https://www.virtualbox.org/wiki/Downloads) dan [Debian](https://www.debian.org/download) terlebih dahulu.
2. Install Virtual Box dan buka Virtual Boxnya.
3. Klik Icon + (Add) di kanan atas Virtual Box. Lalu isi ISO Image sesuai dengan path saat mendownload ISO Debian tadi. Lalu centang "Skip Unattended Installation" agar kita bisa secara manual mengonfigurasi Debiannya.

![](../assets/week-1/pic%20(2).png)
4. Lalu buat memory (RAM) sebanyak 4GB. Dan untuk prosesornya di sini saya memilih 4 cores.
![](../assets/week-1/pic%20(3).png)
5. Buat storagenya sebanyak 25GB.
![](../assets/week-1/pic%20(4).png)
6. Akan muncul summary mengenai Machine Name, OS Type, Hardware, dan Disk. Cek dulu dan pastikan bahwa sudah sesuai dengan apa yang kita inginkan lalu klik Finish.
![](../assets/week-1/pic%20(5).png)
7. Lalu start debiannya dan akan muncul installer menunya. Klik Graphical Install.
![](../assets/week-1/pic%20(6).png)
8. Setelah itu kita akan diarahkan untuk mengonfigurasi lokasi, keyboard, dan bahasa.
![](../assets/week-1/pic%20(7).png)
![](../assets/week-1/pic%20(8).png)
![](../assets/week-1/pic%20(9).png)
![](../assets/week-1/pic%20(10).png)
![](../assets/week-1/pic%20(11).png)
![](../assets/week-1/pic%20(12).png)
![](../assets/week-1/pic%20(13).png)
9. Di sini kita akan mengonfigurasi networknya. Isi hostname dengan format "sysadmin-NRP". Lalu domainnya dikosongi saja.
![](../assets/week-1/pic%20(14).png)
![](../assets/week-1/pic%20(15).png)
10. Setelah itu konfigurasi untuk informasi user.
![](../assets/week-1/pic%20(16).png)
![](../assets/week-1/pic%20(17).png)
![](../assets/week-1/pic%20(18).png)
![](../assets/week-1/pic%20(19).png)
![](../assets/week-1/pic%20(20).png)
11. Lalu kita akan mengonfigurasi partisi disknya. Pilih manual. Untuk partisinya sebagai berikut:
- 20GB, beginning, primary, ext4, mount point: /
- 5GB, end, primary, ext 4, mount point: /storage
- 1GB, beginning, primary, ext 4, mount point: /boot, bootable flag: on
- 843.1MB, end, logical, swap area.
![](../assets/week-1/pic%20(21).png)
![](../assets/week-1/pic%20(22).png)
![](../assets/week-1/pic%20(23).png)
![](../assets/week-1/pic%20(24).png)
![](../assets/week-1/pic%20(25).png)
12. Kita akan masuk ke finalisasi instalasinya. Pilih "no" untuk scan more media. Pilih lokasi "Indonesia" dan untuk mirrornya bisa pilih "deb.debian.org" atau yang terdekat dari lokasi kita sekarang. Untuk http proxy dikosongi saja. Dan untuk software selection, saya menambah centang Web Server dan SSH Server.
![](../assets/week-1/pic%20(27).png)
![](../assets/week-1/pic%20(28).png)
![](../assets/week-1/pic%20(29).png)
![](../assets/week-1/pic%20(30).png)
![](../assets/week-1/pic%20(31).png)
![](../assets/week-1/pic%20(32).png)
13. Tunggu instalasi hingga selesai. Nanti akan muncul konfigurasi Boot Loader, pilih Yes. Tunggu beberapa saat, lalu instalasi Debian sudah berhasil.

## Perbedaan Debian 12 (bookworm) dengan Debian 11 (bullseye)
| Fitur             | Debian 12                                                     | Debian 11                                                        |
| ----------------- | ------------------------------------------------------------- | ---------------------------------------------------------------- |
| Versi Kernel      | 6.1 (LTS)                                                     | 5.10 (LTS)                                                       |
| Kebutuhan Sistem  | Lebih tinggi (terutama RAM)                                   | Lebih rendah                                                     |
| Penerapan systemd | Lebih luas                                                    | Lebih terbatas                                                   |
| Perbedaan Package | Lebih banyak paket baru                                       | Lebih sedikit paket baru                                         |
|                   | Versi software lebih baru (misalnya: LibreOffice 7.4 vs 7.3)  | Versi software lebih lama                                        |
|                   | Paket Flatpak terintegrasi                                    | Tidak ada paket Flatpak                                          |
|                   | Repositori "contrib" dan "non-free" diaktifkan secara default | Repositori "contrib" dan "non-free" dinonaktifkan secara default |

## Fungsi file "/etc/groups"
File "/etc/group" adalah salah satu file konfigurasi pada sistem Linux yang menyimpan informasi tentang grup pengguna (user groups). Grup pengguna digunakan untuk mengelompokkan pengguna dalam kategori tertentu, mempermudah manajemen hak akses file, dan administrasi sistem.

Format file "/etc/group" adalah sebagai berikut:
`group_name:password:GID:user_list`
- group_name: Nama dari grup pengguna.
- password: Biasanya diisi dengan tanda "x". Sebelumnya, ini digunakan untuk menyimpan password grup dalam file ini, tetapi sekarang kebanyakan sistem modern tidak menyimpan password grup di sini dan menggunakan shadow password file (/etc/gshadow) untuk itu. Tanda "x" menandakan bahwa informasi password disimpan di file terpisah.
- GID: Group ID, sebuah bilangan bulat yang unik untuk mengidentifikasi grup secara sistematis.
- user_list: Daftar pengguna yang termasuk dalam grup, dipisahkan oleh koma.

Contoh command dalam "etc/group":
`wheel:x:10:root,user1,user2`
Penjelasan untuk contoh di atas:

- group_name: wheel
- password: x (tidak digunakan)
- GID: 10
- user_list: root, user1, user2

Pada umumnya, file ini digunakan oleh sistem untuk menentukan keanggotaan grup pengguna dan hak akses grup pada sistem Linux.

## Perbedaan "su" dengan "su -"
Perintah `su` dan `su -` di Linux digunakan untuk beralih ke akun pengguna lain. Namun, ada beberapa perbedaan penting antara kedua perintah tersebut:

| su                                                                                          | su -                                                                                                               |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Singkatan dari "switch user".                                                               | Singkatan dari "switch user and become".                                                                           |
| Memungkinkan Anda untuk beralih ke akun pengguna lain tanpa keluar dari akun Anda saat ini. | Memungkinkan Anda untuk beralih ke akun pengguna lain dan sepenuhnya beralih ke lingkungan pengguna tersebut.      |
| Menjalankan shell login baru dengan lingkungan yang diwariskan dari shell Anda saat ini.    | Menjalankan shell login baru dengan lingkungan yang dikonfigurasi untuk pengguna yang Anda alihkan.                |
| Tidak mengubah variabel lingkungan seperti PATH, HOME, dan PWD.                             | Mengubah variabel lingkungan seperti PATH, HOME, dan PWD untuk mencocokkan konfigurasi pengguna yang Anda alihkan. |

Contoh:
Misalkan Anda adalah pengguna user1 dan ingin beralih ke akun pengguna user2.

Dengan `su`:
```
$ su user2
$ pwd 
$ /home/user1
```

Perintah `pwd` menunjukkan bahwa Anda masih berada di direktori home Anda (`/home/user1`).

Dengan `su -`:
```
$ su - user2
$ pwd
/home/user2
$
```

Perintah pwd menunjukkan bahwa Anda sekarang berada di direktori home pengguna `user2` (`/home/user2`).


## Fungsi "sudo"
Sudo adalah singkatan dari "superuser do". Ini adalah program yang memungkinkan pengguna untuk menjalankan program dengan hak akses root (superuser). Root adalah akun pengguna istimewa di Linux yang memiliki akses penuh ke seluruh sistem.

Fungsi utama sudo:

- Memungkinkan pengguna untuk menjalankan perintah administratif tanpa harus login sebagai root. 

Hal ini meningkatkan keamanan dan kemudahan penggunaan, karena pengguna tidak perlu mengetahui password root.
- Memberikan kontrol granular atas akses ke perintah.
 
 Administrator dapat mengkonfigurasi sudo untuk mengizinkan pengguna tertentu untuk menjalankan hanya perintah tertentu, atau untuk menjalankan perintah dengan opsi tertentu.
- Mencatat semua penggunaan sudo. 
  
Ini memungkinkan administrator untuk melacak siapa yang menjalankan perintah apa dan kapan.

## Penambahan User sebagai User Sudo
1. Buka Debian dari VM.
2. Buka terminal lalu jalankan seperti ini:
![](../assets/week-1/sudo%20(1).png)
3. Lalu scroll ke bawah dan pada `# User privilege specification`, tambahkan user kita dan berikan privilege ALL. Setelah itu klik CTRL + X -> ketik Y untuk menyimpan perubahannya.
![](../assets/week-1/sudo%20(2).png)
![](../assets/week-1/sudo%20(3).png)
4. User "alga" sudah berhasil kita tambahkan. Untuk mengeceknya, buka terminal lagi (pastikan bukan di root, melainkan di user kita). Lalu ketik sudo -l. Akan muncul:
```
User alga may run the following commands on sysadmin-3122600010:
    (ALL : ALL) ALL
```

Itu berarti user kita sudah bisa menjalankan privilege superuser.
![](../assets/week-1/sudo%20(4).png)
