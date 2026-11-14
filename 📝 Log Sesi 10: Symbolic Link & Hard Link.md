# 📝 Log Sesi 10 — Symbolic Link & Hard Link

> **Tanggal:** 9 November 2026  
> **Status:** ✅ Selesai  
> **Nilai Praktik:** 100/100

---

## 🎯 1. Materi yang Dipelajari

Pada sesi ini, materi yang dipelajari meliputi:

- **Link:** Nama tambahan atau jalur alternatif untuk mengakses suatu file.
- **Hard Link (`ln`):** Membuat nama tambahan yang mengacu pada data file yang sama.
- **Symbolic Link (`ln -s`):** Membuat tautan yang menunjuk ke lokasi file atau direktori lain.

---

## 🧠 2. Konsep Kunci

### A. Hard Link (`ln`)

Hard Link merupakan nama tambahan yang mengacu pada inode yang sama dengan file aslinya.

**Karakteristik:**

- Membuat nama kedua untuk data file yang sama.
- Data tetap dapat diakses meskipun salah satu nama file dihapus.
- Tidak dapat dibuat untuk direktori menggunakan penggunaan normal.
- Jumlah hard link dapat dilihat pada kolom kedua hasil perintah `ls -l`.
- File asli dan hard link memiliki inode yang sama.

**Contoh perintah:**

```bash
ln asli.txt hardlink.txt
```

**Keterangan:** Membuat hard link bernama `hardlink.txt` yang mengacu pada data yang sama dengan `asli.txt`.

### B. Symbolic Link (`ln -s`)

Symbolic Link merupakan tautan yang menunjuk ke lokasi atau nama file maupun direktori lain. Konsepnya mirip dengan shortcut pada sistem operasi lain.

**Karakteristik:**

- Membuat tautan yang menunjuk ke file atau direktori tujuan.
- Jika file asli dihapus atau lokasi tujuan tidak ditemukan, symbolic link dapat menjadi *broken link*.
- Dapat dibuat untuk file maupun direktori.
- Ditandai dengan huruf `l` pada bagian awal permission.
- Ditampilkan dengan tanda panah (`->`) pada hasil `ls -l`.
- Memiliki inode tersendiri, berbeda dari file tujuan.

**Contoh perintah:**

```bash
ln -s asli.txt symlink.txt
```

**Keterangan:** Membuat symbolic link bernama `symlink.txt` yang menunjuk ke `asli.txt`.

### C. Perbedaan Hard Link dan Symbolic Link

| Aspek | Hard Link | Symbolic Link |
|---|---|---|
| Perintah | `ln` | `ln -s` |
| Inode | Sama dengan file asli | Berbeda |
| Untuk direktori | Tidak (penggunaan normal) | Bisa |
| Jika file asli dihapus | Data tetap dapat diakses melalui hard link | Dapat menjadi broken link |
| Bentuk pada `ls -l` | Menampilkan jumlah hard link | Menampilkan `l` dan tanda `->` |
| Hubungan dengan file asli | Mengacu pada inode yang sama | Menunjuk ke nama atau lokasi tujuan |

---

## 💻 3. Praktik di Terminal

Berikut tahapan praktik yang telah dilakukan:

### A. Membuat File Asli

```bash
echo "Ini adalah file asli" > asli.txt
```

**Keterangan:** Membuat file `asli.txt` dengan isi teks "Ini adalah file asli".

### B. Membuat Hard Link

```bash
ln asli.txt hardlink.txt
```

**Keterangan:** Membuat nama tambahan `hardlink.txt` yang mengacu pada inode yang sama dengan `asli.txt`.

**Hasil:** Jumlah hard link menjadi 2.

### C. Membuat Symbolic Link

```bash
ln -s asli.txt symlink.txt
```

**Keterangan:** Membuat symbolic link bernama `symlink.txt` yang menunjuk ke `asli.txt`.

**Hasil:** Hubungan link ditampilkan sebagai berikut:

```text
symlink.txt -> asli.txt
```

### D. Menghapus File Asli

```bash
rm asli.txt
```

**Keterangan:** Menghapus nama file asli `asli.txt`.

### E. Menguji Kedua Link

**1. Mengakses Hard Link**

```bash
cat hardlink.txt
```

