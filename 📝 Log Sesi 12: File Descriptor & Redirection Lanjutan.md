📝 Log Sesi 12: File Descriptor & Redirection Lanjutan
Tanggal: 14 November 2026
Status: Selesai (Praktik: 100/100)

🎯 Materi yang Dipelajari
File Descriptor: Tiga saluran standar pada setiap proses Linux.

Redirection Lanjutan: Menggabungkan output dan error dengan 2>&1, 1>&2, dan &>.

🧠 Konsep Kunci
1. Tiga File Descriptor Standar

FD	Nama	Fungsi	Default
0	stdin	Input (masukan)	Keyboard
1	stdout	Output normal	Layar
2	stderr	Output error	Layar
2. Redirection Lanjutan

2>&1: Menggabungkan error (2) ke tempat yang sama dengan output (1).

Contoh: ls filetidakada.txt > log.txt 2>&1 -> Output dan error masuk ke log.txt.

1>&2: Mengalihkan output (1) ke tempat yang sama dengan error (2).

Contoh: echo "Pesan" 1>&2 -> Output dianggap sebagai error.

&>: Cara singkat untuk > file 2>&1.

Contoh: ls filetidakada.txt &> log.txt -> Output dan error masuk ke log.txt.

3. Perbedaan 2>&1 dan &>

2>&1 ditulis setelah > (contoh: > file 2>&1).

&> adalah singkatan (contoh: &> file). Fungsinya sama, hanya penulisan berbeda.

💻 Praktik di Terminal
ls filetidakada.txt > log.txt 2>&1 -> Error tersimpan di log.txt.

ls filetidakada2.txt &> log2.txt -> Error tersimpan di log2.txt.

echo "Ini pesan error palsu" 1>&2 -> Pesan muncul di layar (dianggap error).

ls filetidakada.txt 2> error_only.txt -> Hanya error yang tersimpan.

🛡️ Kegunaan di Cyber Security
Analisis Log Forensik: Menggabungkan semua output (normal + error) ke satu file untuk dianalisis.

Menyembunyikan Jejak (Stealth): Mengalihkan error ke /dev/null (2> /dev/null) agar tidak ketahuan.

Command Injection: Menyisipkan perintah seperti ; cat /etc/passwd > /tmp/out.txt 2>&1 untuk mencuri data.

CTF: Menyimpan output ke file untuk dianalisis lebih lanjut.

🔗 Bidang Lain yang Nyambung
System Administration (SysAdmin): Mengelola log server, backup, otomatisasi.

DevOps: Pipeline CI/CD menggunakan redirection untuk mengumpulkan log build.

Data Analysis: Memproses data besar di terminal.

Forensics: Menganalisis log sistem dan jejak serangan.

Software Development: Debugging dengan mengalihkan error ke file.

📚 Kosakata Baru (Inggris)
Descriptor: Penanda.

Standard Input (stdin): Masukan standar.

Standard Output (stdout): Keluaran standar.

Standard Error (stderr): Keluaran error.

Redirect: Mengalihkan.

Log: Catatan.

✅ Yang Perlu Dilatih
Membedakan kapan menggunakan 2>&1 dan &>.

Memahami bahwa 1>&2 mengalihkan output ke error (bukan sebaliknya).
