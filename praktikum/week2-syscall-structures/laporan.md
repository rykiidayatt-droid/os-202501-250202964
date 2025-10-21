
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rifki Hidayat]  
- **NIM**   : [250202964]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
jawab:System Call sebagai Antarmuka antara User dan Kernel System call merupakan mekanisme yang memungkinkan program di user space berinteraksi dengan kernel untuk mengakses sumber daya sistem seperti file, memori, dan perangkat keras. Tanpa system call, program user tidak dapat melakukan operasi penting seperti membaca file atau membuat proses baru.

Kernel bertanggung jawab untuk mengatur alokasi sumber daya seperti CPU, memori, dan perangkat I/O. Ketika program user membutuhkan sumber daya tersebut, kernel akan menangani permintaan melalui system call agar proses tetap terkontrol dan tidak saling mengganggu.

Alur Eksekusi System Call Saat sebuah program memanggil system call (misalnya read()), CPU akan beralih dari user mode ke kernel mode. Kernel kemudian mengeksekusi fungsi yang diminta, mengembalikan hasilnya ke program, dan berpindah kembali ke user mode setelah selesai.

Keamanan dan Isolasi Proses Salah satu tujuan utama penggunaan system call adalah menjaga keamanan sistem. Dengan membatasi akses langsung ke kernel, sistem operasi dapat mencegah kesalahan program atau serangan berbahaya yang dapat merusak data atau mengganggu proses lain.



---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
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
  jawab:Linux menggunakan system calls yang lebih sederhana dan langsung. Sistem operasi Linux memiliki antarmuka sistem pemrograman yang lebih terbuka dan fleksibel, dengan banyak alat debugging dan pemantauan yang dapat digunakan untuk melacak eksekusi system call (misalnya dengan menggunakan alat seperti strace)
  Windows menggunakan API yang lebih kompleks dan memiliki pendekatan yang lebih berbasis objek, seperti Windows API (WinAPI) untuk sistem panggilan. Sebagian besar interaksi dengan kernel dilakukan melalui WinAPI, yang mengabstraksi sistem panggilan lebih jauh dibandingkan Linux.

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
jawab:1.Transisi Aman antara User Mode dan Kernel 
2.Pentingnya System Calls dan Exception Handling

---

## Quizz
-Panggilan sistem (system call) penting untuk keamanan OS karena berfungsi sebagai penghalang antara program dan sumber daya sistem. OS mengontrol akses program ke sumber daya (seperti berkas, memori, dan perangkat keras) melalui panggilan sistem, yang memastikan bahwa program hanya dapat melakukan operasi yang diizinkan dan mencegah program lain mengakses atau mengganggu sumber daya sistem. Panggilan sistem juga menegakkan pemisahan hak istimewa (privilege separation), sehingga program pengguna tidak dapat mengakses memori milik proses lain atau merusak data kernel.
-beberapa cara yang digunakan oleh OS untuk memastikan transisi tersebut berjalan aman:

1. Penggunaan Instruksi yang Dilindungi (Privileged Instructions)
	•	Instruksi Tertentu: Beberapa instruksi hanya dapat dijalankan di dalam kernel mode untuk mencegah program di user mode mengakses atau memodifikasi bagian-bagian kritis dari sistem. Contohnya adalah instruksi untuk mengakses perangkat keras atau mengubah pengaturan memori.
	•	Ketika program dalam user mode mencoba untuk mengeksekusi instruksi yang dilindungi, CPU akan memicu exception atau trap dan memindahkan kontrol ke kernel untuk menangani situasi tersebut.

2. Virtualisasi Memori
	•	OS menggunakan virtual memory untuk memisahkan ruang memori antara user dan kernel. Setiap proses di user mode memiliki ruang memori virtualnya sendiri yang terisolasi dari proses lain dan kernel.
	•	Ketika terjadi transisi ke kernel mode (misalnya saat melakukan system call), OS akan memastikan bahwa akses memori hanya terbatas pada ruang memori yang sah dan tidak memungkinkan proses di user mode untuk mengakses data atau kode kernel secara langsung.
-Contoh sistem call yang sering digunakan:
read: Membaca data dari file descriptor (misalnya, dari keyboard atau file ke dalam buffer memori).
write: Menulis data dari buffer memori ke file descriptor (misalnya, ke console atau file).
open: Membuka sebuah file dan mengembalikan file descriptor yang dapat digunakan untuk operasi selanjutnya.
close: Menutup file descriptor yang telah dibuka.
fork: Membuat salinan dari proses yang sedang berjalan untuk membuat proses baru (child process).
exit: Mengakhiri eksekusi proses saat ini dan membebaskan sumber daya yang digunakan.
exec: Mengganti gambar program yang sedang berjalan dengan program baru.
waitpid: Menunggu proses anak selesai dan mendapatkan statusnya.

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?
  jawab:membuat kodingan
- Bagaimana cara Anda mengatasinya?
  jawab:terus berusaha belajar  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
