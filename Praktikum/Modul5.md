# Praktikum  5 : Dynamic Route dan Middleware

Langkah-langkah dan hasil Screenshot praktikum 5 – Dynamic Route dan Middleware.
## Dynamic Route
* ## Langkah 1 
>  Untuk menambahkan dynamic routes pada aplikasi lumen kita, kita dapat menggunakan syntax berikut,
<br> $router->get('/user/{id}', function ($id) { <br />
<br>  return 'User Id = ' . $id; <br />
<br> }); <br />
$router->get('/post/{postId}/comments/{commentId}', function ($postId, $commentId) {
return 'Post ID = ' . $postId . ' Comments ID = ' . $commentId;
});
> $router->get('/users[/{userId}]', function ($userId = null) {
return $userId === null ? 'Data semua users' : 'Data user dengan id ' . $userId;
});
![Screenshot . Menambahkan syntax dynamic route pada file web.php yang berfungsi
untuk memanggil user berdasarkan ID yang dimasukkan](../Screenshoot/Modul5/1.PNG)

* ## Langkah 2 
> Aliases Route digunakan untuk memberi nama pada route yang telah kita buat, hal ini dapat membantu kita, saat kita ingin memanggil route tersebut pada aplikasi kita. Berikut syntax
untuk menambahkan aliases route
 <br /><br />
 $router->get('/auth/login', ['as' => 'route.auth.login', function (...) {...}])
...
$router->get('/profile', function (Request $request) {
if ($request->isLoggedIn) {
return redirect()->route('route.auth.login');
}
});
![Screenshot jalankan server](../Screenshoot/Modul5/2.PNG)

* ## Langkah 3 
> Setelah aplikasi berhasil dijalankan, kita dapat membuka browser dengan url,
http://localhost:8000/get, path yang akan kita akses akan berbentuk demikian,
http://{BASE_URL}{PATH}, jika BASE_URL kita adalah localhost:8000 dan PATH kita
adalah /get, maka url akan berbentuk seperti diatas.
![Screenshot . Mencoba mengakses url http://localhost:8000/get sesuai endpoint yang telah ditambahkan sebelumnya](../Screenshoot/Modul5/3.PNG)

## POST, PUT, PATCH, DELETE, dan OPTIONS
* ## Langkah 1
>  Sama halnya saat menambahkan method GET, kita dapat menambahkan methode POST, PUT, PATCH, DELETE, dan OPTIONS pada file web.php dengan code seperti ini
> <br> $router->post('/post', function () { </br>
<br> return 'POST'; </br>
<br> }); </br>
<br> $router->put('/put', function () { </br>
<br> return 'PUT'; </br>
<br> }); </br>
<br> $router->patch('/patch', function () {
 return 'PATCH'; </br>
<br> }); </br>
<br> $router->delete('/delete', function () {
 return 'DELETE'; </br>
<br> }); </br>
<br> $router->options('/options', function () {
 return 'OPTIONS'; </br>
<br> }); </br>
![Screenshot Menambahkan endpoint method POST, PUT, PATCH, DELETE, dan OPTIONS](../Screenshoot/Modul5/4.PNG)

* ## Langkah 2
> Mengakses url http://localhost:8000/get pada Postman
![Screenshot npm init -](../Screenshoot/Modul5/5.PNG)

* ## Langkah 3
> Mengakses url http://localhost:8000/post pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul5/6.PNG) 

* ## Langkah 4
> Mengakses url http://localhost:8000/put pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul5/7.PNG) 

* ## Langkah 5
> Mengakses url http://localhost:8000/patch pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul5/8.PNG) 

* ## Langkah 6
> Mengakses url http://localhost:8000/delete pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul5/9.PNG) 

* ## Langkah 7
> Mengakses url http://localhost:8000/options pada Postman
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul5/10.PNG) 

## Migrasi Database
* ## Langkah 1 
>  Sebelum melakukan migrasi database pastikan server database aktif kemudian pastikan sudah membuat database dengan nama lumenapi<br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul5/11.PNG)

* ## Langkah 2 
>  Kemudian ubah konfigurasi database pada file .env menjadi seperti ini<br /><br> DB_CONNECTION=mysql <br />
<br> DB_HOST=127.0.0.1 <br />
<br> DB_PORT=3306 <br />
<br> DB_DATABASE=lumenapi <br />
<br> DB_USERNAME=root <br />
<br> DB_PASSWORD=<<password masing-masing>> <br />
<br> <br />
![Screenshot jalankan node setup](../Screenshoot/Modul5/12.PNG)

* ## Langkah 3 
>Setelah mengubah konfigurasi pada file .env, kita juga perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap dan mengubah baris ini,
> <br>//$app->withFacades();<br />
<br>//$app->withEloquent(); <br />
<br> Menjadi <br />
<br> $app->withFacades();
$app->withEloquent(); <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul5/13.PNG)

* ## Langkah 4
> Setelah itu jalankan command berikut untuk membuat file migration
> <br> php artisan make:migration create_users_table # membuat migrasi
untuk tabel users<br />
<br>php artisan make:migration create_products_table # membuat
migrasi untuk tabel products<br />
<br> Setelah menjalankan 2 syntax diatas akan terbuat 2 file pada folder database/migrations dengan format YYYY_MM_DD_HHmmss_nama_migrasi. Pada file migrasi kita akan menemukan fungsi up() dan fungsi down(), fungsi up() akan digunakan pada saat kita melakukan migrasi, fungsi down() akan digunakan saat kita ingin me-rollback migrasi <br />
![Screenshot insert buku many](../Screenshoot/Modul5/14.PNG)

* ## Langkah 5
> Ubah fungsi up pada file migrasi create_users_table menjadi seperti dibawah ini
<br>public function up()<br />
<br>{<br />
<br>Schema::create('users', function (Blueprint $table) {<br />
<br>$table->id();<br />
<br>$table->timestamps();<br />
<br>$table->string('email');<br />
<br>$table->string('password');<br />
<br>});<br />
<br>}<br />
![Screenshot pencarian buku](../Screenshoot/Modul5/15.PNG)


* ## Langkah 6
> Ubah fungsi up pada file migrasi create_products_table menjadi seperti dibawah ini
<br>public function up()<br />
<br>{<br />
<br>Schema::create('products', function (Blueprint $table) {<br />
<br>$table->id();<br />
<br>$table->timestamps();<br />
<br>$table->string('name');<br />
<br>$table->integer('category_id');<br />
<br>$table->string('slug');<br />
<br>$table->integer('price');<br />
<br>$table->integer('weight');<br />
<br>a$table->text('description');<br />
<br>});<br />
<br>}<br />
![Screenshot pencarian buku](../Screenshoot/Modul5/16.PNG)

* ## Langkah 6
>  Kemudian jalankan command,
  php artisan migrate
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul5/17.PNG)

* ## Langkah 7
> Tampilan tabel yang berhasil dibuat pada database lumenapi di phpmyadmin
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul5/18.PNG)
