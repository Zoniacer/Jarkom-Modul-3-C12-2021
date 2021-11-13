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

8. Loguetown digunakan sebagai client Proxy agar transaksi jual beli dapat terjamin keamanannya, juga untuk mencegah kebocoran data transaksi. Pada Loguetown, proxy harus bisa diakses dengan nama jualbelikapal.yyy.com dengan port yang digunakan adalah 5000. <br>
Jawaban:<br>
Pertama dibuka /etc/bind/named.conf.local pada node enieslobby dan dimasukkan berikut ini <br>
![image](https://user-images.githubusercontent.com/63639703/141604537-ee9dccc3-8067-45d2-b8f2-c6314999040a.png)
<br> kemudian dibuka file /etc/bind/kaizoku/jualbelikapal.c12.com yang di cp dari /etc/bind/db.local dan diubah pada berikut ini <br>
![image](https://user-images.githubusercontent.com/63639703/141604630-921e6bb8-0620-4007-a097-ec9b0547c36a.png)
<br> dilakukan service bind9 restart lalu pada node skypie dibuka /etc/squid/squid.conf dan ditambah sebagai berikut<br>
![image](https://user-images.githubusercontent.com/63639703/141604762-323d7f8c-d3ac-485f-b63c-720227f2fad8.png)
<br> lalu dilakukan service squid restart, kemudian mematikan node lougetown dan menghidupkan node lougetown, lalu export export http_proxy="http://10.20.2.3:5000", bisa dicek melalui env | grep -i proxy untuk berhasil atau tidak proxy<br>
![image](https://user-images.githubusercontent.com/63639703/141604971-0c90fcbe-9c62-4b1b-9f3e-269aee0d7c20.png)
<br> Kemudian langsung saja dicoba dengan lynx google
![image](https://user-images.githubusercontent.com/63639703/141604996-6a4b8832-6875-4150-98f5-5a391e646237.png)
![image](https://user-images.githubusercontent.com/63639703/141604987-bce8fc0b-7ea2-423b-a61a-06be96d9afbe.png)

9. Agar transaksi jual beli lebih aman dan pengguna website ada dua orang, proxy dipasang autentikasi user proxy dengan enkripsi MD5 dengan dua username, yaitu luffybelikapalyyy dengan password luffy_yyy dan zorobelikapalyyy dengan password zoro_yyy. <br>
Jawaban: <br>
Dalam node water7 dilakukan sebagai berikut<br>
![image](https://user-images.githubusercontent.com/63639703/141602384-144a17b9-af59-4096-b1bb-c07b84ee8457.png)
<br>-m menggunakan enkripsi MD5. Kemudian buka file squid.conf dan isi sebagai berikut.<br>
![image](https://user-images.githubusercontent.com/63639703/141602475-5ddd1e86-7d3d-4656-830f-b529c0a78ca2.png)
<br> lalu dilakukan service squid restart dan langsung bisa dicoba di lougetown dengan lynx google.<br>
![image](https://user-images.githubusercontent.com/63639703/141602538-65022be6-c36a-41f4-aa7c-68cc3d659764.png)
![image](https://user-images.githubusercontent.com/63639703/141602632-134211bf-f3d2-426c-8124-2be1f21049ae.png)
![image](https://user-images.githubusercontent.com/63639703/141605246-dc5124d9-e52e-485e-a85e-66870d29911c.png)

10. Transaksi jual beli tidak dilakukan setiap hari, oleh karena itu akses internet dibatasi hanya dapat diakses setiap hari Senin-Kamis pukul 07.00-11.00 dan setiap hari Selasa-Jum’at pukul 17.00-03.00 keesokan harinya (sampai Sabtu pukul 03.00). <br>
Jawaban:<br>

Dalam node water7 /etc/squid/acl.conf dan ditambahkan berikut ini <br>
![image](https://user-images.githubusercontent.com/63639703/141605658-af8f2779-0ca5-409e-9515-e414c9dc552d.png)
<br>Kemudian buka /etc/squid/squid.conf dan ditambhakan berikut ini dan dihapus http_access allow all<br>
![image](https://user-images.githubusercontent.com/63639703/141605701-c9d35119-5e29-4ce3-89f3-23e19a990f4b.png)
![image](https://user-images.githubusercontent.com/63639703/141605739-237ee4b2-2a88-46d4-9f44-c11ce1af774b.png)
<br> Lalu dilakukan service squid restart, kemudian ke node lougetown untuk melakukan testing seperti berikut<br>
- Pada waktu yang tidak diperbolehkan
![image](https://user-images.githubusercontent.com/63639703/141605832-4c940256-1892-4233-9bd0-d29fef51ba83.png)
![image](https://user-images.githubusercontent.com/63639703/141605843-a1c91178-ac92-417f-b2fa-7447f548b79d.png)
- Pada waktu yang diperbolehkan
![image](https://user-images.githubusercontent.com/63639703/141605924-9c5742b8-0105-4b3d-92b4-fcc6b5cd8f16.png)
![image](https://user-images.githubusercontent.com/63639703/141605928-c335d1f1-12d0-4621-b909-9bd752c694db.png)

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
