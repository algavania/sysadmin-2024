---
marp: true
class: invert
---

# <!--fit-->Debian Handbook untuk Pemula :rocket:
Disusun oleh:
1. Fatimah Az-Zahra' Mahros (3122600002)
2. Alga Vania Salsabillah (3122600010)
3. Amirotul Ummah (3122600017)

---

# 8.1 Sumber Software

Debian GNU/Linux menggunakan metode repository untuk mendistribusikan aplikasi. Dengan metode ini, akan ada software centralization serta tampilan yang simpel untuk meng-upgrade sistem kita. Jadi, kita tidak perlu mengunjungi situs softwarenya secara manual untuk meng-install software.

---

## 8.1.1 File sources.list
Alamat URL dari repository Debian disimpan di file `/etc/apt/sources.list`, begitu juga file dengan tipe `/etc/apt/sources.list.d/xxx.list`.

Untuk mengubah file `sources.list`, kita bisa menggunakan salah satu dari command ini (di mode admin):

```
apt edit-sources
nano /etc/apt/sources.list
```

---
Detail informasi yang ada di `sources.list`:
- "deb": Berarti binary repository (software yang sudah di-compile).
- "deb-src": Berarti sumber repository (file berisi kode yang digunakan untuk mengompile software).
- "http:..." atau "https:...": Alamat dari repository server.
- "bookworm" atau "bookworm-security": Branch di dalam repository tree.
- "main" atau "non-free-firmware": Section dari repository.

"bookworm" adalah version name dari sistemnya.

"stable" adalah nama umum dari versi stable yang sekarang.

---

Hingga saat ini, Debian 12 "bookworm" merupakan versi "stable". Tapi, ketika versi "stable" Debian berubah menjadi Debian 13 "Trixie", Debian 12 "bookworm" akan menjadi "oldstable".

Menggunakan version name membuat kita bisa mengontrol jika dan kapan kita akan mengupgrade sistem kita ke versi selanjutnya.

---

## 8.1.2 Repository, branch, dan section/component
Debian mengelola software packagenya di dalam repository. Repository-repository ini dibagi ke beberapa branch dan section/component. Nanti kita akan membahas "testing" dan "unstable" branch.

Ada 4 section di official repository Debian:
- main: memenuhi DFSG tanpa "non-free" dependency apapun.
- non-free-firmware: non-free-firmwares yang termasuk secara default sejak Debian 12
- contrib: memenuhi DFSG dengan beberapa "non-free" dependency.
- non-free: tidak memenuhi DFSG.

---

DFSG (Debian Free Software Guidelines): Prinsip filosofis dari "libre software" menurut Debian.

Hanya package di main section/component yang secara official didukung oleh Debian dan 100% software gratis. Dan yang ada di contrib, non-free, dan non-free-firmware adalah setengah atau sepenuhnya non-free.

Maka dari itu, tergantung dari hardware kita, sangat mungkin bahwa beberapa service tidak akan berjalan dengan benar tanpa menggunakan driver tertentu. Pada case tersebut, maka kita perlu mengubah file `/etc/apt/sources.list`.

---

## 8.1.3 Package Backport
Debian juga menawarkan beberapa repository spesial yang disebut backport, yang isinya adalah versi terbaru dari aplikasi. Repository ini tidak diaktifkan secara default, tapi tidak ada risiko bagi sistem kita. Repository "reguler" mempunyai prioritas tertinggi saat ada update.

Backport adalah mekanisme yang mengizinkan sebuah aplikasi yang sedang berada di Debian development repository "to be ported back" ke versi stable.

---

## 8.1.4 Mengubah repository
Sebelum kita mengubah sumber software dari sistem kita, kita harus sadar dulu akan risiko yang akan kita hadapi saat menggunakan "contrib" atau "non-free" component dari archived branch:
- Kurangnya kebebasan untuk package-package seperti ini.
- Kurangnya dukungan dari Debian.
- Kontaminasi di sistem Debian kita.

Untuk mengubah sumber software/software source, cukup dengan memodifikasi file `sources.list`. Buka terminal dengan mode admin dan ketik `apt edit-sources`.

---

