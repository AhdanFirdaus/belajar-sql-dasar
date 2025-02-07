# Belajar SQL

requirement: https://dev.mysql.com/downloads/installer/

## SQL itu apa bang ?

Nah jadi `SQL (Structured Query Language)` adalah bahasa pemrograman yang digunakan untuk mengelola dan mengakses data yang tersimpan dalam sistem basis data relasional. 

## Sejarah Singkat
SQL pertama kali dikembangkan oleh `IBM` pada tahun 1970-an berdasarkan konsep model relasional yang dikemukakan oleh `Edgar F. Codd`. Pada tahun 1974, IBM mengembangkan bahasa `SEQUEL` untuk bekerja dengan database relasional, yang kemudian disingkat menjadi `SQL`. Pada tahun 1986, ANSI dan ISO mulai menetapkan standar SQL, membuatnya menjadi bahasa universal untuk mengelola data dalam basis data relasional. SQL terus berkembang dan menjadi standar utama yang digunakan di banyak sistem manajemen basis data, seperti `MySQL`, `PostgreSQL`, dan `Oracle`.

## Let's code
> 💡 Jangan lupa pakai titik koma ";" Dan juga disarankan pakai "_" untuk pengganti spasi atau bisa camelcase contoh "dataBarang"


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