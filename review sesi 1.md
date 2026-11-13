# 📝 Log Pendalaman Sesi 1: Permission & chmod Simbolik (Hard Mode)

<p align="left">
  <img src="https://shields.io" alt="Tanggal">
  <img src="https://shields.io" alt="Status">
  <img src="https://shields.io" alt="Nilai">
</p>

---

## 🎯 Materi yang Dipelajari
* **Ketelitian Struktur:** Membaca *permission* secara detail berdasarkan posisi karakter tepatnya.
* **Operasi Simbolik:** Menguasai tiga operasi dasar `chmod` simbolik: `+`, `-`, dan `=`.
* **Fleksibilitas Perintah:** Menggabungkan kombinasi perubahan *permission* dalam satu baris perintah.
* **Konstruksi Target:** Memahami konsep target `a` (*all*) serta gabungan `go` (*group & others*).
* **Hak Akses Direktori:** Memahami perbedaan mendasar arti `r`, `w`, dan `x` pada sebuah folder/direktori.

---

## 🧠 Konsep Kunci

### 1. Membaca Permission (10 Karakter)
Struktur *permission* Linux dipecah menjadi 4 bagian utama berdasarkan urutan karakternya:

| Posisi | Komponen | Deskripsi / Contoh |
| :---: | :--- | :--- |
| **1** | Tipe File | `-` (file biasa), `d` (direktori), `l` (link/shortcut) |
| **2 - 4** | Hak User (`u`) | Hak akses untuk pemilik file (contoh: `rwx`) |
| **5 - 7** | Hak Group (`g`) | Hak akses untuk kelompok pengguna (contoh: `r-x`) |
| **8 - 10** | Hak Others (`o`) | Hak akses untuk pengguna lain di luar pemilik/group (contoh: `r--`) |

### 2. Tiga Operasi Dasar `chmod`
* **`+` (Tambah):** Menambahkan hak spesifik yang belum dimiliki tanpa mengubah hak lainnya.  
  * 💻 *Contoh:* `chmod u+x` *(Menambahkan hak eksekusi untuk user)*
* **`-` (Cabut):** Menghapus hak spesifik yang sedang aktif.  
  * 💻 *Contoh:* `chmod g-w` *(Mencabut hak tulis untuk group)*
* **`=` (Tetapkan):** Mengatur ulang hak secara absolut. Menghapus semua hak lama dan menggantinya hanya dengan yang disebutkan.  
  * 💻 *Contoh:* `chmod o=r` *(Others hanya bisa membaca, hak lain otomatis hilang)*

### 3. Perbandingan Krusial: `+` vs `=`

| Perintah | Kondisi Awal | Hasil Akhir | Mekanisme |
| :--- | :---: | :---: | :--- |
| `chmod u+x` | `rw-` | `rwx` | Menambahkan `x` ke dalam daftar yang sudah ada. |
| `chmod u=x` | `rw-` | `--x` | Menimpa total. `r` dan `w` dihapus, tersisa hanya `x`. |

### 4. Kombinasi Perubahan Lanjutan
* **Multi-Perintah (Koma):** Mengubah banyak target sekaligus dipisahkan dengan koma tanpa spasi.  
  * 💻 *Contoh:* `chmod u+x,g-w,o=r file.txt`
* **Target `a` (All):** Mewakili *user*, *group*, dan *others*.  
  * 💻 *Contoh:* `chmod a+x` *(Memberikan akses eksekusi ke semua orang)*
* **Target `go` (Group & Others):** Menggabungkan target grup dan pihak luar sekaligus.  
  * 💻 *Contoh:* `chmod go-rw` *(Mencabut hak baca dan tulis dari group & others)*

### 5. Karakteristik `chmod` pada Direktori
Hak akses pada sebuah folder memiliki fungsi yang sangat berbeda dibanding pada file biasa:
* **`r` (Read):** Diperlukan untuk melihat daftar file di dalam folder menggunakan perintah `ls`.
* **`w` (Write):** Diperlukan untuk membuat, memodifikasi, atau menghapus file di dalam folder tersebut.
* **`x` (Execute):** Diperlukan untuk memasuki folder menggunakan perintah `cd` serta mengakses isi file di dalamnya.

> 💡 **Penting:** Tanpa hak `x` (execute), Anda tetap **tidak akan bisa masuk** ke dalam direktori meskipun Anda memiliki hak `r` (read) untuk melihat daftarnya.

### 6. Aturan Penghapusan File
> ⚠️ **Aturan Emas:** Hak untuk **menghapus file** ditentukan oleh *permission* pada **direktori tempat file itu berada**, bukan *permission* pada file itu sendiri.
> 
> Jika sebuah direktori memberikan hak `w` (write) kepada user Anda, Anda bisa menghapus file di dalamnya kapan saja, bahkan jika file tersebut dikunci total dengan aturan `-r--r--r--`.

---

## ⚠️ Kesalahan & Koreksi (Hard Mode Review)

| ❌ Kesalahan Asumsi |  Koreksi / Fakta yang Benar |
| :--- | :--- |
| Mengira perintah `a+x` akan menghasilkan error. | **Salah.** Sintaks `a` adalah valid dan merupakan singkatan dari *all*. |
| Mengira hak `x` pada direktori dipakai untuk menjalankan file. | **Salah.** Hak `x` pada direktori berfungsi agar user bisa melakukan `cd` (masuk) ke direktori tersebut. |
| Mengira file dengan status `-r--r--r--` mutlak tidak bisa dihapus. | **Salah.** File tersebut tetap bisa dihapus jika direktori induknya memiliki izin `w` untuk user terkait. |

---

## 📚 Kosakata Baru

* **Execute:** Menjalankan (file biner/script) atau memasuki (untuk direktori).
* **Write:** Menulis, mengedit isi file, atau memodifikasi struktur folder.
* **Read:** Membaca isi teks file atau melihat daftar isi folder.
* **All:** Seluruh kategori pengguna (`u`, `g`, dan `o`).
* **Directory:** Istilah teknis untuk folder penyimpanan file di Linux.

---

## ✅ Rencana Latihan Selanjutnya
- [ ] Membiasakan diri menggunakan operator `=` untuk mengatur ulang konfigurasi hak akses secara presisi dan bersih.
- [ ] Menanamkan pemahaman kuat bahwa tanda `x` pada folder berarti akses "masuk", bukan menjalankan aplikasi.

