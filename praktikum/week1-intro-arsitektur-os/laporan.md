
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : Rizal prasetyo
- **NIM**   : 250202965  
- **Kelas** : 1ikra1

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.

Sistem Operasi dalam Arsitektur Komputer
Sistem operasi (Operating System / OS) adalah perangkat lunak utama yang bertindak sebagai jembatan antara perangkat keras (hardware) dan pengguna serta aplikasi. Dalam arsitektur komputer, OS berperan sebagai:
a. Resource Manager
OS mengelola seluruh sumber daya komputer—CPU, memori, storage, dan perangkat I/O. Tujuannya membagi sumber daya secara efisien, mencegah konflik, dan memastikan sistem berjalan stabil.
b. Program Controller / Supervisor
OS mengatur eksekusi program melalui penjadwalan proses, multitasking, manajemen thread, dan sinkronisasi.
c. Interface Provider
OS menyediakan antarmuka untuk aplikasi, biasanya berupa system call, sehingga aplikasi tidak perlu berinteraksi langsung dengan hardware.
d. Abstraction Layer
OS memberikan abstraksi seperti:
A.	Virtual memory
B.	Virtual file system 
C.	device adstraction
Sehingga programmer tidak perlu memahami detail perangkat keras fisik.
e. Security & Protection
OS mengatur izin akses, sandboxing, isolasi proses, dan mekanisme keamanan lainnya.
2. Komponen Utama Sistem Operasi
a. Kernel
Bagian inti OS yang berjalan dalam mode istimewa (kernel mode). Bertugas mengelola:
A.	proses dan thread
B.	memori
C.	interupsi
D.	sistem berkas
E.	komunikasi antar proses (IPC)
Kernel adalah “otak” dari sistem operasi.
b. System Call Interface (SCI)
Merupakan API yang memungkinkan program pengguna meminta layanan kernel.
Contoh system call: read, write, fork, exec, open
System call menjadi pintu masuk aplikasi untuk mengakses hardware secara aman.


3.Device Driver
Modul OS yang memungkinkan kernel berkomunikasi dengan perangkat keras.
Driver mengubah permintaan abstrak dari OS menjadi instruksi untuk perangkat.
A.	Contoh:
B.	driver GPUdriver keyboard
C.	driver jaringan (network card)
4. File System
Menyediakan cara terorganisir penyimpanan dan pengambilan data.
Contoh file system:
A.	NTFS (Windows)
B.	ext4 (Linux)
C.	APFS (macOS)
3. Perbandingan Model Arsitektur OS
 Monolithic Kernel
Ciri: Semua layanan OS (driver, file system, jaringan) berada di dalam kernel.
         Performanya sangat cepat karena tidak banyak overhead IPC.
Kelemahan: Sulit dipelihara.
                      Jika satu modul rusak, seluruh sistem bisa crash.
Contoh: 
A.	Linux 
B.	BSD (FreeBSD, OpenBSD, NetBSD)
Layered Architecture
Ciri: Sistem OS dibagi menjadi lapisan (layer).
         Setiap layer hanya berinteraksi dengan layer di atas/bawahnya.
         Lebih terstruktur, mudah dianalisis, dan lebih aman.
Kelemahan: Performansi sedikit lebih lambat dibanding monolith.
                      Mendesain batas layer dengan benar cukup sulit.
Contoh: 
A.	THE multiprogramming system (Dijkstra)
B.	Sebagian konsep Windows dan Linux juga menggunakan layering.
Microkernel Ciri:  
A.	Hanya fungsi sangat penting berada dalam kernel (scheduler, memory manager, IPC).
B.	Layanan lain seperti driver, file system, jaringan berjalan di user space sebagai server.
Kelebihan:
A.	Stabilitas tinggi — jika driver rusak, kernel tidak ikut crash.
B.	Lebih mudah dijelaskan dan lebih aman.
Kekurangan: Overhead IPC lebih banyak komunikasi antar proses.
Contoh:QNX,MINIX 3 ,L4 microkernel.


## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

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

---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:Tiga fungsi utama sistem operasi

Manajemen proses
OS mengatur proses yang sedang berjalan. Siapa dapat jatah CPU, siapa nunggu, siapa diberhentikan. Tanpa ini, program bakal berebut CPU seperti antrean sembako tanpa panitia.

Manajemen memori
OS menentukan bagian RAM mana dipakai program A, mana untuk program B, dan memastikan mereka tidak saling menginjak. Kalau ini gagal, hasilnya crash, hang, atau layar biru yang penuh kesabaran.

Manajemen perangkat I/O
OS jadi penerjemah antara software dan hardware. Keyboard, mouse, disk, printer, diatur lewat driver. Program tidak perlu “ngobrol langsung” ke hardware,.

(Sering juga ditambah: manajemen file dan keamanan, tapi tiga di atas adalah fondasinya.
2. [Pertanyaan 2]  
   **Jawaban:Perbedaan kernel mode dan user mode

Kernel Mode
Akses penuh ke hardware dan memori
Bisa menjalankan instruksi berbahaya (privileged instructions)
Dipakai oleh kernel dan driver
Kalau error → sistem bisa langsung crash

User Mode
Akses terbatas
Tidak bisa langsung mengakses hardware
Dipakai oleh aplikasi biasa (browser, editor, game)
Kalau error biasanya cuma aplikasinya yang mati, OS masih hidup

Intinya:
User mode itu "orang numpang", kernel mode itu “pemilik rumah”. orang numpang sok atur rumah, langsung diusir. 
3. [Pertanyaan 3]  
   **Jawaban:3. Contoh OS berdasarkan arsitektur kernel
a. Monolithic Kernel

Semua layanan utama (driver, file system, memory management) berjalan di kernel mode.

Contoh:

Linux

Unix klasik

MS-DOS (versi lama dan sederhana)

Kelebihan: cepat
Kekurangan: kalau satu bagian rusak, bisa meruntuhkan semuanya

b. Microkernel

Kernel dibuat sekecil mungkin. Layanan lain berjalan di user mode sebagai server terpisah.

Contoh:

MINIX

QNX

Mach (dasar macOS, meski macOS modern itu hybrid)

Kelebihan: lebih stabil dan aman
Kekurangan: komunikasi antar komponen lebih lambat

Kalau mau, aku bisa ringkaskan ini jadi jawaban versi ujian, versi makalah, atau versi dosen killer yang suka detail teknis.

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
