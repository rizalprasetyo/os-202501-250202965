
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
Contoh: Menyusun laporan praktikum dengan struktur ilmiah (Pendahuluan–Metode–Hasil–Pembahasan–Kesimpulan).
Menyajikan hasil uji dalam bentuk tabel dan/atau grafik yang jelas.
Menuliskan analisis hasil dengan argumentasi yang logis.
Menyusun sitasi dan daftar pustaka dengan format yang konsisten.
Mengunggah draft laporan ke repositori dengan rapi dan tepat waktu.

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan. 
Penjadwalan CPU merupakan mekanisme penting dalam sistem operasi untuk menentukan urutan eksekusi proses agar pemanfaatan prosesor lebih efisien. Setiap algoritma penjadwalan memiliki karakteristik yang berbeda dan berdampak langsung terhadap kinerja sistem, khususnya pada waktu tunggu (waiting time) dan waktu penyelesaian (turnaround time). Praktikum ini bertujuan untuk membandingkan kinerja algoritma First Come First Served (FCFS) dan Shortest Job First (SJF) menggunakan simulasi berbasis program Python. Data proses dibaca dari file CSV untuk meningkatkan keterulangan eksperimen. Hasil pengujian menunjukkan bahwa algoritma SJF menghasilkan rata-rata waiting time dan turnaround time yang lebih rendah dibandingkan FCFS. Namun, FCFS memiliki keunggulan dari sisi kesederhanaan implementasi. Dengan demikian, pemilihan algoritma penjadwalan harus disesuaikan dengan kebutuhan dan karakteristik sistem.

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
Lingkungan Pengujian

Sistem Operasi: Windows

Bahasa Pemrograman: Python

Editor: Visual Studio Code

Metode Penjadwalan: FCFS dan SJF (non-preemptive)

Data Proses

Data proses disimpan dalam file Scheduling.csv untuk memisahkan data uji dari kode program sehingga eksperimen lebih terstruktur dan mudah direplikasi.

proses	arival time	brust time
p1	0	8
p2	1	4
p3	2	9
p4	3	5
2.1.3 Prosedur Praktikum

Menyusun data proses dalam file CSV.

Membaca data CSV menggunakan program Python.

Melakukan simulasi penjadwalan menggunakan algoritma FCFS.

Menghitung waiting time dan turnaround time setiap proses.

Mengulangi simulasi menggunakan algoritma SJF.

Menampilkan hasil dalam bentuk tabel pada terminal.


## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
- Jelaskan makna hasil percobaan.  
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).  
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  
Berdasarkan hasil praktikum, algoritma LRU menghasilkan jumlah page fault yang lebih sedikit dibandingkan algoritma FIFO. Hal ini menunjukkan bahwa LRU memiliki kinerja yang lebih baik dalam skenario pengujian yang digunakan. Hasil tersebut sejalan dengan teori manajemen memori yang menyatakan bahwa algoritma LRU lebih adaptif terhadap pola akses memori karena mempertimbangkan riwayat penggunaan halaman, sehingga halaman yang masih sering digunakan cenderung dipertahankan di memori utama [2].

Sebaliknya, algoritma FIFO menggantikan halaman berdasarkan urutan kedatangan tanpa memperhatikan frekuensi atau waktu terakhir penggunaan halaman. Akibatnya, halaman yang masih relevan dan sering diakses dapat tergantikan lebih awal, yang menyebabkan peningkatan jumlah page fault. Kondisi ini terlihat pada hasil praktikum, di mana FIFO menghasilkan page fault lebih banyak dibandingkan LRU. Temuan ini juga konsisten dengan hasil penelitian yang membandingkan algoritma page replacement dan menunjukkan bahwa FIFO umumnya kurang efisien dibandingkan algoritma berbasis riwayat akses seperti LRU [1].

Dari sisi ekspektasi teori, hasil praktikum telah sesuai dengan literatur sistem operasi modern yang menyebutkan bahwa LRU cenderung memberikan performa yang lebih baik dalam sebagian besar kasus penggunaan. Namun, keunggulan LRU tersebut diperoleh dengan konsekuensi kompleksitas implementasi yang lebih tinggi dibandingkan FIFO. Dalam sistem nyata, implementasi LRU memerlukan mekanisme tambahan untuk melacak riwayat akses halaman, sedangkan FIFO lebih mudah diimplementasikan dan memiliki overhead yang lebih rendah [2].

