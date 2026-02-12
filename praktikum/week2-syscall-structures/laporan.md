
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [RIZAL PRASETYO]  
- **NIM**   : [250262965]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.

---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan. Sistem Call (System Call): Sistem call adalah antarmuka yang disediakan oleh sistem operasi agar program aplikasi (user mode) dapat meminta layanan dari kernel (kernel mode), seperti manajemen file, proses, memori, dan perangkat I/O.

Mode Kernel vs Mode Pengguna: Sistem operasi membagi eksekusi program menjadi dua mode:

User mode: akses terbatas, tidak dapat langsung mengakses perangkat keras atau memori sistem.

Kernel mode: memiliki hak akses penuh terhadap sistem, digunakan saat menjalankan kode sistem call atau layanan OS.

Fungsi Kernel: Kernel adalah inti dari sistem operasi yang mengelola sumber daya sistem, seperti CPU, memori, file, dan perangkat keras. Fungsi kernel meliputi manajemen proses, manajemen memori, manajemen sistem file, dan pengendalian perangkat.

Interrupt dan Trap: Sistem call dilakukan melalui mekanisme trap, yaitu interrupt yang ditrigger oleh software. Ini memungkinkan transisi dari user mode ke kernel mode agar sistem operasi dapat mengeksekusi permintaan layanan.

---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.
1.Langkah-langkah yang dilakukan:Menyiapkan Lingkungan Percobaan
Menggunakan sistem operasi Linux (bisa via mesin virtual atau dual boot).

Membuka terminal dan memastikan hak akses root/sudo tersedia.

Menyediakan compiler (seperti gcc) untuk menyusun program C.

Membuat Program yang Memanggil System Call

Menulis program C sederhana yang menggunakan system call, seperti:

write() untuk mencetak ke layar,

getpid() untuk mendapatkan ID proses,

fork() untuk membuat proses baru,

open(), read(), close() untuk manajemen file.
2. Perintah yang dijalankan: 1.Menulis dan Menyusun Program C dengan System Call 2.Menjalankan Program 3.Melacak System Call yang Digunakan (dengan strace) 3. File dan kode yang dibuat: 💻 File kode (C / C++) yang berisi struktur system call dan fungsi di dalam kernel (misalnya untuk OS seperti Linux)?

Diagram / dokumen penjelasan tentang struktur sistem call dan fungsi kernel (misalnya untuk laporan atau kuliah sistem operasi)?

Template proyek yang memperlihatkan bagaimana menambahkan system call baru di kernel Linux (file .c, .h, dan Makefile)? 4. Commit message yang digunakan:ika menambahkan struktur dan fungsi kernel baru:

feat(kernel): add system call structure and kernel function implementation

Menjelaskan bahwa kamu menambahkan fitur baru (struktur dan fungsi kernel).

Jika memperbaiki atau mengubah sistem call yang sudah ada:
fix(syscall): correct parameter handling and update kernel function logic

Fokus pada perbaikan bug atau pembaruan logika fungsi.

Jika hanya merapikan atau menambahkan dokumentasi:
docs(kernel): add documentation for system call structure and kernel functions

Jika menambahkan file awal untuk struktur sistem call:
chore(kernel): create initial files for system call structure and kernel function stubs

Jika membuat commit spesifik untuk tugas kuliah / laporan praktikum:
feat(os-lab): implement basic system call structure and kernel function examples

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
include <stdio.h>
#include <unistd.h>

int main() {
    const char *msg = "Hello from User Space!\n";
    write(1, msg, 24); // system call 'write' → mengirim data ke stdout (file descriptor 1)
    return 0;
---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  
Jelaskan makna hasil percobaan:User Program (User Space)
Merupakan program atau aplikasi yang dijalankan oleh pengguna (misalnya ls, cat, atau program C buatan sendiri).

Program ini tidak memiliki akses langsung ke perangkat keras demi keamanan dan stabilitas sistem.

Ketika butuh layanan dari sistem (misalnya membaca file, membuat proses, atau mengakses memori), program akan memanggil system call.

System Call Interface
Ini adalah lapisan perantara antara user space dan kernel space.

Fungsinya menerjemahkan permintaan dari program pengguna menjadi operasi yang bisa dijalankan oleh kernel.

Contohnya: read(), write(), fork(), open(), close() — semuanya melewati system call interface.

Pada tahap ini, CPU berpindah mode dari user mode ke kernel mode.

Kernel Function
Di sinilah fungsi inti kernel dijalankan untuk mengeksekusi permintaan system call.

Kernel memiliki hak akses penuh ke perangkat keras dan memori.

Misalnya, ketika user memanggil write(), kernel function akan mengatur penulisan data ke buffer I/O atau driver perangkat.

Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS): Hubungan dengan Teori Fungsi Kernel
Dalam teori sistem operasi, kernel adalah inti sistem operasi yang mengelola seluruh sumber daya komputer — seperti CPU, memori, dan perangkat I/O.