# 8.2 APT di Terminal
Pada section ini, akan dijelaskan basic command untuk me-manage package Debian menggunakan APT (Advanced Package Tool) di terminal kita.

Debian juga mendukung "aptitude", package manager yang lain, dengan syntax dan behavior yang berbeda. Penjelasan ini ditujukan untuk pemula.

---

## 8.2.1 User command untuk mencari dan menampilkan informasi
Command-command ini bisa dijalankan oleh user biasa karena tidak akan mempengaruhi sistem kita.

- apt show foo: Menampilkan informasi mengenai package foo.
- apt search foo: Mencari package sesuai dengan foo.
- apt-cache policy foo: Menampilkan versi yang tersedia dari foo.

---

## 8.2.2 Command untuk maintenance system dari mode admin
Command-command ini harus dijalankan dengan mode administrator karena akan mempengaruhi sistem. Untuk switch ke mode administrator dari terminal, ketik `su -`.

- apt update: Mengupdate metadata repository.
- apt install foo: Menginstall package foo dan dependencynya.
- apt upgrade: Mengupgrade package-package yang telah di-install.
- apt full-upgrade: Mengupdate packet yang telah di-install dengan menambah/menghapus package lain jika diperlukan.
- apt remove foo: Menghapus package foo tapi tidak dengan file konfigurasinya.

---

- apt autoremove: Menghapus secara otomatis package-package yang tidak penting.
- apt purge foo: Menghapus package foo beserta file konfigurasi.
- apt clean: Membersihkan local cache dari package yang di-install.
- apt autoclean: Membersihkan local cache dari package-package yang outdated.
- apt-mark showmanual: Menandai sebuah package sebagai "manually-installed".

---

Ada juga All-In-One command line (di mode administrator) untuk mengupdate informasi repository + update sistem + membersihkan package di cache:
`apt update && apt full-upgrade && apt autoclean`

Untuk menghapus package-package yang tidak berguna, dependency yang tidak penting, dan file-file konfigurasi yang lama di mode administrator:
`apt autoremove --purge`

---

# 8.3 Software: Package Manager yang Simpel
Software adalah package manager yang simpel untuk aplikasi Debian. Kita bisa search, install, delete, atau update package. Untuk membukanya, bisa di "System" atau search secara langsung dari Gnome search box.

---

## 8.3.1 Mencari sebuah aplikasi
Langsung saja mengklik search button atau dengan memilih salah satu dari kategori yang ditampilkan.

## 8.3.2 Menginstall sebuah aplikasi
Kita bisa menginstall sebuah aplikasi hanya dengan mengklik area deskripsinya dan klik tombol "Install". Nantinya akan diminta password administrator. Setelah itu kita bisa mengikuti progress instalasinya dan membuka secara langsung aplikasi yang barusan di-download.

---

## 8.3.3 Menghapus sebuah aplikasi
Kita bisa uninstall aplikasi hanya dengan mengunjungi kategori "Installed" dan klik tombol "Remove".

## 8.3.4 Upgrade aplikasi
Kita bisa meng-update sistem kita di section "Updates" yang menunjukkan update yang tersedia atau update yang sedang di-download. Jika tidak ada update yang tersedia, kita bisa cek repositorynya dengan menekan tombol di kiri atas.

---

## 8.3.5 Mengubah repository package
Aplikasi "Software" memang simpel, tapi tetap mengizinkan kita untuk mengonfigurasi repository dengan GUI. Dari menu, klik "Repositories". Kita bisa menambahkan sumber "non-free" sources dan/atau mendefinisikan frekuensi dari update repository. Informasi dari alamat repository yang ditampilkan berasal dari file `sources.list`.

## 8.3.6 Update otomatis dengan Software
Untuk menggunakan sistem tanpa harus khawatir dengan update, kita bisa mengaktifkan mekanisme "automatic update". Dari menu "Software", klik "Update Preferences". Lalu nyalakan "Automatic Updates".

---

# 8.4 Discover: Package manager KDE
Gnome menggunakan "Software" untuk mengatur aplikasi secara simple, KDE menerapkan **Discover**, program yang intuitive dan efisien.

