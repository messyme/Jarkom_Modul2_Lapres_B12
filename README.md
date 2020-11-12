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
  </br></br></br>


<!--
![testestes](/ss/0-1.png)
![testestes](/ss/0-2.png)
![testestes](/ss/0-3.png)
![testestes](/ss/0-4.png)
![testestes](/ss/0-5.png)
![testestes](/ss/0-6.png)
</br></br></br>
-->


<a name="1"></a>
## SOAL NO 1
### membuat sebuah website utama dengan alamat http://semerub12.pw yang memiliki
- Buka MALANG dan update package lists dengan menjalankan command: ```apt-get update```
- Install aplikasi bind9 pada MALANG ```apt-get install bind9 -y```
- Pada MALANG lakukan perintah ```nano /etc/bind/named.conf.local```
- Konfigurasi domain semerub12.pw berisi:
```
zone "semerub12.pw" {
	type master;
	file "/etc/bind/jarkom/semerub12.pw";
};
```
   ![testestes](/ss/1-1.png)
- Buat folder ```jarkom``` pada direktori ```/etc/bind``` : ```mkdir /etc/bind/jarkom```
- Salin file ```db.local``` pada ```/etc/bind``` ke dalam  folder jarkom dengan perintah: ```cp /etc/bind/db.local /etc/bind/jarkom/semerub12.pw```
- Buka dan edit file semerub12.pw dengan perintah ```nano /etc/bind/jarkom/semerub12.pw```
    ![testestes](/ss/1-2.png)
    
- Kemudian restart bind9 dengan perintah ```service bind9 restart```
- Pada client GRESIK dan SIDOARJO arahkan nameserver menuju IP MALANG dengan mengedit file resolve.conf dengan perintah ```nano /etc/resolv.conf```
```
nameserver 10.151.71.162     #IP MALANG
```
   ![testestes](/ss/1-3.png)
    
- Untuk mencoba koneksi DNS, lakukan ping domain semerub12.pw dengan melakukan perintah berikut pada client GRESIK dan SIDOARJO ```ping semerub12.pw```
</br></br></br>

<a name="2"></a>
## SOAL NO 2
### alias http://www.semerub12.pw
- Menambahkan konfigurasi pada server MALANG di dalam dile semerub12.pw ```nano /etc/bind/jarkom/semerub12.pw```
```
www	IN	CNAME	semerub12.pw.
```
![testestes](/ss/2-1.png)
	
- Kemudian restart bind9 dengan perintah ```service bind9 restart```
- Lalu cek di  client GRESIK ```ping www.semerub12.pw```
![testestes](/ss/2-ping.png)
</br></br></br>

<a name="3"></a>
## SOAL NO 3
### subdomain http://penanjakan.semerub12.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO serta dibuatkan
- edit file semeru.pw pada MALANG ```nano /etc/bind/jarkom/semerub12.pw```
```
@	IN	A	10.151.83.108	; IP PROBOLINGGO
www	IN	CNAME	semerub12.pw.
penanajakan	IN	A	10.151.83.108	; IP PROBOLINGGO
```
![testestes](/ss/3-1.png)

- edit ```nano /etc/bind/named.conf.local```
![testestes](/ss/3-2.png)

- Kemudian restart bind9 dengan perintah ```service bind9 restart```
- Kemudian pada client GRESIK lakukan testing ```ping penanjakan.semerub12.pw```
![testestes](/ss/3-ping.png)
</br></br></br>

<a name="4"></a>
## SOAL NO 4
### reverse domain untuk domain utama. Untuk mengantisipasi server dicuri/rusak, Bibah minta dibuatkan
- Edit file ```nano /etc/bind/named.conf.local``` pada MALANG
```
zone "83.151.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/83.151.10.in-addr.arpa";
};
```
![testestes](/ss/4-1.png)