Meskipun demikian, praktikum ini memiliki beberapa keterbatasan. Pengujian hanya dilakukan dengan satu skenario page reference dan jumlah frame memori yang terbatas, sehingga hasil yang diperoleh belum tentu merepresentasikan seluruh kondisi penggunaan sistem operasi yang kompleks. Selain itu, simulasi dilakukan secara sederhana tanpa mempertimbangkan faktor lain seperti beban sistem, ukuran halaman yang bervariasi, atau algoritma page replacement lainnya seperti Optimal dan Clock.


---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
Algoritma page replacement LRU menghasilkan jumlah page fault yang lebih sedikit dibandingkan algoritma FIFO pada skenario pengujian yang dilakukan.

FIFO memiliki mekanisme yang lebih sederhana, namun kurang efisien karena tidak mempertimbangkan pola penggunaan halaman.

Pemilihan algoritma page replacement berpengaruh terhadap efisiensi penggunaan memori utama dalam sistem operasi.

Hasil praktikum sesuai dengan teori manajemen memori yang menyatakan bahwa algoritma berbasis riwayat akses, seperti LRU, cenderung memiliki kinerja yang lebih baik.
---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban: 1. Mengapa Format IMRAD Membantu Membuat Laporan Praktikum Lebih Ilmiah dan Mudah Dievaluasi?
Meningkatkan Kualitas Ilmiah: IMRAD (Introduction, Methods, Results, and Discussion) memaksa penulis untuk mengorganisir laporan secara sistematis, mencerminkan proses ilmiah yang objektif dan terstruktur, sehingga menghindari narasi subjektif dan sesuai dengan standar jurnal akademik.
Memudahkan Evaluasi: Evaluator dapat dengan cepat menavigasi bagian tertentu, seperti memeriksa validitas metode di Methods atau akurasi data di Results, tanpa harus membaca seluruh laporan campur aduk.
Mendorong Konsistensi dan Reproducibility: Format ini memastikan laporan dapat direproduksi, meningkatkan kredibilitas, dan membantu mahasiswa belajar menulis seperti peneliti, bukan hanya melaporkan tugas. **  
2. [Pertanyaan 2]  
   **Jawaban: 2. Apa Perbedaan antara Bagian Hasil dan Pembahasan?
Bagian Hasil (Results): Fokus pada presentasi data mentah atau hasil observasi/eksperimen tanpa interpretasi, seperti tabel, grafik, atau deskripsi faktual (misalnya, "Waktu tunggu rata-rata adalah 8.75 detik"). Tujuannya adalah menyajikan fakta apa adanya secara objektif.
Bagian Pembahasan (Discussion): Melibatkan analisis, interpretasi, dan penjelasan hasil, seperti menghubungkan data dengan teori, membandingkan ekspektasi, menjelaskan anomali, dan menarik kesimpulan (misalnya, "WT tinggi karena convoy effect di FCFS"). Ini bersifat analitis dan subjektif berdasarkan konteks.
Perbedaan Utama: Hasil adalah "apa yang terjadi" (deskriptif dan netral), sedangkan Pembahasan adalah "mengapa itu terjadi dan apa artinya" (analitis), sehingga mencegah bias dan memudahkan pembaca membedakan fakta dari opini. **  
3. [Pertanyaan 3]  
   **Jawaban: 3. Mengapa Sitasi dan Daftar Pustaka Penting, Bahkan untuk Laporan Praktikum?
Menghindari Plagiarisme dan Memberikan Kredit: Sitasi menunjukkan bahwa ide, data, atau metode berasal dari sumber lain, mencegah tuduhan plagiarisme dan mengajarkan etika akademik, seperti mengutip manual Linux atau buku OS Concepts.
Mendukung Klaim dengan Bukti: Sitasi memperkuat argumen dengan referensi otoritatif, membuat analisis lebih meyakinkan dan kredibel, terutama saat menjelaskan konsep seperti algoritma scheduling.
Memungkinkan Verifikasi dan Pendalaman: Pembaca dapat memeriksa sumber asli untuk memverifikasi akurasi atau mendalami topik, penting untuk eksperimen berbasis teori di praktikum.
Meningkatkan Kualitas Akademik: Bahkan di laporan praktikum, sitasi menunjukkan kedalaman penelitian dan keterhubungan dengan literatur ilmiah, membedakan laporan mahasiswa dari catatan pribadi, serta mempersiapkan untuk penulisan ilmiah tingkat lanjut. Tanpa sitasi, laporan terlihat kurang profesional dan sulit dievaluasi kredibilitasnya. **  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