**Discover** memungkinkan kita untuk mencari, mengintall, menghapus, dan memperbarui aplikasi melalui satu interface saja. Kita dapat memodifikasi software source untuk menginstall - atau tidak - beberapa aplikasi berbayar.

**Discover** dapat diluncurkan melalui main menu KDE > Applications > System > Software > Software Center

Tidak perlu ragu saat menulusuri aplikasi yang ada, kita akan dimintai konfirmasi atas semua modifikasi yang dilakukan pada package kita.

---

## 8.4.1 Mencari dan meng-install menggunakan Discover
Untuk mencari sebuah aplikasi, ketikkan namanya pada search field atau langsung buka berdasarkan kategori yang ada pada Discover. Kemudian satu klik pada tombol "Install" sudah cukup untuk menginstallnya.
Kita akan dimintai konfirmasi untuk action pada perangkat lunak dnegan password administartornya. Prosesnya akan dijalankan di latar belakang. Progres modifikasi dapat kita ikuti melalui area notifikasi KDE.


### 8.4.1.1 Install desktop widget Plasma dan addons
DIscover memungkinkan kita untuk menambahakan komponen tambahan pada environment Plasma kita. Untuk melakukan ini, buka bagian "Plasma add-ons".
Beberapa modul tambahan juga ada untuk aplikasi kita.

---

## 8.4.2 Uninstall aplikasi menggunakan Discover
Dengan menggunakan DIscover, hanya perlu membuka kategori "Installed" kemudian klik tombol "Remove".

## 8.4.3 Discover: memperbarui aplikasi kita
Ketika KDE memeritahukan pada satu atau lebih update, Discover-lah yang menjalankannya. Untuk melakukan pengecekan terhadap update secara "manual", tekan pada tombol "Refresh".
Hanya perlu menekan tombol "Update all" dan mengkonfirmasi dengan password administrator.
Sebgaaimana pada manajemen software, kita bisa mengikuti proses pada area notifikasi KDE, dan sebuah pesan akan memberitahu kita pada bagian akhir dari proses.

---

## 8.4.4 Discover: memanajemen repositori
Softaware library KDE memungkinkan kita untuk memodifikasi source dari aplikasi kita tanpa menggunakan terminal. Buka bagian "Settings" pada Discove, isinya akan menampilkan alamat-alamat repositiri dari *sources.list* kita.

---

# 8.5 Sypnatic: Package Manager yang Komprehensif
Sypnatic adalah komprehensif graphical interface dari package manager Debian. Dengan ini kita bisa mempunyai total vision dari package-package kita, baik yang sudah di-install atau belum. Ini merupakan versi lebih detail dari Software Center maupun Discover karena ini menampilkan full set dari package-package yang tersedia (termasuk libraries).

- Ini  menyediakan fungsionalitas yang sama dengan apt.
- Kita perlu memasukkan password administrator untuk membuka dan menggunakan Synaptic.
- Koneksi internet dibutuhkan untuk meng-install atau update software kita.

---

## 8.5.1 Synaptic: Main Interface
Window di Sypantic dibagi menjadi 4 area: toolbar di atas, panel di kiri untuk mengurutkan dan memilih package, panel tengah yang menampilkan list dari packagenya, dan di bawahnya ada panel berisi deskripsi dari package yang dipilih.

Di depan tiap-tiap package, ada kotak kecil (warna putih untuk package yang belum di-install, hijau jika sudah di-install, merah apabila rusak). Di sebelah status box, ada logo Debian yang mengindikasikan bahwa package ini "free".

Jangan ragu-ragu untuk mengklik menu-menu yang lain untuk eksplor Sypnatic agar lebih familiar.

Jangan khawatir tentang kerusakan sistem karena tidak akan terjadi apa-apa hingga kita mengklik tombol "Apply". Selain itu, alert dialog untuk konfirmasi juga akan muncul untuk mengonfirmasi.

---

## 8.5.2 Me-manage repository dengan Synaptic
Repository mengizinkan kita untuk update dan install package tambahan. Repository memang sudah dikonfigurasi saat proses instalasi, tapi kita bisa me-manage mereka kapan saja kalo kita butuh. Buka package managernya Synaptic (System -> Synaptic package manager). Di top menu bar, klik "Settings -> Repositories".

