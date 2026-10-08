# Minpro-3-PBO-SistemManajemenKoleksiDiecast

## Deskripsi Singkat Program
Program ini adalah aplikasi Java berbasis CLI (*Command Line Interface*) untuk mengelola koleksi diecast, yaitu miniatur kendaraan. Versi Mini Project 3 ini mengembangkan proyek Minpro 2 dengan menambahkan dukungan untuk merek **Hot Wheels** dan **Mini GT**. Pengguna dapat menambah, melihat, mencari, mengubah, dan menghapus data diecast. Program tetap memakai arsitektur **MVC** dan memperluasnya dengan konsep **Abstraction** (*Abstract Class* & *Abstract Method*), **Polymorphism** (*Method Overriding* & *Method Overloading*), serta **Interface** sebagai nilai tambah.


## Penjelasan Perubahan Struktur (Dari Minpro 2 ke Minpro 3)
Pengembangan dari Mini Project 2 ke Mini Project 3 mencakup beberapa perubahan struktur sesuai modul praktikum:
1. **Penerapan Abstract Class & Abstract Method:** Class `Diecast` menjadi `abstract class` sehingga tidak bisa diinstansiasi langsung. Method pencetakan detail berubah menjadi `abstract void tampilkanDetail()` dan wajib di-override oleh subclass `HotWheels` dan `MiniGT`.
2. **Penambahan Interface (`Pajangable`):** File interface baru `Pajangable.java` dibuat di dalam package `model`. Interface ini mendeklarasikan method `pajang(String tujuan)` dan `cekKondisi()`.
3. **Penerapan Method Overloading:** Class `Diecast` mendapat dua method bernama `rawatKoleksi()` tanpa parameter dan `rawatKoleksi(String cairan)` dengan parameter. Keduanya menjadi bentuk polimorfisme statis.
4. **Pembaruan Menu Utama:** Menu ke-7 ditambahkan untuk mensimulasikan fitur dari Interface `Pajangable`. Simulasi ini memakai pengecekan tipe `instanceof` dan *downcasting*.


## Penjelasan Alur Program

<img width="382" height="163" alt="image" src="https://github.com/user-attachments/assets/020f870d-3678-45e1-86e4-7ee9baf47a6b" />

Saat program dijalankan, sistem memuat *dummy data* ke dalam memori, lalu menampilkan menu utama. Pilih angka menu yang diinginkan, lalu masukkan nilai sesuai instruksi.

**1. Tampilkan Semua Koleksi**

<img width="682" height="83" alt="image" src="https://github.com/user-attachments/assets/3bf23f92-8753-450c-bc98-d501d4849ad3" />

Program menampilkan daftar semua diecast beserta tipe dan atribut khususnya. Jika `ArrayList` masih kosong, program menampilkan pesan bahwa data koleksi belum ada.

**2. Cari Data Koleksi**

<img width="649" height="109" alt="image" src="https://github.com/user-attachments/assets/7e2bfc86-c18e-4f75-8628-b2853e23aff9" />

Masukkan ID Koleksi atau kata kunci nama model. Program mencocokkan input dengan data di `ArrayList` dan menampilkan hasilnya. Jika tidak ada yang cocok, program menampilkan pesan "Data tidak ditemukan."

**3. Tambah Hot Wheels & 4. Tambah Mini GT**

<img width="292" height="134" alt="image" src="https://github.com/user-attachments/assets/1983098b-02aa-48be-822f-c7b14c33f63b" />

Masukkan ID, Nama Model, dan Tahun Rilis.
* Pada menu 3 (Hot Wheels), program meminta satu input tambahan: apakah diecast tersebut tipe *Treasure Hunt* (y/n).
* Pada menu 4 (Mini GT), program meminta *Nomor Box* (angka).

Setelah semua data diisi, program menyimpannya ke dalam `ArrayList`.

**5. Ubah Data Koleksi**

<img width="690" height="161" alt="image" src="https://github.com/user-attachments/assets/0322f1af-35bd-4dde-81f5-8e34d60a8b0b" />

Program menampilkan daftar koleksi. Masukkan ID diecast yang ingin diubah, lalu masukkan Nama Model dan Tahun Rilis yang baru. Program memperbarui data di `ArrayList`.

**6. Hapus Koleksi**

<img width="683" height="129" alt="image" src="https://github.com/user-attachments/assets/0c501c61-362f-4472-abd9-e85f5b93e837" />

Program menampilkan daftar koleksi. Masukkan ID diecast yang akan dihapus, lalu program menghapusnya dari `ArrayList`. Jika ID tidak ditemukan, program menampilkan pesan error.

**7. Simulasi Pajang & Cek Kondisi (Interface)**

<img width="621" height="166" alt="image" src="https://github.com/user-attachments/assets/bdf69826-c9ce-4fd5-9955-8bf1f91d22a2" />

