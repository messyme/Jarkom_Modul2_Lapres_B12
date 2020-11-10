# Jarkom_Modul2_Lapres_B12

1. 05111840000057 - Maisie Chiara Salsabila
2. 05111840000062 - Geizka Wahyu Fahriza


## Daftar Isi
  1. [Nomor 1](#1)
  2. [Nomor 2](#2)
  3. [Nomor 3](#3)
  4. [Nomor 4](#4)
  5. [Nomor 5](#5)
  6. [Nomor 6](#6)
  7. [Nomor 7](#7)
  8. [Nomor 8](#8)
  9. [Nomor 9](#9)
  10. [Nomor 10](#10)
  11. [Nomor 11](#11)
  12. [Nomor 12](#12)
  13. [Nomor 13](#13)
  14. [Nomor 14](#14)
  15. [Nomor 15](#15)
  16. [Nomor 16](#16)
  17. [Nomor 17](#17)


<a name="1"></a>
## SOAL NO 1
### membuat sebuah website utama dengan alamat http://semerub12.pw yang memiliki

<a name="2"></a>
## SOAL NO 2
### alias http://www.semerub12.pw

<a name="3"></a>
## SOAL NO 3
### subdomain http://penanjakan.semerub12.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO serta dibuatkan

<a name="4"></a>
## SOAL NO 4
### reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan

<a name="5"></a>
## SOAL NO 5
### DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan 


<a name="6"></a>
## SOAL NO 6
### subdomain dengan alamat http://gunung.semerub12.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO. Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan 

<a name="7"></a>
## SOAL NO 7
### subdomain dengan nama http://naik.gunung.semerub12.pw, domain ini diarahkan ke IP Server PROBOLINGGO. Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server.

<a name="8"></a>
### SOAL NO 8
### Domain http://semerub12.pw memiliki DocumentRoot pada /var/www/semerub12.pw. Awalnya web dapat diakses menggunakan alamat http://semerub12.pw/index.php/home . Karena dirasa alamat urlnya kurang bagus, maka

<a name="9"></a>
### SOAL NO 9
### diaktifkan mod rewrite agar urlnya menjadi http://semerub12.pw/home.

<a name="10"></a>
### SOAL NO 10
### Web http://penanjakan.semerub12.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semerub12.pw dan memiliki struktur folder sebagai berikut:
### /var/www/penanjakan.semerub12.pw
### /public/javascripts
### /public/css
### /public/images
### /errors


<a name="11"></a>
### SOAL NO 11
### Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan.

<a name="12"></a>
### SOAL NO 12
### Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache.

<a name="13"></a>
### SOAL NO 13
### Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semerub12.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semerub12.pw/js. Untuk web http://gunung.semerub12.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 


<a name="14"></a>
### SOAL NO 14
### sedangkan web http://naik.gunung.semerub12.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semeruyyy.pw. Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private 

<a name="15"></a>
### SOAL NO 15
### Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password "kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeruyyy.pw melainkan laman  default Apache yang bertuliskan “It works!”.

<a name="16"></a>
### SOAL NO 16
### Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw.

<a name="17"></a>
### SOAL NO 17
### Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.