- copykan file db.local ke dalam file 83.151.10.in-addr.arpa pada folder jarkom dengan perintah ```cp /etc/bind/db.local /etc/bind/jarkom/83.151.10.in-addr.arpa```
- ```83.151.10``` merupakan 3 byte pertama IP MALANG yang di-reverse urutannya
- Kemudian edit file dengan ```nano /etc/bind/jarkom/83.151.10.in-addr.arpa```
![testestes](/ss/4-2.png)

- Kemudian restart bind9 dengan perintah ```service bind9 restart```
- Untuk mengecek konfigurasi dapat melakukan perintah ```host -t PTR 10.151.83.106``` pada client GRESIK
![testestes](/ss/4-ping.png)
</br></br></br>

<a name="5"></a>
## SOAL NO 5
### DNS Server Slave pada MOJOKERTO agar Bibah tidak terganggu menikmati keindahan Semeru pada Website. Selain website utama Bibah juga meminta dibuatkan 
- Pada MALANG edit ```nano /etc/bind/named.conf.local```
```
zone "semerub12.pw" {
    type master;
    notify yes;
    also-notify { 10.151.83.107; }; // IP MOJOKERTO
    allow-transfer { 10.151.83.107; }; // MOJOKERTO
    file "/etc/bind/jarkom/semerub12.pw";
};
```
![testestes](/ss/5-1.png)

- Kemudian restart bind9 dengan perintah ```service bind9 restart```
- Buka MOJOKERTO dan update package lists dengan menjalankan command: ```apt-get update```
- Kemudian install aplikasi bind9 pada MOJOKERTO ```apt-get install bind9 -y```
- Edit file pada MOJOKERTO ```nano /etc/bind/named.conf.local```
![testestes](/ss/5-2.png)

- Kemudian restart bind9 pada MOJOKERTO dengan perintah ```service bind9 restart```
- Pada sever MALANG matikan service bind9 ```service bind9 stop```
- Pada client GRESIK atur nameserver mengarah ke IP MALANG dan MOJOKERTO ```nano /etc/resolv.conf```
![testestes](/ss/5-3.png)

- Lakukan ```ping semerub12.pw``` pada client GRESIK
![testestes](/ss/5-ping.png)
</br></br></br>

<a name="6"></a>
## SOAL NO 6
### subdomain dengan alamat http://gunung.semerub12.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO. Bibah juga ingin memberi petunjuk mendaki gunung semeru kepada anggota komunitas sehingga dia meminta dibuatkan 
#### MALANG
- Edit file ```nano /etc/bind/jarkom/semerub12.pw```
- Tambahkan konfigurasi
```
gunung	IN	A	10.151.83.108	; IP PROBOLINGGO
naik	IN	NS	gunung
```
![testestes](/ss/6-1.png)

- Edit ```nano /etc/bind/named.conf.options```
- Comment kan ```dnssec-validation auto;``` menjadi ```//dnssec-validation auto;```
- Tambahkan ```allow-query{any;};```

- Edit ```nano /etc/bind/named.conf.local```
```
zone "semerub12.pw" {
    type master;
    notify yes;
    also-notify { 10.151.83.107; }; // IP MOJOKERTO
    allow-transfer { 10.151.83.107; }; // MOJOKERTO
    file "/etc/bind/jarkom/semerub12.pw";
};
```
![testestes](/ss/6.png)
- Kemudian restart bind9 dengan perintah ```service bind9 restart```

#### MOJOKERTO
- Edit ```nano /etc/bind/named.conf.options```
- Comment kan ```//dnssec-validation auto;```
- Tambahkan ```allow-query{any;};```

- Edit file ```nano /etc/bind/named.conf.local```
```
zone "semerub12.pw" {
    type slave;
    masters { 10.151.83.107; }; // IP MALANG
    file "/var/lib/bind/gunung.semerub12.pw";
};
```
![testestes](/ss/6-2.png)

