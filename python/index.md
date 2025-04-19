---
layout: default
title: Python Notes
---
**Materi Lanjutan Python + MySQL: Relasi Antar Tabel dan JOIN**

**Topik**: Membuat relasi antar tabel dan menampilkan data gabungan menggunakan JOIN di Python

---

### 🧠 Tujuan Pembelajaran

1. Siswa memahami konsep relasi antar tabel di database
2. Siswa dapat membuat foreign key di MySQL
3. Siswa mampu menggunakan JOIN untuk menggabungkan data antar tabel
4. Siswa bisa menampilkan data hasil JOIN melalui program Python
5. Siswa terbiasa membaca dan menganalisis hasil query untuk memahami struktur data
6. Siswa mampu merancang sistem database kecil untuk kebutuhan sederhana

---

### 📖 Pengenalan

Di dunia nyata, data dalam aplikasi biasanya **terhubung antar tabel**. Contohnya:

- Produk termasuk dalam kategori
- Buku ditulis oleh penulis
- Transaksi dilakukan oleh pelanggan

Relasi ini dapat direpresentasikan dengan **foreign key** dan diakses menggunakan **JOIN**. JOIN memungkinkan kita membaca data yang tersebar di banyak tabel seolah-olah itu satu tabel besar. Ini membantu menjaga struktur data tetap rapi dan efisien tanpa pengulangan informasi.

---

### 🧩 Apa itu JOIN?

JOIN adalah perintah dalam SQL yang digunakan untuk **menggabungkan data dari dua atau lebih tabel** berdasarkan kolom yang saling terkait, biasanya melalui **foreign key**. Tanpa JOIN, kita hanya bisa membaca satu tabel dalam satu waktu. Tapi dengan JOIN, kita bisa membaca informasi gabungan dan menghemat waktu dan baris kode.

JOIN sering digunakan ketika kita ingin menampilkan informasi dari dua tabel yang saling berhubungan. Misalnya, kita ingin menampilkan daftar produk lengkap dengan nama kategori mereka.

---

### 🎯 Tujuan Penggunaan JOIN

- Menyatukan informasi dari beberapa tabel agar dapat ditampilkan secara utuh
- Menghindari data yang berulang di dalam satu tabel
- Meningkatkan efisiensi dan struktur data
- Mengurangi duplikasi data dan potensi kesalahan input
- Membuat tampilan data yang lebih lengkap dan bermakna

---

### 🏗️ Contoh Pembuatan dan Pengisian Tabel

Untuk mempraktikkan JOIN, kamu harus memiliki dua tabel yang sudah diisi dengan data yang saling berhubungan. Berikut adalah contoh lengkap:

#### 🔹 Buat Database dan Tabel

```sql
CREATE DATABASE toko_relasi;
USE toko_relasi;

CREATE TABLE kategori (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nama_kategori VARCHAR(100)
);

CREATE TABLE produk (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nama VARCHAR(100),
  harga INT,
  kategori_id INT,
  FOREIGN KEY (kategori_id) REFERENCES kategori(id)
);
```

#### 🔹 Masukkan Data ke Tabel `kategori`

```sql
INSERT INTO kategori (nama_kategori) VALUES
('Elektronik'),
('Pakaian'),
('Alat Tulis');
```

#### 🔹 Masukkan Data ke Tabel `produk`

```sql
INSERT INTO produk (nama, harga, kategori_id) VALUES
('Kipas Angin', 150000, 1),
('Kaos Polos', 50000, 2),
('Pensil 2B', 3000, 3),
('Laptop', 7000000, 1),
('Kemeja Batik', 120000, 2);
```

Setelah menjalankan perintah di atas, kamu akan memiliki:

- 3 kategori
- 5 produk yang masing-masing terhubung ke salah satu kategori

Dengan data tersebut, kamu bisa langsung mencoba berbagai jenis JOIN dan melihat hasilnya. Kamu bisa mulai dari INNER JOIN untuk menampilkan data yang cocok di kedua tabel, lalu eksplorasi LEFT JOIN untuk melihat apa yang terjadi jika ada produk yang tidak punya kategori. Ini penting untuk memahami bagaimana sistem database menangani hubungan antar data.

