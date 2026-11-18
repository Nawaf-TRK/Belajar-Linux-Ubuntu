# 📝 Log Sesi 6: Filter & Utilitas Linux

**Tanggal:** 1 November 2026  
**Status:** Selesai  
**Nilai Praktik:** 95/100

---

## 🎯 1. Materi yang Dipelajari

Pada sesi ini, saya mempelajari perintah filter dan utilitas dasar Linux yang digunakan untuk mengolah serta menampilkan data dari sebuah file.

Materi utama:

- **Filter:** Perintah untuk mengolah data, seperti menyaring, mengurutkan, dan menghitung.
- **Utilitas Dasar:** Mengenal perintah `sort`, `head`, `tail`, dan `wc`.
- **Pipeline Lanjutan:** Menggabungkan beberapa perintah menggunakan operator `|` (pipe).

---

## 🧠 2. Konsep Kunci

| Perintah | Fungsi |
|---|---|
| `sort` | Mengurutkan baris secara alfabetis (A–Z). |
| `head -n X` | Menampilkan X baris pertama dari file. |
| `tail -n X` | Menampilkan X baris terakhir dari file. |
| `wc -l` | Menghitung jumlah baris dalam file. |
| `\|` | Menghubungkan output perintah pertama menjadi input perintah berikutnya. |

### Contoh Kombinasi Perintah

```bash
sort buah.txt | head -n 2
