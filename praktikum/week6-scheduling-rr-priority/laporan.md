
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizalprasetyuo]  
- **NIM**   : [250202935]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  1.Menghitung waiting time dan turnaround time pada algoritma RR dan Priority. 
2.Menyusun tabel hasil perhitungan dengan benar dan sistematis. 
3.Membandingkan performa algoritma RR dan Priority. 
4.Menjelaskan pengaruh time quantum dan prioritas terhadap keadilan eksekusi proses. 
5.Menarik kesimpulan mengenai efisiensi dan keadilan kedua algoritma.



---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
Penjadwalan CPU adalah mekanisme dalam sistem operasi yang bertugas menentukan urutan eksekusi proses yang berada dalam antrian siap (ready queue). Tujuannya adalah untuk memaksimalkan penggunaan CPU, meminimalkan waktu tunggu, serta meningkatkan efisiensi dan kinerja sistem secara keseluruhan. Salah satu algoritma penjadwalan yang paling umum digunakan adalah Round Robin (RR). Algoritma ini bersifat preemptive dan menggunakan time quantum atau jatah waktu yang sama untuk setiap proses. Proses akan dieksekusi secara bergiliran; jika waktu yang dialokasikan habis sebelum proses selesai, maka CPU akan menghentikan sementara proses tersebut dan memberikannya kembali giliran setelah semua proses lain mendapatkan jatahnya.

Round Robin memiliki karakteristik yang adil karena setiap proses memperoleh kesempatan eksekusi yang sama, sehingga cocok untuk sistem time-sharing atau sistem interaktif. Namun, ukuran quantum harus ditentukan dengan hati-hati. Quantum yang terlalu kecil dapat menyebabkan terlalu banyak context switching, sehingga meningkatkan overhead sistem, sedangkan quantum yang terlalu besar akan membuat algoritma ini berperilaku seperti First Come First Serve (FCFS).

Sementara itu, Priority Scheduling adalah algoritma penjadwalan yang memilih proses berdasarkan tingkat prioritas. Proses dengan prioritas tertinggi akan dieksekusi terlebih dahulu, baik dengan cara preemptive (menghentikan proses lain yang sedang berjalan) maupun non-preemptive (menunggu proses selesai terlebih dahulu). Algoritma ini efisien dalam menangani proses penting atau kritis, terutama dalam sistem real-time.

Namun, kelemahan utama Priority Scheduling adalah kemungkinan terjadinya starvation, yaitu kondisi di mana proses dengan prioritas rendah tidak pernah mendapat giliran eksekusi karena selalu kalah oleh proses dengan prioritas tinggi. Untuk mengatasinya, dapat digunakan teknik aging, yaitu menaikkan prioritas proses yang telah menunggu terlalu lama. Secara umum, Round Robin lebih menekankan pada keadilan waktu eksekusi, sedangkan Priority Scheduling berfokus pada pentingnya urutan eksekusi berdasarkan tingkat kepentingan proses.
---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.  
2. Perintah yang dijalankan.  
3. File dan kode yang dibuat.  
4. Commit message yang digunakan.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
Siapkan Data Proses Gunakan contoh data berikut (boleh dimodifikasi sesuai kebutuhan):

Proses Burst Time Arrival Time Priority P1 5 0 2 P2 3 1 1 P3 8 2 4 P4 6 3 3 Eksperimen 1 – Round Robin (RR)

Gunakan time quantum (q) = 3. Hitung waiting time dan turnaround time untuk tiap proses. Proses CT Arivaal TAT(ct-at) WT(TAT-bt) P1 14 0 14-0=14 14-5=9 P2 6 1 6-1=5 5-3=2 P3 22 2 22-2=20 20-8=12 P4 20 3 20-3=17 17-6=11 Rata rata TAT:14 Rata rata WT :8,5

Simulasikan eksekusi menggunakan Gantt Chart (manual atau spreadsheet). | P1 | P2 | P3 | P4 | P1 | P3 | P4 | P3 | 0 3 6 9 12 14 17 20 22 Catat sisa burst time tiap putaran. waktu Brust sisa waktu 0-3 5-3=0 P1 sisa 2 3-6 3-3=0 2 selesai 6-9 8-3=5 P3 sisa 5 9-12 6-3=3 P4 sisa 3 12-14 2 < 3 P1 selesai 14-17 5-3=0 P3 sisa 2 17-20 3-3=0 P4 selesai 20-22 2 < 3 P3 selesai Eksperimen 2 – Priority Scheduling (Non-Preemptive) Urutkan proses berdasarkan nilai prioritas (angka kecil = prioritas tinggi). Lakukan perhitungan manual untuk: WT[i] = waktu mulai eksekusi - Arrival[i] TAT[i] = WT[i] + Burst[i]o Buat tabel perbandingan hasil RR dan Priority. Proses BT AT PRIO ST WT(ST-AT) TAT(WT+BT) P1 5 0 2 0 0 5 P2 3 1 1 5 4 7 P4 6 3 3 8 5 11 P3 8 2 4 14 12 20 Rata rata WT :5,25 Rata rata TAT :10,75

Eksperimen 3 – Analisis Variasi Time Quantum (Opsional) Ubah quantum menjadi 2 dan 5. Amati perubahan nilai rata-rata waiting time dan turnaround time. Quantum 2

Proses CT AT BT TAT WT P1 18 0 5 18 13 P2 13 1 3 12 9 P3 24 2 8 22 14 P4 22 3 6 19 13 Rata-rata 17.75 12.25 Quantum 5

Proses CT AT BT TAT WT P1 5 0 5 5 0 P2 8 1 3 7 4 P3 21 2 8 19 11 P4 22 3 6 19 13 Rata-rata 12.5 7 Buat tabel perbandingan efek quantum. Eksperimen 4 – Dokumentasi

Simpan semua hasil tabel dan screenshot ke:

praktikum/week6-scheduling-rr-priority/screenshots/ Buat tabel perbandingan seperti berikut:

Algoritma Avg Waiting Time Avg Turnaround Time Kelebihan Kekurangan RR 8,5 14 Adil terhadap semua proses Tidak efisien jika quantum tidak tepat Priority 5,25 10,75 Efisien untuk proses penting Potensi starvation pada prioritas rendah Commit & Push

git add . git commit -m "Minggu 6 - CPU Scheduling RR & Priority" git push origin main
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
   **Jawaban:Apa perbedaan utama antara Round Robin dan Priority Scheduling?:
Round Robin (RR) adalah algoritma preemptive yang memberikan setiap proses kesempatan eksekusi selama time quantum tertentu secara bergantian, mempromosikan keadilan. Priority Scheduling mengatur proses berdasarkan nilai prioritas (prioritas tinggi dulu), bisa preemptive atau non-preemptive, fokus pada efisiensi untuk proses penting.**  
2. [Pertanyaan 2]  
   **Jawaban:Apa pengaruh besar/kecilnya time quantum terhadap performa sistem?:
Time quantum kecil meningkatkan responsivitas dan keadilan, cocok sistem interaktif, tapi meningkatkan overhead context switch dan WT rata-rata. Time quantum besar mengurangi switch, menurunkan WT, tapi bisa membuat sistem kurang responsif dan mirip non-preemptive.**  
3. [Pertanyaan 3]  
   **Jawaban:Mengapa algoritma Priority dapat menyebabkan starvation? :
Karena proses dengan prioritas rendah terus ditunda oleh proses prioritas tinggi yang datang terus-menerus, sehingga proses rendah mungkin tidak pernah dieksekusi jika tidak ada mekanisme aging atau preemption.**  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
