# Belajar SQL

requirement: https://dev.mysql.com/downloads/installer/

## SQL itu apa bang ?

Nah jadi `SQL (Structured Query Language)` adalah bahasa pemrograman yang digunakan untuk mengelola dan mengakses data yang tersimpan dalam sistem basis data relasional. 

## Sejarah Singkat
SQL pertama kali dikembangkan oleh `IBM` pada tahun 1970-an berdasarkan konsep model relasional yang dikemukakan oleh `Edgar F. Codd`. Pada tahun 1974, IBM mengembangkan bahasa `SEQUEL` untuk bekerja dengan database relasional, yang kemudian disingkat menjadi `SQL`. Pada tahun 1986, ANSI dan ISO mulai menetapkan standar SQL, membuatnya menjadi bahasa universal untuk mengelola data dalam basis data relasional. SQL terus berkembang dan menjadi standar utama yang digunakan di banyak sistem manajemen basis data, seperti `MySQL`, `PostgreSQL`, dan `Oracle`.

## Let's code
> [!TIP]
> Jangan lupa pakai titik koma ";" Dan juga disarankan pakai "_" untuk pengganti spasi atau bisa camelcase contoh "dataBarang"


### Create Database

**Membuat Database**

```sql
CREATE DATABASE nama_database;
```

**Membuat Database Namun tidak mau sama**

```sql
CREATE DATABASE IF NOT EXISTS nama_database;
```
**Menghapus Database**

```sql
DROP DATABASE nama_database;
```

### Use Select Database

**Memilih & Mengaktifkan Database**

```sql
USE nama_database;
```

**Cek database yang sedang aktif.**

```sql
SELECT DATABASE();
```

### Show Database

**Cek Isi Database**

```sql
SHOW DATABASES;
```

**Cek sesuai yang ingin dicek saja**

```sql
SHOW DATABASES LIKE "nama_database";
```

**Cek sesuai awalan kata**

```sql
SHOW DATABASES LIKE "%nama_database";
```

**Cek sesuai akhir kata**

```sql
SHOW DATABASES LIKE "nama_database%";
```

### Create Table

**Membuat Table**

```sql
CREATE TABLE pelanggan(
  id_pelanggan INT AUTO_INCREMENT PRIMARY KEY,
  nama VARCHAR(50) NOT NULL,
  umur INT NOT NULL,
  alamat VARCHAR(100)
);
```

**Membuat Table tidak mau sama**

```sql
CREATE TABLE IF NOT EXISTS pelanggan_tetap(
  id_pelanggan INT AUTO_INCREMENT PRIMARY KEY,
  nama VARCHAR(50) NOT NULL,
  umur INT NOT NULL,
  alamat VARCHAR(100)
);
```

**Membuat Table sesuai table yang ada**

```sql
CREATE TABLE pelanggan_aktif AS SELECT id_pelanggan, nama, umur FROM pelanggan;
```

**Melihat isi Table**

```sql
DESC pelanggan;
```

**Melihat ada Table apa saja**

```sql
SHOW TABLES;
```

### Tipe Data

1. `Tipe Data Numerik`
Digunakan untuk menyimpan angka, baik bilangan bulat maupun desimal.

```md
`INTEGER (INT, BIGINT, SMALLINT, TINYINT)` → Bilangan bulat.
`DECIMAL (NUMERIC, FIXED)` → Bilangan desimal dengan presisi tetap.
`FLOAT (REAL, DOUBLE PRECISION)` → Bilangan desimal dengan presisi tidak tetap.
```

2. `Tipe Data String (Karakter & Teks)`
Digunakan untuk menyimpan teks atau karakter.

```md
`CHAR(n)` → String dengan panjang tetap.
`VARCHAR(n)` → String dengan panjang variabel.
`TEXT (TINYTEXT, MEDIUMTEXT, LONGTEXT)` → Menyimpan teks dalam jumlah besar.
```

3. `Tipe Data Date & Time (Tanggal & Waktu)`
Digunakan untuk menyimpan informasi tanggal dan waktu.

```md
`DATE` → Menyimpan tanggal (YYYY-MM-DD).
`TIME` → Menyimpan waktu (HH:MM:SS).
`DATETIME` → Menyimpan tanggal dan waktu (YYYY-MM-DD HH:MM:SS).
`TIMESTAMP` → Menyimpan stempel waktu dalam format Unix.
```

