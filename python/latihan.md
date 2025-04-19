---
layout: default
title: Latihan Python - Dikumpul Minggu Depan
---
# **Tugas Untuk Minggu Depan**

---

### Instructions:

- Kerjakan semua soal di bawah ini di dalam file Python (.py)w
- Sertakan komentar di setiap kode sebagai penjelasan (gunakan bahasa Indonesia)

---

### 📌 **Part 1: Variabel dan Tipe Data**

1. Buatlah 3 variabel yang menyimpan nama, umur, dan tinggi badanmu.
2. Tampilkan ketiga variabel tersebut dalam satu print statement menggunakan f-string.

### 📌 **Part 2: Operator Aritmatika**

3. Buat program sederhana untuk menghitung luas dan keliling lingkaran.
   - Input: jari-jari
   - Output: luas dan keliling
4. Buat program konversi suhu dari Celcius ke Fahrenheit.

### 📌 **Part 3: Kondisional (If Statement)**

5. Buat program yang mengecek apakah seseorang cukup umur (>= 17) untuk membuat KTP.
6. Buat program yang menentukan apakah suatu bilangan genap atau ganjil.

### 📌 **Part 4: Perulangan (Loop)**

7. Buat program untuk menampilkan angka dari 1 hingga 20 menggunakan for loop.
8. Buat program untuk menampilkan bilangan ganjil antara 1 hingga 20 menggunakan while loop.

### 📌 **Part 5: List dan Perulangan**

9. Buat list yang berisi 5 nama temanmu.
10. Gunakan for loop untuk mencetak salam untuk setiap teman di dalam list.

### 📌 **Part 6: Fungsi**

11. Buat fungsi dengan nama `luas_persegi_panjang(panjang, lebar)` dan tampilkan hasilnya untuk panjang 8 dan lebar 4.
12. Buat fungsi `cek_prima(angka)` yang mengecek apakah suatu bilangan prima atau tidak.

---

### 📌 **Part 7: Relational Database & JOIN (MySQL + Python)**

13. Buat database bernama `perpustakaan` yang memiliki 4 tabel dengan relasi sebagai berikut:
    - `anggota(id, nama, alamat)`
    - `buku(id, judul, penulis)`
    - `peminjaman(id, anggota_id, tanggal_pinjam)` dengan FOREIGN KEY ke tabel `anggota`
    - `detail_peminjaman(id, peminjaman_id, buku_id)` dengan FOREIGN KEY ke tabel `peminjaman` dan `buku`

14. Isi tabel `anggota` dengan minimal 5 data, `buku` dengan 8 data, `peminjaman` dengan 3 data, dan `detail_peminjaman` dengan 6 data.

15. Buat program Python yang:
    - Menyambungkan ke database MySQL
    - Menambahkan data ke dalam tabel `anggota`, `buku`, dan `peminjaman` via input
    - Menampilkan daftar semua anggota
    - Menampilkan daftar buku yang dipinjam, beserta nama anggota dan tanggal pinjam, menggunakan JOIN antar keempat tabel

16. Tampilkan hasil query menggunakan:
    - **INNER JOIN**: hanya buku yang benar-benar dipinjam oleh anggota
    - **LEFT JOIN**: semua peminjaman termasuk yang tidak punya detail buku

17. Tambahkan satu peminjaman tanpa detail peminjaman dan tunjukkan hasil LEFT JOIN untuk kasus tersebut.

18. Coba hapus satu data anggota yang masih memiliki data peminjaman, lalu catat error yang muncul (uji FOREIGN KEY constraint)

---

### 📸 **Pengumpulan Tugas:**

- Kirim *screenshot* hasil output program dari semua tugas yang telah dikerjakan.
- Kirim juga **video rekaman singkat** yang menunjukkan pengerjaan kode dan hasilnya.
- Kirim juga file Python yang kalian kerjakan Masing Masing.
- Submit ke Google Classroom atau platform yang ditentukan oleh guru.

---

Selamat mengerjakan dan tetap semangat belajar Python & MySQL

---