Lalu kita akan melihat bahwa listnya itu sesuai dengan konten dari file `/etc/apt/sources.list`.

Sekarang, kita bisa mengubah repository source sesuai dengan kemauan kita. Hanya dengan mengklik ke sebuah source untuk memodifikasi atau klik tombol "New" untuk menambahkan source yang baru.

Setelah modifikasi kita divalidasi, aplikasinya akan menawarkan kita untuk me-reload list repository agar perubahannya dapat di-apply.

Catat juga apabila kita ingin menggunakan "check-box-only" simplified interface di Xfce, LXDE, atau LXQt, kita perlu menginstall package 
"software-properties-gtk".

---

## 8.5.3 Mengupdate sistem dengan Synaptic
Sebelum mengupdate sistem, sangat penting untuk "Reload" package listnya terlebih dahulu dengan mengklik tombolnya atau ke menu "Edit -> Reload Packages Information" (atau [CTRL]+r jika ingin menggunakan shortcut keyboard). Ini digunakan untuk memeriksa apakah versi package kita itu yang paling terbaru atau tidak.

Lalu klik "Mark All Upgrades" atau ke menu "Edit -> Mark All Upgrades". Jika tidak ada yang terjadi setelah menekan "Upgrade everything", berarti sistem kita sudah up-to-date. Kita bisa meng-close Synapticnya.

Jika beberapa package butuh di-install atau update. Kita bisa melihatnya di section "Status" -> "installed (upgradable)".

---

## 8.5.4 Mencari sebuah software
Jika kita tahu nama dari packagenya, klik tombol search dan masukkan keywordnya.

Jika kita tidak tahu nama packagenya, kita bisa mem-filter berdasarkan section, status, origin, dsb. Contohnya jika kita mencari sebuah game, klik Sections lalu scroll ke "Games dan Amusement", nanti semua package yang berhubungan dengan games and amusement akan muncul.

---

## 8.5.5 Menginstall package dengan Synaptic
Untuk menginstall satu atau beberapa package, klik kanan di kotak kecil di depan nama packagenya dan pilih "Mark for Installation". Jika, agar bisa dipakai, packagenya butuh menginstall package lain, package-package tersebut akan otomatis ditambahkan. Lalu, kita hanya perlu mengklik tombol Apply dan mengonfirmasi perubahannya.

### 8.5.5.1 Reinstall sebuah package
Kadang-kadang kita ingin re-install sebuah package yang sudah di-install. Dalam kasus ini, klik "Mark for Reinstall". Ini membuat aplikasinya ke-restore ke default configuration.

---

## 8.5.6 Uninstall sebuah package dengan Synaptic
Seperti instalasi, klik kanan di kotak kecil di depan nama package, klik "Mark for Removal". Lalu klik "Apply".

**Simple Removal** tidak menghapus file konfigurasi dari sistem, jaga-jaga misal kita akan re-install.

**Mark for Complete Removal** akan menghapus file konfigurasi. Kalo di terminal, ekuivalennya adalah purge.

---

### 8.5.6.1 Synaptic: membersihkan package tidak berguna
Seringkali, ketika software di-uninstall, beberapa package (dependency) masih tetap ada di sistem walaupun sudah tidak berguna. Package-package tidak berguna ini bisa dengan mudah dihapus dengan Synaptic.

Klik "Status" di kanan bawah. Jika "Installed (Auto removable)" muncul, klik agar menampilkan package-package yang sesuai. Lalu kita tinggal klik kanan "Mark for Complete Removal" dan klik tombol "Apply".

---

### 8.5.6.2 Menghapus sisa-sisa konfigurasi
Walaupun software sudah dihapus sepenuhnya, bebrapa sisa-sisa konfigurasi kemungkinan masih ada di dalam sistem, tapi mereka juga bisa dengan mudah dihapus menggunakan Synaptic.

Klik tombol "Status" di kiri bawah. Jika kategori "Not installed (residual config)" muncul, pilih itu. Setelah itu kita tinggal klik kanan di masing-masing package di bagian tengah dan pilih "Mark for Complete Removal". Setelah semuanya ditandai, klik tombol "Apply".

---

