📝 Log Sesi 6: Filter & Utilitas Linux (+ Ujian Komprehensif)
Tanggal: 1 November 2026
Status: Selesai (Nilai Praktik: 95/100)

🎯 Materi yang Dipelajari
Filter: Perintah yang mengolah data (menyaring, mengurutkan, menghitung).

Utilitas Dasar: sort, head, tail, wc.

Pipeline Lanjutan: Menggabungkan filter dengan |.

🧠 Konsep Kunci
sort: Mengurutkan baris secara alfabetis (A-Z).

head -n X: Menampilkan X baris pertama dari sebuah file.

tail -n X: Menampilkan X baris terakhir dari sebuah file.

wc -l: Menghitung jumlah baris (lines) dari input.

Kombinasi: sort file.txt | head -n 2 akan mengurutkan file, lalu mengambil 2 baris teratas.

💻 Praktik di Terminal
Membuat file buah.txt berisi 5 nama buah.

sort buah.txt -> Mengurutkan buah (Anggur, Apel, Jeruk, Mangga, Pisang).

head -n 2 buah.txt -> Menampilkan Mangga, Apel (2 baris pertama file asli).

tail -n 2 buah.txt -> Menampilkan Pisang, Anggur (2 baris terakhir file asli).

wc -l buah.txt -> Menampilkan angka 5 (jumlah baris).

sort buah.txt | head -n 2 -> Menampilkan Anggur, Apel (hasil sort, diambil 2 teratas).

📝 Log Ujian Komprehensif & Remedial (Sesi 1-6)
Status: Lulus Remedial

📊 Hasil Ujian
Ujian Awal (25 Soal): 64/100 (Belum Lulus).

Remedial (4 Fokus): 100/100 (Lulus).

⚠️ Celah yang Ditemukan & Diperbaiki
cat vs more: cat menampilkan seluruh isi sekaligus (layar bisa penuh dan baris awal tidak terlihat). more menampilkan per layar.

> vs >>: > menimpa isi file. >> menambahkan teks baru di akhir tanpa menghapus isi lama.

Pipeline (|): Bukan sekadar "menjalankan perintah ganda", tetapi menyambung output perintah pertama menjadi input perintah kedua.

2>: Tanda khusus untuk mengalihkan pesan error ke file. Tidak bisa diganti dengan >>.

✅ Kesimpulan
Fondasi Sesi 1-6 sudah kokoh. Siap melanjutkan ke Sesi 7 (Wildcard & Regular Expression).

📚 Kosakata Baru (Inggris)
Filter: Penyaring.

Sort: Mengurutkan.

Head: Bagian atas/awal.

Tail: Bagian ekor/akhir.

Count: Menghitung.

