# Jarkom_Modul2_Lapres_E08

## 1. Membuat sebuah website utama dengan alamat http://semeruyyy.pw
- Install bind9 di UML Malang ```apt-get install bind9```
- Buka file ```nano /etc/bind/named.conf.local```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 1a](img/1a.png)
- Buat folder baru ```mkdir etc/bind/semeru```
- Copy file etc/bind/db.local ke file baru di dalam folder semeru ```cp /etc/bind/db.local /etc/bind/semeru/semerue08.pw```
- Buka file ```nano /etc/bind/semeru/semerue08.pw```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 1b](img/1b.png)
- Jalankan ```service bind9 restart```
- Pada UML Gresik dan Sidoarjo (client), buka file ```nano /etc/resolv.conf```
- Masukkan IP Malang lalu save
- Berhasil ketika UML Gresik dan/atau Sidoarjo berhasil ping ```ping semerue08.pw```
- ![foto 1c](img/1c.png)

## 2. Website memiliki alias http://www.semeruyyy.pw
- Pada UML Malang buka file ```nano /etc/bind/semeru/semerue08.pw```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 2a](img/2a.png)
- Jalankan ```service bind9 restart```
- Berhasil ketika UML Gresik dan/atau Sidoarjo berhasil ping ```ping www.semerue08.pw```
- ![foto 2b](img/2b.png)

## 3. Website memiliki subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO
- Pada UML Malang buka file ```nano /etc/bind/semeru/semerue08.pw```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 3a](img/3a.png)
- Jalankan ```sevice bind9 restart```
- Berhasil ketika UML Gresik dan/atau Sidoarjo berhasil ping ```ping penanjakan.semerue08.pw```
- ![foto 3b](img/3b.png)

## 4. Dibuatkan reverse domain untuk domain utama
- Pada UML Malang buka file ```nano /etc/bind/named.conf.local```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 4a](img/4a.png)
- Jalankan ```cp /etc/bind/db.local /etc/bind/semeru/71.151.10.in-addr.arpa```
- Buka file ```nano /etc/bind/semeru/71.151.10.in-addr.arpa```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 4b](img/4b.png)
- Jalankan ```service bind9 restart```
- Berhasil ketika UML Gresik dan/atau Sidoarjo berhasil menjalankan ```host -t PTR 10.151.71.74```
- ![foto 4c](img/4c.png)

## 5. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website.
- Pada UML Malang buka file ```nano /etc/bind/named.conf.local```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 5a](img/5a.png)
- Pada UML Mojokerto jalankan ```apt-get install bind9```
- Pada UML Mojokerto buka file ```nano /etc/bind/named.conf.local```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 5b](img/5b.png)
- Pada UML Malang jalankan ```service bind9 stop```
- Pada UML Mojokerto jalankan ```service bind9 restart```
- Pada UML Gresik dan Sidoarjo (client), buka file ```nano /etc/resolv.conf```
- Masukkan IP Mojokerto lalu save
- Berhasil ketika UML Gresik dan/atau Sidoarjo berhasil ping ```ping semerue08.pw```
- ![foto 5c](img/5c.png)

## 6. Meminta dibuatkan (6) subdomain dengan alamat http://gunung.semeruyyy.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO.
- Pada UML Malang buka file ```nano /etc/bind/semeru/semerue08.pw```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 6a](img/6a.png)
- Pada UML Malang buka file ```nano /etc/bind/named.conf.options```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 6b](img/6b.png)
- Pada UML Malang buka file ```nano /etc/bind/named.conf.local```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- Jalankan ```service bind9 restart```
- Pada UML Mojokerto buka file ```nano /etc/bind/named.conf.local```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 6c](img/6c.png)
- Buat folder baru ```mkdir /etc/bind/delegasi```
- Jalankan ```cp /etc/bind/db.local /etc/bind/delegasi/gunung.semerue08.pw```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 6d](img/6d.png)
- Jalankan ```service bind9 restart```
- Berhasil ketika UML Gresik dan/atau Sidoarjo ping ```gunung.semerue08.pw```
- ![foto 6e](img/6e.png)

## 7. Meminta dibuatkan subdomain dengan nama http://naik.gunung.semeruyyy.pw , domain ini diarahkan ke IP Server PROBOLINGGO.
- Pada UML Mojokerto buka file ```nano /etc/bind/delegasi/gunung.semerue08.pw```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 7a](img/7a.png)
- Berhasil ketika UML Gresik dan/atau Sidoarjo ping ```naik.gunung.semerue08.pw```
- ![foto 7b](img/7b.png)

## 8. Mengatur web server. Domain http://semeruyyy.pw memiliki DocumentRoot pada /var/www/semeruyyy.pw
- Pada UML Probolinggo install apache2 ```apt-get install apache2```
- Install php ```apt-get install php7.0```
- Jalankan ```cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/semerue08.pw.conf```
- Konfigurasi file tersebut seperti gambar di bawah lalu simpan
- ![foto 8a](img/8a.png)
- Jalankan ```cd /var/www```
- Jalankan ```wget 10.151.36.202/semeru.pw.zip``` di direktori tersebut
- Unzip
- Jalankan ```a2ensite semerue08.pw.conf```
- Jalankan ```service apache2 restart```
- Berhasil ketika bisa akses semerue08.pw melalui browser
- ![foto 8b](img/8b.png)

