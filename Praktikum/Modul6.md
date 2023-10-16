# Modul 6 Pemrograman Integratif TI-A

<div align="center">
<strong><p>Modul 6 Pemrograman Integratif TI-A - Model, Controller, dan Request-Response Handler</p></strong>
<strong><p>Hanifah Rahmajati - 215150700111049</p></strong>
</div>  
  
## Model
### Langkah 1
Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya. <br /><br />

### Langkah 2
Mengganti baris kode pada file app/Models/User.php seperti berikut. <br /><br />
![ss langkah 1](../Screenshot/Modul6/ss1.png) <br /><br />

## Controller
### Langkah 1
Copy file "ExampleController.php", ubah nama file menjadi "HomeController.php", kemudian masukkan baris kode berikut. <br /><br />
![ss langkah 2](../Screenshot/Modul6/ss2.png) <br /><br />

### Langkah 2
Ubah route `/` pada file routes/web.php menjadi seperti berikut. <br /><br />
![ss langkah 3](../Screenshot/Modul6/ss3.png) <br /><br />

### Langkah 3
Buka browser dan akses path ```http://localhost:8000``` <br /><br />
![ss langkah 4](../Screenshot/Modul6/ss4.png) <br /><br />

## Request Handler
### Langkah 1
Import library Request pada file app/Http/Controllers/HomeController.php <br /><br />
![ss langkah 5](../Screenshot/Modul6/ss5.png) <br /><br />

### Langkah 2
Ubah baris kode pada fungsi index seperti berikut. <br /><br />
![ss langkah 6](../Screenshot/Modul6/ss6.png) <br /><br />

### Langkah 3
Buka browser dan akses path ```http://localhost:8000``` <br /><br />
![ss langkah 7](../Screenshot/Modul6/ss7.png) <br /><br />

## Response Handler
### Langkah 1
Import library Response pada file app/Http/Controllers/HomeController.php <br /><br />
![ss langkah 8](../Screenshot/Modul6/ss8.png) <br /><br />

### Langkah 2
Buat fungsi hello() dan menambahkan baris kode seperti berikut. <br /><br />
![ss langkah 9](../Screenshot/Modul6/ss9.png) <br /><br />

### Langkah 3
Tambahkan route /hello pada file routes/web.php <br /><br />
![ss langkah 10](../Screenshot/Modul6/ss10.png) <br /><br />

### Langkah 4
Buka browser dan akses path ```http://localhost:8000/hello``` <br /><br />
![ss langkah 11](../Screenshot/Modul6/ss11.png) <br /><br />

## Penerapan
### Langkah 1
Import library model User pada file app/Http/Controllers/HomeController.php <br /><br />
![ss langkah 12](../Screenshot/Modul6/ss12.png) <br /><br />

### Langkah 2
Tambahkan route middleware dengan baris kode berikut. <br /><br />
![ss langkah 13](../Screenshot/Modul6/ss13.png) <br /><br />
![ss langkah 14](../Screenshot/Modul6/ss14.png) <br /><br />
![ss langkah 15](../Screenshot/Modul6/ss15.png) <br /><br />

### Langkah 3
Tambahkan fungsi defaultUser(), createUser(), dan getUser() dengan baris kode berikut pada file routes/web.php <br /><br />
![ss langkah 16](../Screenshot/Modul6/ss16.png) <br /><br />

### Langkah 4
Jalankan aplikasi pada postman sesuai endpoint. <br /><br />
A. POST users/default <br /><br />
![ss langkah 17](../Screenshot/Modul6/ss17.png) <br /><br />
B. POST users/new <br /><br />
![ss langkah 18](../Screenshot/Modul6/ss18.png) <br /><br />
C. GET users/all <br /><br />
![ss langkah 19](../Screenshot/Modul6/ss19.png) <br /><br />