
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
