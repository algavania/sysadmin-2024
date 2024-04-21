# Week 7

## Table of Contents

- [Week 7](#week-7)
  - [Table of Contents](#table-of-contents)
  - [Mail Server](#mail-server)

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