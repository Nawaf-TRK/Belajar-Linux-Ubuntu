# 🐧 Master Catatan Linux & Cyber Security: Permission, File Descriptor & Redirection

> 🗂️ **Daftar Isi Materi:**
> * [Bagian 1: Panduan Praktis & Keamanan `umask`](#-bagian-1-panduan-praktis--keamanan-umask-di-linux)
> * [Bagian 2: Konsep Dasar File Descriptor & I/O Redirection](#-bagian-2-konsep-dasar-file-descriptor--io-redirection)
> * [Bagian 3: Log Sesi 12 — File Descriptor & Redirection Lanjutan](#-bagian-3-log-sesi-12--file-descriptor--redirection-lanjutan)

---

# 🛡️ Bagian 1: Panduan Praktis & Keamanan `umask` di Linux

> 💡 **Inti Konsep:** `umask` (User File-Creation Mode Mask) adalah **garis pertahanan pertama** di Linux yang secara otomatis membatasi *permission* (izin akses) setiap kali file atau folder baru dibuat, sehingga tidak terbuka terlalu lebar secara *default*.

## 📊 Cheat Sheet Nilai `umask` Populer

| Nilai `umask` | Skenario Penggunaan | Efek pada File / Folder Baru |
| :--- | :--- | :--- |
| **`077`** | **Privasi Maksimal** (Lab kampus, server bersama, kunci SSH) | Hanya pemilik (*owner*) yang bisa membaca/mengubah. Orang lain diblokir total. |
| **`027`** | **Hardening Server** (Standar keamanan ketat) | Pemilik bebas akses, grup hanya bisa baca (*read*), publik tidak punya akses. |
| **`022`** | **Standar Web Server** (Default kebanyakan distro Linux) | Pemilik bebas akses, grup & publik hanya bisa baca (*read-only*). |
| **`002`** | **Kolaborasi Tim** (Proyek bersama dalam satu server) | Pemilik & anggota grup yang sama bisa membaca dan mengubah (*read/write*). |
| **`000`** | ⚠️ **Sangat Berbahaya** (Hindari di produksi) | File baru terbuka lebar (`666` / `777`), rentan dimodifikasi siapa saja. |

## 🐧 Kegunaan di Linux (Sehari-hari)

* **Keamanan File Pribadi (`077`):** Memastikan file sensitif baru (catatan pribadi, kunci SSH) tidak bisa diintip pengguna lain di komputer atau server yang dipakai bersama.
* **Kolaborasi Tim (`002`):** Memudahkan anggota dalam satu grup proyek untuk saling membaca dan mengedit file baru tanpa perlu mengatur ulang izin secara manual setiap saat.
* **Standar Server Web (`022`):** Menjaga agar file hasil *upload* atau buatan aplikasi web tetap bisa dibaca oleh server, tetapi tidak bisa sembarangan diubah oleh pengguna lain.
* **Mencegah Human Error:** Mencegah skrip atau file konfigurasi baru terbuat dengan izin terlalu terbuka (seperti `777`) yang berisiko menjadi celah keamanan.

## 🛡️ Penerapan di Cyber Security

1. **Pencegahan Privilege Escalation:** Dalam *pentesting* atau CTF, penyerang mencari file/folder berizin longgar (`777` atau `SUID`) untuk disisipi kode berbahaya demi mendapat akses `root`. `umask` yang salah (misalnya `000`) memicu celah ini.
2. **Analisis Forensik:** Saat menginvestigasi server yang diretas, *permission* `-rw-rw-rw-` (`666`) pada file atau `drwxrwxrwx` (`777`) pada folder menjadi indikator merah (*red flag*) titik masuk penyerang.
3. **Server Hardening:** Administrator sistem mengatur `umask` secara global di `/etc/profile` atau `/etc/bashrc` menjadi `027` atau `077` untuk memperketat keamanan seluruh sistem.
4. **Kepatuhan Standar (Compliance):** Membantu sistem memenuhi syarat kontrol akses ketat yang diwajibkan standar industri seperti **PCI-DSS** dan **ISO 27001**.

## 🎯 Studi Kasus: Skenario CTF (Linux Privilege Escalation)

* **Situasi:** Anda masuk ke server target sebagai pengguna web standar (`www-data`).
* **Temuan Celah:** Direktori `/var/www/html` memiliki *permission* `drwxrwxrwx` (`777`), yang artinya siapa pun di sistem bisa membuat file di dalamnya.
* **Eksploitasi:** Anda mengunggah skrip berbahaya (*web shell*) ke folder tersebut dan mengaksesnya lewat browser untuk mengambil alih kendali penuh server.
* **Mitigasi:** Jika administrator menerapkan `umask 022` sejak awal, folder tersebut tidak akan pernah berstatus `777` dan serangan ini gagal.

---
---

# 🧠 Bagian 2: Konsep Dasar File Descriptor & I/O Redirection

> 💡 **Inti Konsep:** Setiap program di Linux memiliki tiga saluran standar (**File Descriptor**) layaknya lampu indikator di dashboard mobil—untuk input, output normal, dan error. **Redirection** (`>`, `2>`, `2>&1`) adalah cara membelokkan aliran data tersebut dari layar terminal ke dalam file.

## 📊 Cheat Sheet File Descriptor & Operator Dasar

| FD / Simbol | Nama & Fungsi | Analogi Dashboard & Detektif | Contoh Perintah |
| :---: | :--- | :--- | :--- |
| **`0` (`stdin`)** | **Standard Input** — Jalur masuknya data (default: keyboard) | Lampu kuning (mengisi bensin) / Indera masuk | `cat < input.txt` |
| **`1` (`stdout`)** | **Standard Output** — Jalur keluarnya hasil normal (default: layar) | Lampu hijau (sistem berjalan normal) | `ls > output.txt` |
| **`2` (`stderr`)** | **Standard Error** — Jalur keluarnya pesan error (default: layar) | Lampu merah (ada masalah) | `find / 2> error.log` |
| **`2> /dev/null`** | **Buang Error** — Membuang pesan error ke "tempat sampah" Linux | Mematikan notifikasi error yang mengganggu | `nmap -sS target 2> /dev/null` |
| **`> file 2>&1`** | **Gabung Semua Output** — Menyatukan `stdout` dan `stderr` ke satu file | Menggabungkan catatan normal & error ke 1 buku | `./backup.sh > log.txt 2>&1` |

## 🎯 Kegunaan di Linux (Sehari-hari)

1. **Menyimpan Log Eksekusi:** Merekam seluruh hasil skrip panjang (baik hasil sukses maupun error) agar bisa dicek belakangan.
   * *Contoh:* `./backup.sh > log.txt 2>&1`
2. **Menyembunyikan Error Tidak Penting:** Membuang pesan *"Permission denied"* ke `/dev/null` saat mencari file di sistem agar tampilan layar tetap bersih.
   * *Contoh:* `find / -name "*.txt" 2> /dev/null`
3. **Memisahkan Output Normal dan Error:** Mengarahkan hasil normal dan catatan error ke dua file terpisah agar mudah dipilah.
   * *Contoh:* `ls -l /etc > output.txt 2> error.txt`

## 🛡️ Penerapan di Cyber Security

1. **Analisis Log Forensik:** Investigator menggabungkan seluruh output dan error ke satu file terpusat untuk mengaudit jejak serangan.
   * *Contoh:* `cat /var/log/auth.log > analisis.txt 2>&1`
2. **Menyembunyikan Jejak (Stealth):** Saat melakukan *penetration testing*, penyerang membuang pesan error ke `/dev/null` agar layar bersih dan aktivitas lebih senyap.
   * *Contoh:* `nmap -sS target 2> /
