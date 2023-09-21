# Praktikum 3 : Integrasi MongoDB dan Express

Langkah - langkah dan hasil Screenshot praktikum CRUD MongoDB Compass dan Shell.
## Percobaan instalasi NodeJS
* ## Langkah 1 
>  Buka halaman https://nodejs.org/en/ <br /><br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul3/1.1.PNG)

* ## Langkah 2 
> Download dan jalankan node setup <br /><br />
![Screenshot jalankan node setup](../Screenshoot/Modul3/1.PNG)

* ## Langkah 3 
> Setelah instalasi selesai jalankan command node -v untuk memeriksa apakah
NodeJS sudah terinstall
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/2.PNG)

## Inisiasi project Express dan pemasangan package
* ## Langkah 1
>  Lakukan pembuatan folder dengan nama express-mongodb dan masuk ke dalam
folder tersebut lalu buka melalui text editor masing-masing
![Screenshot pembuatan folder](../Screenshoot/Modul3/2.2.PNG)

* ## Langkah 2
> Lakukan npm init untuk mengenerate file package.json dengan menggunakan
command npm init -y
![Screenshot npm init -](../Screenshoot/Modul3/3.PNG)

* ## Langkah 3
> Lakukan instalasi express, mongoose, dan dotenv dengan menggunakan command
npm i express mongoose dotenv
![Screenshot instalasi express, mongoose, dan dotenv  ](../Screenshoot/Modul3/4.PNG) 

## Koneksi Express ke MongoDB
* ## Langkah 1 
>  Buatlah file index.js pada root folder dan masukkan kode di bawah ini <br /><br />
<br> require('dotenv').config(); <br />
<br>const express = require('express');<br />
<br>const mongoose = require('mongoose');<br />
<br>const app = express();<br />
<br>app.use(express.json());<br />
<br>app.get('/', (req, res) => {<br />
<br>res.status(200).json({<br />
<br>message: '<nama>,<nim>'<br />
<br>})<br />
<br>})<br />
<br>const PORT = 8000;<br />
<br>app.listen(PORT, () => {<br />
<br>console.log(`Running on port ${PORT}`);<br />
<br>})<br />
> <br> Setelah itu coba jalankan aplikasi dengan command node index.js <br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul3/4.1.PNG)

* ## Langkah 2 
>  Lakukan pembuatan file .env dan masukkan baris berikut <br /><br />
![Screenshot jalankan node setup](../Screenshoot/Modul3/5.PNG)

* ## Langkah 3 
> Setelah instalasi selesai jalankan command node -v untuk memeriksa apakah
NodeJS sudah terinstall
> Setelah itu ubahlah kode pada listening port menjadi berikut dan coba jalankan aplikasi kembali
> <br> const PORT = process.env.PORT || 8000; <br />
<br> app.listen(PORT, () => { <br />
<br> console.log(`Running on port ${PORT}`); <br />
<br> }) <br />
<br> MONGO_URI=<Connection string masing-masing> <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/7.PNG)

* ## Langkah 4
> Tambahkan baris kode berikut pada file index.js
> <br> require('dotenv').config();  <br />
<br> const express = require('express');  <br />
<br> const mongoose = require('mongoose');  <br />
<br> mongoose.connect(process.env.MONGO_URI);  <br />
<br> const db = mongoose.connection;  <br />
<br> db.on('error', (error) => {  <br />
<br> console.log(error); <br />
<br> }); <br />
<br> db.once('connected', () => {  <br />
<br> console.log('Mongo connected');  <br />
<br> }) <br />
![Screenshot insert buku many](../Screenshoot/Modul3/9.1.PNG)

## Pembuatan routing
* ## Langkah 1 
>  Lakukan pembuatan direktori routes di tingkat yang sama dengan index.js <br /><br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul3/9.2.PNG)

* ## Langkah 2 
>   Buatlah file book.route.js di dalamnya <br /><br />
![Screenshot jalankan node setup](../Screenshoot/Modul3/9.3.PNG)

* ## Langkah 3 
> Tambahkan baris kode berikut untuk fungsi getAllBooks
<br>const router = require('express').Router(); <br />
<br>router.get('/', function getAllBooks(req, res) { <br />
<br>res.status(200).json({ <br />
<br>message: 'mendapatkan semua buku' <br />
<br>}) <br />
<br>}) <br />
<br>module.exports = router; <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/9.PNG)

