
# Laporan Praktikum Minggu [X]
Topik: [Tuliskan judul topik, misalnya "Arsitektur Sistem Operasi dan Kernel"]

---

## Identitas
- **Nama**  : [Rizal prasetyo  
- **NIM**   : [250202965]  
- **Kelas** : [1IKRA]

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  
Menginstal perangkat lunak virtualisasi (VirtualBox/VMware).
Membuat dan menjalankan sistem operasi guest di dalam VM.
Mengatur konfigurasi resource VM (CPU, RAM, storage).
Menjelaskan mekanisme proteksi OS melalui virtualisasi.
Menyusun laporan praktikum instalasi dan konfigurasi VM secara sistematis.

## Dasar Teori
Tuliskan ringkasan teori (3–5 poin) yang mendasari percobaan.
1.Virtualisasi memungkinkan satu komputer fisik menjalankan beberapa sistem operasi secara bersamaan dengan memanfaatkan hypervisor sebagai pengelola sumber daya.

2.Hypervisor bertugas mengisolasi dan mengatur akses CPU, memori, storage, dan perangkat I/O antara host dan guest agar tidak saling mengganggu.

3.Virtual Machine (VM) menyediakan lingkungan terisolasi (sandbox) sehingga sistem operasi guest dapat diuji atau digunakan tanpa memengaruhi sistem host.

4.Isolasi sumber daya pada VM meningkatkan keamanan dan stabilitas sistem, karena kesalahan atau crash pada guest tidak berdampak langsung ke host.

5.Hardening OS dapat diterapkan pada guest dan host dengan membatasi akses, layanan, dan sumber daya untuk memperkecil risiko keamanan.
---

## Langkah Praktikum
1.Menyiapkan lingkungan

-Mengaktifkan fitur virtualization pada sistem host. -Mengunduh dan menginstal VirtualBox di sistem operasi host. -Mengunduh file ISO Ubuntu Desktop (LTS).

2.Konfigurasi awal VirtualBox

-Mengatur Default Machine Folder ke drive yang diinginkan (misalnya drive D). -Memastikan tidak ada invalid settings pada VirtualBox.

3.Membuat mesin virtual baru

-Membuat VM baru dengan tipe Linux dan versi Ubuntu (64-bit). -Menentukan alokasi RAM dan CPU sesuai kemampuan sistem. -Membuat virtual hard disk (VDI) dengan metode dynamically allocated.

4.Pengaturan sistem VM

-Menonaktifkan opsi Use EFI. -Menonaktifkan Unattended Installation agar instalasi dilakukan manual. -Menambahkan file ISO Ubuntu pada menu Storage.

5.Instalasi Ubuntu

-Menjalankan VM dan memilih Install Ubuntu. -Mengatur bahasa, keyboard. -Membuat akun pengguna dan menunggu proses instalasi selesai.

6.Penyelesaian instalasi

-Me-restart VM setelah instalasi selesai. -Login ke desktop Ubuntu.
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
Instalasi Ubuntu menggunakan VirtualBox berhasil dilakukan tanpa memengaruhi sistem host karena seluruh proses berjalan pada lingkungan virtual yang terisolasi. VirtualBox berfungsi sebagai hypervisor yang mengelola sumber daya dan menerapkan konsep sandboxing, sehingga guest OS tidak dapat mengakses hardware host secara langsung. Pengaturan instalasi manual meningkatkan kestabilan sistem, sementara Guest Additions membantu mengoptimalkan tampilan dan kinerja Ubuntu. Praktikum ini menunjukkan bahwa virtualisasi merupakan metode yang aman dan efektif untuk pembelajaran sistem operasi.



---

## Kesimpulan
Tuliskan 2–3 poin kesimpulan dari praktikum ini.
Instalasi Ubuntu menggunakan VirtualBox berhasil dilakukan dengan aman tanpa memengaruhi sistem operasi host.

Teknologi virtualisasi menyediakan isolasi yang baik antara host dan guest melalui hypervisor.

Mesin virtual berfungsi sebagai sandbox yang mendukung keamanan dan stabilitas sistem.

Pengaturan sistem yang tepat serta instalasi Guest Additions meningkatkan performa dan kenyamanan penggunaan Ubuntu.
---

## Quiz
1. [Pertanyaan 1]  
   **Jawaban:Perbedaan antara Host OS dan Guest OS

Host OS (Host Operating System): Merupakan sistem operasi utama yang berjalan langsung di atas hardware fisik (seperti CPU, RAM, dan disk drive). Host OS bertanggung jawab mengelola sumber daya hardware dan menjalankan aplikasi secara native. Dalam konteks virtualisasi, host OS menyediakan platform untuk hypervisor atau virtualisasi software.
Guest OS (Guest Operating System): Merupakan sistem operasi yang berjalan di dalam virtual machine (VM), yang dikelola oleh hypervisor. Guest OS tidak berinteraksi langsung dengan hardware fisik; semua aksesnya melalui hypervisor. Guest OS dapat berupa OS yang sama atau berbeda dari host OS, dan dapat dijalankan multiple instance secara terisolasi.
Perbedaan Utama: Host OS mengontrol hardware secara langsung, sedangkan guest OS beroperasi dalam lingkungan virtual yang disimulasikan. Host OS adalah "pemilik" sistem fisik, sementara guest OS adalah "penyewa" yang bergantung pada host untuk sumber daya.**  
2. [Pertanyaan 2]  
   **Jawaban: Peran Hypervisor dalam Virtualisasi

Pengelolaan Sumber Daya: Hypervisor (juga disebut virtual machine monitor atau VMM) bertindak sebagai lapisan perantara antara hardware fisik dan virtual machines (VMs). Ia mengalokasikan sumber daya seperti CPU, RAM, dan storage ke setiap VM secara efisien.
Isolasi dan Abstraksi: Hypervisor menyediakan abstraksi hardware, memungkinkan multiple guest OS berjalan secara independen tanpa saling mengganggu. Ia menangani virtualisasi hardware, seperti emulasi perangkat I/O dan manajemen memori.
Jenis Hypervisor: Ada dua tipe utama – Type 1 (bare-metal, seperti VMware ESXi atau Hyper-V, berjalan langsung di hardware) dan Type 2 (hosted, seperti VirtualBox, berjalan di atas host OS). Perannya umumnya sama: memfasilitasi virtualisasi untuk meningkatkan utilisasi hardware, fleksibilitas, dan keamanan.
Fitur Tambahan: Hypervisor juga mendukung fitur seperti live migration (memindahkan VM tanpa downtime), snapshot, dan load balancing, membuatnya esensial untuk cloud computing dan data centers. **  
3. [Pertanyaan 3]  
   **Jawaban: Mengapa Virtualisasi Meningkatkan Keamanan Sistem

Isolasi Proses: Setiap virtual machine (VM) berjalan dalam lingkungan terisolasi, sehingga malware atau serangan di satu VM tidak dapat menyebar ke VM lain atau host OS. Ini mencegah risiko seperti lateral movement dalam jaringan.
Kontrol Akses dan Segmentasi: Virtualisasi memungkinkan pembuatan "sandbox" untuk aplikasi atau layanan tertentu, membatasi hak akses dan mengurangi surface attack. Administrator dapat mengatur kebijakan keamanan per VM, seperti firewall virtual atau enkripsi data.
Snapshot dan Rollback: Hypervisor memungkinkan pembuatan snapshot sistem, sehingga jika terjadi breach, sistem dapat dikembalikan ke keadaan aman sebelumnya tanpa mempengaruhi hardware fisik.
Pengurangan Risiko Hardware: Dengan virtualisasi, sistem fisik dapat diisolasi dari ancaman langsung, dan updates keamanan dapat diterapkan pada level VM tanpa mengganggu operasi utama. Ini juga mendukung compliance seperti HIPAA atau GDPR dengan segmentasi data sensitif.
Efisiensi dalam Keamanan: Virtualisasi memfasilitasi testing malware di lingkungan terkontrol, serta deployment zero-trust models, di mana setiap VM diperlakukan sebagai entitas terpisah dengan verifikasi identitas. Namun, hypervisor itu sendiri harus diamankan untuk menghindari risiko seperti VM escape attacks. **  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