### 8.5.7 Melihat informasi detail di package
Dengan klik di sebuah package, deskripsinya akan muncul di tengah bawah Synaptic. Untuk mendapatkan informasi lebih lanjutnya, klik kanan dan pilih Properties. Atau pergi ke menu "Packages -> Properties".

---

### 8.5.8 Preferensi Synaptic
- General: Opsi-opsi yang ada di sini itu eksplisit. Kita juga bisa tidak mencentang opsi "Consider recommended packages as dependencies" jika kita mau sistem kita lebih ringan.
- Columns and Fonts: Memunculkan beberapa kolom di package list dan fontnya (jika dibutuhkan).
- Colors: Kamu bisa mendefinisikan package warna sesuai dengan statusnya.

---

- Files: Ketika kamu menginstall sebuah software, itu akan disimpan di cache terlebih dahulu sebelum di-install. Package-package tersebut bisa ada di banyak tempat dan menyita storage komputer kita. Di sini, kita bisa menghapus mereka secara langsung atau mengonfigurasi action otomatis.
- Network: Ini adalah cara Synaptic terhubung ke internet. Kita harus tahu apabila kondisi kita membutuhkan modifikasi dari parameter-parameter yang ada di Network.
- Distribution: Mendefinisikan behavior untuk meng-upgrade package. Kalo kita ragu, jangan mengubah ini!

---

# 8.6 Pembersihan Sistem
Walaupun kapasitas hard disk bisa bertambah, kita tetap membutuhkan free space. Terdapat beberapa scripts yang dapat membersihkan disk secara otomatis, akan tetapi lebih baik mengecek terlebih dahulu sebelum menggunakan command rm (remove).

1. Terminal Mode: Command df untuk menampilkan ringkasan dari disk space usage untuk setiap system mount points (disk dan partisi).
2. Sortir file berdasarkan size (terbesar - terkecil): Menampilkan direktori dari size terbesar ke terkecil menggunakan command du dan sort. Size file akan ditampilkan dengan unit MB.
3. Ncdu: Disk Space Analyzer dengan Console Mode. Untuk menggunakannya, ketik “ncdu” pada terminal. Berikut command untuk instalasi software tersebut: `apt update && apt install ncdu`
4. Baobab: Disk Space Analyzer dengan Graphic Mode.

---

## 8.6.2. Pembersihan Packages

apt/attitude/dpkg adalah package manager Debian pada umumnya. Ketika kita menginstall sebuah package, file archivesource/deb akan disimpan di dalam system kita (di dalam direktori /var/cache/apt/archives) untuk mengaktifkan reinstallation yang mungkin terjadi tanpa koneksi intenet. Untuk membersihkan “apt cache”, gunakan command dengan administrator mode sebagai berikut:
`apt clean`

---

Ketika cache dari instalasi package sudah dibersihkan, kita juga menghapus packages yang tidak digunakan dari system, begitu juga file konfigurasi.
Peringatan : 
Periksa list packages yang akan dihapus dengan cermat sebelum meng-accept operation yang tengah berjalan.
`apt autoremove –purge`

---

Setelah kita meng-upgrade sistem, kemungkinan beberapa packages tersebut sudah tidak tersedia lagi di dalam repositori yang baru. Packages tersebut sudah usang. Untuk menyortir dan menghapus beberapa packages tersebut, gunakan command ‘apt’ dan jangan lupa periksa dengan cermat package yang akan dihapus.
```
apt list ‘?obsolete’
apt remove ‘?obsolete’
```
Kemudian, untuk menyortir lalu menghapus konfigurasi file yang masih ada, gunakan command sebagai berikut:
```
dpkg --list | awk ‘/^rc/{print $2’
apt purge $(dpkg --list | awk ‘/^rc/ {print $2}’)
```

---

Agar lebih MANIAC!!! Kita bisa meng-install deborphan tool yang dapat menyortir orphaned package di sistem kita. Orphan packaged merupakan package yang tidak bergantung kepada package yang lain.

Peringatan:
Periksa list packages yang akan dihapus dengan cermat sebelum meng-accept operation yang tengah berjalan.
```
apt install deborphan		        		
echo $(deborphan)				
apt autoremove --purge $(deborphan)
```
---

