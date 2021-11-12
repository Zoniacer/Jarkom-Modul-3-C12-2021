# Jarkom-Modul-3-C12-2021

### C12
Daffa Amanullah Setyawan - 05111940000071\
Satrio Hanif Wicaksono - 05111940000103\
Shidqi Dhaifullah - 05111940000108

### PRAKTIKUM MODUL 3

<br>
<br>
<br>
<br>
<br>
<br>

11. Agar transaksi bisa lebih fokus berjalan, maka dilakukan redirect website agar mudah mengingat website transaksi jual beli kapal. Setiap mengakses google.com, akan diredirect menuju super.franky.yyy.com dengan website yang sama pada soal shift modul 2. Web server super.franky.yyy.com berada pada node Skypie.<br>
Jawaban:
- Pada node EnniesLobby, Edit file named.conf.local menggunakan nano /etc/bind/named.conf.local seperti gambar di bawah

![No  11 part 1 Screenshot 2021-11-11 182915](https://user-images.githubusercontent.com/73422724/141290702-fa589046-7d43-429a-ad40-5983763b1d68.png)


- EnniesLobby, Copy file db.local ke file baru jual jualbelikapal.c12.com menggunakan cp /etc/bind/db.local /etc/bind/kaizoku/jualbelikapal.c12.com
- EnniesLobby, Edit file jualbelikapal.c12.com menggunakan nano /etc/bind/kaizoku/jualbelikapal.c12.com seperti gambar di bawah

![No  11 part 2 Screenshot 2021-11-11 183309](https://user-images.githubusercontent.com/73422724/141291216-f7ea65a6-6ba2-482b-8a33-9b463dccaceb.png)

- EnniesLobby, Jalankan perintah service bind9 restart
- Skypie, Jalankan perintah apt-get update
- Skypie, Install apache2, php, libapache2-mod-php7.0, wget, dan unzip menggunakan apt-get install [ ... ]
- Skypie, Jalankan perintah wget https://raw.githubusercontent.com/FeinardSlim/Praktikum-Modul-2-Jarkom/main/super.franky.zip
- Skypie, Jalankan perintah unzip file super.franky.zip ke direktori /var/www/ menggunakan unzip super.franky.zip -d /var/www/
- Skypie, Ubah nama folder hasil unzip menjadi super.franky.c12.com menggunakan mv /var/www/super.franky /var/www/super.franky.c12.com
- Skypie, Copy file 000-default.conf menjadi file super.franky.c12.com.conf menggunakan cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/super.franky.c12.com.conf
- Skypie, Edit file super.franky.c12.com.conf menggunakan nano /etc/apache2/sites-available/super.franky.c12.com.conf seperti gambar di bawah

![No  11 part 3 Screenshot 2021-11-11 184850](https://user-images.githubusercontent.com/73422724/141293212-cdc1a456-c694-49b7-be26-1c7e17e3edb1.png)

- Skypie, Jalankan perintah a2ensite super.franky.c12.com
- Skypie, Jalankan perintah service apache2 restart
- Water 7, Edit file super.franky.c12.com.conf menggunakan nano /etc/apache2/sites-available/super.franky.c12.com.conf seperti gambar di bawah

![No  11 part 4 Screenshot 2021-11-11 185459](https://user-images.githubusercontent.com/73422724/141293998-df140017-626c-4d13-8954-00681deab5d8.png)

-  Water 7, Edit file resolv.conf menggunakan nano /etc/resolv.conf seperti gambar di bawah

![No  11 part 5 Screenshot 2021-11-11 185739](https://user-images.githubusercontent.com/73422724/141294353-fabd47c3-5510-4586-8861-75d3b1f1c24b.png)

- Water 7, Jalankan perintah service squid restart 
- Loguetown, Jalankan perintah lynx ke google menggunakan lynx google.com menghasilkan tampilan berikut yaitu isi dari zip yang telah didownload

![No  11 part 7 Screenshot 2021-11-11 190809](https://user-images.githubusercontent.com/73422724/141295588-ceea3834-b120-4608-afc6-7023faa5893a.png)

12. Saatnya berlayar! Luffy dan Zoro akhirnya memutuskan untuk berlayar untuk mencari harta karun di super.franky.yyy.com. Tugas pencarian dibagi menjadi dua misi, Luffy bertugas untuk mendapatkan gambar (.png, .jpg), sedangkan Zoro mendapatkan sisanya. Karena Luffy orangnya sangat teliti untuk mencari harta karun, ketika ia berhasil mendapatkan gambar, ia mendapatkan gambar dan melihatnya dengan kecepatan 10 kbps.<br>
Jawaban:
- Water 7, Edit file acl-bandwidth.conf menggunakan nano /etc/squid/acl-bandwidth.conf seperti gambar di bawah

![No  12 part 1 Screenshot 2021-11-11 191049](https://user-images.githubusercontent.com/73422724/141295962-2beb05e6-7154-4cdb-b65e-6e0d761ae819.png)

- Water 7, Tambahkan line include berikut pada file squid.conf menggunakan nano /etc/squid/squid.conf seperti gambar di bawah

![No  12 part 2 Screenshot 2021-11-11 191323](https://user-images.githubusercontent.com/73422724/141296250-4b1dcad9-63e9-49c0-b71f-07c0a8b8bfb2.png)

- Water 7, Jalankan perintah service squid restart 
- Loguetown, Jalankan perintah lynx ke google menggunakan lynx google.com
- Loguetown, Pilih public > image > background-frank.jpg
- Loguetown, Download file background-frank.jpg maka terlihat kecepatan stabil seperti gambar di bawah

![No  12 part 3 Screenshot 2021-11-09 191823](https://user-images.githubusercontent.com/73422724/141296832-ae6bc23d-f8f8-4634-8a84-9560acd4434d.png)

13. Sedangkan, Zoro yang sangat bersemangat untuk mencari harta karun, sehingga kecepatan kapal Zoro tidak dibatasi ketika sudah mendapatkan harta yang diinginkannya.<br>
Jawaban:
- Water 7, Edit file acl-bandwidth.conf menggunakan nano /etc/squid/acl-bandwidth.conf tambahkan dari sebelumnya seperti gambar di bawah

![No  13 part 1 Screenshot 2021-11-11 192034](https://user-images.githubusercontent.com/73422724/141297080-bc86b7a3-d66a-474b-bff1-6f3cf9564a82.png)

- Water 7, Jalankan perintah service squid restart 
- Loguetown, Jalankan perintah lynx ke google menggunakan lynx google.com
- Loguetown, Pilih public > image > background-frank.jpg
- Loguetown, Download file background-frank.jpg maka terlihat kecepatan stabil seperti gambar di bawah

![No  13 part 3 Untitled](https://user-images.githubusercontent.com/73422724/141297164-8e0b37c0-0140-43aa-a8ec-c21a2b896b73.png)
