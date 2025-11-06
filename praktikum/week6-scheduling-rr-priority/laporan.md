
# Laporan Praktikum Minggu 6
Topik:  Penjadwalan CPU – Round Robin (RR) dan Priority Scheduling

---

## Identitas
- **Nama**  : Muhammad Maulidana Nerazzuri
- **NIM**   : 250202922
- **Kelas** : 1IKRA 

---

## Tujuan
1. Menghitung waiting time dan turnaround time pada algoritma RR dan Priority.
2. Menyusun tabel hasil perhitungan dengan benar dan sistematis.
3. Membandingkan performa algoritma RR dan Priority.
4. Menjelaskan pengaruh time quantum dan prioritas terhadap keadilan eksekusi proses.
5. Menarik kesimpulan mengenai efisiensi dan keadilan kedua algoritma.

---

## Dasar Teori
Round Robin adalah algoritma penjadwalan CPU yang menggunakan konsep time sharing, dimana setiap proses diberikan jatah waktu eksekusi yang sama dalam bentuk time quantum. Ketika time quantum habis, proses akan di-preempt dan dipindahkan kembali ke antrian ready queue untuk mendapatkan giliran berikutnya. Pendekatan ini menjadikan Round Robin bersifat adil (fair) terhadap seluruh proses karena semua proses memperoleh kesempatan eksekusi secara bergilir. Efektivitas dari RR sangat dipengaruhi besar kecilnya nilai quantum: quantum terlalu kecil menghasilkan overhead switching tinggi, sedangkan quantum terlalu besar justru membuat sistem menjadi mirip First Come First Serve (FCFS). RR banyak digunakan pada sistem interaktif karena mampu memberikan response time yang cepat

Priority Scheduling adalah algoritma penjadwalan CPU yang menentukan urutan eksekusi proses berdasarkan tingkat prioritas. Proses dengan prioritas tertinggi akan dieksekusi terlebih dahulu, baik dalam bentuk preemptive maupun non-preemptive. Mekanisme ini memungkinkan sistem mengelola proses sesuai tingkat kepentingan sehingga proses yang lebih kritikal dapat lebih cepat dilayani. Namun algoritma ini memiliki kelemahan yaitu risiko starvation (kelaparan proses) dimana proses dengan prioritas rendah dapat tertunda lama. Untuk mencegah hal tersebut, teknik ageing sering diterapkan dengan meningkatkan prioritas proses yang sudah terlalu lama menunggu.

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
