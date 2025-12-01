
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rifki HIdayat]  
- **NIM**   : [NIM Mahasiswa]  
- **Kelas** : [1IKRA]

---

## Tujuan
Setelah menyelesaikan tugas ini, mahasiswa mampu:

1.Mengidentifikasi empat kondisi penyebab deadlock (mutual exclusion, hold and wait, no preemption, circular wait).
2.Menjelaskan mekanisme sinkronisasi menggunakan semaphore atau monitor.
3.Menganalisis dan memberikan solusi untuk kasus deadlock.
4.Berkolaborasi dalam tim untuk menyusun laporan analisis.
5.Menyajikan hasil studi kasus secara sistematis.


---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

Concurrency adalah kondisi ketika beberapa proses atau thread dapat berjalan secara bersamaan, baik secara paralel pada banyak inti prosesor maupun secara bergantian sangat cepat pada satu inti CPU. Tujuan utama concurrency adalah meningkatkan pemanfaatan CPU, efisiensi, dan responsivitas sistem. Namun, concurrency juga menimbulkan sejumlah permasalahan seperti race condition, inkonsistensi data, kelaparan (starvation), dan deadlock, sehingga mekanisme sinkronisasi seperti lock, semaphore, dan monitor sangat diperlukan untuk menjaga konsistensi dan koordinasi antarproses. Salah satu masalah penting yang muncul dari concurrency adalah deadlock, yaitu keadaan ketika dua atau lebih proses saling menunggu resource yang tidak pernah dilepaskan sehingga tidak ada proses yang dapat melanjutkan eksekusi. Deadlock hanya dapat terjadi jika empat kondisi terpenuhi secara bersamaan, yaitu mutual exclusion (resource hanya dapat digunakan satu proses pada satu waktu), hold and wait (proses memegang satu resource sambil menunggu resource lain), no preemption (resource tidak bisa diambil paksa), dan circular wait (terjadi rantai proses yang saling menunggu secara melingkar). Penyebab deadlock umumnya berasal dari pengelolaan resource bersama yang tidak tepat, penguncian yang tidak konsisten, dan koordinasi proses yang salah. Dalam sistem operasi, penanganan deadlock dapat dilakukan melalui pencegahan (preventing), penghindaran (avoidance), pendeteksian (detection), dan pemulihan (recovery). Dengan demikian, concurrency dan deadlock memiliki hubungan erat karena eksekusi bersamaan tanpa pengaturan yang baik dapat memicu kondisi saling menunggu yang berujung pada deadlock.
---

## Langkah Praktikum
1.Persiapan Tim

-Bentuk kelompok beranggotakan 3–4 orang.
-Tentukan ketua dan pembagian tugas (analisis, implementasi, dokumentasi).
2.Eksperimen 1 – Simulasi Dining Philosophers (Deadlock Version)

-Implementasikan versi sederhana dari masalah Dining Philosophers tanpa mekanisme pencegahan deadlock.
-Contoh pseudocode:
```bash
while true:
  think()
  pick_left_fork()
  pick_right_fork()
  eat()
  put_left_fork()
  put_right_fork()
```
-Jalankan simulasi atau analisis alur (boleh menggunakan pseudocode atau diagram alur).
-Identifikasi kapan dan mengapa deadlock terjadi.
3.Eksperimen 2 – Versi Fixed (Menggunakan Semaphore / Monitor)

-Modifikasi pseudocode agar deadlock tidak terjadi, misalnya:
-Menggunakan semaphore (mutex) untuk mengontrol akses.
-Membatasi jumlah filosof yang dapat makan bersamaan (max 4).
-Mengatur urutan pengambilan garpu (misal, filosof terakhir mengambil secara terbalik).
-Analisis hasil modifikasi dan buktikan bahwa deadlock telah dihindari.
4.Eksperimen 3 – Analisis Deadlock

-Jelaskan empat kondisi deadlock dari versi pertama dan bagaimana kondisi tersebut dipecahkan pada versi fixed.

-Sajikan hasil analisis dalam tabel seperti contoh berikut:

     | Kondisi Deadlock | Terjadi di Versi Deadlock | Solusi di Versi Fixed |
     |------------------|---------------------------|------------------------|
     | Mutual Exclusion | Ya (satu garpu hanya satu proses) | Gunakan semaphore untuk kontrol akses |
     | Hold and Wait | Ya | Hindari proses menahan lebih dari satu sumber daya |
     | No Preemption | Ya | Tidak ada mekanisme pelepasan paksa |
     | Circular Wait | Ya | Ubah urutan pengambilan sumber daya |
5.Eksperimen 4 – Dokumentasi

-Simpan semua diagram, screenshot simulasi, dan hasil diskusi di:
```bash
praktikum/week7-concurrency-deadlock/screenshots/
```
-Tuliskan laporan kelompok di laporan.md (format IMRaD singkat: Pendahuluan, Metode, Hasil, Analisis, Diskusi).
6.Commit & Push
```bash
git add .
git commit -m "Minggu 7 - Sinkronisasi Proses & Deadlock"
git push origin main
```


---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