* ## Langkah 4
> Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan
deleteBook
> <br> const router = require('express').Router();
 <br>...
 <br>router.get('/:id', function getOneBook(req, res) {
 <br>const id = req.params.id;
 <br>res.status(200).json({
 <br>message: 'mendapatkan satu buku',
 <br>id,
 <br>})
 <br>})
 <br>router.post('/', function createBook(req, res)
 <br> res.status(200).json({
 <br>message: 'membuat buku baru'
 <br>})
 <br>})
 <br>router.put('/:id', function updateBook(req, res) {
 <br>const id = req.params.id;
 <br>res.status(200).json({
 <br>message: 'memperbaharui satu buku',
 <br>id,
 <br>})
 <br>})
 <br>router.delete('/:id', function deleteBook(req, res) {
 <br>const id = req.params.id;
 <br>res.status(200).json({
 <br>message: 'menghapus satu buku',
 <br>id,
 <br>})
 <br>})
 <br>module.exports = router { <br />
![Screenshot insert buku many](../Screenshoot/Modul3/10.PNG)
* ## Langkah 5
> Lakukan import book.route.js pada file index.js dan tambahkan baris kode berikut
<br>require('dotenv').config();
<br>const express = require('express');
<br>const mongoose = require('mongoose');
<br>const bookRoutes = require('./routes/book.route'); //
<br>...
<br>app.get('/', (req, res) => {
<br>res.status(200).json({
<br>message: ','
<br>})
<br>})
<br>app.use('/books', bookRoutes); //
<br>const PORT = process.env.PORT || 8000;
<br>app.listen(PORT, () => {
<br>console.log(Running on port ${PORT});
<br>})
![Screenshot pencarian buku](../Screenshoot/Modul3/11.PNG)

* ## Langkah 6
>  Uji salah satu endpoint dengan Postman
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul3/13.PNG)

## Pembuatan controller
* ## Langkah 1 
> Lakukan pembuatan direktori controllers di tingkat yang sama dengan index.js <br /><br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul3/14.1.PNG)

* ## Langkah 2 
>  Buatlah file book.controller.js di dalamnya <br /><br />
![Screenshot jalankan node setup](../Screenshoot/Modul3/14.2.PNG)

* ## Langkah 3 
>  Salin baris kode dari routes untuk fungsi getAllBooks
<br>cfunction getAllBooks(req, res) {
res.status(200).json({
message: 'mendapatkan semua buku'
})
};
module.exports = {
getAllBooks,
} <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/9.PNG)

* ## Langkah 4
> Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan
deleteBook
> <br> const router = require('express').Router();
 <br>...
 <br>router.get('/:id', function getOneBook(req, res) {
 <br>const id = req.params.id;
 <br>res.status(200).json({
 <br>message: 'mendapatkan satu buku',
 <br>id,
 <br>})
 <br>})
 <br>router.post('/', function createBook(req, res)
 <br> res.status(200).json({
 <br>message: 'membuat buku baru'
 <br>})
 <br>})
 <br>router.put('/:id', function updateBook(req, res) {
 <br>const id = req.params.id;
 <br>res.status(200).json({
 <br>message: 'memperbaharui satu buku',
 <br>id,
 <br>})
 <br>})
 <br>router.delete('/:id', function deleteBook(req, res) {
 <br>const id = req.params.id;
 <br>res.status(200).json({
 <br>message: 'menghapus satu buku',
 <br>id,
 <br>})
 <br>})
 <br>module.exports = router { <br />
![Screenshot insert buku many](../Screenshoot/Modul3/10.PNG)
* ## Langkah 5
> Lakukan import book.route.js pada file index.js dan tambahkan baris kode berikut
<br>require('dotenv').config();
<br>const express = require('express');
<br>const mongoose = require('mongoose');
<br>const bookRoutes = require('./routes/book.route'); //
<br>...
<br>app.get('/', (req, res) => {
<br>res.status(200).json({
<br>message: ','
<br>})
<br>})
<br>app.use('/books', bookRoutes); //
<br>const PORT = process.env.PORT || 8000;
<br>app.listen(PORT, () => {
<br>console.log(Running on port ${PORT});
<br>})
![Screenshot pencarian buku](../Screenshoot/Modul3/11.PNG)

* ## Langkah 6
>  Uji salah satu endpoint dengan Postman
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul3/13.PNG)



































* ## Langkah 7
> Melakukan perubahan summary pada buku “Hujan” menjadi “Buku yang bagus
(<NAMA>,<NIM>) dengan mengunakan command db.books.updateOne({<filter>},
{$set: {<data yang akan di update>}}) sehingga output yang dihasilkan oleh MongoDB
akan menjadi seperti berikut
![Screenshot update buku](../Screenshoot/Modul2/14.png)

* ## Langkah 8
> Melakukan perubahan publisher menjadi “Yen Press” pada semua buku “Osamu
Dazai” dengan menggunakan command db.books.updateMany({<filter>}, {$set: {<data
yang akan di update>}})
![Screenshot update buku](../Screenshoot/Modul2/15.png)

* ## Langkah 9
> Melakukan penghapusan pada buku “Overlord I” dengan menggunakan command
db.books.deleteOne({<argument>})
![Screenshot delete buku](../Screenshoot/Modul2/16.png)

* ## Langkah 10
> Melakukan penghapusan pada semua buku “Osamu Dazai dengan menggunakan
command db.books.deleteMany({<argument>})
![Screenshot delete buku](../Screenshoot/Modul2/17.png)