4. `Tipe Data Boolean`

```md
`BOOLEAN (BOOL)` → Biasanya disimpan sebagai TINYINT(1), di mana 0 berarti FALSE dan 1 berarti TRUE.
```

5. `Tipe Data Binary (Biner)`
Digunakan untuk menyimpan data dalam format biner seperti gambar atau file.

```md
`BLOB (TINYBLOB, MEDIUMBLOB, LONGBLOB)` → Menyimpan data biner dalam berbagai ukuran.
`BINARY(n), VARBINARY(n)` → Data biner dengan panjang tetap atau variabel.
```

6. `Tipe Data Lainnya`

```md
`ENUM` → Menyimpan nilai tetap yang bisa dipilih dari daftar tertentu.
`SET` → Menyimpan satu atau lebih nilai dari daftar yang telah ditentukan.
```

### Create Value

**Menambahkan Data pada table**

```sql
INSERT INTO pelanggan VALUES (NULL, "dadan", 17, "semarang");
```

**Menampilkan semua isi data pada table**

```sql
SELECT * FROM pelanggan;
```

**Menampilkan isi data yang diinginkan saja**

```sql
SELECT nama, umur FROM pelanggan;
```

### Delete & Truncate


| Aspek           | DELETE                                              | TRUNCATE                                           |
|----------------|-----------------------------------------------------|---------------------------------------------------|
| **Fungsi**      | Menghapus data dari tabel dengan kondisi tertentu (bisa sebagian atau semua). | Menghapus semua data dalam tabel tanpa kondisi. |
| **WHERE Clause** | Bisa menggunakan `WHERE` untuk menghapus data tertentu. | Tidak bisa menggunakan `WHERE`, langsung menghapus semua data. |
| **Rollback (Undo)** | Bisa dikembalikan (`ROLLBACK`) jika dalam transaksi (`BEGIN TRANSACTION`). | Tidak bisa di-rollback, karena langsung menghapus semua data secara permanen. |
| **Auto Increment** | Tidak mengubah nilai `AUTO_INCREMENT`. | Me-reset nilai `AUTO_INCREMENT` kembali ke awal. |
| **Trigger**     | Menjalankan trigger `AFTER DELETE` jika ada. | Tidak menjalankan trigger karena tidak terjadi operasi baris per baris. |


**Kapan Menggunakan DELETE atau TRUNCATE?**
- Gunakan `DELETE` jika kamu ingin menghapus `sebagian data` berdasarkan kondisi tertentu atau ingin mempertahankan perubahan dalam transaksi.
- Gunakan `TRUNCATE` jika kamu ingin menghapus `semua data` dalam tabel dengan cepat dan tidak perlu menyimpan histori penghapusan.

**Menghapus Table**

```sql
TRUNCATE TABLE pelanggan;
```

**Menghapus isi Table**

```sql
DELETE FROM pelanggan WHERE alamat = "semarang";
```

### Cloning Table

**Copy Tanpa Data**

```sql
CREATE TABLE pelanggan_copy LIKE pelanggan;
```

**Copy Dengan Data**

```sql
CREATE TABLE pelanggan_copy AS SELECT * FROM pelanggan;
```

**Copy Table berdasarkan data yang diinginkan saja**

```sql
CREATE TABLE pelanggan_jakarta AS SELECT * FROM pelanggan WHERE alamat = "semarang";
```


**Menghapus Table**

```sql
DROP TABLE pelanggan_copy;
```

### Temporary Table

`Temporary Table` adalah tabel sementara yang dibuat dalam sesi database tertentu dan otomatis terhapus setelah sesi berakhir atau setelah tabel tersebut tidak lagi dibutuhkan. Tabel ini sering digunakan untuk menyimpan data sementara dalam query kompleks, pengolahan batch, atau penyimpanan hasil sementara.


**Temporary Table di MySQL**

- Berlaku hanya dalam sesi saat ini.
- Tidak bisa diakses oleh sesi lain.
- Harus dibuat dengan kata kunci TEMPORARY.

contoh:
```sql
CREATE TEMPORARY TABLE tempOrders (
    order_id INT PRIMARY KEY,
    customer_name VARCHAR(100)
);

INSERT INTO tempOrders VALUES (101, 'dadan'), (102, 'ahdan');

SELECT * FROM tempOrders;

DROP TEMPORARY TABLE tempOrders;
```

