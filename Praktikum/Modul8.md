# Praktikum  8 : Register, Authentication dan Authorization

Langkah-langkah dan hasil Screenshot praktikum  8 : Register, Authentication dan Authorization
* ## Register
* ### Langkah 1
Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab 3 Basic Routing dan Migration,</br>
![](../Screenshoot/Modul8/1.PNG)
* ### Langkah 2
Pastikan terdapat model User.php yang digunakan pada bab 5 Model, Controller dan Request-Response Handler.
![](../Screenshoot/Modul8/2.PNG)
* ### Langkah 3
Membuat file AuthController.php
![](../Screenshoot/Modul8/3.PNG)
* ### Langkah 4
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul8/4.PNG)
* ### Langkah 5
Menjalankan aplikasi pada endpoint /auth/register
![](../Screenshoot/Modul8/5.PNG)

* ## Authentication
* ### Langkah 1
Membuatfungsi login(Request $request) pada file AuthController.php
![](../Screenshoot/Modul8/6.PNG)
* ### Langkah 2
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul8/7.PNG)
* ### Langkah 3
Menjalankan aplikasi pada endpoint /auth/login
![](../Screenshoot/Modul8/8.PNG)

* ## Token
* ### Langkah 1
Membuat migrasi baru
![](../Screenshoot/Modul8/9.PNG)
* ### Langkah 2
Menambahkan baris berikut pada migration yang baru terbuat
![](../Screenshoot/Modul8/10.PNG)
* ### Langkah 3
Menambahkan atribut token di $fillable pada User.php
![](../Screenshoot/Modul8/11.PNG)
* ### Langkah 4
Menambahkan baris berikut pada file AuthController.php
![](../Screenshoot/Modul8/12.PNG)
* ### Langkah 5
Menjalankan migrasi terbaru
![](../Screenshoot/Modul8/13.PNG)
* ### Langkah 6
Menjalankan aplikasi pada endpoint /auth/login
![](../Screenshoot/Modul8/14.PNG)

* ## Authorization
* ### Langkah 1
Membuat file Authorization.php pada folder App/Http/Middleware
![](../Screenshoot/Modul8/15.PNG)
* ### Langkah 2
Menambahkan middleware yang baru dibuat pada bootstrap/app.php.
![](../Screenshoot/Modul8/16.PNG)
* ### Langkah 3
Membuat fungsi home() pada HomeController.php
![](../Screenshoot/Modul8/17.PNG)
* ### Langkah 4
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul8/18.PNG)
* ### Langkah 5
Menjalankan aplikasi pada endpoint /home dengan melampirkan nilai token yang didapat setelah login
![](../Screenshoot/Modul8/19.PNG)
