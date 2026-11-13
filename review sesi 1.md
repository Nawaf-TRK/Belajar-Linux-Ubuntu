📝 Log Pendalaman Sesi 1: Permission & chmod Simbolik (Hard Mode)
Tanggal: 13 November 2026
Status: Selesai (Nilai: 100/100)

🎯 Materi yang Dipelajari (Pendalaman)
Membaca permission dengan teliti (posisi karakter).

Tiga operasi chmod simbolik: +, -, =.

Kombinasi perubahan permission.

chmod pada direktori (arti r, w, x yang berbeda).

Konsep a (all) dan go (group & others).

🧠 Konsep Kunci
1. Membaca Permission (10 Karakter)

Posisi 1: Tipe file (- file, d folder, l link).

Posisi 2-4: Hak User (rwx).

Posisi 5-7: Hak Group (r-x).

Posisi 8-10: Hak Others (r--).

2. Tiga Operasi chmod

+ (Tambah): Menambahkan hak yang belum ada. Contoh: chmod u+x (tambah eksekusi).

- (Cabut): Menghapus hak yang ada. Contoh: chmod g-w (cabut tulis).

= (Tetapkan): Menetapkan hak persis, menghapus hak lain yang tidak disebut. Contoh: chmod o=r (others hanya baca).

3. Perbedaan + dan =

chmod u+x -> menambahkan x ke hak yang sudah ada (misal rw- menjadi rwx).

chmod u=x -> menetapkan hanya x (misal rw- menjadi --x, menghapus r dan w).

4. Kombinasi Perubahan

Gunakan koma: chmod u+x,g-w,o=r file.txt.

a = all (user, group, others). Contoh: chmod a+x (tambah eksekusi ke semua).

go = group dan others. Contoh: chmod go-rw (cabut baca/tulis group & others).

5. chmod pada Direktori (Arti Berbeda)

r (read): Melihat daftar file (ls).

w (write): Membuat/menghapus file di dalam direktori.

x (execute): Masuk ke direktori (cd) dan mengakses file di dalamnya.

Penting: Tanpa x, Anda tidak bisa masuk ke direktori meskipun bisa melihat daftar file (r).

6. Menghapus File

Untuk menghapus file, yang menentukan adalah permission direktori, bukan permission file itu sendiri.

Jika direktori memiliki w untuk user, file bisa dihapus meskipun file tersebut -r--r--r--.

⚠️ Kesalahan & Koreksi (dari Hard Mode)
Kesalahan: Mengira a+x error. Koreksi: a = all, a+x valid.

Kesalahan: Mengira x pada direktori untuk "menjalankan file". Koreksi: x untuk masuk (cd) ke direktori.

Kesalahan: Mengira file -r--r--r-- tidak bisa dihapus. Koreksi: Tergantung permission direktori.

📚 Kosakata Baru (Inggris)
Execute: Menjalankan.

Write: Menulis/mengubah.

Read: Membaca.

All: Semua (user, group, others).

Directory: Direktori/folder.

✅ Yang Perlu Dilatih
Membiasakan menggunakan = untuk menetapkan permission secara persis.

Mengingat bahwa x pada direktori artinya "masuk", bukan "menjalankan".
