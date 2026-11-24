# 📝 Log Sesi 8: Regular Expression (Regex) dengan `grep`

| Atribut | Detail |
| :--- | :--- |
| **Tanggal** | 6 November 2026 |
| **Status** | ✅ Selesai |
| **Skor** | Praktik: **100/100** \| Teori: **100/100** |

---

## 🎯 Materi yang Dipelajari
* **Regular Expression (Regex):** Pola pencarian teks yang lebih fleksibel dan spesifik dibandingkan pencarian teks biasa.
* **Metakarakter Dasar:** Penggunaan simbol `^`, `$`, `.`, dan `[]` bersama perintah `grep`.

---

## 🧠 Konsep Kunci

| Simbol | Nama / Fungsi | Penjelasan | Contoh Perintah | Hasil Pencocokan |
| :--- | :--- | :--- | :--- | :--- |
| **`^`** | Awal Baris (*Caret*) | Mencari pola yang berada tepat di awal baris. | `grep "^root" /etc/passwd` | Baris yang diawali kata `"root"` |
| **`$`** | Akhir Baris (*Dollar*) | Mencari pola yang berada tepat di akhir baris. | `grep "bash$" /etc/passwd` | Baris yang diakhiri kata `"bash"` |
| **`.`** | Karakter Tunggal (*Dot*) | Mewakili **satu** karakter apa saja (huruf, angka, atau simbol). | `grep "r.t" file.txt` | `"rot"`, `"rat"`, `"rut"`, `"r1t"` |
| **`[]`** | Kumpulan Karakter (*Brackets*) | Mencocokkan salah satu karakter yang ada di dalam kurung. | `grep "r[oa]t" file.txt` | Hanya `"rot"` atau `"rat"` |

---

## 💻 Praktik di Terminal

**1. Persiapan File (`regex.txt`)**
Membuat file `regex.txt` berisi 4 baris pengujian yang memuat kata `"root"` di posisi berbeda (awal dan akhir baris).

**2. Eksekusi Perintah**
```bash
# Mencari kata "root" di awal baris -> Output: Baris 1 dan 3
grep "^root" regex.txt

# Mencari kata "root" di akhir baris -> Output: Baris 2 dan 4
grep "root$" regex.txt

# Mencari pola 'r' + 1 karakter bebas + 't' -> Output: Kosong (tidak ada yang cocok)
grep "r.t" regex.txt

# Mencari kata "rot" atau "rat" -> Output: Kosong (tidak ada yang cocok)
grep "r[oa]t" regex.txt