## 8.6.3 Pengosongan Trash Bin

Terdapat 3 trash-bin yang berbeda (wastebaskets) yang harus dibawa ke dalam akun
The user wastebasket: ~/.local/share/Trash.
Kita bisa mengosongkannya dengan sistem file manager atau melalui terminal dengan command sebagai berikut:
`rm -Rf ~/.local/share/Trash/*`

The administrator wastebasket: /root/.local/share/Trash
Untuk mengosongkannya dengan cara yang lebih baik, gunakan terminal dengan command sebagai berikut:
`rm -Rf /root/.local/share/Trash/*`

The external wastebaskets
Terletak di disk eksternal dan biasa dinamakan dengan ‘/media/your_id/your_disk/.Trash_1000’. ‘your_id’ adalah nama kita saat login.

---

## 8.6.4 Membersihkan Caches Aplikasi
Beberapa aplikasi menggunakan cache folder, yakni tempat untuk menyimpan gambar, video, dan beraneka ragam file informasi grafis. Biasanya data-data tersebut tidak menempati fisk space yang terlalu banyak. Namun jika kita men-detect ada suatu folder menjadi sangat penuh, jangan ragu untuk menghapusnya.
`rm -Rf ~/.cache/*`

Setiap aplikasi mempunyai cara sendiri untuk me-manage cache-nya sendiri: ada beberapa yang langsung membersihkan cache saat aplikasinya tertutup, ada juga yang menyimpan cache nya di folder /tmp yang akan dibersihkan ketika sesi logout, dan beberapa lainnya menyimpan cache di folder tertentu.

Firefox, misalnya, kita bisa membersihkan cache dari preferences menu, kemudian menjadikannya secara otomatis membersihkan cache setiap aplikasinya tertutup.

---

## 8.6.5 Membersihkan Thumbnails
Setiap kali kita membuka suatu folder yang berisi gambar atau video, thumbnail akan terbentuk untuk merepresentasikan grafisnya. Thumbnail ini akan disimpan di suatu folder tertentu untuk digunakan, jadi tidak perlu re-compute thumbnail tersebut setiap kita membuka suatu file.
Namun masalahnya adalah saat kamu menghapus file grafisnya. Karena thumbnail tersimpan di dalam system, maka kita akan membutuhkan sedikit lagi disk space untuk menyimpan file grafis yang sudah usang.
`rm -Rf ~/.thumbnails`
Folder ini akan terbentuk kembali ketika sistem kembali men-generate thumbnail

---

# 8.7 Menginstall package ".deb" eksternal
Debian GNU/Linux menggunkan sistem package repositoriy untuk mengatur software dengan lebih baik dan meningkatkan keamanan dari sistem kita. Akan tetapi, mungkin bagi kita untuk membutuhkan package eksternal untuk format ".deb".

**... tapi siapa si "deb" ini??**

**deb** adalah singkatan dari "debian", perusahaan induknya. Untuk mendistribusikan perangkat lunaknya, Debian menggunakan format file arsip yang spesifik: ".deb". Format ini berupa compressed format seperti ".zip" yang kita gunakan untuk menyimpan data. Arsip ".deb" ini dikenali oleh berbagai package manager Debian(APT dan graphical interface Synaptic-nya) sehingga dapat ditangani dengan lebih mudah.

---

## 8.7.1 Menginstall dalam mode grafis menggunakan GDebi
GDebi adalah utilitas grafik yang memungkinkan instalasi package eksternal dengan format ".deb", juga memanajemen dependency-nya.
Untuk meng-installnya, cari "gdebi" pada package manager kesukaan kita(Synaptic, Discover, Software) atau hanya melalui terminal pada mode administrator menggunakan "su".
`apt update && apt install gdebi`

--- 
Di saat kita mengunduh package eksternal Debian, klik kanan pada package-nya dan pilih "Open with gdebi".
Di dalam menu, klik pada File > Open dan masukkan path menuju file ".deb"
Kemudian klik "Install Package". Password kita akan diminta untuk memvalidasi instalasi.
Untuk meng-uninstall pun sangat mudah: hanya perlu menekan pada "Remove Package"

