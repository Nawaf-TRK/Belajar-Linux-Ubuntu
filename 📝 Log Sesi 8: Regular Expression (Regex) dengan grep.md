📝 Log Sesi 8: Regular Expression (Regex) dengan grep
Tanggal: 6 November 2026
Status: Selesai (Praktik: 100/100, Teori: 100/100)

🎯 Materi yang Dipelajari
Regular Expression (Regex): Pola pencarian teks yang lebih canggih.

Simbol dasar: ^, $, ., [].

🧠 Konsep Kunci
^ (Awal Baris): Mencari pola yang ada di awal baris.

Contoh: grep "^root" /etc/passwd -> Mencari baris yang diawali "root".

$ (Akhir Baris): Mencari pola yang ada di akhir baris.

Contoh: grep "bash$" /etc/passwd -> Mencari baris yang diakhiri "bash".

. (Titik): Mewakili satu karakter apa saja.

Contoh: grep "r.t" file.txt -> Cocok dengan "rot", "rat", "rut".

[] (Kurung Siku): Mencocokkan salah satu karakter di dalamnya.

Contoh: grep "r[oa]t" file.txt -> Hanya cocok dengan "rot" atau "rat".

💻 Praktik di Terminal
Membuat file regex.txt dengan 4 baris yang mengandung kata "root".

grep "^root" regex.txt -> Menampilkan baris 1 dan 3 (awal baris).

grep "root$" regex.txt -> Menampilkan baris 2 dan 4 (akhir baris).

grep "r.t" regex.txt -> Kosong (tidak ada yang cocok).

grep "r[oa]t" regex.txt -> Kosong (tidak ada yang cocok).

⚠️ Kesalahan & Koreksi
Tidak ada kesalahan konsep yang berarti. Hanya sempat ragu pada soal yang hasilnya kosong, tetapi itu wajar.
