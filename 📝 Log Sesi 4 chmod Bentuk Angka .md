📝 Log Sesi 4: chmod Bentuk Angka (Okthal)
Tanggal: 31 Oktober 2026
Status: Selesai

🎯 Materi yang Dipelajari
Konversi permission huruf (rwx) ke angka (oktal).

Aturan nilai: r = 4, w = 2, x = 1, - = 0.

Cara menjumlahkan nilai untuk setiap kelompok (Pemilik, Group, Others).

Perintah chmod menggunakan angka.

🧠 Konsep Kunci
Angka 7 = 4+2+1 = rwx (baca, ubah, jalan).

Angka 6 = 4+2+0 = rw- (baca, ubah).

Angka 5 = 4+0+1 = r-x (baca, jalan).

Angka 4 = 4+0+0 = r-- (baca saja).

Angka 0 = 0+0+0 = --- (tidak ada hak).

Urutan Angka: [Pemilik] [Group] [Others].

Contoh: 755 berarti Pemilik=rwx, Group=r-x, Others=r-x.

💻 Praktik di Terminal
Membuat file uji: mkdir sesi4, cd sesi4, touch uji.sh.

Latihan mengubah permission:

chmod 640 uji.sh -> Hasil: -rw-r--- (Cocok)

chmod 755 uji.sh -> Hasil: -rwxr-xr-x (Cocok)

chmod 600 uji.sh -> Hasil: -rw--- (Cocok)

⚠️ Kesalahan & Koreksi
Kesalahan: Tidak teliti saat mengetik angka (mengetik 775 padahal maksudnya 755).

Koreksi: Selalu baca ulang angka sebelum menekan Enter. Ingat, angka tengah adalah untuk Group. Jika 7 (rwx), group bisa mengubah file. Jika 5 (r-x), group hanya bisa membaca dan menjalankan.

📚 Kosakata Baru (Inggris)
Value: Nilai.

Sum: Jumlah.

Octal: Bilangan basis 8 (sistem angka yang digunakan di chmod).

✅ Yang Perlu Dilatih
Ketelitian dalam mengetik angka (cek ulang sebelum Enter).

Terjemahkan huruf ke angka dengan menjumlahkan, bukan menebak.