---

## 8.7.2 Instalasi pada mode terminal menggunakan Dpkg
Dpkag adalah utilitas software yang menangani package, seperti halnya apt, tapi tanpa memanajemen dependency-nya. Ini berarti saat kita menggunakan dpkg untuk menginstall package eksternal, kita butuh menginstall package "dependen" satu demi satu melalui terminal kita. Secara default dpkg sudah terinstall pada Debian, dan harus digunakan dalam mode administrative.

---

**Untuk menginstall package eksternal**
`dpkg -i package_name.deb`
Sebuah pesan error akan memberitahu kita apabila terdapat dependency yang tidak ada. Lalu hanya perlu untuk menginstallnya secara jadul menggunakan apt:
`apt install dependency_1 dependency_2 ...`
Kemudian lakukan ulang instalasi package eksternalnya.
`dpkg -i package_name.deb`
**Untuk menghapus package eksternal**
`dpkg --purge package_name`

---

# 8.8 Menginstall aplikasi Flatpak
Flatpak adalah aplikasi virtualisasi sistem untuk GNU/Linux. Tujuannya adalah untuk menyediakan environment "sandbox" yang aman, terpisah dari sistem, di mana pengguna bisa menjalankan aplikasi yang tidak divalidasi oleh repository distribusi.

---

**... Aku memvirtualisasi di dalam sandbox ...?**
Aplikasi yang kita download dari repository Debian mempunyai format ".deb" yang berisi aplikasi itu sendiri. Aplikasi-aplikasi tersebut menggunakan common dependencies, yang terhubung ke satu sama lain, dan mempunyai akses ke seluruh sistem kita. Repository Debian itu aman, jadi tidak usah khawatir dengan masalah ini. Tapi terus kenapa kita harus menggunakan Flatpak?

---

Formatnya Flatpak itu berbeda: aplikasi di-compress dengan semua dependencynya, membuatnya menjadi sepenuhnya independen dari sistem di mana dia di-install. Jadi, di sini kita bisa meng-install dan menggunakan aplikasi yang telah di-update atau bahkan aplikasi yang baru, dibandingkan dengan repository Debian.

Keuntungan kedua dari format ini adalah "sandbox". Sandbox merupakan semacam "secure box" yang mana aplikasi berjalan, tanpa mempunyai akses ke seuruh sistem (kecuali kalo diizinkan sama pengguna), yang bisa mencegah software berbahaya untuk menginfeksi sistem kita.

---

Keuntungan terakhir adalah bahwa ini memungkinkan kita untuk menjalankan beberapa versi dari aplikasi yang sama.

Kerugian dari format ini adalah bahwa ini tidak diverifikasi oleh Debian security: ketika meng-install flatpak, kita harus lebih memilih aplikasi yang sudah terpercaya (Gimp, VLC, Blender ...).

---

## 8.8.1 Menginstall Flatpak
Untuk bisa mengambil keuntungan dari aplikasi dengan format Flatpak, kita harus menginstall packagenya dari mode administrasi:
`apt install flatpak`

## 8.8.2 Menambah repository Flatpak
Untuk menambah sebuah repository seperti Flathub, ketik ini di terminal:
`flatpak remote-add flathub https://flathub.org/repo/flathub.flatpakrepo`
Lalu kita akan dimintai password administrator. Dan kita harus restart sistem kita agar perubahan bisa diterapkan.

---

## 8.8.3 Mengatur aplikasi Flatpak di Gnome dengan Software
Untuk bisa mengatur flatpak dengan software manager, kita harus menambahkan plugin sesuai dengan environment kita. Untuk Gnome, di terminal dan mode administrasi, ketik:
`apt install gnome-software-plugin-flatpak`
Sekarang kita bisa mengatur flatpak seperti aplikasi-aplikasi lainnya di Software.

## 8.8.4 Mengatur aplikasi Flatpak di KDE dengan Discover
Kita harus menginstall plugin yang sesuai. Di terminal dan mode administrasi, ketik:
`apt install plasma-discover-backend-flatpak`
Kita sekarang bisa mengatur flatpak seperti aplikasi-aplikasi lainnya di Discover.

---