**Hasil:** ✅ Berhasil.

Data masih dapat dibaca karena `hardlink.txt` tetap mengacu pada inode yang menyimpan data file tersebut.

**2. Mengakses Symbolic Link**

```bash
cat symlink.txt
```

**Hasil:** ❌ Gagal.

Muncul pesan `No such file or directory` karena symbolic link masih menunjuk ke `asli.txt`, sedangkan nama file tersebut sudah dihapus.

---

## ⚠️ 4. Kesalahan dan Koreksi

**Status:** Tidak ditemukan kesalahan selama praktik.

Pemahaman mengenai perbedaan Hard Link dan Symbolic Link sudah baik.

Hal penting yang berhasil dipahami:

- Hard link tetap dapat mengakses data meskipun nama file asli dihapus.
- Symbolic link dapat rusak jika tujuan yang ditunjuk tidak ditemukan.
- Kedua jenis link memiliki cara kerja dan karakteristik inode yang berbeda.

---

## 🔗 5. Hubungan dengan Bidang Lain

| Bidang | Hubungan dengan Materi |
|---|---|
| System Administration | Mengelola file dan direktori menggunakan beberapa jalur akses. |
| Linux File System | Memahami inode dan hubungan antara nama file dengan data. |
| Software Development | Menggunakan symbolic link untuk menghubungkan direktori proyek. |
| DevOps | Mengelola konfigurasi dan direktori aplikasi melalui symbolic link. |
| Cyber Security | Memahami hubungan file dan tautan ketika melakukan pemeriksaan sistem. |

---

## 📚 6. Kosakata Baru (Vocabulary)

| Istilah Bahasa Inggris | Arti Bahasa Indonesia |
|---|---|
| Link | Tautan |
| Hard Link | Tautan keras |
| Symbolic Link | Tautan simbolik |
| Broken Link | Tautan rusak |
| Pointer | Penunjuk |
| Inode | Struktur data yang menyimpan informasi tentang file pada sistem file Linux |
| Directory | Direktori atau folder |
| Target | Tujuan yang ditunjuk oleh tautan |

---

## ✅ 7. Evaluasi dan Hal yang Perlu Dilatih

### A. Materi yang Sudah Dikuasai

- [x] Memahami pengertian Link.
- [x] Memahami fungsi Hard Link.
- [x] Memahami fungsi Symbolic Link.
- [x] Membuat Hard Link menggunakan `ln`.
- [x] Membuat Symbolic Link menggunakan `ln -s`.
- [x] Memahami kondisi Broken Link.
- [x] Menguji perbedaan kedua link setelah file asli dihapus.

### B. Materi yang Perlu Diperkuat

- [ ] Mengingat bahwa Hard Link tidak dapat dibuat untuk direktori dalam penggunaan normal.
- [ ] Memahami bahwa Symbolic Link dapat digunakan untuk file dan direktori.
- [ ] Memahami hubungan inode dengan Hard Link dan Symbolic Link.
- [ ] Berlatih mengidentifikasi kedua jenis link melalui perintah `ls -l`.

---

## 📝 8. Kesimpulan Sesi

Pada sesi ke-10, saya mempelajari dua jenis tautan pada Linux, yaitu Hard Link dan Symbolic Link. Saya memahami bahwa Hard Link merupakan nama tambahan yang mengacu pada inode yang sama dengan file asli, sedangkan Symbolic Link merupakan tautan yang menunjuk ke lokasi file atau direktori lain.

Melalui praktik terminal, saya berhasil membuat kedua jenis link dan menguji perilakunya setelah file asli dihapus. Hasil praktik menunjukkan bahwa Hard Link tetap dapat digunakan untuk mengakses data, sedangkan Symbolic Link dapat menjadi Broken Link apabila tujuan yang ditunjuk sudah tidak ditemukan.

**Hasil akhir:** Materi dan praktik sesi ke-10 berhasil diselesaikan dengan nilai praktik 100/100.

---

**📌 Catatan Tambahan:**  
Materi selanjutnya dapat dikembangkan dengan mempelajari inode lebih mendalam, memeriksa nomor inode menggunakan `ls -i`, serta memahami hubungan antara file, direktori, dan sistem file Linux.
