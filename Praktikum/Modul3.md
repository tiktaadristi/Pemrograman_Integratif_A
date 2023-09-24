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
> <br> const router = require('express').Router();  <br />
 <br>... <br />
 <br>router.get('/:id', function getOneBook(req, res) { <br />
 <br>const id = req.params.id; <br />
 <br>res.status(200).json({ <br />
 <br>message: 'mendapatkan satu buku', <br />
 <br>id, <br />
 <br>}) <br />
 <br>}) <br />
 <br>router.post('/', function createBook(req, res) <br />
 <br> res.status(200).json({ <br />
 <br>message: 'membuat buku baru' <br />
 <br>}) <br />
 <br>}) <br />
 <br>router.put('/:id', function updateBook(req, res) { <br />
 <br>const id = req.params.id; <br />
 <br>res.status(200).json({ <br />
 <br>message: 'memperbaharui satu buku', <br />
 <br>id, <br />
 <br>}) <br />
 <br>}) <br />
 <br>router.delete('/:id', function deleteBook(req, res) { <br />
 <br>const id = req.params.id; <br />
 <br>res.status(200).json({ <br />
 <br>message: 'menghapus satu buku', <br />
 <br>id, <br />
 <br>}) <br />
 <br>}) <br />
 <br>module.exports = router { <br />
![Screenshot insert buku many](../Screenshoot/Modul3/10.PNG)
* ## Langkah 5
> Lakukan import book.route.js pada file index.js dan tambahkan baris kode berikut
<br>require('dotenv').config(); <br />
<br>const express = require('express'); <br />
<br>const mongoose = require('mongoose'); <br />
<br>const bookRoutes = require('./routes/book.route'); // <br />
<br>... <br />
<br>app.get('/', (req, res) => { <br />
<br>res.status(200).json({ <br />
<br>message: ',' <br />
<br>}) <br />
<br>}) <br />
<br>app.use('/books', bookRoutes); // <br />
<br>const PORT = process.env.PORT || 8000; <br />
<br>app.listen(PORT, () => { <br />
<br>console.log(Running on port ${PORT}); <br />
<br>}) <br />
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
<br>cfunction getAllBooks(req, res) { <br />
<br>res.status(200).json({ <br />
<br>message: 'mendapatkan semua buku'  <br />
<br>}) <br />
<br>}; <br />
<br>module.exports = { <br />
<br>getAllBooks,  <br />
<br>}  <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/14.PNG)

* ## Langkah 4
>  Lakukan hal yang sama untuk getOneBook, createBook, updateBook, dan
deleteBook
> <br> function getOneBook(req, res) { <br />
 <br> const id = req.params.id;<br />
 <br> res.status(200).json({<br />
 <br> message: 'mendapatkan satu buku',<br />
 <br> id,<br />
 <br> })<br />
 <br> }<br />
 <br> function createBook(req, res) {<br />
 <br> res.status(200).json({<br />
 <br> message: 'membuat buku baru'<br />
 <br> })<br />
 <br> }<br />
 <br> function updateBook(req, res) {<br />
 <br> const id = req.params.id;<br />
 <br> res.status(200).json({<br />
 <br> message: 'memperbaharui satu buku',<br />
 <br> id,<br />
 <br> })<br />
 <br> }<br />
 <br> function deleteBook(req, res) {<br />
 <br> const id = req.params.id;<br />
 <br> res.status(200).json({<br />
 <br> message: 'menghapus satu buku',<br />
 <br> id,<br />
 <br> })<br />
 <br> }<br />
 <br> module.exports = {<br />
 <br> getAllBooks,<br />
 <br> getOneBook, //<br />
 <br> createBook, //<br />
 <br> updateBook, //<br />
 <br> deleteBook //<br />
 <br> }<br />
 <br /><br />
![Screenshot insert buku many](../Screenshoot/Modul3/15.PNG)
* ## Langkah 5
> Lakukan import book.controller.js pada file book.route.js
<br>const router = require('express').Router();<br />
<br>const book = require('../controllers/book.controller');;<br />
<br>module.exports = router;<br />
![Screenshot pencarian buku](../Screenshoot/Modul3/15.1.PNG)

