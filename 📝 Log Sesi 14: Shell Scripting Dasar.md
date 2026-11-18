## 📝 Log Sesi 14: Shell Scripting Dasar

**Tanggal:** 18 November 2026
**Status:** Selesai (Praktik: 90/100)

### 🎯 Materi yang Dipelajari
*   **Variabel**: Menyimpan nilai dalam skrip (`NAMA="Zhafran"`).
*   **Parameter**: Mengambil input saat menjalankan skrip (`$1`, `$2`).
*   **Konstruksi `if`**: Membuat keputusan berdasarkan kondisi.

### 🧠 Konsep Kunci
*   **Variabel**: `NAMA="Zhafran"` (tanpa spasi di sekitar `=`).
*   **Parameter**: `$1` (parameter pertama), `$2` (parameter kedua).
*   **`if`**: `if [ kondisi ]; then perintah; fi`.
    *   **Penting**: Ada spasi setelah `[` dan sebelum `]`.
    *   **`fi`**: Penutup blok `if` (wajib).

### 💻 Praktik di Terminal
*   Membuat `perkenalan.sh` -> Menampilkan "Halo, nama saya Zhafran".
*   Membuat `salam.sh` -> Menampilkan "Halo, Zhafran! Selamat datang di Linux" (dengan parameter).
*   Membuat `cek_nama.sh` -> Mengecek apakah parameter sama dengan "Zhafran".
    *   `./cek_nama.sh Zhafran` -> "Halo, Admin Zhafran!"
    *   `./cek_nama.sh yanto` -> "Halo, pengguna biasa."

### ⚠️ Kesalahan & Koreksi
*   **Kesalahan**: Nama file salah ketik (`cek_nama.sh` vs `cek_nama.sh`).
*   **Koreksi**: Perhatikan nama file dengan teliti.
*   **Kesalahan**: Lupa spasi pada `if ["$1" = "Zhafran" ]`.
*   **Koreksi**: Spasi wajib: `if [ "$1" = "Zhafran" ]; then`.

### 📚 Kosakata Baru (Inggris)
*   **Variable**: Variabel.
*   **Parameter**: Parameter.
*   **Condition**: Kondisi.
*   **If**: Jika.
*   **Else**: Selain itu.

### ✅ Yang Perlu Dilatih
*   Menulis spasi yang benar pada `if [ ... ]`.
*   Memastikan nama file sesuai saat menjalankan skrip.
