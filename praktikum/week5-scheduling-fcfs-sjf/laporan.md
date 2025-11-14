  
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rifki Hidayat]  
- **NIM**   : [NIM Mahasiswa]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
1.Menghitung waiting time dan turnaround time untuk algoritma FCFS dan SJF.
2.Menyajikan hasil perhitungan dalam tabel yang rapi dan mudah dibaca.
3.Membandingkan performa FCFS dan SJF berdasarkan hasil analisis.
4.Menjelaskan kelebihan dan kekurangan masing-masing algoritma.
5.Menyimpulkan kapan algoritma FCFS atau SJF lebih sesuai digunakan.


---

## Dasar Teori
1.FCFS (First Come First Served)

Konsep dasar: Proses yang datang lebih dulu akan dieksekusi lebih dulu, seperti antrian di loket — prinsipnya first in, first out (FIFO).

Sederhana & mudah diimplementasikan, karena proses dijadwalkan berdasarkan urutan waktu kedatangan (arrival time).

Tidak adil untuk proses pendek, karena proses dengan burst time kecil bisa menunggu lama di belakang proses besar (convoy effect).

Tidak preemptive, artinya proses yang sedang berjalan tidak bisa dihentikan sampai selesai.

Kinerja baik untuk beban kerja seragam, tapi kurang efisien untuk campuran proses panjang dan pendek.

2.SJF (Shortest Job First)

Konsep dasar: Proses dengan waktu eksekusi (burst time) paling pendek dieksekusi lebih dulu untuk meminimalkan waktu tunggu rata-rata.

Tujuan utama: Menghasilkan rata-rata waiting time dan turnaround time paling kecil dibanding FCFS.

Dapat bersifat non-preemptive (sekali jalan sampai selesai) atau preemptive (dikenal sebagai Shortest Remaining Time First).

Butuh prediksi burst time, sehingga implementasinya sulit pada sistem nyata tanpa informasi tambahan.

Optimal secara teori, tetapi bisa menyebabkan starvation bagi proses panjang jika banyak proses pendek datang terus-menerus.

---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Gunakan tabel proses berikut sebagai contoh (boleh dimodifikasi dengan data baru):
   | Proses | Burst Time | Arrival Time |
   |:--:|:--:|:--:|
   | P1 | 6 | 0 |
   | P2 | 8 | 1 |
   | P3 | 7 | 2 |
   | P4 | 3 | 3 |
  
   2.Eksperimen 1 – FCFS (First Come First Served)

Urutkan proses berdasarkan Arrival Time. P1-P2-P3-P4

Hitung nilai berikut untuk tiap proses:

Waiting Time (WT) = waktu mulai eksekusi - Arrival Time
```bash
- P1 = 0 - 0 = 0

              - P2 = 6 - 1 = 5

              - P3 = 14 - 2 = 12

              - P4 = 21 - 3 = 18
```
Turnaround Time (TAT) = WT + Burst Time

P1: 0 + 6 = 6 → 6 − 0 = 6

P2: 6 + 8 = 14 → 14 − 1 = 13

P3: 14 + 7 = 21 → 21 − 2 = 19

P4: 21 + 3 = 24 → 24 − 3 = 21

Hitung rata-rata Waiting Time dan Turnaround Time.

rata rata TAT = (6 + 13 + 19 + 21) ÷ 4 = 59 ÷ 4 = 14.75

rata rata WT = (0 + 5 + 12 + 18) ÷ 4 = 35 ÷ 4 = 8.75

-Gantt Chart (FCFS):
```bash
| P1 | P2 | P3 | P4 |
 0    6    14   21   24
```
3.Eksperimen 2 – SJF (Shortest Job First)

Urutkan proses berdasarkan Burst Time terpendek (dengan memperhatikan waktu kedatangan).

Karena hanya P1 yang datang pertama, P1 dijalankan lebih dulu. Setelah itu urutannya berdasarkan burst time menjadi P4, P3, dan terakhir P2. Jadi urutan eksekusi proses adalah P1 → P4 → P3 → P2.

Lakukan perhitungan WT dan TAT seperti langkah sebelumnya.

P1: 0 + 6 = 6 → WT = 0 − 0 = 0, TAT = 6 − 0 = 6

P4: 6 + 3 = 9 → WT = 6 − 3 = 3, TAT = 9 − 3 = 6

P3: 9 + 7 = 16 → WT = 9 − 2 = 7, TAT = 16 − 2 = 14

P2: 16 + 8 = 24 → WT = 16 − 1 = 15, TAT = 24 − 1 = 23

Rata-rata WT = (0 + 3 + 7 + 15) ÷ 4 = 25 ÷ 4 = 6.25

Rata-rata TAT = (6 + 6 + 14 + 23) ÷ 4 = 49 ÷ 4 = 12.25

  4. **Eksperimen 3 – Visualisasi Spreadsheet (Opsional)**
     - Gunakan Excel/Google Sheets untuk membuat perhitungan otomatis:
     - Kolom: Arrival, Burst, Start, Waiting, Turnaround, Finish.
     - Gunakan formula dasar penjumlahan/subtraksi.
     - Screenshot hasil perhitungan dan simpan di:


---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)
<img width="1363" height="764" alt="ss github" src="https://github.com/user-attachments/assets/b8b8888c-400e-42f8-b670-3e907403dad0" />

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  
RATA RATA FCFS
rata-rata Waiting Time (WT) = 8,75
rata-rata Turnaround Time (TAT) = 14,75
RATA RATA FJS

rata-rata Waiting Time (WT) = 6,25
rata-rata Turnaround Time (TAT) = 12,25
SJF lebih unggul dari FCFS ketika:
Waktu eksekusi (burst time) setiap proses sudah diketahui atau dapat diperkirakan dengan baik. Karena SJF memilih proses dengan waktu terpendek, algoritma ini dapat meminimalkan waktu tunggu rata-rata dan meningkatkan efisiensi CPU.

Proses-proses yang datang memiliki variasi burst time yang besar. Dalam kondisi ini, SJF mampu menyelesaikan proses-proses kecil dengan cepat, sehingga total waktu tunggu keseluruhan menjadi jauh lebih kecil dibanding FCFS.

Lingkungan sistem bersifat batch (non-interaktif). Pada sistem batch, semua proses sudah diketahui di awal, sehingga mudah menentukan urutan yang paling efisien dengan SJF.

FCFS lebih unggul dari SJF ketika:
Waktu kedatangan proses tidak dapat diprediksi dan burst time sulit diketahui. FCFS tidak memerlukan perkiraan waktu eksekusi, jadi lebih sederhana dan mudah diterapkan dalam kondisi nyata.

Lingkungan sistem bersifat interaktif atau multitasking. Dalam sistem seperti ini, FCFS lebih adil karena setiap proses dilayani berdasarkan urutan datangnya, tanpa menunda proses panjang terlalu lama.

Tujuan utama adalah keadilan, bukan efisiensi. FCFS memastikan semua proses mendapat giliran secara berurutan, sehingga tidak terjadi starvation seperti pada SJF.


---

## Kesimpulan
1.FCFS
Proses dieksekusi berdasarkan urutan kedatangan, sehingga sederhana dan mudah diterapkan. Dapat menyebabkan waktu tunggu rata-rata tinggi jika proses panjang datang lebih dulu (convoy effect). Lebih menekankan keadilan waktu datang, bukan efisiensi waktu eksekusi.

2.SJF

Menjalankan proses dengan burst time paling pendek terlebih dahulu, sehingga menghasilkan rata-rata waktu tunggu minimum. Lebih efisien dibanding FCFS, tetapi sulit diterapkan karena memerlukan perkiraan waktu eksekusi yang akurat. Dapat menyebabkan starvation bagi proses panjang jika proses pendek terus datang.

---

## Quiz
1.Apa perbedaan utama antara FCFS dan SJF?
2.Mengapa SJF dapat menghasilkan rata-rata waktu tunggu minimum?
3.Apa kelemahan SJF jika diterapkan pada sistem interaktif?
JAWABAN
1.FCFS (First Come First Served) adalah algoritma penjadwalan CPU yang mengeksekusi proses berdasarkan urutan kedatangannya. Artinya, proses yang datang lebih dulu akan dieksekusi lebih dulu juga. Konsepnya seperti antrian di kasir — siapa datang dulu, dilayani dulu. Algoritma ini sangat sederhana dan mudah diterapkan, tetapi memiliki kelemahan yaitu convoy effect, di mana proses dengan waktu eksekusi (burst time) pendek harus menunggu proses panjang selesai terlebih dahulu. Akibatnya, waktu tunggu rata-rata bisa menjadi lama.
2.SJF (Shortest Job First) adalah algoritma yang memilih proses dengan waktu eksekusi paling pendek untuk dijalankan terlebih dahulu. Tujuannya agar waktu tunggu rata-rata menjadi sekecil mungkin. SJF dapat berbentuk non-preemptive (proses tidak dapat diganggu sampai selesai) atau preemptive, yang dikenal sebagai SRTF (Shortest Remaining Time First) — di mana proses baru dengan waktu lebih pendek dapat menghentikan proses yang sedang berjalan.
Algoritma SJF (Shortest Job First) mampu menghasilkan rata-rata waktu tunggu minimum karena selalu mengeksekusi proses dengan waktu eksekusi (burst time) paling pendek terlebih dahulu. Dengan cara ini, proses-proses singkat dapat segera selesai tanpa harus menunggu proses panjang, sehingga total waktu tunggu seluruh proses menjadi lebih efisien. Pendekatan ini membuat SJF dianggap sebagai algoritma penjadwalan yang paling optimal dalam meminimalkan waktu tunggu rata-rata.

3.Kelemahan SJF pada sistem interaktif adalah sulit menentukan burst time secara akurat, berisiko menyebabkan starvation pada proses panjang, dan membuat sistem kurang responsif terhadap permintaan pengguna. Karena itu, algoritma ini jarang digunakan pada sistem interaktif dan lebih cocok untuk sistem batch yang beban kerjanya sudah diketahui sebelumnya.


---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
