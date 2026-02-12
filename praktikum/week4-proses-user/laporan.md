
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizalprasetyo]  
- **NIM**   : [250202965]  
- **Kelas** : [1ikra]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
Menjelaskan konsep proses dan user di Linux.
Menampilkan dan memantau proses yang berjalan.
Membuat dan mengelola user.
Mengontrol proses menggunakan PID.
Menjelaskan kaitan manajemen user dengan keamanan sistem.


---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.

---

## Langkah Praktikum

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
Perintah pertama yaitu pwd digunakan untuk mengetahui direktori aktif atau lokasi kamu berada saat ini di sistem file. Misalnya, hasilnya menunjukkan /home/kiaarawrr, yang berarti kamu sedang berada di dalam folder rumah pengguna dengan nama kiaarawrr. Mengetahui direktori aktif penting supaya kamu tidak bingung saat menjalankan perintah lain yang bergantung pada lokasi tersebut.

Kemudian, perintah ls -l digunakan untuk melihat daftar isi folder secara rinci. Perintah ini menampilkan nama file atau folder beserta informasi tambahan seperti ukuran file, tanggal pembuatan atau modifikasi, dan hak akses (permissions) yang dimiliki file tersebut. Dengan cara ini, kamu bisa mengetahui lebih banyak detail tentang isi direktori saat ini, misalnya apakah sebuah file bisa dibaca atau ditulis oleh pengguna.

Setelah itu, kamu menjalankan perintah cd /tmp untuk berpindah ke direktori /tmp, yaitu folder khusus yang biasanya dipakai oleh sistem untuk menyimpan file sementara. Setelah berpindah, perintah ls -a digunakan untuk menampilkan semua isi folder, termasuk file atau folder tersembunyi yang namanya diawali dengan titik (.). Contohnya, di /tmp terdapat folder tersembunyi .X11-unix dan beberapa file sistem yang penting. Dengan perintah-perintah ini, kamu dapat dengan mudah berpindah tempat dan melihat isi folder baik yang terlihat maupun tersembunyi.
---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.

---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:Apa fungsi dari proses init atau systemd dalam sistem Linux?
Proses init (atau systemd di sistem modern) adalah proses pertama yang dijalankan saat boot (PID 1). Fungsinya adalah menginisialisasi sistem, mengelola proses lainnya, menangani startup/shutdown layanan, dan memastikan sistem berjalan stabil. Ia bertindak sebagai "parent" untuk semua proses.
2. [Pertanyaan 2]  
   **Jawaban:2.Apa arti dari kode permissionrwxr-xr--? Jawaban: Kode rwxr-xr-- menunjukkan hak akses file atau direktori: rwx → Pemilik (user) memiliki hak read, write, dan execute. r-x → Grup (group) memiliki hak read dan execute saja. r-- → Pengguna lain (others) hanya memiliki hak read saja. Artinya, hanya pemilik file yang dapat mengedit atau menjalankan file, sementara grup hanya bisa menjalankan dan membaca, dan pengguna lain hanya dapat membaca tanpa mengubah isi.
3. [Pertanyaan 3]  
   **Jawaban:3.Jelaskan perbedaan antara chown dan chmod. Jawaban: Perintah chown digunakan untuk mengubah kepemilikan file atau direktori, baik pemilik (user) maupun grup-nya, sedangkan chmod digunakan untuk mengubah hak akses atau permission terhadap file atau direktori tersebut. Dengan kata lain, chown mengatur siapa yang memiliki file, sedangkan chmod mengatur apa yang boleh dilakukan terhadap file itu.**  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