Pada hasil percobaan (diagram), bagian “Kernel Function” menunjukkan bagaimana kernel menangani permintaan yang datang dari user program melalui system call.

Fungsi kernel meliputi:

Manajemen proses: membuat, menjadwalkan, dan mengakhiri proses.

Manajemen memori: mengalokasikan dan mengatur memori antar proses.

Manajemen perangkat I/O: melalui driver untuk membaca/menulis data.

Artinya, diagram tadi mencerminkan bagaimana fungsi kernel berperan sebagai pengendali utama antara aplikasi dan perangkat keras.

Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)? Perbedaan Arsitektur Sistem Aspek Linux Windows Tipe arsitektur Monolithic kernel Hybrid kernel Deskripsi Semua komponen inti (scheduler, memory manager, file system, driver) berada di dalam satu ruang kernel. Kombinasi antara microkernel dan monolithic, dengan sebagian layanan kernel dijalankan sebagai modul terpisah (misalnya Windows Executive, HAL, dll). Implikasi pada hasil percobaan System call langsung berinteraksi dengan kernel, sehingga lebih cepat namun berisiko bila bug terjadi. System call melalui beberapa lapisan (napi.dll → kernel32.dll → ntoskrnl.exe), sedikit lebih lambat namun lebih stabil dan modular. Perbedaan Mekanisme System Call Aspek Linux Windows Interface system call Langsung melalui tabel sys_call_table di kernel. Melalui Windows API (user mode) → Native API (kernel mode). Contoh pemanggilan write(), read(), open() — langsung menuju fungsi kernel (sys_write, sys_read, dll). WriteFile(), ReadFile() — dipanggil melalui kernel32.dll → ntdll.dll → ntoskrnl.exe. Jumlah system call Lebih terbuka (ratusan system call dapat dilihat via strace atau /usr/include/syscall.h). Lebih tertutup (API tidak semua didokumentasikan secara publik). Akses developer Open source — tabel dan implementasi system call bisa dimodifikasi dan dipelajari. Closed source — hanya API level yang bisa digunakan, implementasi internal kernel disembunyikan.
---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
ystem call berfungsi sebagai jembatan utama antara program pengguna (user space) dan kernel (kernel space), memungkinkan aplikasi mengakses layanan sistem seperti manajemen file, proses, dan memori dengan aman.
---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:Fungsi utama system call
Fungsi utama system call adalah menjadi jembatan resmi antara program user dan kernel.
Program user hidup di dunia aman dan dibatasi, sedangkan kernel pegang semua kekuasaan berbahaya. Kalau program kita:
akses file,
bikin proses,
pakai memori,

atau ngobrol dengan perangkat keras,
dia wajib minta izin lewat system call. Tanpa ini, tiap program bisa berkuasa dan OS langsung berubah jadi anarki digital.

Singkatnya:System call memungkinkan program user meminta layanan OS secara aman dan terkontrol.


2. [Pertanyaan 2]  
   **Jawaban:2. Empat kategori system call yang umum

Ini versi yang hampir pasti keluar di ujian.

Process Control
Untuk ngatur proses.
Contoh:

fork()

exec()

exit()

wait()

File Management
Untuk urusan file, karena file itu milik OS, bukan milik ego program.
Contoh:

open()

read()

write()

close()

delete()

Device Management
Untuk komunikasi dengan perangkat keras.
Contoh:

ioctl()

read()

write()

request & release device

Information Maintenance
Untuk ambil atau set informasi sistem.
Contoh:
getpid()
time()
getuid()
stat()
(Alternatif kategori lain yang kadang dipakai: Communication dan Memory Management, tapi empat di atas sudah aman.)
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
