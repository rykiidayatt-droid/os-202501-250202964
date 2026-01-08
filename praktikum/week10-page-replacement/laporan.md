
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : Rifki Hidayat
- **NIM**   : 250202964 
- **Kelas** : 1IKRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
1.Mengimplementasikan algoritma page replacement FIFO dalam program.
2.Mengimplementasikan algoritma page replacement LRU dalam program.
3.Menjalankan simulasi page replacement dengan dataset tertentu.
4.Membandingkan performa FIFO dan LRU berdasarkan jumlah page fault.
5.Menyajikan hasil simulasi dalam laporan yang sistematis.
---

## Dasar Teori
1.Manajemen Memori Manajemen memori adalah bagian dari sistem operasi yang bertugas mengatur penggunaan memori utama agar dapat digunakan secara efisien oleh banyak proses. Salah satu masalah utama dalam manajemen memori adalah keterbatasan jumlah frame memori fisik dibandingkan dengan kebutuhan program.

2.Page Replacement Page replacement adalah mekanisme yang digunakan ketika terjadi page fault, yaitu saat halaman yang dibutuhkan tidak tersedia di memori utama. Sistem operasi harus mengganti salah satu halaman yang ada di memori dengan halaman baru berdasarkan algoritma tertentu.

3.Page Fault dan Page Hit Page fault terjadi ketika halaman yang diakses tidak ada di memori, sehingga sistem harus mengambilnya dari penyimpanan sekunder (disk). Page hit terjadi ketika halaman yang diakses sudah berada di memori, sehingga tidak diperlukan penggantian halaman.

4.Algoritma FIFO (First In First Out) Algoritma FIFO mengganti halaman yang pertama kali masuk ke memori tanpa memperhatikan apakah halaman tersebut masih sering digunakan atau tidak. FIFO sederhana dan mudah diimplementasikan, namun tidak selalu memberikan hasil yang efisien.

5.Algoritma LRU (Least Recently Used) Algoritma LRU mengganti halaman yang paling lama tidak digunakan. Algoritma ini lebih efisien dibanding FIFO karena mempertimbangkan pola penggunaan halaman, meskipun implementasinya lebih kompleks.



---

## Langkah Praktikum
1.Menyiapkan Lingkungan Praktikum Praktikum dilakukan menggunakan bahasa pemrograman Python. Pastikan Python telah terpasang dan dapat dijalankan melalui terminal atau command prompt.

2.Menentukan Reference String dan Jumlah Frame Reference string yang digunakan adalah: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2 Jumlah frame memori yang digunakan adalah 3 frame.

3.Membuat Program Simulasi Page Replacement Program dibuat untuk mensimulasikan dua algoritma page replacement, yaitu FIFO dan LRU. Program mencatat setiap kejadian page hit dan page fault, serta menghitung total page fault.

4.Menjalankan Program Program dijalankan melalui terminal menggunakan perintah:
```bash
python page_replacement.py

```
Hasil eksekusi berupa tampilan isi frame memori, status HIT atau FAULT, serta total page fault untuk masing-masing algoritma.

5.Menganalisis Hasil Simulasi Hasil simulasi FIFO dan LRU dibandingkan berdasarkan jumlah page fault. Analisis dilakukan untuk menentukan algoritma yang lebih efisien dalam penggunaan memori.

6.Menyimpan dan Mengelola Kode dengan Git Kode program dan hasil praktikum disimpan dalam repository Git, kemudian dilakukan commit dan push menggunakan perintah:
```bash
git add .
git commit -m "Minggu 10 - Page Replacement FIFO & LRU"
git push origin main.
```

---

## Kode / Perintah
def fifo_page_replacement(reference_string, frame_count): frames = [] page_faults = 0 index = 0
```bash
print("=== FIFO Page Replacement ===")
for page in reference_string:
    if page not in frames:
        page_faults += 1
        if len(frames) < frame_count:
            frames.append(page)
        else:
            frames[index] = page
            index = (index + 1) % frame_count
        status = "Fault"
    else:
        status = "Hit"

    print(f"Page: {page} -> Frames: {frames} ({status})")

return page_faults  
```
def lru_page_replacement(reference_string, frame_count): frames = [] recent = {} page_faults = 0 time = 0
```bash
print("\n=== LRU Page Replacement ===")
for page in reference_string:
    time += 1
    if page not in frames:
        page_faults += 1
        if len(frames) < frame_count:
            frames.append(page)
        else:
            lru_page = min(recent, key=recent.get)
            frames[frames.index(lru_page)] = page
            del recent[lru_page]
        status = "Fault"
    else:
        status = "Hit"

    recent[page] = time
    print(f"Page: {page} -> Frames: {frames} ({status})")

return page_faults
```
reference_string = [7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2] frame_count = 3

fifo_faults = fifo_page_replacement(reference_string, frame_count) lru_faults = lru_page_replacement(reference_string, frame_count)

print("\n=== HASIL AKHIR ===") print(f"Total Page Fault FIFO: {fifo_faults}") print(f"Total Page Fault LRU : {lru_faults}")
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