### Alter Table

`ALTER TABLE` adalah perintah di SQL yang digunakan untuk mengubah struktur tabel yang sudah ada tanpa menghapus dan membuat ulang tabel tersebut.

**Menambahkan struktur table**

```sql
ALTER TABLE user_kita ADD tanggal_lahir DATE;
```

**Menghapus column**

```sql
ALTER TABLE user_kita DROP COLUMN tanggal_lahir;
```

**Modif**

```sql
ALTER TABLE user_kita MODIFY nama VARCHAR(50);
```

**Rename**

```sql
ALTER TABLE user_kita RENAME COLUMN nama TO nama_user;
```

**Rename Table**

```sql
ALTER TABLE user_kita RENAME TO user_milik_kita;
```

### Constraint

Constraint adalah aturan atau batasan yang diterapkan pada kolom di tabel database untuk memastikan `integritas` dan `validitas data`. Constraint membantu dalam mencegah kesalahan atau inkonsistensi dalam database.

`NOT NULL` = tidak boleh kosong
`UNIQUE` = tidak boleh kembar
`PRIMARY KEY` = bisa dikombinasi sama NOT NULL, menentukan kolom sebagai identitas unik untuk setiap baris dalam tabel dan tidak boleh NULL dan harus unik.
`CHECK` = mengisi nilai dengan kondisi" tertentu
contoh:
```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    age INT CHECK (age >= 18)
);
```
`DEFAULT` = memberikan nilai default jika tidak ada nilai yang dimasukkan.
contoh:
```sql
CREATE TABLE accounts (
    account_id INT PRIMARY KEY,
    balance DECIMAL(10,2) DEFAULT 0.00
);
```
`FOREIGN KEY` = menghubungkan dua tabel untuk menjaga hubungan referensial dan mencegah penyisipan data yang tidak valid.
contoh:
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```
cara bacanya: `user_id` harus sesuai dengan `id` di tabel `users`

### Insert Query 

**Menambahkan data**

```sql
INSERT INTO user VALUES (1, "dadan", "dadan@email.com", "jakarta"), (2, "ahdan", "ahdan@email.com", "semarang");
```

**Menambahkan data yang diinginkan saja**

```sql
INSERT INTO user (id_user, nama) VALUES (3, "firdaus")
```

### Select Query

**Menampilkan semua isi tablenya**

```sql
SELECT * FROM user;
```

**Menampilkan isi sesuai target**

```sql
SELECT nama, kota FROM user;
```

**Menampilkan sesuai isi target**

```sql
SELECT * FROM user WHERE kota = "aceh";
```

**Menampilkan sesuai isi target dan target yang lain**

```sql
SELECT * FROM user WHERE kota = "aceh" AND email LIKE "%gmail.com";
```

**Mengurutkan berdasarkan nama**

```sql
SELECT * FROM user ORDER BY nama;
```

**Mengurutkan dari bawah**

```sql
SELECT * FROM user ORDER BY nama DESC;
```

**Menampilkan 2 pertama**

```sql
SELECT * FROM user LIMIT 2;
```

**Menampilkam Total**

```sql
SELECT COUNT(*) AS total_user FROM user;
```

**Menampilkan yang unik**

```sql
SELECT DISTINCT kota FROM user;
```

### Update Query

**Mengubah**

```sql
UPDATE user SET kota = "jakarta";
```

**Mengubah sesuai target**

```sql
UPDATE user SET kota = "bandung" WHERE id_user = 1;
```

**Mengubah beberapa data secara langsung**

```sql
UPDATE user SET email = "contoh@email.com" kota = "semarang" WHERE id_user = 2;
```

**Mengubah sesuai kondisi**

```sql
UPDATE user SET kota = "surabaya" WHERE id_user > 1;
```

**Mengubah data secara dinamis**

```sql
UPDATE barang SET stok_barang = stok_barang + 5;
```

### Delete Query

**Menghapus data bukan strukturnya**

```sql
DELETE FROM user;
```

**Menghapus sesuai yang diinginkan**

```sql
DELETE FROM user WHERE id_user = 2;
```

**Menghapus sesuai informasi yang diberikan**

```sql
DELETE FROM user WHERE kota = "semarang" OR nama LIKE "%dadan%";
```