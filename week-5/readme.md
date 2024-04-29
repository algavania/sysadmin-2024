# Week 5
## Table of Contents

- [Week 5](#week-5)
  - [Table of Contents](#table-of-contents)
  - [Bind9](#bind9)


## Bind9
1. Install bind9 melalui terminal.

![](assets/1.png)

2. Cek file-filenya di /etc/bind.

![](assets/2.png)

3. Buka konfigurasi di named.conf dan sesuaikan konfigurasi seperti di gambar.

![](assets/3.png)

4. Buka konfigurasi di named.conf.default-zones dan sesuaikan konfigurasi seperti di gambar.

![](assets/4.png)

5. Buka konfigurasi di named.conf.options dan sesuaikan konfigurasi seperti di gambar. Di listen-on, sesuaikan dengan kelompok masing-masing.

![](assets/5.png)

![](assets/5_2.png)

6. Buka konfigurasi di named.conf.local dan sesuaikan zone dengan kelompok masing-masing.

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