## 8.8.5 Mengatur aplikasi Flatpak dari terminal
Ini adalah basic command untuk mengatur flatpak dari terminal:
| Command                                 | Action                                     |
| --------------------------------------- | ------------------------------------------ |
| flatpak search flatpak_name             | Mencari sebuah flatpak di semua repository |
| flatpak install repository flatpak_name | Menginstall flatpak dari repository        |
| flatpak uninstall flatpak_name          | Menghapus flatpak                          |
| flatpak uninstall --unused              | Menghapus dependency yang tidak digunakan  |
| flatpak update                          | Mengupdate semua flatpak yang ter-install  |
| flatpak run flatpak_name                | Menjalankan flatpak                        |

---

Special case: Menginstall sebuah flatpak hanya untuk pengguna saat ini dengan opsi "--user" maka file-filenya akan diletakkan di direktory user ($HOME/.local/share/flatpak/).
`flatpak --user install *repository* flatpak_name`

**Contoh dengan LibreOffice:**
Dari Flathub:
`flatpak install flathub.org.libreoffice.LibreOffice`
Untuk menjalankan LibreOffice dari flatpak:
`flatpak run org.libreoffice.LibreOffice`

---

## 8.8.6 Menghapus sebuah aplikasi Flatpak
Jika kita sudah menginstall flatpak dari Software atau Discover, maka tinggal hapus aja dari menu di software managernya.

Jika kita ingin menghapus semua dependency, kita harus menjalankan command berikut di terminal:
`flatpak uninstall --unused`

---

## 8.8.7 Beberapa repository Flatpak
Flathub repository https://flathub.org/ mempunyai aplikasi dalam jumlah banyak:
`flatpak remote-add flathub https://flathub.org/repo/flathub.flatpakrepo`

KDE Flatpak repository:
`flatpak remote-add kdeapps httos://distribute.kde.org/kdeapps.flatpakrepo`

Gnome-nightly Flatpak repository:
`flatpak remote-add gnome-nightly https://nightly.gnome.org/gnome-nightly.flatpakrepo`

---

# 8.9 Siapa sih Sid ini?
Pertama-tama, kita harus tahu bahwa beberapa cabang distribusi Debian ada secara pararel. Yaitu **oldstable**, **stable**, **testing**, dan **unstable**, serta **experimental** branch. 

Distribusi **stable** adalah distribusi resmi Debian, yang dirilis pada saat ini, dan dipelihara dan diperbarui oleh tim Debian. Satu-satunya perubahan yang dibuat padanya adalah terkait pembaruan keamanan dan perbaikan bug. Disarankan untuk memilih versi ini.

Distribusi **oldstable** adalah versi stabil sebelumnya. Biasanya didukung oleh tim Debian selama satu tahun setelah rilis versi stabil baru. Namun, bisa bertahan lebih lama jika cukup banyak individu atau perusahaan yang terus menjamin pemeliharaannya. Kemudian disebut distribusi LTS (Long Term Support): kita memperpanjang umurnya.

---

Distribusi **Testing** adalah versi Stabil mendatang. Digunakan untuk mempersiapkan versi stabil berikutnya. Ketika semuanya baik-baik saja, ketika semua bagian berfungsi dengan baik bersama-sama, ketika semua fitur yang ditargetkan oleh tim Debian sudah termasuk, dan setelah periode pembekuan perangkat lunak dan perburuan bug, maka versi Pengujian menjadi distribusi Stabil baru resmi.

Distribusi **Unstable**, yang disebut Sid, adalah versi yang menerima semua versi paket baru dan berada di ujung inovasi, tetapi tidak sangat stabil: itu adalah laboratorium riset. Meskipun demikian, beberapa petualang berani menggunakannya secara harian.

---

Distribusi **Experimental** bukan distribusi Debian yang sesungguhnya, melainkan repositori tempat versi perangkat lunak alpha atau beta diuji coba.

Semua distribusi ini diberi julukan yang dipilih di antara karakter-karakter film kartun Toy Story. Saat ini, nama **versi stablenya adalah Bookworm**, nama **versi testingnya adalah Trixie**, nama **versi oldstable adalah Bullseye**, dan Experimental tidak memiliki nickname.