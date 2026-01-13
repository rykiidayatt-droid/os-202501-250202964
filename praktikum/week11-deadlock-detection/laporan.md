
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : Rifki Hidayat  
- **NIM**   : 250202964
- **Kelas** : 1IKRA

---

## Tujuan
Setelah menyelesaikan tugas ini, mahasiswa mampu:

1.Membuat program sederhana untuk mendeteksi deadlock.
2.Menjalankan simulasi deteksi deadlock dengan dataset uji.
3.Menyajikan hasil analisis deadlock dalam bentuk tabel.
4.Memberikan interpretasi hasil uji secara logis dan sistematis.
5.Menyusun laporan praktikum sesuai format yang ditentukan.
---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Deadlock adalah kondisi ketika dua atau lebih proses saling menunggu resource yang sedang digunakan proses lain, sehingga tidak ada proses yang dapat melanjutkan eksekusi.

2.Empat Kondisi Deadlock. Deadlock terjadi apabila mutual exclusion, hold and wait, no preemption, dan circular wait terpenuhi secara bersamaan.

3.Deteksi deadlock dilakukan dengan menganalisis alokasi dan permintaan resource untuk menentukan apakah terdapat proses yang tidak dapat diselesaikan, yang menandakan terjadinya deadlock.
---

## Langkah Praktikum
1.Menyiapkan Dataset Gunakan dataset sederhana yang berisi: Daftar proses Resource Allocation Resource Request / Need
2.Implementasi Algoritma Deteksi Deadlock Program minimal harus: Membaca data proses dan resource. Menentukan apakah sistem berada dalam kondisi deadlock. Menampilkan proses mana saja yang terlibat deadlock.
3.Eksekusi & Validasi Jalankan program dengan dataset uji. Validasi hasil deteksi dengan analisis manual/logis. Simpan hasil eksekusi dalam bentuk screenshot.
4.Analisis Hasil Sajikan hasil deteksi dalam tabel (proses deadlock / tidak). Jelaskan mengapa deadlock terjadi atau tidak terjadi. Kaitkan hasil dengan teori deadlock (empat kondisi).
5.Commit & Push git add . git commit -m "Minggu 11 - Deadlock Detection" git push origin main
---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
praktikum/week11-deadlock-detection/
├─ code/
│  ├─ deadlock_detection.*
│  └─ dataset_deadlock.csv
├─ screenshots/
│  └─ hasil_deteksi.png
└─ laporan.md
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:**  
2. [Pertanyaan 2]  
   **Jawaban:**  
3. [Pertanyaan 3]  
   **Jawaban:**  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
