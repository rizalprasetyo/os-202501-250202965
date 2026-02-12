
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizal prasetyo]  
- **NIM**   : [N250202965]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Contoh:  1.Menulis Dockerfile sederhana untuk sebuah aplikasi/skrip.
2.Membangun image dan menjalankan container.
3.Menjalankan container dengan pembatasan CPU dan memori.
4.Mengamati dan menjelaskan perbedaan eksekusi container dengan dan tanpa limit resource.
5.Menyusun laporan praktikum secara runtut dan sistematis.
## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Containerization memungkinkan aplikasi berjalan dalam lingkungan terisolasi dengan berbagi kernel sistem operasi host, sehingga lebih ringan dan efisien dibandingkan mesin virtual.

2.Control Groups (cgroups), docker menggunakan mekanisme cgroups pada Linux untuk membatasi penggunaan resource seperti CPU dan memori pada container.

3.Resource Limiting, pembatasan CPU dan memori mencegah container menggunakan resource secara berlebihan, serta dapat menghentikan container secara otomatis ketika batas memori terlampaui (OOM Kill).

---

## Langkah Praktikum
1.Persiapan Lingkungan

-Pastikan Docker terpasang dan berjalan. -Verifikasi:

docker version
docker ps
2.Membuat Aplikasi/Skrip Uji

Buat program sederhana di folder code/ (bahasa bebas) yang:

-Melakukan komputasi berulang (untuk mengamati limit CPU), dan/atau -Mengalokasikan memori bertahap (untuk mengamati limit memori). 3.Membuat Dockerfile

Tulis Dockerfile untuk menjalankan program uji. Build image:

docker build -t week13-resource-limit .
Menjalankan Container Tanpa Limit

-Jalankan container normal:

docker run --rm week13-resource-limit
-Catat output/hasil pengamatan. 5.Menjalankan Container Dengan Limit Resource

-Jalankan container dengan batasan resource (contoh):

docker run --rm --cpus="0.5" --memory="256m" week13-resource-limit
-Catat perubahan perilaku program (mis. lebih lambat, error saat memori tidak cukup, dll.). 6.Monitoring Sederhana

-Jalankan container (tanpa --rm jika perlu) dan amati penggunaan resource:

docker stats
-Ambil screenshot output eksekusi dan/atau docker stats. 7.Commit & Push

git add .
git commit -m "Minggu 13 - Docker Resource Limit"
git push origin main


---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
import time
import os

def stress_test():
    memory_holder = []
    iteration = 0
    
    print("--- Memulai Stress Test ---")
    print(f"PID: {os.getpid()}")
    
    try:
        while True:
            # 1. Komputasi CPU (Menghitung pangkat)
            _ = [i**2 for i in range(1000)]
            
            # 2. Alokasi Memori (~10MB setiap iterasi)
            chunk = ' ' * (10 * 1024 * 1024)
            memory_holder.append(chunk)
            
            iteration += 1
            print(f"Iterasi: {iteration} | Estimasi Memori: {iteration * 10} MB")
            
            time.sleep(1)
    except MemoryError:
        print("Selesai: Terkena Limit Memori (Memory Error)!")
    except Exception as e:
        print(f"Terhenti karena: {e}")

if __name__ == "__main__":
    stress_test()
    # Gunakan image Python yang ringan
FROM python:3.9-slim
    # Set direktori kerja di dalam kontainer
WORKDIR /app

    # Salin skrip uji ke dalam kontainer
COPY app.py .

    # Jalankan skrip saat kontainer dimulai
CMD ["python", "-u", "app.py"]
     docker version
     docker ps
    docker build -t week13-resource-limit .
     docker run --rm week13-resource-limit
   docker run --rm --cpus="0.5" --memory="256m" week13-resource-limit
     docker stats


## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](screenshots/example.png)

---

## Analisis
Pada percobaan ini dilakukan pengujian container Docker dengan dan tanpa pembatasan resource CPU dan memori. Saat dijalankan tanpa limit, aplikasi dapat menggunakan resource sistem secara bebas sehingga proses berjalan lebih cepat dan penggunaan CPU terlihat tinggi.

Ketika container dijalankan dengan limit CPU, kecepatan eksekusi program menurun karena jatah waktu prosesor dibatasi. Sementara itu, pembatasan memori membatasi penggunaan RAM oleh aplikasi dan dapat menyebabkan proses dihentikan ketika melewati batas yang ditentukan.

Hasil percobaan menunjukkan bahwa pembatasan resource pada Docker efektif untuk mengontrol penggunaan CPU dan memori serta menjaga kestabilan sistem host saat menjalankan beberapa container secara bersamaan.


---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
1.Docker memungkinkan pembatasan penggunaan CPU dan memori pada container sehingga aplikasi tidak dapat menggunakan resource sistem secara berlebihan.

2.Penerapan limit CPU dan memori memengaruhi kinerja aplikasi, seperti eksekusi yang lebih lambat atau penghentian proses ketika memori tidak mencukupi.

3.Pembatasan resource pada container penting untuk menjaga kestabilan dan efisiensi penggunaan resource pada sistem host.
---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban: 1. Mengapa Container Perlu Dibatasi CPU dan Memori?
Container adalah teknologi virtualisasi ringan yang berbagi kernel host OS, sehingga tanpa pembatasan sumber daya, satu container dapat mengonsumsi seluruh CPU dan memori yang tersedia, mempengaruhi performa container lain atau sistem host secara keseluruhan. Berikut alasan utamanya:

