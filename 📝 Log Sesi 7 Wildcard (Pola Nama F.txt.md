📝 Log Sesi 7: Wildcard (Pola Nama File)
Tanggal: 3 November 2026
Status: Selesai (Praktik: 100/100, Teori: 50/100)

🎯 Materi yang Dipelajari
Wildcard: Simbol khusus untuk mencocokkan nama file berdasarkan pola tertentu.

Tiga jenis wildcard: *, ?, dan [].

🧠 Konsep Kunci (Analogi "Kunci dan Lubang Kunci")
* (Bintang) = Kunci Master (Apa Saja Boleh)

Arti: Mewakili 0 karakter, 1 karakter, atau lebih (apa saja).

Contoh: ls *.txt -> Menampilkan semua file yang berakhiran .txt (misal: laporan1.txt, data2.txt).

Tidak cocok untuk: gambar.jpg (karena akhirannya bukan .txt).

? (Tanya) = Kunci dengan Satu Gigi Hilang (Tepat Satu Karakter)

Arti: Mewakili tepat satu karakter. Tidak boleh kurang, tidak boleh lebih.

Contoh: ls laporan?.txt -> Cocok dengan laporan1.txt, laporanA.txt.

Tidak cocok untuk: laporan10.txt (karena "10" dua karakter).

[] (Kurung Siku) = Kunci dengan Pilihan Gigi (Pilih Salah Satu)

Arti: Mencocokkan salah satu karakter yang ada di dalam kurung.

Contoh: ls laporan[12].txt -> Cocok dengan laporan1.txt dan laporan2.txt.

Tidak cocok untuk: laporanA.txt (karena 'A' tidak ada di dalam [12]).

💻 Praktik di Terminal
Membuat file uji: touch buku1.txt buku2.txt buku10.txt bukuA.txt.

ls buku?.txt -> Menampilkan buku1.txt, buku2.txt, bukuA.txt.

ls buku[12].txt -> Menampilkan buku1.txt, buku2.txt.

ls buku*.txt -> Menampilkan buku10.txt, buku1.txt, buku2.txt, bukuA.txt.

⚠️ Kesalahan & Koreksi
Kesalahan: Dalam kuis teori, hanya menulis simbol * tanpa perintah lengkap ls.

Koreksi: Perintah harus ditulis lengkap: ls *.txt, bukan hanya *.

Kesalahan: Membedakan arti * dan ?. * artinya "apa saja" (0 atau lebih), sedangkan ? artinya "tepat satu karakter".

📚 Kosakata Baru (Inggris)
Wildcard: Karakter pengganti.

Pattern: Pola.

Match: Cocok.

Asterisk: Tanda bintang (*).
