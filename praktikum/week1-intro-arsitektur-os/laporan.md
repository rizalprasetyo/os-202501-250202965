
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : Rizal prasetyo
- **NIM**   : 250202965  
- **Kelas** : 1ikra

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
1.langkah-langkah yang dilakukan oleh sistem operasi:

1.Bootstrapping

2.Inisialisasi

3.*Manajemen proses

4.Manajemen Memori

5.Manajemen File

6.Manajemen Input/Output

7.Penjadwalan

8.Keamanan

9.*Pengelolaan Sumber Daya

10.Pengelolaan Jaringan

11.Sistem operasi menjalankan berbagai perintah, antara lain:

12.Proses: Membuat, menjalankan, menghentikan, dan mengelola proses.

13.Manajemen File: Membuat, menghapus, mengganti nama, dan mengelola file dan direktori.

14.Manajemen Memori: Mengalokasikan, dealokasikan, dan mengelola memori.

15.Input/Output: Mengelola input/output dari perangkat keras, seperti keyboard, mouse, dan printer.

16.Jaringan: Mengelola komunikasi jaringan, termasuk mengirim dan menerima data.

17.Keamanan: Melakukan autentikasi, autorisasi, dan enkripsi untuk melindungi sistem.

18.Penjadwalan: Menentukan prioritas dan waktu eksekusi proses.

19.Pengelolaan Sumber Daya: Mengelola sumber daya sistem, seperti CPU, memori, dan perangkat keras. 3.Sistem operasi membuat dan mengelola berbagai jenis file dan kode, antara lain:

File Sistem Operasi

1.Kernel: File kernel adalah inti dari sistem operasi yang mengelola sumber daya sistem dan menyediakan layanan dasar.
2.Device Driver: File device driver adalah kode yang memungkinkan sistem operasi berkomunikasi dengan perangkat keras.
3.Sistem File: File sistem file adalah struktur data yang digunakan oleh sistem operasi untuk mengelola file dan direktori.

Kode Sistem Operasi

1.Kode Sumber: Kode sumber adalah kode yang ditulis dalam bahasa pemrograman tertentu untuk membuat sistem operasi.
2.Kode Objek: Kode objek adalah kode yang dihasilkan oleh kompiler dari kode sumber.
3.Kode Mesin: Kode mesin adalah kode yang dapat dijalankan langsung oleh prosesor.

File Konfigurasi

1.File Konfigurasi Sistem: File konfigurasi sistem adalah file yang berisi pengaturan dan konfigurasi sistem operasi.
2.File Konfigurasi Perangkat Keras: File konfigurasi perangkat keras adalah file yang berisi pengaturan dan konfigurasi perangkat keras.

File Lainnya

1.Log File: File log adalah file yang berisi catatan aktivitas sistem operasi.

2.File Temporer: File temporer adalah file yang dibuat oleh sistem operasi untuk keperluan sementara. 4.Commit message yang digunakan oleh sistem operasi dapat bervariasi tergantung pada proyek dan tim pengembangnya. Namun, berikut adalah beberapa contoh commit message yang umum digunakan dalam pengembangan sistem operasi:

3.fix: memperbaiki bug pada kernel

4.feat: menambahkan dukungan untuk perangkat keras baru

5.docs: memperbarui dokumentasi sistem operasi

6.perf: meningkatkan kinerja sistem operasi

7.security: memperbaiki kerentanan keamanan

8.refactor: memperbaiki struktur kode sistem operasi

9.merge: menggabungkan branch baru ke dalam main branch

