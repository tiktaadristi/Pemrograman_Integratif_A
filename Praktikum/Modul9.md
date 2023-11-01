# Praktikum  9 : JSON Web Token (JWT)

Langkah-langkah dan hasil Screenshot praktikum 9 : JSON Web Token (JWT)
* ## Penyesuaian Database
* ### Langkah 1
Lakukan perubahan pada length kolom token dengan menghapus parameter 72 di
belakangnya/br>
![](../Screenshoot/Modul8/1.png)
```
<?php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;
class AddColumnTokenToUsers extends Migration
{
 /**
 * Run the migrations.
 *
 * @return void
 */
// from this
public function up()
 {
 Schema::table('users', function (Blueprint $table) {
 $table->string('token', 72)->unique()->nullable(); //
 });
 }
// to this
 public function up()
 {
 Schema::table('users', function (Blueprint $table) {
 $table->string('token')->unique()->nullable();
 });
 }
...
}
```
* ### Langkah 2
Pastikan terdapat model User.php yang digunakan pada bab 5 Model, Controller dan Request-Response Handler.
![](../Screenshoot/Modul8/2.png)
* ### Langkah 3
Membuat file AuthController.php
![](../Screenshoot/Modul8/3.png)
* ### Langkah 4
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul8/4.png)
* ### Langkah 5
Menjalankan aplikasi pada endpoint /auth/register
![](../Screenshoot/Modul8/5.png)

* ## Authentication
* ### Langkah 1
Membuatfungsi login(Request $request) pada file AuthController.php
![](../Screenshoot/Modul8/6.png)
* ### Langkah 2
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul8/7.png)
* ### Langkah 3
Menjalankan aplikasi pada endpoint /auth/login
![](../Screenshoot/Modul8/8.png)

* ## Token
* ### Langkah 1
Membuat migrasi baru
![](../Screenshoot/Modul8/9.png)
* ### Langkah 2
Menambahkan baris berikut pada migration yang baru terbuat
![](../Screenshoot/Modul8/10.png)
* ### Langkah 3
Menambahkan atribut token di $fillable pada User.php
![](../Screenshoot/Modul8/11.png)
* ### Langkah 4
Menambahkan baris berikut pada file AuthController.php
![](../Screenshoot/Modul8/12.png)
* ### Langkah 5
Menjalankan migrasi terbaru
![](../Screenshoot/Modul8/13.png)
* ### Langkah 6
Menjalankan aplikasi pada endpoint /auth/login
![](../Screenshoot/Modul8/14.png)

* ## Authorization
* ### Langkah 1
Membuat file Authorization.php pada folder App/Http/Middleware
![](../Screenshoot/Modul8/15.png)
* ### Langkah 2
Menambahkan middleware yang baru dibuat pada bootstrap/app.php.
![](../Screenshoot/Modul8/16.png)
* ### Langkah 3
Membuat fungsi home() pada HomeController.php
![](../Screenshoot/Modul8/17.png)
* ### Langkah 4
Menambahkan baris berikut pada routes/web.php
![](../Screenshoot/Modul8/18.png)
* ### Langkah 5
Menjalankan aplikasi pada endpoint /home dengan melampirkan nilai token yang didapat setelah login
![](../Screenshoot/Modul8/19.png)
