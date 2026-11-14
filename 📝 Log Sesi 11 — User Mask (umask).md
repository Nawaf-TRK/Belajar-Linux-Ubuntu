# 📝 Log Sesi 11 — User Mask (`umask`)

> **Tanggal:** 13 November 2026  
> **Status:** ✅ Selesai  
> **Nilai:** 90/100

---

## 🎯 1. Materi yang Dipelajari

Pada sesi ini, materi yang dipelajari meliputi:

- **User Mask (`umask`):** Pengaturan yang menentukan permission default ketika membuat file atau direktori baru.
- **Perhitungan Permission:** Memahami cara menghitung hak akses akhir berdasarkan nilai `umask`.
- **Penerapan Permission:** Mempraktikkan perubahan `umask` dan mengamati pengaruhnya terhadap file dan direktori baru.

---

## 🧠 2. Konsep Kunci

### A. Permission Default

Sebelum menerapkan `umask`, Linux memiliki nilai dasar permission yang berbeda untuk file dan direktori.

| Jenis | Permission Dasar | Simbol |
|---|:---:|---|
| File | `666` | `-rw-rw-rw-` |
| Folder | `777` | `drwxrwxrwx` |

**Catatan:**
- File tidak memiliki permission eksekusi secara default.
- Direktori memiliki permission eksekusi karena diperlukan untuk mengakses atau menelusuri direktori.

### B. Pengertian `umask`

`umask` merupakan pengaturan yang menentukan permission mana yang tidak diberikan secara default ketika file atau direktori baru dibuat.

Semakin besar nilai `umask`, semakin banyak permission yang dibatasi.

### C. Rumus Menghitung Permission

```text
Permission Dasar - Umask = Permission Akhir
```

**Contoh 1: `umask 022`**

| Jenis | Perhitungan | Permission Akhir |
|---|---|---|
| File | `666` dengan mask `022` | `644` |
| Folder | `777` dengan mask `022` | `755` |

Hasil simbolik:

- File: `-rw-r--r--`
- Folder: `drwxr-xr-x`

**Contoh 2: `umask 077`**

| Jenis | Perhitungan | Permission Akhir |
|---|---|---|
| File | `666` dengan mask `077` | `600` |
| Folder | `777` dengan mask `077` | `700` |

Hasil simbolik:

- File: `-rw-------`
- Folder: `drwx------`

> **Penting:** Perhitungan `umask` menggunakan konsep pembatasan bit permission, bukan pengurangan aritmetika biasa untuk semua nilai. Rumus di atas merupakan cara ringkas untuk memahami contoh umum.

---

## 💻 3. Praktik di Terminal

Berikut tahapan praktik yang telah dilakukan:

### A. Memeriksa Nilai `umask`

```bash
umask
```

**Hasil:**

```text
0002
```

**Keterangan:** Menampilkan nilai `umask` yang sedang aktif pada shell.

### B. Membuat File Baru

```bash
touch file_umask.txt
```

**Hasil permission:**

```text
-rw-rw-r--
```

**Keterangan:** File baru mendapatkan permission `664` karena nilai `umask` aktif adalah `0002`.

### C. Membuat Folder Baru

```bash
mkdir folder_umask
```

**Hasil permission:**

```text
drwxrwxr-x
```

**Keterangan:** Folder baru mendapatkan permission `775`.

### D. Mengubah Nilai `umask`

```bash
umask 077
```

**Keterangan:** Mengubah nilai `umask` menjadi `077`, sehingga permission default file dan direktori baru menjadi lebih terbatas.

### E. Membuat File Setelah Mengubah `umask`

```bash
touch file_umask_baru.txt
```

**Hasil permission:**

```text
-rw-------
```

**Nilai oktal:** `600`

**Keterangan:** File baru hanya memiliki permission baca dan tulis untuk pemiliknya.

### Ringkasan Hasil Praktik

| Perintah | Hasil |
|---|---|
| `umask` | `0002` |
| `touch file_umask.txt` | `664` |
| `mkdir folder_umask` | `775` |
| `umask 077` | Mengubah mask menjadi `077` |
| `touch file_umask_baru.txt` | `600` |

