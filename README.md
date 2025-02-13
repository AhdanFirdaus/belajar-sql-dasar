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