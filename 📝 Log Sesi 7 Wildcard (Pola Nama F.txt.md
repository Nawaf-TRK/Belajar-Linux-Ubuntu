# 📝 Log Sesi 7: Wildcard (Pola Nama File)

| Atribut | Detail |
| :--- | :--- |
| **Tanggal** | 3 November 2026 |
| **Status** | ✅ Selesai |
| **Skor** | Praktik: **100/100** \| Teori: **50/100** |

---

## 🎯 Materi yang Dipelajari
* **Wildcard:** Simbol khusus di shell untuk mencocokkan atau memfilter nama file berdasarkan pola tertentu (*globbing*).
* **Tiga Simbol Utama:** `*` (*asterisk*), `?` (*question mark*), dan `[]` (*square brackets*).

---

## 🧠 Konsep Kunci (Analogi "Kunci dan Lubang Kunci")

### 1. `*` (Bintang) — Kunci Master (Apa Saja Boleh)
* **Arti:** Mewakili **0 karakter, 1 karakter, atau lebih** (karakter apa saja).
* **Contoh:** `ls *.txt`
  * ✅ **Cocok:** `laporan1.txt`, `data2.txt`, `.txt`
  * ❌ **Tidak Cocok:** `gambar.jpg` (akhiran bukan `.txt`)

### 2. `?` (Tanya) — Kunci dengan Satu Gigi Hilang (Tepat Satu Karakter)
* **Arti:** Mewakili **tepat satu karakter** bebas. Tidak boleh kosong dan tidak boleh lebih dari satu.
* **Contoh:** `ls laporan?.txt`
  * ✅ **Cocok:** `laporan1.txt`, `laporanA.txt`
  * ❌ **Tidak Cocok:** `laporan10.txt` (`"10"` terdiri dari dua karakter)

### 3. `[]` (Kurung Siku) — Kunci dengan Pilihan Gigi (Pilih Salah Satu)
* **Arti:** Mencocokkan **satu karakter** yang dipilih dari daftar karakter di dalam kurung.
* **Contoh:** `ls laporan[12].txt`
  * ✅ **Cocok:** `laporan1.txt`, `laporan2.txt`
  * ❌ **Tidak Cocok:** `laporanA.txt` (huruf `'A'` tidak terdaftar di dalam `[12]`)

---

## 💻 Praktik di Terminal

**1. Membuat File Uji**
```bash
touch buku1.txt buku2.txt buku10.txt bukuA.txt
# Mencocokkan tepat 1 karakter setelah "buku" -> Output: buku1.txt, buku2.txt, bukuA.txt
ls buku?.txt

# Mencocokkan angka '1' atau '2' setelah "buku" -> Output: buku1.txt, buku2.txt
ls buku[12].txt

# Mencocokkan 0 atau lebih karakter setelah "buku" -> Output: buku10.txt, buku1.txt, buku2.txt, bukuA.txt
ls buku*.txt