---

## ⚠️ 4. Kesalahan dan Koreksi

### A. Kesalahan Pertama: Menganggap `umask` = `755`

**Kesalahan:** Mengira nilai `755` merupakan nilai `umask`.

**Koreksi:** `755` merupakan nilai permission, bukan nilai `umask`.

Contoh nilai `umask`:

```text
022
077
002
027
```

### B. Kesalahan Kedua: Salah Menghitung Permission Folder

**Kesalahan:** Menghasilkan permission `775` ketika menggunakan `umask 022`.

**Koreksi:**

```text
777 dengan umask 022 = 755
```

Hasil simbolik:

```text
drwxr-xr-x
```

**Hal yang perlu dipahami:** Permission dasar direktori adalah `777`, sehingga dengan `umask 022` hasilnya adalah `755`.

---

## 🔗 5. Hubungan dengan Bidang Lain

| Bidang | Hubungan dengan Materi |
|---|---|
| System Administration | Mengatur permission default untuk file dan direktori pengguna. |
| Cyber Security | Membatasi akses yang tidak diperlukan terhadap file dan direktori. |
| Linux File System | Memahami hubungan antara file, direktori, dan hak akses. |
| Server Management | Mengatur hak akses file yang dibuat oleh layanan server. |
| DevOps | Mengelola permission file konfigurasi dan hasil otomatisasi. |

---

## 📚 6. Kosakata Baru (Vocabulary)

| Istilah Bahasa Inggris | Arti Bahasa Indonesia |
|---|---|
| Mask | Topeng atau pembatas |
| Default | Bawaan atau dasar |
| Permission | Izin atau hak akses |
| Owner | Pemilik |
| Group | Kelompok pengguna |
| Others | Pengguna lainnya |
| Read | Membaca |
| Write | Menulis |
| Execute | Menjalankan atau mengeksekusi |
| Directory | Direktori atau folder |

---

## ✅ 7. Evaluasi dan Hal yang Perlu Dilatih

### A. Materi yang Sudah Dikuasai

- [x] Memahami pengertian `umask`.
- [x] Memahami permission dasar file (`666`).
- [x] Memahami permission dasar folder (`777`).
- [x] Memeriksa nilai `umask` menggunakan perintah `umask`.
- [x] Mengubah nilai `umask` menggunakan `umask 077`.
- [x] Mengamati perubahan permission file dan folder.

### B. Materi yang Perlu Diperkuat

- [ ] Menghitung permission akhir dengan lebih teliti.
- [ ] Membedakan nilai `umask` dan nilai permission.
- [ ] Membedakan permission file (`-`) dan direktori (`d`).
- [ ] Memahami hubungan nilai `umask` dengan hak akses owner, group, dan others.
- [ ] Berlatih menghitung permission menggunakan berbagai nilai `umask`.

---

## 📝 8. Kesimpulan Sesi

Pada sesi ke-11, saya mempelajari konsep User Mask (`umask`) pada sistem operasi Linux. Saya memahami bahwa `umask` berfungsi membatasi permission default ketika membuat file atau direktori baru.

Saya juga mempelajari bahwa permission dasar file adalah `666`, sedangkan permission dasar direktori adalah `777`. Melalui praktik terminal, saya berhasil memeriksa nilai `umask`, membuat file dan direktori, serta mengubah nilai `umask` menjadi `077`.

Selain itu, saya belajar memperbaiki kesalahan dalam membedakan nilai `umask` dengan permission serta menghitung permission akhir untuk direktori.

**Hasil akhir:** Materi dan praktik sesi ke-11 berhasil diselesaikan dengan nilai 90/100.

---

**📌 Catatan Tambahan:**  
Materi berikutnya dapat dikembangkan dengan mempelajari hubungan `umask` dengan `chmod`, perbedaan permission simbolik dan oktal, serta pengaturan permission untuk kebutuhan keamanan sistem Linux.