## 9. Diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home
- Jalankan ```a2enmod rewrite``` lalu ```service apache2 restart```
- Jalankan ```cd /var/www/semerue08.pw```
- Buat file baru ```nano .htaccess```
- Konfigurasi file tersebut sesuai dengan yang di bawah ini lalu simpan
- ![foto 9a](img/9a.png)
- Pindah ke directory lain ```cd /etc/apache2/sites-available```
- Buka file ```nano semerue08.pw.conf```
- Konfigurasi file tersebut sesuai yang di bawah ini lalu simpan
- ![foto 9b](img/9b.png)
- Jalankan ```service apache2 restart```
- Berhasil ketika bisa mengakses ```semerue08/home”```
- ![foto 9c](img/9c.png)

## 10. Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semeruyyy.pw dan memiliki struktur folder sebagai berikut
## ![foto 10a](img/10a.png)
- Masuk ke directory ```cd /var/www```
- Jalankan ```wget 10.151.36.202/penanjakan.semeru.pw.zip```
- Unzip
- Pindah ke directory lain ```cd /etc/apache2/sites-available```
- Jalankan ```cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/penanjakan.semerue08.pw.conf```
- Konfigurasi file tersebut hingga seperti yang di bawah ini lalu simpan
- ![foto 10b](img/10b.png)
- ![foto 10c](img/10c.png)
- Jalankan ```a2ensite penanjakan.semerue08.pw.conf``` dan ```service apache2 restart```
- ![foto 10d](img/10d.png)
- ![foto 10e](img/10e.png)

## 11. Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan.
- Jalankan ```nano /etc/apache2/sites-available/penanjakan.semerue08.pw.conf```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 11a](img/11a.png)
- Jalankan ```service apache2 restart```
- ![foto 11b](img/11b.png)
- ![foto 11c](img/11c.png)
- ![foto 11d](img/11d.png)
- ![foto 11e](img/11e.png)

## 12. Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache.
- Masuk ke directory ```cd /etc/apache2/sites-available```
- Jalankan ```nano /etc/apache2/sites-available/penanjakan.semerue08.pw.conf```
- Konfigurasi file tersebut seperti gamabar di bawah ini lalu simpan
- ![foto 12a](img/12a.png)
- Jalankan ```service apache2 restart```
- ![foto 12b](img/12b.png)

## 13. Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js.
- Jalankan ```nano /etc/apache2/sites-available/penanjakan.semerue08.pw.conf```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 13a](img/13a.png)
- Jalankan ```service apache2 restart```
- ![foto 13b](img/13b.png)

## 14. Untuk web http://gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai.sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semeruyyy.pw. Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private
- Masuk ke directory /var/www dengan menjalankan ```cd /var/www```
- Jalankan ```wget 10.151.36.202/naik.gunung.semeru.pw.zip```
- Unzip dan rename folder hasil unzip menjadi ```naik.gunung.semerue08.pw```
- Masuk ke directory ```/etc/apache2/sites-available``` dengan menjalankan ```cd /etc/apache2/sites-available```
- Jalankan ```cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/naik.gunung.semerue08.pw.conf```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 14a](img/14a.png)
- Tambahkan port 8888 pada ports.conf dengan menjalankan ```nano /etc/apache2/ports.conf```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 14b](img/14b.png)
- Jalankan ```a2ensite naik.gunung.semerue08.pw``` lalu ```service apache2 restart```
- ![foto 14c](img/14c.png)

## 15. Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman default Apache yang bertuliskan “It works!”.
- Masuk ke directory “/etc/apache2” dengan menjalankan “cd /etc/apache2”
- Jalankan “htpasswd -c /etc/apache2/.htpasswd semeru” untuk menambahkan user “semeru”
- Isi password dengan “kuynaikgunung”
- Masuk ke directory “/etc/apache2/sites-available” dengan menjalankan “cd /etc/apache2/sites-available”
- Jalankan “nano naik.gunung.semerue08.pw.conf”
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 15a](img/15a.png)
- Buka http://naik.gunung.semerue08.pw:8888/ di browser
- ![foto 15b](img/15b.png)

## 16. Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw.
- Masuk ke directory ```/etc/apache2/sites-available``` dengan menjalankan ```cd /etc/apache2/sites-available```
- Jalankan ```nano  000-default.conf```
- Konfigurasi file tersebut seperti gambar di bawah ini lalu simpan
- ![foto 16a](img/16a.png)
- Jalankan ```service apache2 restart```
- Buka 10.151.71.76 di browser
- ![foto 16b](img/16b.png)

## 17. Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.
- Jalankan ```cd /var/www/penanjakan.semerue08.pw```
- Buat file baru ```nano .htaccess```
- Konfigurasi file tersebut seperti gambar di bawah ini
- ![foto 17a](img/17a.png)
- Jalankan ```service apache2 restart```
- Buka http://penanjakan.semerue08.pw/public/images/semeru.jpg di browser
- ![foto 17b](img/17b.png)
