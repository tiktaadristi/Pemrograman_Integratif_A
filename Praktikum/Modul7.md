# Modul 7 Pemrograman Integratif TI-A Relasi One-to-Many dan Many-to-Many

  
## Pembuatan Table
### Langkah 1
Sebelum membuat migrasi database atau membuat tabel pastikan server database aktif kemudian pastikan sudah membuat database dengan nama "lumenpost". <br /><br />
![ langkah 1](../Screenshot/Modul7/1.PNG) <br /><br />
![ langkah 2](../Screenshot/Modul7/2.PNG) <br /><br />

### Langkah 2
Kemudian ubah konfigurasi database pada file .env menjadi seperti gambar berikut. <br /><br />
![ langkah 3](../Screenshot/Modul7/3.PNG) <br /><br />

### Langkah 3
Setelah mengubah konfigurasi pada file .env, kita perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap dan mengaturnya seperti gambar berikut. <br /><br />
![ langkah 4](../Screenshot/Modul7/4.PNG) <br /><br />

### Langkah 4
Setelah itu buat file migration. <br /><br />
![ langkah 5](../Screenshot/Modul7/5.PNG) <br /><br />

### Langkah 5
Ubah fungsi up() pada file migrasi create_posts_table. <br /><br />
![ langkah 6](../Screenshot/Modul7/6.PNG) <br /><br />

### Langkah 6
Ubah fungsi up() pada file migrasi create_comments_table. <br /><br />
![ langkah 7](../Screenshot/Modul7/7.PNG) <br /><br />

### Langkah 7
Ubah fungsi up() pada file migrasi create_tags_table. <br /><br />
![ langkah 8](../Screenshot/Modul7/8.PNG) <br /><br />

### Langkah 8
Ubah fungsi up() pada file migrasi create_post_tag_table. <br /><br />
![ langkah 9](../Screenshot/Modul7/9.PNG) <br /><br />

### Langkah 9
Kemudian jalankan command php artisan migrate <br /><br />
![ langkah 1](../Screenshot/Modul7/10.PNG) <br /><br />

## Pembuatan Model
### Langkah 1
Buatlah file dengan nama Post.php dan isi dengan baris kode berikut. <br /><br />
![ langkah 11](../Screenshot/Modul7/11.PNG) <br /><br />

### Langkah 2
Buatlah file dengan nama Comment.php dan isi dengan baris kode berikut. <br /><br />
![ langkah 12](../Screenshot/Modul7/12.PNG) <br /><br />

### Langkah 3
Buatlah file dengan nama Tag.php dan isi dengan baris kode berikut. <br /><br />
![ langkah 13](../Screenshot/Modul7/13.PNG) <br /><br />

## Relasi One-to-Many
### Langkah 1
Tambahkan fungsi comments() pada file Post.php <br /><br />
![ langkah 14](../Screenshot/Modul7/14.PNG) <br /><br />

### Langkah 2
Tambahkan fungsi post() dan atribut postId pada $fillable pada file Comment.php <br /><br />
![ langkah 15](../Screenshot/Modul7/15.PNG) <br /><br />

### Langkah 3
Membuat file PostController.php dan isilah dengan baris kode berikut. <br /><br />
![ langkah 16](../Screenshot/Modul7/16.PNG) <br /><br />

### Langkah 4
Membuat file CommentController.php dan isilah dengan baris kode berikut. <br /><br />
![ langkah 17](../Screenshot/Modul7/17.PNG) <br /><br />

### Langkah 5
Tambahkan baris berikut pada routes/web.php <br /><br />
![ langkah 18](../Screenshot/Modul7/18.PNG) <br /><br />

### Langkah 6
Membuat satu post menggunakan Postman. <br /><br />
![ langkah 2](../Screenshot/Modul7/20.PNG) <br /><br />

### Langkah 7
Membuat satu comment menggunakan Postman. <br /><br />
![ langkah 21](../Screenshot/Modul7/21.PNG) <br /><br />

### Langkah 8
Tampilkan post menggunakan Postman. <br /><br />
![ langkah 22](../Screenshot/Modul7/22.PNG) <br /><br />

## Relasi Many-to-Many
### Langkah 1
Tambahkan fungsi tags() pada file Post.php <br /><br />
![ langkah 23](../Screenshot/Modul7/23.PNG) <br /><br />

### Langkah 2
Tambahkan fungsi posts() pada file Tag.php <br /><br />
![ langkah 24](../Screenshot/Modul7/24.PNG) <br /><br />

### Langkah 3
Membuat file TagController.php dan isilah dengan baris kode berikut. <br /><br />
![ langkah 25](../Screenshot/Modul7/25.PNG) <br /><br />

### Langkah 4
Menambahkan fungsi addTag dan response tags pada PostController.php <br /><br />
![ langkah 26](../Screenshot/Modul7/26.PNG) <br /><br />

### Langkah 5
Menambahkan baris baru pada routes/web.php untuk add dan create tag. <br /><br />
![ langkah 27](../Screenshot/Modul7/27.PNG) <br /><br />

### Langkah 6
Membuat satu tag menggunakan Postman. <br /><br />
![ langkah 28](../Screenshot/Modul7/36.PNG) <br /><br />

### Langkah 7
Membuat tag "jadul" pada post "disana engkau berdua". <br /><br />
![ langkah 28](../Screenshot/Modul7/28.PNG) <br /><br />

### Langkah 8
Menampilkan post "disana engkau berdua" menggunakan Postman. <br /><br />
![ langkah 29](../Screenshot/Modul7/29.PNG) <br /><br />

### Langkah 9
Membuat postingan "tanpamu apa artinya" menggunakan Postman. <br /><br />
![ langkah 3](../Screenshot/Modul7/30.PNG) <br /><br />

### Langkah 1
Menambahkan tag "jadul" pada postingan "tanpamu apa artinya". <br /><br />
![ langkah 31](../Screenshot/Modul7/31.PNG) <br /><br />

### Langkah 11
Membuat tag "lagu" menggunakan Postman. <br /><br />
![ langkah 32](../Screenshot/Modul7/32.PNG) <br /><br />

### Langkah 12
Menambahkan tag "lagu" pada postingan "tanpamu apa artinya". <br /><br />
![ langkah 33](../Screenshot/Modul7/33.PNG) <br /><br />

### Langkah 13
Menampilkan post pertama. <br /><br />
![ langkah 34](../Screenshot/Modul7/34.PNG) <br /><br />

### Langkah 14
Menampilkan post kedua. <br /><br />
![ langkah 35](../Screenshot/Modul7/35.PNG) <br /><br />
