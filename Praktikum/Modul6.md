# Modul 6 Pemrograman Integratif TI-A
  
## Model
### Langkah 1
Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya. <br /><br />
![ langkah 1](../Screenshoot/Modul6/1.PNG) <br /><br />

### Langkah 2
Mengganti baris kode pada file app/Models/User.php seperti berikut. <br /><br />
<?php
namespace App\Models;
use Illuminate\Database\Eloquent\Model;
cla User extends Model
{
/**
* The attributes that are ma aignable.
*
* @var array
/
protected $fillable = [ 'name', 'email', 'paword'];
/**
The attributes excluded from the model's JSON form.
*
* @var array
*/
protected $hidden = [];
}
![ langkah 1](../Screenshoot/Modul6/2.PNG) <br /><br />

## Controller
### Langkah 1
Copy file "ExampleController.php", ubah nama file menjadi "HomeController.php", kemudian masukkan baris kode berikut. <br /><br />
![ langkah 2](../Screenshoot/Modul6/3.PNG) <br /><br />

### Langkah 2
Ubah route `/` pada file routes/web.php menjadi seperti berikut. <br /><br />
![ langkah 3](../Screenshoot/Modul6/4.PNG) <br /><br />

### Langkah 3
Buka browser dan akses path ```http://localhost:8000``` <br /><br />
![ langkah 4](../Screenshoot/Modul6/5.PNG) <br /><br />

## Request Handler
### Langkah 1
Import library Request pada file app/Http/Controllers/HomeController.php <br /><br />
![ langkah 5](../Screenshoot/Modul6/6.PNG) <br /><br />

### Langkah 2
Ubah baris kode pada fungsi index seperti berikut. <br /><br />
![ langkah 6](../Screenshoot/Modul6/7.PNG) <br /><br />

### Langkah 3
Buka browser dan akses path ```http://localhost:8000``` <br /><br />
![ langkah 7](../Screenshoot/Modul6/8.PNG) <br /><br />

## Response Handler
### Langkah 1
Import library Response pada file app/Http/Controllers/HomeController.php <br /><br />
![ langkah 8](../Screenshoot/Modul6/9.PNG) <br /><br />

### Langkah 2
Buat fungsi hello() dan menambahkan baris kode seperti berikut. <br /><br />
![ langkah 9](../Screenshoot/Modul6/10.PNG) <br /><br />

### Langkah 3
Tambahkan route /hello pada file routes/web.php <br /><br />
![ langkah 10](../Screenshoot/Modul6/11.PNG) <br /><br />

### Langkah 4
Buka browser dan akses path ```http://localhost:8000/hello``` <br /><br />
![ langkah 11](../Screenshoot/Modul6/12.PNG) <br /><br />

## Penerapan
### Langkah 1
Import library model User pada file app/Http/Controllers/HomeController.php <br /><br />
![ langkah 12](../Screenshoot/Modul6/13.PNG) <br /><br />

### Langkah 2
Tambahkan route middleware dengan baris kode berikut. <br /><br />
![ langkah 13](../Screenshoot/Modul6/14.PNG) <br /><br />


### Langkah 3
Tambahkan fungsi defaultUser(), createUser(), dan getUser() dengan baris kode berikut pada file routes/web.php <br /><br />
![ langkah 15](../Screenshoot/Modul6/15.PNG) <br /><br />

### Langkah 4
Jalankan aplikasi pada postman sesuai endpoint. <br /><br />
A. POST users/default <br /><br />
![ langkah 16](../Screenshoot/Modul6/16.PNG) <br /><br />
B. POST users/new <br /><br />
![ langkah 17](../Screenshoot/Modul6/17.PNG) <br /><br />
C. GET users/all <br /><br />
![ langkah 18](../Screenshoot/Modul6/18.PNG) <br /><br />
