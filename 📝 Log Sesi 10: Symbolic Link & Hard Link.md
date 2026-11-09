📝 Log Sesi 10: Symbolic Link & Hard Link
Tanggal: 9 November 2026
Status: Selesai (Praktik: 100/100)

🎯 Materi yang Dipelajari
Link: "Jalan pintas" atau nama kedua untuk sebuah file.

Dua jenis link: Hard Link (ln) dan Symbolic Link (ln -s).

🧠 Konsep Kunci
Hard Link (ln):

Membuat "nama kedua" untuk file yang sama.

Data file tetap ada meskipun salah satu nama dihapus.

Tidak bisa dibuat untuk folder (direktori).

Jumlah link bertambah (terlihat di kolom kedua ls -l).

Symbolic Link (ln -s):

Membuat file baru yang "menunjuk" ke file asli (seperti catatan tempel).

Jika file asli dihapus, link akan rusak (broken link).

Bisa dibuat untuk file dan folder.

Ditandai dengan huruf l di awal permission dan tanda panah (->) pada ls -l.

💻 Praktik di Terminal
Membuat file asli: echo "Ini adalah file asli" > asli.txt.

Membuat hard link: ln asli.txt hardlink.txt -> Jumlah link menjadi 2.

Membuat symbolic link: ln -s asli.txt symlink.txt -> symlink.txt -> asli.txt.

Menghapus file asli: rm asli.txt.

Mengakses link:

cat hardlink.txt -> Berhasil (data masih ada).

cat symlink.txt -> Gagal (No such file or directory, karena link rusak).

⚠️ Kesalahan & Koreksi
Tidak ada kesalahan. Pemahaman konsep hard link dan symbolic link sudah sangat baik.

📚 Kosakata Baru (Inggris)
Link: Tautan.

Hard Link: Tautan keras (nama kedua).

Symbolic Link: Tautan simbolik (jalan pintas).

Broken Link: Tautan rusak.

Pointer: Penunjuk.

✅ Yang Perlu Dilatih
Mengingat bahwa hard link tidak bisa untuk folder, sedangkan symbolic link bisa.
