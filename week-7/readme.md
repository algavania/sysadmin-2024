# Week 7

## Table of Contents

- [Week 7](#week-7)
  - [Table of Contents](#table-of-contents)
  - [Mail Server](#mail-server)
    - [Roundcube](#roundcube)

## Mail Server
1. Konfigurasi db.kelompok1.local.

![](assets/mail-1.png)

2. Konfigurasi db.kelompok1.local.inv.

![](assets/mail-2.png)

3. Jalankan nslookup mail.kelompok1.local.

![](assets/mail-3.png)

4. Install systemd-timesyncd untuk Network Time Protocol.

![](assets/mail-4.png)

5. Set timezone ke Jakarta, ntp true, dan local rtc false.

![](assets/mail-5.png)

6. Konfigurasi file timesyncd.conf di /etc/systemd dan ubah pool menjadi yang paling dekat agar delaynya pendek.

![](assets/mail-6.png)

7. Restart service dan cek statusnya.

![](assets/mail-7.png)

8. Cek tanggalnya.

![](assets/mail-8.png)

9. Install Apache 2.

![](assets/mail-9.png)

10. Ubah ServerTokens menjadi Prod.

![](assets/mail-10.png)

11. Tambahkan ServerName sesuai kelompok.

![](assets/mail-11.png)

12. Ubah ServerAdmin sesuai kleompok.

![](assets/mail-12.png)

13. Reload Apache.

![](assets/mail-13.png)

14. Cek apakah webserver berhasil berjalan.

![](assets/mail-14.png)

15. Install PHP dengan `sudo apt -y install php8.2 php8.2-mbstring php-pear`

16. Install PHP FPM dengan `sudo apt -y install php-fpm`.

17. Konfigurasi file default-ssl.conf.

![](assets/mail-17.png)

18. Lakukan setenvif di ae2enmod proxy_fcgi dan load confignya.

![](assets/mail-18.png)

19. Restart servicenya.

![](assets/mail-19.png)

20. Install maria db dengan `sudo apt -y install mariadb-server`

21. Ubah charset ke utf8mb4 di file `/etc/mysql/mariadb.conf.d/50-server.cnf`, lalu restart mariadb.

22. Jalankan `sudo mysql_secure_installation`.

23. Install `sudo nano apt -y install postfix sasl2-bin` lalu pilih No Configuration.

24. Copy file config `/usr/share/postfix/main.cf.dist` ke `/etc/postfix/main.cf`.

![](assets/mail-20.png)

![](assets/mail-21.png)

![](assets/mail-22.png)

![](assets/mail-23.png)

![](assets/mail-24.png)

![](assets/mail-25.png)

![](assets/mail-26.png)

![](assets/mail-27.png)

![](assets/mail-28.png)

![](assets/mail-29.png)

![](assets/mail-30.png)

25. Jalankan `sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd`

26. Uncomment `listen = *, ::` di file `/etc/dovecot/dovecot.conf`.
    
27. Ubah `auth_mechanism = plain login` di file `/etc/dovecot/conf.d/10-auth.conf`.

28. Konfigurasi file mail.

![](assets/mail-31.png)

29. Konfigurasi file master.

![](assets/mail-32.png)

30. Lalu coba jalankan telnet, cek apakah sudah terhubung.

![](assets/mail-35.png)

31. Buka Debian Evolution untuk GUI emailnya dan di sini saya akan mencoba mengirimkan ke kelompok 2.

![](assets/mail-36.png)

![](assets/mail-37.png)

### Roundcube
1. Install roundcube dengan `suto apt install roundcube`.

![](assets/mail-38.png)

![](assets/mail-39.png)

![](assets/mail-40.png)

2. Lalu kita buat MariaDB database dan user untuk roundcubenya.

![](assets/mail-41.png)

3. Lalu konfigurasi config.inc.php di roundcube.

![](assets/mail-42.png)

4. Konfigurasi apache.conf.

![](assets/mail-43.png)

5. Konfigurasi 000-default.conf.

![](assets/mail-44.png)

6. Lalu rekonfigurasi dengan `sudo dpkg-reconfigure roundcube-core`.

![](assets/mail-45.png)

![](assets/mail-46.png)

![](assets/mail-47.png)

![](assets/mail-48.png)

![](assets/mail-49.png)

![](assets/mail-50.png)

![](assets/mail-51.png)

![](assets/mail-52.png)

![](assets/mail-53.png)

![](assets/mail-54.png)

![](assets/mail-55.png)

![](assets/mail-56.png)

![](assets/mail-57.png)

![](assets/mail-58.png)

![](assets/mail-59.png)

7. Roundcube berhasil terkonfigurasi. Navigasi ke browser dan buka mail.kelompok1.local. Di sini saya login dengan user debian saya.

![](assets/mail-60.png)

8. Terlihat bahwa isi dari Roundcube sudah sama dengan Debian Evolution.

![](assets/mail-61.png)

9. Di sini saya coba kirim ke kelompok 2. 

![](assets/mail-62.png)

11.  Lalu berhasil mendapat balasan.

![](assets/mail-63.png)