Program menampilkan daftar koleksi. Masukkan ID diecast yang ingin dipajang, lalu masukkan tujuan pemajangan (misalnya "Dijual", "Dikoleksi", atau "Disimpan"). Program memanggil `pajang()` dan `cekKondisi()` sesuai kelas masing-masing.

**8. Keluar**

<img width="294" height="37" alt="image" src="https://github.com/user-attachments/assets/ee8ef150-4404-498f-9628-7ef77b55f2d5" />

Pilih angka 8 di menu utama. Program berhenti dan menampilkan "Terima kasih, program selesai."


## Penjelasan Penerapan Encapsulation dan Inheritance

**A. Encapsulation (Pembungkusan Data):**
Atribut di `Diecast.java`, `HotWheels.java`, dan `MiniGT.java` menggunakan access modifier `protected` atau `private`. Dengan begitu, data tidak bisa diubah sembarangan dari luar. Data hanya bisa dibaca dan diubah melalui method *Getter* dan *Setter*.

**B. Inheritance (Pewarisan):**
Program memiliki satu superclass dan dua subclass:
* **Superclass (`Diecast`):** Menyimpan atribut dasar yang dimiliki semua diecast, yaitu ID Koleksi, Nama Model, dan Tahun Rilis.
* **Subclass (`HotWheels` & `MiniGT`):** Mewarisi atribut induk melalui keyword `extends Diecast`, lalu menambahkan atribut khusus: `isTreasureHunt` pada Hot Wheels dan `nomorBox` pada Mini GT. Constructor subclass wajib memanggil `super()` untuk meneruskan data ke kelas induk.


## Penjelasan Penerapan Abstraction dan Polymorphism

<img width="610" height="141" alt="image" src="https://github.com/user-attachments/assets/99c2efc6-c442-4419-887d-f5b84c999abb" />

**A. Abstraction (Abstraksi):**
* **Abstract Class:** `Diecast` dideklarasikan sebagai `public abstract class Diecast`. Akibatnya, `new Diecast()` tidak bisa dipanggil.
* **Abstract Method:** `public abstract void tampilkanDetail();` tidak memiliki body di kelas induk. Method ini memaksa `HotWheels` dan `MiniGT` menyediakan implementasi sendiri untuk menampilkan detail masing-masing.

**B. Polymorphism (Polimorfisme):**
* **Method Overriding (Dynamic Polymorphism):** Diterapkan pada `tampilkanDetail()`, `pajang()`, dan `cekKondisi()`. Method dideklarasikan di superclass atau interface, lalu di-override (`@Override`) di `HotWheels` dan `MiniGT`. Hasilnya, output setiap jenis diecast berbeda.
* **Method Overloading (Static Polymorphism):** Diterapkan di `Diecast` lewat dua method dengan nama sama tetapi parameter berbeda: `rawatKoleksi()` untuk pembersihan dasar dan `rawatKoleksi(String cairan)` untuk pemolesan dengan cairan tertentu.
* **Polymorphic Collection:** `ArrayList` di dalam Controller bertipe induk `ArrayList<Diecast>`. Satu list ini dapat menampung objek `HotWheels` dan `MiniGT` sekaligus.


## Penjelasan Letak Penerapan Nilai Tambah

**A. Menerapkan Struktur MVC (Model-View-Controller)**

<img width="357" height="219" alt="image" src="https://github.com/user-attachments/assets/c2432563-f92a-404e-b647-1e479404a63f" />

Program memisahkan logika dan tampilan ke dalam beberapa package:
* **`package main`:** Berisi `Main.java`, titik masuk (*entry point*) aplikasi.
* **`package model`:** Berisi `Diecast.java`, `HotWheels.java`, `MiniGT.java`, dan `Pajangable.java`. Package ini menangani struktur data, aturan bisnis, dan interface.
* **`package view`:** Berisi `KoleksiView.java`. Package ini hanya mencetak menu, tata letak, dan pesan ke konsol (*System.out.println*).
* **`package controller`:** Berisi `KoleksiController.java`. Class ini memegang `ArrayList`, memproses input pengguna, memperbarui data di `model`, lalu meminta `view` menampilkan hasilnya.

**B. Interface (`Pajangable.java`) dan Operator `instanceof`**

<img width="663" height="368" alt="image" src="https://github.com/user-attachments/assets/6d9947ff-d257-4d56-b366-6b84a908f853" />

* **Interface `Pajangable`:** Berada di `package model` dan memuat kontrak method `pajang(String tujuan)` dan `cekKondisi()`. `HotWheels` dan `MiniGT` mengimplementasikannya dengan keyword `implements`.
* **Downcasting dengan `instanceof`:** Pada method `simulasiPajang()` di `KoleksiController.java`, program mengecek `if (d instanceof Pajangable)` terlebih dahulu. Cast ke `(Pajangable) d` baru dijalankan jika objek memang mengimplementasikan interface tersebut.
