# Week 3

## Table of Contents

- [Week 3](#week-3)
  - [Table of Contents](#table-of-contents)
  - [Bagaimana Internet Bekerja?](#bagaimana-internet-bekerja)
  - [Bind9](#bind9)


## Bagaimana Internet Bekerja?
Internet adalah jaringan global yang terdiri dari jutaan perangkat yang terhubung secara fisik melalui kabel serat optik, kabel tembaga, satelit, dan teknologi nirkabel lainnya. Proses kerja Internet melibatkan beberapa tahapan yang kompleks, di antaranya:

1. **Perangkat Pengguna**: Pengguna mengakses Internet melalui perangkat seperti komputer, smartphone, tablet, dan perangkat lainnya. Perangkat ini terhubung ke jaringan melalui penyedia layanan internet, baik melalui koneksi kabel maupun nirkabel.

2. **Protokol Komunikasi**: Internet menggunakan serangkaian protokol komunikasi, terutama TCP/IP, yang mengatur bagaimana data dikirim, diterima, dan diproses di seluruh jaringan. TCP (Transmission Control Protocol) memastikan pengiriman data yang andal, sedangkan IP (Internet Protocol) mengatur pengalamatan dan routing data.

3. **Routing**: Data yang dikirim melalui Internet melewati serangkaian perangkat jaringan yang disebut router. Router bertanggung jawab untuk mengarahkan data ke tujuan yang tepat melalui jalur yang optimal. Proses routing ini memastikan data mencapai tujuannya dengan efisien.

4. **Domain Name System (DNS)**: DNS adalah sistem yang menerjemahkan nama domain yang mudah diingat (seperti www.example.com) menjadi alamat IP yang diperlukan untuk mengidentifikasi tujuan komunikasi. Ini memungkinkan pengguna untuk mengakses situs web dan layanan online dengan menggunakan nama domain alih-alih harus mengingat alamat IP yang rumit.

5. **Server**: Ketika pengguna mengakses konten di internet, permintaan tersebut dikirim ke server yang menyimpan konten tersebut. Server merespons permintaan tersebut dengan mengirimkan data kembali ke perangkat pengguna. Ada berbagai jenis server, termasuk server web, server email, server file, dan lainnya.

6. **Penyedia Layanan Internet (ISP)**: ISP adalah perusahaan yang menyediakan akses ke Internet. Mereka menghubungkan pengguna ke jaringan Internet dan menyediakan layanan seperti koneksi internet, hosting website, layanan email, dan lainnya. ISP juga bertanggung jawab untuk mengelola lalu lintas data antara pengguna dan internet secara keseluruhan.

Dengan kerjasama antara semua komponen ini, data dapat dikirimkan dengan cepat dan efisien di seluruh dunia, memungkinkan pengguna untuk mengakses informasi, berkomunikasi, dan berbagi konten secara global. Internet terus berkembang dan menjadi bagian integral dari kehidupan modern, memungkinkan terciptanya ekosistem digital yang luas dan terhubung.

## Bind9
1. Install bind9 melalui terminal.

![](assets/1.png)

2. Cek file-filenya di /etc/bind.

![](assets/2.png)

3. Buka konfigurasi di named.conf dan sesuaikan konfigurasi seperti di gambar.

![](assets/3.png)

4. Buka konfigurasi di named.conf-default-zones dan sesuaikan konfigurasi seperti di gambar.

![](assets/4.png)

5. Buka konfigurasi di named-conf.options dan sesuaikan konfigurasi seperti di gambar. Di listen-on, sesuaikan dengan kelompok masing-masing.

![](assets/5.png)

6. Buka konfigurasi di named-conf.local dan sesuaikan zone dengan kelompok masing-masing.

![](assets/6.png)

7. Lakukan pengecekan konfigurasi dengan sudo named-checkconf. Jika tidak ada error, maka konfigurasi sudah benar.

![](assets/7.png)

8. Navigasi ke /var/lib/bind lalu konfigurasikan db.kelompok1.local seperti di gambar.

![](assets/8.png)

9. Konfigurasikan juga db.kelompok1.local.inv

![](assets/9.png)

10. Jalankan sudo systemctl restart named.
11. Jalankan perintah dig.
  
![](assets/11.png)


12. Jalankan perintah nslookup.

![](assets/12.png)
