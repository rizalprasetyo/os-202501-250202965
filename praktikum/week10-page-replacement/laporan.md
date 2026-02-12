
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizalprasetyo]  
- **NIM**   : [250202965]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  
> Mahasiswa mampu menjelaskan fungsi utama sistem operasi dan peran kernel serta system call.
1.Mengimplementasikan algoritma page replacement FIFO dalam program.
2.Mengimplementasikan algoritma page replacement LRU dalam program.
3.Menjalankan simulasi page replacement dengan dataset tertentu.
4.Membandingkan performa FIFO dan LRU berdasarkan jumlah page fault.
5.Menyajikan hasil simulasi dalam laporan yang sistematis.
---

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Manajemen Memori Manajemen memori adalah bagian dari sistem operasi yang bertugas mengatur penggunaan memori utama agar dapat digunakan secara efisien oleh banyak proses. Salah satu masalah utama dalam manajemen memori adalah keterbatasan jumlah frame memori fisik dibandingkan dengan kebutuhan program.

2.Page Replacement Page replacement adalah mekanisme yang digunakan ketika terjadi page fault, yaitu saat halaman yang dibutuhkan tidak tersedia di memori utama. Sistem operasi harus mengganti salah satu halaman yang ada di memori dengan halaman baru berdasarkan algoritma tertentu.

3.Page Fault dan Page Hit Page fault terjadi ketika halaman yang diakses tidak ada di memori, sehingga sistem harus mengambilnya dari penyimpanan sekunder (disk). Page hit terjadi ketika halaman yang diakses sudah berada di memori, sehingga tidak diperlukan penggantian halaman.

4.Algoritma FIFO (First In First Out) Algoritma FIFO mengganti halaman yang pertama kali masuk ke memori tanpa memperhatikan apakah halaman tersebut masih sering digunakan atau tidak. FIFO sederhana dan mudah diimplementasikan, namun tidak selalu memberikan hasil yang efisien.

5.Algoritma LRU (Least Recently Used) Algoritma LRU mengganti halaman yang paling lama tidak digunakan. Algoritma ini lebih efisien dibanding FIFO karena mempertimbangkan pola penggunaan halaman, meskipun implementasinya lebih kompleks.


---

## Langkah Praktikum
1.Menyiapkan Lingkungan Praktikum Praktikum dilakukan menggunakan bahasa pemrograman Python. Pastikan Python telah terpasang dan dapat dijalankan melalui terminal atau command prompt.

2.Menentukan Reference String dan Jumlah Frame Reference string yang digunakan adalah: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2 Jumlah frame memori yang digunakan adalah 3 frame.

3.Membuat Program Simulasi Page Replacement Program dibuat untuk mensimulasikan dua algoritma page replacement, yaitu FIFO dan LRU. Program mencatat setiap kejadian page hit dan page fault, serta menghitung total page fault.

4.Menjalankan Program Program dijalankan melalui terminal menggunakan perintah:

python page_replacement.py
Hasil eksekusi berupa tampilan isi frame memori, status HIT atau FAULT, serta total page fault untuk masing-masing algoritma.

5.Menganalisis Hasil Simulasi Hasil simulasi FIFO dan LRU dibandingkan berdasarkan jumlah page fault. Analisis dilakukan untuk menentukan algoritma yang lebih efisien dalam penggunaan memori.

6.Menyimpan dan Mengelola Kode dengan Git Kode program dan hasil praktikum disimpan dalam repository Git, kemudian dilakukan commit dan push menggunakan perintah:

git add .
git commit -m "Minggu 10 - Page Replacement FIFO & LRU"
git push origin main.

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
frame_list = []
faults = 0

print(f"Reference: {reference}")
print(f"Frames: {frames}\n")
print(f"{'#':>2} {'P':>2}  Action       Frames")

for i, p in enumerate(reference, start=1):
    if p in frame_list:
        action = 'Hit'
    else:
        faults += 1
        action = 'Page Fault'
        if len(frame_list) < frames:
            frame_list.append(p)
        else:
            frame_list.pop(0)
            frame_list.append(p)

    display = ['-'] * (frames - len(frame_list)) + [str(x) for x in frame_list]
    print(f"{i:>2} {p:>2}  {action:12} {display}")

