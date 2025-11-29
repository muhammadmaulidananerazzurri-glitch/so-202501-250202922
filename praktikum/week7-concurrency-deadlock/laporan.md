
# Laporan Praktikum Minggu 7
Topik:  Sinkronisasi Proses dan Masalah Deadlock

---

## Identitas
- **Nama**  : Muhammad Maulidana Nerazzuri  
- **NIM**   : 250202922
- **Kelas** : 1IKRA

---

## Tujuan
1. Memahami cara proses berjalan secara bersamaan (concurrency)
2. Mencegah kondisi race condition
3. Menguasai mekanisme pengendalian akses ke resource bersama
4. Meningkatkan efisiensi dan kinerja sistem
5. Membangun kemampuan merancang program paralel yang aman 

---

## Dasar Teori

1. Konkurensi dan Critical Section
Saat beberapa proses/thread berjalan bersamaan, mereka dapat mengakses data atau resource yang sama. Bagian kode yang mengakses resource bersama disebut critical section, dan harus dilindungi agar tidak terjadi race condition.

2. Mekanisme Sinkronisasi
Untuk mengatur akses ke critical section, digunakan mekanisme seperti mutex, semaphore, monitor, dan lock. Tujuan utamanya adalah memastikan hanya satu proses mengakses resource pada satu waktu serta menjaga konsistensi data.

3. Kondisi Terjadinya Deadlock
Deadlock muncul ketika proses saling menunggu resource yang tidak akan pernah dilepaskan. Empat syarat deadlock menurut Coffman adalah: mutual exclusion, hold and wait, no preemption, dan circular wait.

4. Penanganan Deadlock

Ada tiga pendekatan utama yaitu:

    Pencegahan (prevention): Menghilangkan salah satu dari empat kondisi deadlock.

    Penghindaran (avoidance): Menggunakan analisis alokasi resource (misal Banker’s Algorithm).

    Deteksi & Pemulihan (detection & recovery): Mengizinkan deadlock terjadi lalu mendeteksinya dan memulihkan sistem.

5. Resource Allocation & State System
Sistem operasi memetakan resource ke proses. Kesalahan dalam pengalokasian atau sinkronisasi dapat menyebabkan deadlock atau kondisi kompetisi. Karena itu, desain algoritma sinkronisasi dan manajemen resource menjadi aspek utama percobaan.

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
   **Jawaban:**  
2. [Pertanyaan 2]  
   **Jawaban:**  
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