Selanjutnya, kamu bisa lanjutkan dengan RIGHT JOIN untuk menampilkan semua kategori yang mungkin belum digunakan oleh produk manapun. Bahkan kamu juga bisa mencoba gabungan dari LEFT dan RIGHT JOIN menggunakan UNION agar bisa mensimulasikan efek FULL JOIN di MySQL. Dengan mencoba semua jenis JOIN ini menggunakan data yang sudah kamu buat sendiri, kamu akan lebih memahami kapan dan mengapa setiap jenis JOIN digunakan dalam proyek nyata.

Jangan lupa juga untuk mengamati hasil query setiap JOIN dan membandingkan baris mana saja yang muncul. Ini akan membantumu berpikir secara logis dan kritis saat merancang relasi data. Jika kamu merasa nyaman, cobalah mengubah isi tabel dan ulangi JOIN-nya agar kamu tahu bagaimana perubahan data bisa memengaruhi hasil penggabungan. Ini adalah latihan yang sangat penting sebelum kamu membuat aplikasi skala nyata seperti sistem kasir, perpustakaan, atau manajemen data pelanggan.

---

### 🔐 Apa itu FOREIGN KEY dan REFERENCES?

**FOREIGN KEY** adalah kolom dalam sebuah tabel yang menunjuk ke **PRIMARY KEY** di tabel lain. Ini digunakan untuk membuat **relasi antar tabel**. Tujuan utamanya adalah memastikan bahwa data dalam kolom tersebut valid, sesuai dengan data yang ada di tabel tujuan.

**REFERENCES** digunakan dalam sintaks SQL untuk menyatakan bahwa kolom FOREIGN KEY mengacu pada kolom PRIMARY KEY di tabel lain.

**Contoh:**

```sql
FOREIGN KEY (kategori_id) REFERENCES kategori(id)
```

Artinya: kolom `kategori_id` pada tabel `produk` harus berisi ID yang sudah ada di kolom `id` milik tabel `kategori`. Jika kita mencoba memasukkan nilai yang tidak ada di `kategori`, maka sistem akan menolak.

---

### 🧾 Kenapa di Tabel Produk Ada `kategori_id`?

Karena setiap produk harus termasuk dalam satu kategori. Misalnya:

- "Kipas Angin" termasuk kategori "Elektronik"
- "Kaos Polos" termasuk kategori "Pakaian"

Daripada menulis "Elektronik" atau "Pakaian" langsung di tabel `produk`, kita cukup simpan `kategori_id`, yaitu angka yang menunjuk ke baris di tabel `kategori`.

**Dari mana kita tahu ID-nya?** Kita bisa melihatnya dari tabel `kategori`. Misalnya setelah menjalankan:

```sql
SELECT * FROM kategori;
```

kita akan melihat hasil seperti:

```
1 | Elektronik
2 | Pakaian
3 | Alat Tulis
```

Maka kalau kita ingin memasukkan produk ke kategori "Pakaian", kita isi `kategori_id` dengan angka 2.

Langkah ini memastikan bahwa produk memiliki kategori yang valid dan tidak sembarangan.

---

### 📘 Jenis-Jenis JOIN dan Contoh

#### 1. **INNER JOIN**

Menampilkan hanya data yang cocok di kedua tabel.

**Contoh:**

```sql
SELECT produk.nama, kategori.nama_kategori
FROM produk
INNER JOIN kategori ON produk.kategori_id = kategori.id;
```

**Penjelasan:**

- Hanya menampilkan produk yang memiliki kategori\_id yang cocok dengan id di tabel kategori.

---

#### 2. **LEFT JOIN**

Menampilkan semua data dari tabel kiri (produk), dan data yang cocok dari tabel kanan (kategori). Jika tidak ada pasangan, akan ditampilkan NULL.

**Contoh:**

```sql
SELECT produk.nama, kategori.nama_kategori
FROM produk
LEFT JOIN kategori ON produk.kategori_id = kategori.id;
```

**Penjelasan:**

- Semua produk akan ditampilkan, walaupun tidak memiliki kategori.

---

#### 3. **RIGHT JOIN**

Kebalikan dari LEFT JOIN: menampilkan semua data dari tabel kanan (kategori), dan yang cocok dari tabel kiri (produk).