10.release: rilis versi baru sistem operasi

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
Hasil percobaan sistem operasi dapat memberikan informasi yang berharga tentang kinerja, stabilitas, dan keamanan sistem operasi. Berikut adalah beberapa kemungkinan hasil percobaan sistem operasi dan maknanya:
Kinerja sistem operasi: Hasil percobaan dapat menunjukkan bagaimana sistem operasi berjalan pada perangkat keras yang berbeda-beda, termasuk kecepatan prosesor, kapasitas memori, dan kinerja grafis.
Stabilitas sistem operasi: Hasil percobaan dapat menunjukkan apakah sistem operasi dapat berjalan stabil dan tidak mengalami crash atau error pada kondisi tertentu.
Keamanan sistem operasi: Hasil percobaan dapat menunjukkan apakah sistem operasi dapat melindungi diri dari serangan malware, virus, atau ancaman lainnya.
Kompatibilitas perangkat keras: Hasil percobaan dapat menunjukkan apakah sistem operasi dapat berjalan pada perangkat keras yang berbeda-beda, termasuk perangkat keras lama atau baru.
Kinerja aplikasi: Hasil percobaan dapat menunjukkan bagaimana aplikasi berjalan pada sistem operasi, termasuk kecepatan loading, responsivitas
Hasil percobaan sistem operasi dapat dihubungkan dengan teori tentang fungsi kernel, system call, dan arsitektur OS sebagai berikut:
Fungsi Kernel: Hasil percobaan dapat menunjukkan bagaimana kernel mengelola sumber daya sistem, seperti prosesor, memori, dan perangkat keras lainnya. Kernel yang efektif dapat meningkatkan kinerja sistem operasi.
System Call: Hasil percobaan dapat menunjukkan bagaimana system call digunakan oleh aplikasi untuk mengakses layanan sistem operasi. System call yang efisien dapat meningkatkan kinerja aplikasi.
Arsitektur OS: Hasil percobaan dapat menunjukkan bagaimana arsitektur OS mempengaruhi kinerja, stabilitas, dan keamanan sistem operasi. Arsitektur OS yang baik dapat meningkatkan kinerja dan keamanan sistem operasi.
Dengan memahami hubungan antara hasil percobaan dan teori tentang fungsi kernel, system call, dan arsitektur OS, pengembang dapat:

Mengoptimalkan kernel: Mengoptimalkan kernel untuk meningkatkan kinerja sistem operasi.
Mengoptimalkan system call: Mengoptimalkan system call untuk meningkatkan kinerja aplikasi.
Mengembangkan arsitektur OS yang baik: Mengembangkan arsitektur OS yang baik untuk meningkatkan kinerja, stabilitas, dan keamanan sistem operasi.
Dengan demikian, hasil percobaan sistem operasi dapat digunakan untuk meningkatkan kualitas dan kinerja sistem operasi.

Perbedaan hasil di lingkungan OS berbeda (Linux vs Windows) dapat disebabkan oleh beberapa faktor:
Arsitektur OS: Linux dan Windows memiliki arsitektur OS yang berbeda, sehingga dapat mempengaruhi kinerja, stabilitas, dan keamanan sistem.
Kernel: Linux memiliki kernel yang open-source dan dapat disesuaikan, sedangkan Windows memiliki kernel yang proprietary dan tidak dapat disesuaikan.
Sistem File: Linux dan Windows memiliki sistem file yang berbeda, seperti ext4 untuk Linux dan NTFS untuk Windows.
Manajemen Memori: Linux dan Windows memiliki manajemen memori yang berbeda, sehingga dapat mempengaruhi kinerja aplikasi.
Kompatibilitas Perangkat Keras: Linux dan Windows memiliki kompatibilitas perangkat keras yang berbeda, sehingga dapat mempengaruhi kinerja sistem.
Perbedaan hasil di lingkungan OS berbeda dapat terlihat dalam beberapa aspek, seperti:

Kinerja Aplikasi: Aplikasi dapat berjalan lebih cepat pada satu OS dibandingkan dengan OS lainnya.
Stabilitas Sistem: Sistem operasi dapat memiliki stabilitas yang berbeda-beda, tergantung pada bagaimana mereka mengelola sumber daya sistem.
Keamanan: Sistem operasi dapat memiliki keamanan yang berbeda-beda, tergantung pada bagaimana mereka mengelola akses dan proteksi data.
Dalam melakukan pengujian, perlu mempertimbangkan perbedaan-perbedaan tersebut untuk mendapatkan hasil yang akurat dan relevan.


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
