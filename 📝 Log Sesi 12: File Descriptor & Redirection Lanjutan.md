# 📝 Log Sesi 12: File Descriptor & Redirection Lanjutan

| 📅 Tanggal | 📌 Status | 🏆 Skor Praktik |
| :--- | :--- | :--- |
| 14 November 2026 | ✅ Selesai | **100 / 100** |

> 🎯 **Target Materi:** Memahami tiga saluran standar proses Linux (**File Descriptor**) serta teknik **Redirection Lanjutan** untuk menggabungkan maupun mengalihkan arus output dan error (`2>&1`, `1>&2`, dan `&>`).

---

## 🧠 Konsep Kunci

### 1. Tiga File Descriptor Standar

Setiap proses yang berjalan di Linux memiliki tiga saluran komunikasi dasar:

| FD | Nama | Fungsi | Default |
| :---: | :--- | :--- | :--- |
| **`0`** | `stdin` | Input (masukan data) | Keyboard |
| **`1`** | `stdout` | Output normal (hasil sukses) | Layar Terminal |
| **`2`** | `stderr` | Output error (pesan kesalahan) | Layar Terminal |

### 2. Redirection Lanjutan

* **`2>&1`** — Menggabungkan *error* (`2`) ke tujuan yang sama dengan *output normal* (`1`).
  * **Contoh:** `ls filetidakada.txt > log.txt 2>&1` *(Output dan error masuk ke `log.txt`)*
* **`1>&2`** — Mengalihkan *output normal* (`1`) ke saluran *error* (`2`).
  * **Contoh:** `echo "Pesan" 1>&2` *(Output normal diperlakukan sebagai pesan error)*
* **`&>`** — Cara penulisan singkat (shorthand) dari `> file 2>&1`.
  * **Contoh:** `ls filetidakada.txt &> log.txt` *(Output dan error masuk ke `log.txt`)*

> 💡 **Perbedaan `2>&1` vs `&>`:** Fungsinya **sama persis**, hanya berbeda cara penulisan. `2>&1` ditulis di belakang setelah file tujuan (`> file 2>&1`), sedangkan `&>` ditulis langsung di depan file tujuan (`&> file`).

---

## 💻 Praktik di Terminal

```bash
# 1. Menyimpan output & error ke log.txt menggunakan 2>&1
ls filetidakada.txt > log.txt 2>&1

# 2. Menyimpan output & error ke log2.txt menggunakan bentuk singkat &>
ls filetidakada2.txt &> log2.txt

# 3. Mengarahkan output teks biasa agar dianggap sebagai pesan error (stderr)
echo "Ini pesan error palsu" 1>&2

# 4. Menyimpan HANYA pesan error ke dalam file terpisah
ls filetidakada.txt 2> error_only.txt
