# 📝 Log Sesi 13: Filter Lanjutan (`cut`, `tr`, `paste`)

| Atribut | Detail |
| :--- | :--- |
| **Tanggal** | 16 November 2026 |
| **Status** | ✅ Selesai |
| **Skor Praktik** | **90 / 100** |

---

## 🎯 Materi yang Dipelajari
* **`cut`**: Memotong kolom atau karakter tertentu dari sebuah baris teks.
* **`tr`**: Mengganti (*translate*) atau menghapus karakter dari input standar.
* **`paste`**: Menggabungkan dua file atau lebih secara berdampingan (kolom demi kolom).

---

## 🧠 Konsep Kunci

### 1. `cut` (Memotong)
Digunakan untuk mengekstrak bagian tertentu dari setiap baris dalam file.
* `cut -d':' -f1 file.txt` — Mengambil *field* (kolom) pertama dengan pemisah (*delimiter*) titik dua (`:`).
* `cut -d':' -f2 file.txt` — Mengambil *field* kedua.
* `cut -c1-5 file.txt` — Mengambil karakter ke-1 sampai ke-5 dari setiap baris.

### 2. `tr` (*Translate / Delete*)
Digunakan untuk memodifikasi karakter secara *stream* (biasanya dikombinasikan dengan *pipe* `|`).
* `tr 'a-z' 'A-Z'` — Mengubah semua huruf kecil menjadi huruf kapital.
* `tr -d 'a'` — Menghapus semua karakter `'a'` dari input.

### 3. `paste` (Menggabungkan Berdampingan)
Digunakan untuk menyatukan baris-baris dari beberapa file secara horizontal (berdampingan).
* `paste file1.txt file2.txt` — Menggabungkan baris ke-1 `file1.txt` dengan baris ke-1 `file2.txt`, baris ke-2 dengan baris ke-2, dan seterusnya.
* **Catatan:** Perintah ini menggabungkan tampilan secara berdampingan, bukan menambahkan isi ke bagian bawah file (*append*).

---

## 💻 Praktik di Terminal

**1. Persiapan File (`data.txt`)**
```text
apel:merah
pisang:kuning
jeruk:oranye

# Mengambil nama buah (kolom 1) -> Output: apel, pisang, jeruk
cut -d':' -f1 data.txt

# Mengambil warna buah (kolom 2) -> Output: merah, kuning, oranye
cut -d':' -f2 data.txt

# Mengubah seluruh teks menjadi huruf kapital
cat data.txt | tr 'a-z' 'A-Z'

# Menghapus seluruh huruf 'a'
cat data.txt | tr -d 'a'

# Menggabungkan data.txt dan angka.txt secara berdampingan
paste data.txt angka.txt