print(f"\nTotal page faults: {faults} / {len(reference)}")
if name == 'main': # example reference string and 3 frames ref = [7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2] simulate_fifo(ref, 3)

# SIMULASI 2: LRU (Least Recently Used)

def simulate_lru(reference, frames):

    frame_list = []
    recent = []  # most recent at end
    faults = 0

    print()
    print(f"Reference: {reference}")
    print(f"Frames: {frames}\n")
    print(f"{'#':>2} {'P':>2}  Action       Frames")
Hasil Eksekusi Sertakan screenshot hasil percobaan atau diagram: Screenshot hasil

Analisis Hasil percobaan menunjukkan bagaimana strategi penggantian halaman memengaruhi jumlah page fault. Pada reference string yang sama, algoritma LRU biasanya menghasilkan lebih sedikit page fault dibandingkan FIFO, karena LRU memilih halaman yang paling jarang dipakai terakhir, sehingga lebih sesuai dengan pola akses data yang berulang.

Pada algoritma FIFO, halaman yang masuk pertama akan dikeluarkan terlebih dahulu tanpa mempertimbangkan apakah halaman tersebut masih sering dipakai. Hal ini membuat FIFO lebih sederhana, tetapi dapat menyebabkan anomali Belady, yaitu jumlah frame lebih banyak belum tentu menurunkan page fault.

Dengan observasi frame saat simulasi berjalan, terlihat bahwa LRU lebih adaptif terhadap pola referensi, sehingga halaman yang masih sering diakses dipertahankan lebih lama di memori. Efeknya, jumlah page fault pada LRU cenderung lebih stabil atau lebih rendah, terutama pada dataset yang memiliki pengulangan nilai.

Secara keseluruhan, percobaan membuktikan bahwa pemilihan algoritma memori berdampak langsung pada performa sistem, terutama pada efisiensi penggunaan memori dan kecepatan eksekusi program yang bergantung pada jumlah page fault.

Kesimpulan Algoritma penggantian halaman memiliki dampak langsung pada performa sistem: semakin kecil jumlah page fault, semakin efisien penggunaan memori dan semakin cepat proses berjalan.

LRU umumnya memberikan hasil lebih baik daripada FIFO pada pola akses yang berulang, karena mempertahankan halaman yang baru digunakan dan membuang halaman yang jarang dipakai.

FIFO lebih mudah diimplementasikan, tetapi kurang adaptif terhadap pola referensi, sehingga berpotensi menghasilkan lebih banyak page fault dan bahkan anomali Belady pada kondisi tertentu.

Quiz [Apa perbedaan utama FIFO dan LRU?]

FIFO mengganti halaman yang masuk paling awal, sedangkan LRU mengganti halaman yang paling lama tidak digunakan.

[Mengapa FIFO dapat menghasilkan Belady’s Anomaly?]

Karena FIFO tidak mempertimbangkan pola penggunaan halaman, sehingga menambah jumlah frame justru bisa membuat page fault meningkat.

[Mengapa LRU umumnya menghasilkan performa lebih baik dibanding FIFO?]

Karena LRU mempertahankan halaman yang baru digunakan, sehingga lebih sesuai dengan pola akses nyata yang sering mengulang data, sehingga page fault cenderung lebih sedikit.

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
   **Jawaban: 1.Apa perbedaan utama FIFO dan LRU? Jawaban:
    FIFO mengganti halaman berdasarkan urutan kedatangan paling awal di memori, sedangkan LRU mengganti halaman yang paling lama tidak digunakan berdasarkan riwayat akses.   **  
3. [Pertanyaan 2]  
   **Jawaban: . 2.Mengapa FIFO dapat menghasilkan Belady’s Anomaly? Jawaban:
   Karena FIFO tidak mempertimbangkan frekuensi atau pola penggunaan halaman, sehingga penambahan jumlah frame justru dapat meningkatkan jumlah page fault (Belady’s Anomaly). **  
5. [Pertanyaan 3]  
   **Jawaban:  3.Mengapa LRU umumnya menghasilkan performa lebih baik dibanding FIFO? Jawaban:
    LRU mempertimbangkan pola akses halaman dengan mempertahankan halaman yang sering digunakan, sehingga lebih adaptif terhadap perilaku program dan menghasilkan page fault yang lebih sedikit. **  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
