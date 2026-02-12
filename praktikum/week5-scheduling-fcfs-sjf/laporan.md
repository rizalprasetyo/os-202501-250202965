
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
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
1.Menghitung waiting time dan turnaround time untuk algoritma FCFS dan SJF.
2.Menyajikan hasil perhitungan dalam tabel yang rapi dan mudah dibaca.
3.Membandingkan performa FCFS dan SJF berdasarkan hasil analisis.
4.Menjelaskan kelebihan dan kekurangan masing-masing algoritma.
5.Menyimpulkan kapan algoritma FCFS atau SJF lebih sesuai digunakan.


---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.FCFS (First Come First Served)

Konsep dasar: Proses yang datang lebih dulu akan dieksekusi lebih dulu, seperti antrian di loket — prinsipnya first in, first out (FIFO).

Sederhana & mudah diimplementasikan, karena proses dijadwalkan berdasarkan urutan waktu kedatangan (arrival time).

Tidak adil untuk proses pendek, karena proses dengan burst time kecil bisa menunggu lama di belakang proses besar (convoy effect).

Tidak preemptive, artinya proses yang sedang berjalan tidak bisa dihentikan sampai selesai.

Kinerja baik untuk beban kerja seragam, tapi kurang efisien untuk campuran proses panjang dan pendek.

2.SJF (Shortest Job First)

Konsep dasar: Proses dengan waktu eksekusi (burst time) paling pendek dieksekusi lebih dulu untuk meminimalkan waktu tunggu rata-rata.

Tujuan utama: Menghasilkan rata-rata waiting time dan turnaround time paling kecil dibanding FCFS.

Dapat bersifat non-preemptive (sekali jalan sampai selesai) atau preemptive (dikenal sebagai Shortest Remaining Time First).

Butuh prediksi burst time, sehingga implementasinya sulit pada sistem nyata tanpa informasi tambahan.

Optimal secara teori, tetapi bisa menyebabkan starvation bagi proses panjang jika banyak proses pendek datang terus-menerus.
---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
Setup Environment
Folder kerja: praktikum/week5-scheduling-fcfs-sjf/.
Struktur folder:

Copy code
praktikum/week5-scheduling-fcfs-sjf/
├── laporan.md
├── screenshots/
│   └── (screenshot spreadsheet jika ada)
└── (file lainnya jika ada)
Eksperimen 1: FCFS (First Come First Served)
Urutkan proses berdasarkan Arrival Time:
Proses dijalankan sesuai urutan kedatangan: P1 (Arrival 0), P2 (1), P3 (2), P4 (3).

Perhitungan WT dan TAT:

P1: Mulai eksekusi pada waktu 0, selesai pada 6.
WT = 0 - 0 = 0
TAT = 0 + 6 = 6
P2: Mulai eksekusi pada waktu 6, selesai pada 14.
WT = 6 - 1 = 5
TAT = 5 + 8 = 13
P3: Mulai eksekusi pada waktu 14, selesai pada 21.
WT = 14 - 2 = 12
TAT = 12 + 7 = 19
P4: Mulai eksekusi pada waktu 21, selesai pada 24.
WT = 21 - 3 = 18
TAT = 18 + 3 = 21
Rata-rata Waiting Time dan Turnaround Time:

Avg WT = (0 + 5 + 12 + 18) / 4 = 35 / 4 = 8.75
Avg TAT = (6 + 13 + 19 + 21) / 4 = 59 / 4 = 14.75
Gantt Chart Sederhana:
| P1 | P2 | P3 | P4 |
0 6 14 21 24

Eksperimen 2: SJF (Shortest Job First)
Urutkan proses berdasarkan Burst Time terpendek (dengan memperhatikan Arrival Time):
SJF non-preemptive: Proses dijalankan berdasarkan burst time terkecil yang sudah tiba.

Waktu 0: P1 tiba (burst 6), jalankan P1 sampai selesai (0-6).
Waktu 6: P2 (8), P3 (7), P4 (3) sudah tiba. Burst terkecil: P4 (3), lalu P3 (7), P2 (8).
Urutan: P1, P4, P3, P2.
Perhitungan WT dan TAT:

P1: Mulai eksekusi pada waktu 0, selesai pada 6.
WT = 0 - 0 = 0
TAT = 0 + 6 = 6
P4: Mulai eksekusi pada waktu 6, selesai pada 9.
WT = 6 - 3 = 3
TAT = 3 + 3 = 6
P3: Mulai eksekusi pada waktu 9, selesai pada 16.
WT = 9 - 2 = 7
TAT = 7 + 7 = 14
P2: Mulai eksekusi pada waktu 16, selesai pada 24.
WT = 16 - 1 = 15
TAT = 15 + 8 = 23
Rata-rata Waiting Time dan Turnaround Time:

Avg WT = (0 + 3 + 7 + 15) / 4 = 25 / 4 = 6.25
Avg TAT = (6 + 6 + 14 + 23) / 4 = 49 / 4 = 12.25
Gantt Chart Sederhana:
| P1 | P4 | P3 | P2 |
0 6 9 16 24

Perbandingan FCFS dan SJF:

Algoritma

Avg Waiting Time

Avg Turnaround Time

Kelebihan

Kekurangan

FCFS

8.75

14.75

Sederhana dan mudah diterapkan

Tidak efisien untuk proses panjang

SJF

6.25

12.25

Optimal untuk job pendek

Menyebabkan starvation pada job panjang

