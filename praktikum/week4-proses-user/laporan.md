
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
1.Menampilkan daftar proses yang sedang berjalan dan statusnya.
2.Menggunakan perintah untuk membuat dan mengelola user.
3.Menghentikan atau mengontrol proses tertentu menggunakan PID.
4.Menjelaskan kaitan antara manajemen user dan keamanan sistem.
5.Menjelaskan konsep proses dan user dalam sistem operasi Linux.



---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Konsep Proses dalam Sistem Operasi
2.Manajemen Proses oleh Sistem Operasi
3.Monitoring Proses
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
<img width="1363" height="764" alt="ss github" src="https://github.com/user-attachments/assets/e417298c-a63f-448c-8ea9-260f1312d330" />


## Analisis
Dari hasil percobaan yang telah dilakukan, dapat dipahami bahwa setiap aktivitas di sistem operasi Linux dijalankan sebagai suatu proses yang memiliki identitas unik berupa PID (Process ID). Melalui perintah seperti ps, top, dan pstree, pengguna dapat memantau status, hierarki, serta penggunaan sumber daya dari setiap proses yang berjalan. Selain itu, dengan perintah sleep dan kill, pengguna juga dapat membuat, memantau, atau menghentikan proses secara langsung. Hasil ini menunjukkan bahwa Linux memiliki sistem multitasking yang efisien dan terstruktur, di mana setiap proses dapat dijalankan secara paralel tanpa saling mengganggu. Dengan adanya informasi seperti USER, %CPU, dan %MEM, pengguna dapat memahami bagaimana sistem mengalokasikan sumber daya untuk setiap proses.

Hasil percobaan ini berkaitan erat dengan teori dasar tentang fungsi kernel dan system call dalam arsitektur sistem operasi. Kernel berperan sebagai inti sistem yang bertugas untuk mengelola proses, memori, dan komunikasi antar-proses. Ketika pengguna menjalankan perintah melalui shell, kernel akan memanggil system call seperti fork() dan exec() untuk membuat dan mengeksekusi proses baru. Hal ini menunjukkan bahwa ada interaksi langsung antara user space (tempat perintah dijalankan) dengan kernel space (tempat kernel bekerja). Arsitektur Linux yang berlapis (layered architecture) memisahkan kedua ruang tersebut agar sistem tetap stabil dan aman. Dengan demikian, percobaan ini membuktikan bagaimana perintah sederhana di terminal sebenarnya merupakan bagian dari mekanisme yang lebih dalam antara shell, kernel, dan manajemen proses di sistem operasi.

---

## Kesimpulan
manajemen proses dan user di Linux merupakan bagian penting untuk menjaga stabilitas, keamanan, dan efisiensi sistem. Proses di Linux memiliki struktur hierarki, di mana setiap proses memiliki PID dan dapat memiliki proses anak, dan semuanya dikendalikan oleh proses induk utama seperti init atau system. User dan group digunakan untuk mengatur hak akses, sehingga hanya pengguna tertentu yang dapat melakukan operasi sensitif, sementara root memiliki hak istimewa untuk mengelola seluruh sistem. Melalui percobaan ini, pemahaman tentang perintah seperti ps, top, kill, killall, chmod, dan chown menjadi lebih jelas, sehingga teori tentang proses dan manajemen user dapat diterapkan secara praktis di sistem Linux.



---

## Quiz
1.Apa fungsi dari proses init atau systemd dalam sistem Linux? Jawaban:
Proses init atau systemd adalah proses pertama yang dijalankan saat Linux dinyalakan dan berfungsi sebagai induk dari semua proses lain di sistem. Ia bertugas memulai berbagai layanan penting seperti jaringan, login, dan pengelolaan sistem, serta memastikan semua proses berjalan dan dihentikan dengan benar. Jika ada proses yang kehilangan induknya, systemd akan “mengadopsinya” agar sistem tetap stabil. Selain itu, systemd juga mengatur proses saat komputer dimatikan atau direstart, sehingga sistem bisa beroperasi dan berhenti dengan aman serta teratur.

2.Apa perbedaan antara kill dan killall? Jawaban:
Perintah kill dan killall di Linux sama-sama digunakan untuk menghentikan proses, tetapi cara kerjanya berbeda. kill bekerja dengan menggunakan PID (Process ID), yaitu nomor unik yang diberikan sistem untuk setiap proses yang sedang berjalan. Jadi, agar bisa menggunakan kill, kamu harus tahu nomor PID proses yang ingin dihentikan, misalnya dengan perintah ps atau top. Contohnya, kill 1234 akan menghentikan proses dengan PID 1234 saja. Sementara itu, killall lebih praktis karena kamu hanya perlu menyebut nama programnya, bukan PID-nya. Misalnya, killall firefox akan menghentikan semua proses yang bernama firefox sekaligus. Dengan kata lain, kill cocok untuk menghentikan satu proses tertentu, sedangkan killall lebih efisien untuk menutup beberapa proses yang menjalankan program yang sama.

3.Mengapa user root memiliki hak istimewa di sistem Linux? Jawaban:
Karena root berperan sebagai administrator utama atau superuser, ia memiliki hak istimewa di sistem Linux untuk mengendalikan seluruh aspek sistem. Hak ini memungkinkan root melakukan tugas penting seperti menginstal atau menghapus program, mengubah konfigurasi sistem, mengelola user lain, serta mengatur izin dan kepemilikan file. Hak istimewa ini diperlukan agar sistem tetap aman, stabil, dan terkelola dengan baik, karena jika semua user biasa bisa melakukan operasi sensitif, risiko kesalahan atau penyalahgunaan akan sangat tinggi. Dengan demikian, root memiliki kontrol penuh untuk menjaga keamanan dan kelancaran sistem Linux secara menyeluruh.



---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