**Contoh:**

```sql
SELECT produk.nama, kategori.nama_kategori
FROM produk
RIGHT JOIN kategori ON produk.kategori_id = kategori.id;
```

**Penjelasan:**

- Semua kategori akan ditampilkan, walau belum digunakan oleh produk manapun.

---

#### 4. **FULL JOIN** (tidak didukung di MySQL secara langsung)

Menggabungkan semua data dari kedua tabel, termasuk data yang tidak cocok di salah satu tabel.

**Contoh (di PostgreSQL):**

```sql
SELECT produk.nama, kategori.nama_kategori
FROM produk
FULL OUTER JOIN kategori ON produk.kategori_id = kategori.id;
```

**Alternatif di MySQL:** Gunakan UNION dari LEFT dan RIGHT JOIN.

```sql
SELECT produk.nama, kategori.nama_kategori
FROM produk
LEFT JOIN kategori ON produk.kategori_id = kategori.id
UNION
SELECT produk.nama, kategori.nama_kategori
FROM produk
RIGHT JOIN kategori ON produk.kategori_id = kategori.id;
```

**Penjelasan:**

- Gabungan LEFT dan RIGHT JOIN akan mencakup semua baris dari kedua tabel, cocok ataupun tidak.

---

### 📁 Studi Kasus: Produk & Kategori

Kita akan membuat dua tabel:

1. `kategori` — daftar kategori produk
2. `produk` — daftar produk yang terhubung ke kategori

---

### 📦 Struktur Tabel dengan Relasi

```sql
CREATE DATABASE toko_relasi;
USE toko_relasi;

CREATE TABLE kategori (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nama_kategori VARCHAR(100)
);

CREATE TABLE produk (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nama VARCHAR(100),
  harga INT,
  kategori_id INT,
  FOREIGN KEY (kategori_id) REFERENCES kategori(id)
);
```

---

### 🔗 Hubungkan Python ke Database

```python
import mysql.connector

db = mysql.connector.connect(
    host="localhost",
    user="root",
    password="",
    database="toko_relasi"
)
cursor = db.cursor()
```

---

### 📝 Tambah Data Kategori

```python
def tambah_kategori():
    nama = input("Nama kategori: ")
    sql = "INSERT INTO kategori (nama_kategori) VALUES (%s)"
    cursor.execute(sql, (nama,))
    db.commit()
```

---

### 📝 Tambah Data Produk (dengan kategori)

```python
def tambah_produk():
    nama = input("Nama produk: ")
    harga = int(input("Harga: "))
    lihat_kategori()  # tampilkan ID kategori yang tersedia
    kategori_id = int(input("Pilih ID kategori: "))
    sql = "INSERT INTO produk (nama, harga, kategori_id) VALUES (%s, %s, %s)"
    val = (nama, harga, kategori_id)
    cursor.execute(sql, val)
    db.commit()
```

---

### 📖 Lihat Kategori

```python
def lihat_kategori():
    cursor.execute("SELECT * FROM kategori")
    for row in cursor:
        print(row)
```

---

### 📖 Lihat Produk dengan JOIN

```python
def lihat_produk_dengan_kategori():
    sql = '''
    SELECT produk.id, produk.nama, produk.harga, kategori.nama_kategori
    FROM produk
    JOIN kategori ON produk.kategori_id = kategori.id
    '''
    cursor.execute(sql)
    for row in cursor:
        print(f"ID: {row[0]} | Nama: {row[1]} | Harga: {row[2]} | Kategori: {row[3]}")
```

---

### 📋 Menu Interaktif

```python
while True:
    print("\n=== MENU ===")
    print("1. Tambah Kategori")
    print("2. Tambah Produk")
    print("3. Lihat Kategori")
    print("4. Lihat Produk dengan Kategori")
    print("5. Keluar")

    pilih = input("Pilih menu: ")
    if pilih == "1":
        tambah_kategori()
    elif pilih == "2":
        tambah_produk()
    elif pilih == "3":
        lihat_kategori()
    elif pilih == "4":
        lihat_produk_dengan_kategori()
    elif pilih == "5":
        break
    else:
        print("Pilihan tidak valid")
```

---