Eksperimen 3: Visualisasi Spreadsheet (Opsional)
Gunakan Excel atau Google Sheets untuk perhitungan otomatis.
Kolom: Proses, Arrival, Burst, Start, Waiting, Turnaround, Finish.
Formula contoh:
Start: Untuk FCFS, Start_P1 = 0; Start_P2 = Finish_P1; dll.
Waiting: Start - Arrival.
Turnaround: Waiting + Burst.
Finish: Start + Burst.
Untuk SJF, sesuaikan urutan berdasarkan burst time yang tersedia.
Screenshot hasil perhitungan disimpan di praktikum/week5-scheduling-fcfs-sjf/screenshots/ (misalnya, fcfs_calc.png dan sjf_calc.png).
Catatan: Jika tidak menggunakan spreadsheet, perhitungan manual di atas sudah cukup.
Analisis
Perbandingan Rata-rata WT dan TAT: SJF memiliki avg WT (6.25) dan avg TAT (12.25) yang lebih rendah dibanding FCFS (8.75 dan 14.75). Ini menunjukkan SJF lebih efisien dalam mengurangi waktu tunggu rata-rata.
Kapan SJF Lebih Unggul dari FCFS: SJF lebih unggul ketika ada variasi besar dalam burst time, terutama jika proses pendek tiba lebih dulu, karena memprioritaskan yang cepat selesai, mengurangi bottleneck. FCFS lebih unggul dalam skenario sederhana atau ketika arrival time berurutan dan burst time seragam, karena tidak memerlukan sorting tambahan.
Kesimpulan Singkat: Algoritma SJF memberikan performa yang lebih baik dalam hal efisiensi CPU dibanding FCFS, namun risiko starvation pada proses panjang membuatnya kurang adil. Pemilihan algoritma tergantung pada kebutuhan sistem, seperti interaktif atau batch processing.

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
rata-rata Waiting Time (WT) = 6,25 rata-rata Turnaround Time (TAT) = 12,25 SJF lebih unggul dari FCFS ketika: Waktu eksekusi (burst time) setiap proses sudah diketahui atau dapat diperkirakan dengan baik. Karena SJF memilih proses dengan waktu terpendek, algoritma ini dapat meminimalkan waktu tunggu rata-rata dan meningkatkan efisiensi CPU.

Proses-proses yang datang memiliki variasi burst time yang besar. Dalam kondisi ini, SJF mampu menyelesaikan proses-proses kecil dengan cepat, sehingga total waktu tunggu keseluruhan menjadi jauh lebih kecil dibanding FCFS.

Lingkungan sistem bersifat batch (non-interaktif). Pada sistem batch, semua proses sudah diketahui di awal, sehingga mudah menentukan urutan yang paling efisien dengan SJF.

FCFS lebih unggul dari SJF ketika: Waktu kedatangan proses tidak dapat diprediksi dan burst time sulit diketahui. FCFS tidak memerlukan perkiraan waktu eksekusi, jadi lebih sederhana dan mudah diterapkan dalam kondisi nyata.

Lingkungan sistem bersifat interaktif atau multitasking. Dalam sistem seperti ini, FCFS lebih adil karena setiap proses dilayani berdasarkan urutan datangnya, tanpa menunda proses panjang terlalu lama.

Tujuan utama adalah keadilan, bukan efisiensi. FCFS memastikan semua proses mendapat giliran secara berurutan, sehingga tidak terjadi starvation seperti pada SJF.

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
1.FCFS Proses dieksekusi berdasarkan urutan kedatangan, sehingga sederhana dan mudah diterapkan. Dapat menyebabkan waktu tunggu rata-rata tinggi jika proses panjang datang lebih dulu (convoy effect). Lebih menekankan keadilan waktu datang, bukan efisiensi waktu eksekusi.

2.SJF

Menjalankan proses dengan burst time paling pendek terlebih dahulu, sehingga menghasilkan rata-rata waktu tunggu minimum. Lebih efisien dibanding FCFS, tetapi sulit diterapkan karena memerlukan perkiraan waktu eksekusi yang akurat. Dapat menyebabkan starvation bagi proses panjang jika proses pendek terus datang.
---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:Apa perbedaan utama antara FCFS dan SJF? :
    FCFS menjadwalkan proses berdasarkan urutan kedatangan (first come, first served), tanpa memperhatikan burst time. SJF menjadwalkan proses berdasarkan burst time terkecil yang sudah tiba, memprioritaskan proses yang lebih cepat selesai. **  
3. [Pertanyaan 2]  
   **Jawaban:Mengapa SJF dapat menghasilkan rata-rata waktu tunggu minimum? :
   SJF meminimalkan waktu tunggu rata-rata karena memilih proses dengan burst time terkecil terlebih dahulu, sehingga proses lain menunggu lebih sedikit waktu secara keseluruhan. Ini adalah algoritma optimal untuk non-preemptive scheduling dalam hal rata-rata WT, karena mengurangi idle time CPU dan bottleneck dari proses panjang. **  
4. [Pertanyaan 3]  
   **Jawaban:Apa kelemahan SJF jika diterapkan pada sistem interaktif? :
   SJF dapat menyebabkan starvation pada proses dengan burst time panjang, karena mereka terus ditunda oleh proses pendek yang datang. Di sistem interaktif, ini tidak adil dan dapat membuat responsivitas buruk, karena proses interaktif (yang mungkin memiliki burst time bervariasi) tidak diprioritaskan berdasarkan kebutuhan real-time.

Commit & Push**  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