Mencegah Resource Exhaustion: Tanpa batas, container yang boros sumber daya (misalnya, aplikasi dengan loop tak terbatas) dapat menyebabkan sistem host crash atau menjadi tidak responsif, terutama di lingkungan multi-container seperti Kubernetes atau Docker Swarm.
Memastikan Keadilan dan Stabilitas: Pembatasan memungkinkan alokasi sumber daya yang adil antar container, mendukung multi-tenancy di cloud computing. Ini juga mencegah "noisy neighbor" effect, di mana satu container memperlambat yang lain.
Dukungan untuk Billing dan Monitoring: Di platform cloud (seperti AWS atau GCP), batas CPU/memori digunakan untuk metering penggunaan, memungkinkan billing berdasarkan konsumsi. Selain itu, memudahkan monitoring dan debugging performa aplikasi.
Keamanan dan Isolasi: Meskipun container kurang terisolasi dibanding VM, batas sumber daya mencegah eksploitasi seperti denial-of-service (DoS) internal, di mana container jahat menguras sumber daya untuk mengganggu layanan lain. **  
2. [Pertanyaan 2]  
   **Jawaban:2. Apa Perbedaan VM dan Container dalam Konteks Isolasi Resource?
VM (Virtual Machine) dan container keduanya menyediakan isolasi sumber daya, tetapi pendekatannya berbeda karena arsitektur yang mendasari. VM menggunakan hypervisor untuk virtualisasi penuh, sedangkan container menggunakan fitur kernel Linux seperti namespaces dan cgroups. Berikut perbedaannya:

Tingkat Isolasi:
VM: Isolasi lengkap karena setiap VM memiliki OS guest sendiri (terpisah dari host OS), sehingga sumber daya (CPU, memori, disk) sepenuhnya terpisah. Hypervisor (Type 1 atau 2) mengelola alokasi, mencegah satu VM mengakses sumber daya VM lain secara langsung.
Container: Isolasi parsial melalui namespaces (untuk proses, jaringan, dan filesystem) dan cgroups (untuk batas CPU/memori). Container berbagi kernel host OS, sehingga lebih ringan tapi rentan terhadap kerentanan kernel yang dapat mempengaruhi semua container di host.
Overhead dan Efisiensi:
VM: Overhead lebih tinggi karena menjalankan OS penuh per VM, memerlukan lebih banyak RAM dan CPU. Cocok untuk isolasi ketat, seperti menjalankan OS berbeda (Windows di Linux host).
Container: Overhead rendah karena hanya mengemas aplikasi dan dependensinya, berbagi kernel. Lebih efisien untuk deployment cepat, tapi isolasi sumber daya kurang kuat—misalnya, container dapat saling mempengaruhi jika batas tidak diterapkan.
Keamanan dan Fleksibilitas:
VM: Lebih aman untuk workload sensitif karena emulasi hardware penuh, mengurangi risiko cross-VM attacks. Namun, startup lebih lambat dan resource-intensive.
Container: Lebih fleksibel untuk microservices, tapi keamanan bergantung pada konfigurasi (misalnya, menggunakan seccomp atau AppArmor). Risiko lebih tinggi jika kernel host compromised, karena semua container terpengaruh.
Contoh Penggunaan: VM ideal untuk testing OS berbeda atau legacy apps; container untuk aplikasi cloud-native yang skalabel. **  
3. [Pertanyaan 3]  
   **Jawaban: 3. Apa Dampak Limit Memori terhadap Aplikasi yang Boros Memori?
Limit memori di container (atau VM) membatasi jumlah RAM yang dapat digunakan aplikasi, yang dikelola oleh kernel melalui mekanisme seperti cgroups di Linux. Untuk aplikasi yang boros memori (misalnya, database besar atau aplikasi dengan memory leaks), dampaknya bisa positif atau negatif tergantung implementasi:

Pencegahan Crash Sistem: Jika aplikasi melebihi limit, kernel dapat memicu Out-of-Memory (OOM) killer, yang menghentikan proses aplikasi untuk melindungi sistem host. Ini mencegah sistem crash total, tapi aplikasi akan berhenti tiba-tiba, menyebabkan downtime atau kehilangan data jika tidak ada checkpoint.
Pengurangan Performa dan Responsivitas: Aplikasi mungkin mengalami thrashing (swapping berlebihan ke disk), memperlambat eksekusi karena memori terbatas. Untuk aplikasi yang membutuhkan RAM tinggi (seperti machine learning models), limit dapat menyebabkan error atau kegagalan alokasi memori, memaksa developer untuk mengoptimalkan kode (misalnya, menggunakan pagination atau caching eksternal).
Mendorong Efisiensi dan Optimisasi: Limit memaksa aplikasi untuk menggunakan memori secara bijak, mencegah waste dan mendukung skalabilitas. Di container orchestration seperti Kubernetes, limit memori memungkinkan auto-scaling atau eviction aplikasi yang boros, memastikan sumber daya dialokasikan ke workload penting.
Risiko untuk Aplikasi Kritis: Jika limit terlalu ketat, aplikasi mungkin gagal start atau crash selama peak usage, terutama di lingkungan produksi. Namun, dengan monitoring (misalnya, via Prometheus), administrator dapat menyesuaikan limit untuk menghindari masalah, mempromosikan stabilitas keseluruhan sistem. **  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