<img width="909" height="514" alt="wek7" src="https://github.com/user-attachments/assets/6f67945d-bb0e-493b-a6fa-86b85cd8ba03" />

<img width="910" height="499" alt="ke27" src="https://github.com/user-attachments/assets/46872e66-0075-4055-b517-c75a937670f4" />

Eksperimen 1
---
versi phyton
```bash
import threading
import time

forks = [threading.Lock() for _ in range(5)]

def philosopher(i):
    left = i
    right = (i + 1) % 5

    while True:
        print(f"Philosopher {i} is thinking")
        time.sleep(1)

        forks[left].acquire()
        print(f"Philosopher {i} picked left fork {left}")

        forks[right].acquire()
        print(f"Philosopher {i} picked right fork {right}")

        print(f"Philosopher {i} is eating")
        time.sleep(1)

        forks[left].release()
        forks[right].release()

# jalankan semua thread
for i in range(5):
    threading.Thread(target=philosopher, args=(i,)).start()
```
output
```bash
Philosopher 0 is thinking
Philosopher 1 is thinking
Philosopher 2 is thinking
Philosopher 3 is thinking
Philosopher 4 is thinking
Philosopher 1 picked left fork 1
Philosopher 2 picked left fork 2
Philosopher 3 picked left fork 3
Philosopher 4 picked left fork 4
Philosopher 0 picked left fork 0
```
Kapan Deadlock Terjadi?

Deadlock bisa terjadi tepat saat semua filsuf secara simultan mengambil garpu kiri mereka dan kemudian berusaha mengambil garpu kanan, yang sudah dipegang oleh tetangganya. Karena setiap filsuf menunggu garpu kanan yang tidak pernah dilepaskan, sistem macet dan tidak ada yang bisa melanjutkan untuk makan.

Mengapa Deadlock Terjadi?

Deadlock terjadi karena setiap filsuf bersikeras mengambil dan menahan satu resource (garpu kiri) sambil menunggu resource lain (garpu kanan) yang dipegang oleh filsuf lain. Tidak ada mekanisme pencegahan seperti pelepasan resource secara paksa, pengambilan resource dalam urutan tertentu, atau timeout yang bisa memutus siklus tunggu ini.
---
Eksperimen 2
```bash
import threading
import time
import random

NUM_PHILOSOPHERS = 5
forks = [threading.Lock() for _ in range(NUM_PHILOSOPHERS)]

# Semaphore: maksimal 4 filosof boleh makan bersamaan
max_eaters = threading.Semaphore(4)

def philosopher(i):
    left = i
    right = (i + 1) % NUM_PHILOSOPHERS

    while True:
        print(f"Philosopher {i} is thinking")
        time.sleep(random.uniform(0.2, 0.6))

        # Meminta izin makan
        max_eaters.acquire()

        # ================================
        #  KHUSUS FILOSOF TERAKHIR (4)
        #  Ambil garpu terbalik: right → left
        # ================================
        if i == NUM_PHILOSOPHERS - 1:
            print(f"Philosopher {i} picked right fork {right}")
            forks[right].acquire()

            print(f"Philosopher {i} picked left fork {left}")
            forks[left].acquire()

        # ================================
        #  Filosof lain normal: left → right
        # ================================
        else:
            print(f"Philosopher {i} picked left fork {left}")
            forks[left].acquire()

            print(f"Philosopher {i} picked right fork {right}")
            forks[right].acquire()

        print(f"Philosopher {i} is eating")
        time.sleep(random.uniform(0.2, 0.5))

        # Letakkan garpu
        forks[left].release()
        forks[right].release()
        print(f"Philosopher {i} released both forks")

        # Izinkan filosof lain makan
        max_eaters.release()
        time.sleep(random.uniform(0.2, 0.6))


threads = []
for i in range(NUM_PHILOSOPHERS):
    t = threading.Thread(target=philosopher, args=(i,))
    t.start()
    threads.append(t)

```
output
```bash
Philosopher 0 is thinking
Philosopher 1 is thinking
Philosopher 2 is thinking
Philosopher 3 is thinking
Philosopher 4 is thinking

Philosopher 1 picked left fork 1
Philosopher 1 picked right fork 2
Philosopher 1 is eating
Philosopher 3 picked left fork 3
Philosopher 3 picked right fork 4
Philosopher 3 is eating
Philosopher 0 picked left fork 0
Philosopher 0 picked right fork 1   ← menunggu jika fork 1 dipakai
Philosopher 1 released both forks
Philosopher 0 picked right fork 1
Philosopher 0 is eating

Philosopher 4 picked right fork 0
Philosopher 4 picked left fork 4
Philosopher 4 is eating

Philosopher 2 picked left fork 2
Philosopher 2 picked right fork 3
Philosopher 2 is eating

Philosopher 3 released both forks
Philosopher 4 released both forks
Philosopher 0 released both forks
Philosopher 2 released both forks

Philosopher 1 is thinking
Philosopher 3 is thinking
Philosopher 0 is thinking
Philosopher 4 is thinking
Philosopher 2 is thinking
---






```
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