- Buat direktori delegasi ```mkdir /etc/bind/delegasi```
- Copykan db.local ke dalam gunung.semeru.b12.pw ```cp /etc/bind/db.local /etc/bind/delegasi/gunung.semerub12.pw```
- Edit ```nano /etc/bind/delegasi/gunung.semerub12.pw``` menjadi seperti gambar di bawah
![testestes](/ss/6-3.png)
- Kemudian restart bind9 dengan perintah ```service bind9 restart```

- Lakukan testing ```ping gunung.semerub12.pw```
![testestes](/ss/6-4.png)
</br></br></br>

<a name="7"></a>
## SOAL NO 7
### subdomain dengan nama http://naik.gunung.semerub12.pw, domain ini diarahkan ke IP Server PROBOLINGGO. Setelah selesai membuat keseluruhan domain, kamu diminta untuk segera mengatur web server.
- Pada MOJOKERTO edit ```nano /etc/bind/delegasi/gunung.semerub12.pw``` dan tambahkan 
	```naik	IN	A	10.151.83.108```
![testestes](/ss/7-1.png)
- Kemudian restart bind9 dengan perintah ```service bind9 restart```

- Lakukan testing ```ping gunung.semerub12.pw```
![testestes](/ss/7.png)
</br></br></br>

<a name="8"></a>
### SOAL NO 8
### Domain http://semerub12.pw memiliki DocumentRoot pada /var/www/semerub12.pw. Awalnya web dapat diakses menggunakan alamat http://semerub12.pw/index.php/home . Karena dirasa alamat urlnya kurang bagus, maka
![testestes](/ss/8-1.png)
![testestes](/ss/8.png)
</br></br></br>

<a name="9"></a>
### SOAL NO 9
### diaktifkan mod rewrite agar urlnya menjadi http://semerub12.pw/home.
![testestes](/ss/9-1.png)
![testestes](/ss/9-2.png)
</br></br></br>

<a name="10"></a>
### SOAL NO 10
### Web http://penanjakan.semerub12.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semerub12.pw dan memiliki struktur folder sebagai berikut:
```
	/var/www/penanjakan.semerub12.pw
 	/public/javascripts
 	/public/css
 	/public/images
	/errors
```
![testestes](/ss/10-3.png)
![testestes](/ss/10-1.png)
![testestes](/ss/10-2.png)
</br></br></br>

<a name="11"></a>
### SOAL NO 11
### Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan.
![testestes](/ss/11.png)
![testestes](/ss/11-1.png)
</br></br></br>

<a name="12"></a>
### SOAL NO 12
### Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache.
![testestes](/ss/12-1.png)
![testestes](/ss/12.png)
</br></br></br>

<a name="13"></a>
### SOAL NO 13
### Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semerub12.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semerub12.pw/js. Untuk web http://gunung.semerub12.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. 
![testestes](/ss/13.png)
![testestes](/ss/13-1.png)
</br></br></br>


<a name="14"></a>
### SOAL NO 14
### sedangkan web http://naik.gunung.semerub12.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semerub12.pw. Dikarenakan web http://naik.gunung.semerub12.pw bersifat private 
![testestes](/ss/14-1.png)
![testestes](/ss/14-2.png)
![testestes](/ss/14.png)
</br></br></br>

<a name="15"></a>
### SOAL NO 15
### Bibah meminta kamu membuat web http://naik.gunung.semerub12.pw agar diberi autentikasi password dengan username “semeru” dan password "kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya. Saat Bibah mengunjungi IP PROBOLINGGO, yang muncul bukan web utama http://semeru12.pw melainkan laman  default Apache yang bertuliskan “It works!”.
![testestes](/ss/15-1.png)
</br></br></br>

<a name="16"></a>
### SOAL NO 16
### Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semerub12.pw.
![testestes](/ss/16.png)
![testestes](/ss/16-1.png)
</br></br></br>

<a name="17"></a>
### SOAL NO 17
### Karena pengunjung pada /var/www/penanjakan.semerub12.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.
![testestes](/ss/17-1.png)
![testestes](/ss/17-2.png)
![testestes](/ss/17-3.png)
</br></br></br>
