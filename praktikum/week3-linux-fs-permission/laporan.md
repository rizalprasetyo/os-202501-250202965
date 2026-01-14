
# Laporan Praktikum Minggu [X]
Topik: Manajemen File dan Permission di Linux

---

## Identitas
- **Nama**  : Rizalprasetyo 
- **NIM**   : 250202965
- **Kelas** : 1ikra

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
      Perintah                                     Fungsi                                        Hasil Observasi                                  

 1 `pwd`                                      Menampilkan direktori kerja aktif             Menunjukkan lokasi direktori saat ini            
 2 `ls -l`                                    Menampilkan daftar file secara detail         Menampilkan permission, owner, ukuran, dan waktu 
 3 `cd /tmp`                                  Berpindah ke direktori '/tmp'                 Direktori aktif berubah ke '/tmp'               
 4 `ls -a`                                    Menampilkan semua file termasuk tersembunyi   File yang diawali `.` ikut ditampilkan           
 5`cat /etc/passwd \| head -n 5`             Menampilkan 5 baris awal file '/etc/passwrd'  Menampilkan data akun user sistem                
 6 `echo "Hello <NAMA><NIM>" > percobaan.txt` Membuat file dan menulis teks                 File 'percobaan.txt' berhasil dibuat             
 7 `ls -l percobaan.txt`                      Melihat permission awal file                  Permission default ditampilkan                   
 8 `chmod 600 percobaan.txt`                  Mengubah hak akses file                       Permission berubah menjadi hanya owner           
 9 `sudo chown root percobaan.txt`            Mengubah pemilik file                         Owner file berubah menjadi 'root'                

2. [Pertanyaan 2]

Fungsi Tiap Perintah dan Arti Permission
Fungsi Perintah
pwd → Menampilkan direktori kerja aktif
ls → Menampilkan isi direktori
cd → Berpindah direktori
cat → Menampilkan isi file
chmod → Mengubah hak akses file
chown → Mengubah kepemilikan file
Arti Permission rwxr-xr--
Permission terbagi menjadi 3 bagian:

Bagian	Keterangan
rwx	Hak akses pemilik (read, write, execute)
r-x	Hak akses grup (read, execute)
r--	Hak akses user lain (read)
Arti simbol:
r = read (baca)
w = write (tulis)
x = execute (eksekusi)
- = tidak memiliki izin
Makna lengkap:
Pemilik file memiliki akses penuh, grup hanya bisa membaca dan menjalankan, sedangkan user lain hanya bisa membaca. 
3. [Pertanyaan 3]
  
4. [pernyataan 4]
  
    

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
