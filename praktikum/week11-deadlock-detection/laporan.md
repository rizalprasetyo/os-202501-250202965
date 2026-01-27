
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizal prasetyo]  
- **NIM**   : [250202965]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Mengimplementasikan algoritma page replacement FIFO dalam program. -Mengimplementasikan algoritma page replacement LRU dalam program. -Menjalankan simulasi page replacement dengan dataset tertentu. -Membandingkan performa FIFO dan LRU berdasarkan jumlah page fault. -Menyajikan hasil simulasi dalam laporan yang sistematis..

---

## Dasar Teori
Manajemen Memori – Page Replacement (FIFO & LRU)
Manajemen memori merupakan mekanisme sistem operasi untuk mengelola pemakaian memori utama agar setiap proses dapat dieksekusi secara optimal dan tidak saling mengganggu.
Ketika sebuah proses membutuhkan halaman yang belum tersedia di memori utama dan kapasitas memori telah penuh, maka sistem akan melakukan page replacement untuk menentukan halaman mana yang harus digantikan.
Algoritma FIFO (First In First Out) bekerja dengan cara mengganti halaman yang paling awal dimuat ke dalam memori, tanpa memperhatikan frekuensi atau waktu penggunaannya.
Sementara itu, algoritma LRU (Least Recently Used) mengganti halaman yang sudah paling lama tidak diakses, sehingga lebih menyesuaikan dengan pola penggunaan halaman oleh proses.
.

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
   Perbedaan utama FIFO dan LRU ada pada cara menentukan halaman yang diganti saat memori penuh.
FIFO mengganti halaman yang pertama kali masuk ke memori, tanpa melihat apakah halaman tersebut masih sering digunakan atau tidak. Cara ini sederhana, tapi kadang kurang efisien karena bisa saja halaman yang masih dibutuhkan justru terhapus.

Sementara itu, LRU mengganti halaman yang sudah paling lama tidak digunakan. Algoritma ini mencoba meniru kebiasaan penggunaan program, dengan asumsi bahwa halaman yang baru dipakai kemungkinan besar akan dipakai lagi. Karena itu, LRU biasanya menghasilkan jumlah page fault yang lebih sedikit dibandingkan FIFO. 

2. [Pertanyaan 2]  
  FIFO dapat menghasilkan Belady’s Anomaly karena algoritma ini hanya melihat urutan masuk halaman ke memori, bukan seberapa sering atau seberapa penting halaman tersebut digunakan. Ketika jumlah frame ditambah, FIFO bisa saja tetap menghapus halaman yang masih sering dipakai hanya karena halaman itu masuk lebih dulu.

Akibatnya, penambahan jumlah frame yang seharusnya membantu justru membuat jumlah page fault meningkat. Inilah yang disebut Belady’s Anomaly. Masalah ini muncul karena FIFO tidak mempertimbangkan pola akses halaman, sehingga keputusan penggantian halaman sering tidak efisien.

3. [Pertanyaan 3]  
   LRU umumnya menghasilkan performa lebih baik dibanding FIFO karena algoritma ini mempertimbangkan pola penggunaan halaman. LRU mengganti halaman yang sudah lama tidak digunakan, dengan asumsi bahwa halaman yang baru saja diakses kemungkinan besar akan digunakan kembali dalam waktu dekat.

Pendekatan ini lebih sesuai dengan cara kerja program pada umumnya, di mana akses memori cenderung berulang pada halaman yang sama dalam periode tertentu. Karena keputusan penggantian halaman lebih tepat, LRU biasanya menghasilkan jumlah page fault yang lebih sedikit dibandingkan FIFO, sehingga kinerja sistem menjadi lebih efisien.  

---

## Refleksi Diri
Tuliskan secara singkat:
- SAYA KESULITAN UNTUK MENGERJAKAN TUGAS INI SECARA MANDIRI?  
- DENGAN CARA MELIHAT TUTORIAL DARI YT DAN BANTUAN DARI GOOGLE?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
