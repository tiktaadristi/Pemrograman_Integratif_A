# Modul 7 Pemrograman Integratif TI-A

<div align="center">
<strong><p>Modul 7 Pemrograman Integratif TI-A - Relasi One-to-Many dan Many-to-Many</p></strong>
<strong><p>Hanifah Rahmajati - 215150700111049</p></strong>
</div>  
  
## Pembuatan Table
### Langkah 1
Sebelum membuat migrasi database atau membuat tabel pastikan server database aktif kemudian pastikan sudah membuat database dengan nama "lumenpost". <br /><br />
![ss langkah 1](../Screenshot/Modul7/ss01.png) <br /><br />
![ss langkah 2](../Screenshot/Modul7/ss02.png) <br /><br />

### Langkah 2
Kemudian ubah konfigurasi database pada file .env menjadi seperti gambar berikut. <br /><br />
![ss langkah 3](../Screenshot/Modul7/ss03.png) <br /><br />

### Langkah 3
Setelah mengubah konfigurasi pada file .env, kita perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap dan mengaturnya seperti gambar berikut. <br /><br />
![ss langkah 4](../Screenshot/Modul7/ss04.png) <br /><br />

### Langkah 4
Setelah itu buat file migration. <br /><br />
![ss langkah 5](../Screenshot/Modul7/ss05.png) <br /><br />

### Langkah 5
Ubah fungsi up() pada file migrasi create_posts_table. <br /><br />
![ss langkah 6](../Screenshot/Modul7/ss06.png) <br /><br />

### Langkah 6
Ubah fungsi up() pada file migrasi create_comments_table. <br /><br />
![ss langkah 7](../Screenshot/Modul7/ss07.png) <br /><br />

### Langkah 7
Ubah fungsi up() pada file migrasi create_tags_table. <br /><br />
![ss langkah 8](../Screenshot/Modul7/ss08.png) <br /><br />

### Langkah 8
Ubah fungsi up() pada file migrasi create_post_tag_table. <br /><br />
![ss langkah 9](../Screenshot/Modul7/ss09.png) <br /><br />

### Langkah 9
Kemudian jalankan command php artisan migrate <br /><br />
![ss langkah 10](../Screenshot/Modul7/ss10.png) <br /><br />

## Pembuatan Model
### Langkah 1
Buatlah file dengan nama Post.php dan isi dengan baris kode berikut. <br /><br />
![ss langkah 11](../Screenshot/Modul7/ss11.png) <br /><br />

### Langkah 2
Buatlah file dengan nama Comment.php dan isi dengan baris kode berikut. <br /><br />
![ss langkah 12](../Screenshot/Modul7/ss12.png) <br /><br />

### Langkah 3
Buatlah file dengan nama Tag.php dan isi dengan baris kode berikut. <br /><br />
![ss langkah 13](../Screenshot/Modul7/ss13.png) <br /><br />

## Relasi One-to-Many
### Langkah 1
Tambahkan fungsi comments() pada file Post.php <br /><br />
![ss langkah 14](../Screenshot/Modul7/ss14.png) <br /><br />

### Langkah 2
Tambahkan fungsi post() dan atribut postId pada $fillable pada file Comment.php <br /><br />
![ss langkah 15](../Screenshot/Modul7/ss15.png) <br /><br />

### Langkah 3
Membuat file PostController.php dan isilah dengan baris kode berikut. <br /><br />
![ss langkah 16](../Screenshot/Modul7/ss16.png) <br /><br />

### Langkah 4
Membuat file CommentController.php dan isilah dengan baris kode berikut. <br /><br />
![ss langkah 17](../Screenshot/Modul7/ss17.png) <br /><br />

### Langkah 5
Tambahkan baris berikut pada routes/web.php <br /><br />
![ss langkah 18](../Screenshot/Modul7/ss18.png) <br /><br />

### Langkah 6
Membuat satu post menggunakan Postman. <br /><br />
![ss langkah 20](../Screenshot/Modul7/ss20.png) <br /><br />

### Langkah 7
Membuat satu comment menggunakan Postman. <br /><br />
![ss langkah 21](../Screenshot/Modul7/ss21.png) <br /><br />

### Langkah 8
Tampilkan post menggunakan Postman. <br /><br />
![ss langkah 22](../Screenshot/Modul7/ss22.png) <br /><br />

## Relasi Many-to-Many
### Langkah 1
Tambahkan fungsi tags() pada file Post.php <br /><br />
![ss langkah 23](../Screenshot/Modul7/ss23.png) <br /><br />

### Langkah 2
Tambahkan fungsi posts() pada file Tag.php <br /><br />
![ss langkah 24](../Screenshot/Modul7/ss24.png) <br /><br />

### Langkah 3
Membuat file TagController.php dan isilah dengan baris kode berikut. <br /><br />
![ss langkah 25](../Screenshot/Modul7/ss25.png) <br /><br />

### Langkah 4
Menambahkan fungsi addTag dan response tags pada PostController.php <br /><br />
![ss langkah 26](../Screenshot/Modul7/ss26.png) <br /><br />

### Langkah 5
Menambahkan baris baru pada routes/web.php untuk add dan create tag. <br /><br />
![ss langkah 27](../Screenshot/Modul7/ss27.png) <br /><br />

### Langkah 6
Membuat satu tag menggunakan Postman. <br /><br />
![ss langkah 28](../Screenshot/Modul7/ss36.png) <br /><br />

### Langkah 7
Membuat tag "jadul" pada post "disana engkau berdua". <br /><br />
![ss langkah 28](../Screenshot/Modul7/ss28.png) <br /><br />

### Langkah 8
Menampilkan post "disana engkau berdua" menggunakan Postman. <br /><br />
![ss langkah 29](../Screenshot/Modul7/ss29.png) <br /><br />

### Langkah 9
Membuat postingan "tanpamu apa artinya" menggunakan Postman. <br /><br />
![ss langkah 30](../Screenshot/Modul7/ss30.png) <br /><br />

### Langkah 10
Menambahkan tag "jadul" pada postingan "tanpamu apa artinya". <br /><br />
![ss langkah 31](../Screenshot/Modul7/ss31.png) <br /><br />

### Langkah 11
Membuat tag "lagu" menggunakan Postman. <br /><br />
![ss langkah 32](../Screenshot/Modul7/ss32.png) <br /><br />

### Langkah 12
Menambahkan tag "lagu" pada postingan "tanpamu apa artinya". <br /><br />
![ss langkah 33](../Screenshot/Modul7/ss33.png) <br /><br />

### Langkah 13
Menampilkan post pertama. <br /><br />
![ss langkah 34](../Screenshot/Modul7/ss35.png) <br /><br />

### Langkah 14
Menampilkan post kedua. <br /><br />
![ss langkah 35](../Screenshot/Modul7/ss34.png) <br /><br />