* ## Langkah 6
>   Lakukan perubahan pada fungsi agar dapat memanggil fungsi dari book.controller.js
> <br> const router = require('express').Router();         <br />
<br>const book = require('../controllers/book.controller');    <br />
<br>router.get('/', book.getAllBooks);          <br />
<br> router.get('/:id', book.getOneBook);         <br />
<br>router.post('/', book.createBook);          <br />
<br> router.put('/:id', book.updateBook);         <br />
<br>router.delete('/:id', book.deleteBook);          <br />
<br> module.exports = router; <br />
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul3/15.2.PNG)
## Pembuatan model
* ## Langkah 1 
>Lakukan pembuatan direktori models di tingkat yang sama dengan index.js <br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul3/16.1.PNG)

* ## Langkah 2 
> Buatlah file book.model.js di dalamnya <br />
![Screenshot jalankan node setup](../Screenshoot/Modul3/16.2.PNG)

* ## Langkah 3 
> Tambahkan baris kode berikut sesuai dengan tabel di atas
<br>const mongoose = require('mongoose');<br />
<br>const bookSchema = new mongoose.Schema({<br />
<br>title: {<br />
<br>type: String<br />
<br>},<br />
<br>author: {<br />
<br>type: String<br />
<br>},<br />
<br>year: {<br />
<br>type: Number<br />
<br>},<br />
<br>pages: {<br />
<br>type: Number<br />
<br>},<br />
<br>summary: {<br />
<br>type: String<br />
<br>},<br />
<br>publisher: {<br />
<br>type: String<br />
<br>}<br />
<br>})<br />
<br>module.exports = mongoose.model('book', bookSchema); <br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/16.PNG)
## Operasi CRUD
* ## Langkah 1 
> Hapus semua data pada collection books <br /><br />
![Screenshot halaman https://nodejs.org/en/](../Screenshoot/Modul3/17.PNG)

* ## Langkah 2 
>  Hapus semua data pada collection books <br />
<br>const Book = require('../models/book.model');<br />
![Screenshot jalankan node setup](../Screenshoot/Modul3/18.PNG)

* ## Langkah 3 
>  Lakukan perubahan pada fungsi createBook
<br>const Book = require('../models/book.model');<br />
<br>...<br />
<br>async function createBook(req, res) {<br />
<br>const book = new Book({<br />
<br>title: req.body.title,<br />
<br>author: req.body.author,<br />
<br>year: req.body.year,<br />
<br>pages: req.body.pages,<br />
<br>summary: req.body.summary,<br />
<br>publisher: req.body.publisher,<br />
<br>})<br />
<br>try {<br />
<br>const savedBook = await book.save();<br />
<br>res.status(200).json({<br />
<br>message: 'membuat buku baru',<br />
<br>book: savedBook,<br />
<br>})<br />
<br>} catch (error) {<br />
<br>res.status(500).json({<br />
<br>message: 'kesalahan pada server',<br />
<br>error: error.message,<br />
<br>})<br />
<br>}<br />
<br>}<br />
![Screenshot jalankan command node -v ](../Screenshoot/Modul3/19.PNG)

* ## Langkah 4
>   Buatlah dua buah buku dengan data di bawah ini dengan Postman
> <br> {<br />
<br> "title": "Dilan 1990",<br />
<br> "author": "Pidi Baiq",<br />
<br> "year": 2014,<br />
<br> "pages": 332,<br />
<br> "summary": "Mirea, anata wa utsukushī",<br />
<br> "publisher": "Pastel Books"<br />
<br>}<br />
 <br>{<br />
<br>"title": "Dilan 1991",<br />
<br>"author": "Pidi Baiq",<br />
<br>"year": 2015,<br />
<br>"pages": 344,<br />
<br>"summary": "Watashi ga kare o aishite iru to ittara",<br />
<br>"publisher": "Pastel Books"<br />
<br>}<br />
![Screenshot insert buku many](../Screenshoot/Modul3/20.PNG)
![Screenshot insert buku many](../Screenshoot/Modul3/21.PNG)
* ## Langkah 5
>  Lakukan perubahan pada fungsi getAllBooks
<br>const Book = require('../models/book.model'); <br />
<br>async function getAllBooks(req, res) {<br />
<br>try {<br />
<br>const books = await Book.find();<br />
<br>res.status(200).json({<br />
<br>message: 'mendapatkan semua buku',<br />
<br>books,<br />
<br>})<br />
<br>} catch (error) {<br />
<br>res.status(500).json({<br />
<br>message: 'kesalahan pada server',<br />
<br>error: error.message,<br />
<br>})<br />
<br>}<br />
<br>}<br />
![Screenshot pencarian buku](../Screenshoot/Modul3/22.PNG)

* ## Langkah 6
> Lakukan perubahan pada fungsi getOneBook
> <br> const Book = require('../models/book.model'); <br />
<br>async function getOneBook(req, res) {<br />
<br> const id = req.params.id;<br />
<br> try {<br />
<br> const book = await Book.findById(id);<br />
<br> res.status(200).json({<br />
<br> message: 'mendapatkan satu buku',<br />
<br> book,<br />
<br> })<br />
<br> } catch (error) {<br />
<br> res.status(500).json({<br />
<br> message: 'kesalahan pada server',<br />
<br> error: error.message,<br />
<br> })<br />
<br> }<br />
<br> }<br /><br />
![Screenshot menampilkan seluruh buku](../Screenshoot/Modul3/23.PNG)

* ## Langkah 7
> Tampilkan semua buku dengan Postman
![Screenshot update buku](../Screenshoot/Modul3/24.PNG)

* ## Langkah 8
>  Tampilkan buku Dilan 1990 dengan Postman
![Screenshot update buku](../Screenshoot/Modul3/25.PNG)

* ## Langkah 9
> Lakukan perubahan pada fungsi updateBook
<br>const Book = require('../models/book.model');<br />
<br>...<br />
<br>async function updateBook(req, res) {<br />
<br>const id = req.params.id;<br />
<br>try {<br />
<br>const book = await Book.findByIdAndUpdate(<br />
<br>id, req.body, { new: true }<br />
<br>)<br />
<br>res.status(200).json({<br />
<br>message: 'memperbaharui satu buku',<br />
<br>book,<br />
<br>})<br />
<br>} catch (error) {<br />
<br>res.status(500).json({<br />
<br>message: 'kesalahan pada server',<br />
<br>error: error.message,<br />
<br>})<br />
<br>}<br />
<br>}<br />
![Screenshot delete buku](../Screenshoot/Modul3/27.PNG)

* ## Langkah 10
> Ubah judul buku Dilan 1991 menjadi "NAMA PANGGILAN" 1991" disini milik saya menjadi Tikta 1991 dengan Postman
![Screenshot delete buku](../Screenshoot/Modul3/29.PNG)

* ## Langkah 11
> Lakukan perubahan pada fungsi deleteBook
<br>const Book = require('../models/book.model');<br />
<br>async function deleteBook(req, res) {<br />
<br>const id = req.params.id;<br />
<br>try {<br />
<br>const book = await Book.findByIdAndDelete(id);<br />
<br>res.status(200).json({<br />
<br>message: 'menghapus satu buku',<br />
<br>book,<br />
<br>})<br />
<br>} catch (error) {<br />
<br>res.status(500).json({<br />
<br>message: 'kesalahan pada server',<br />
<br>error: error.message,<br />
<br>})<br />
<br>}<br />
<br>}<br />
![Screenshot delete buku](../Screenshoot/Modul3/30.PNG)

* ## Langkah 12
> Hapus buku Dilan 1990 dengan Postman
![Screenshot delete buku](../Screenshoot/Modul3/32.PNG)





