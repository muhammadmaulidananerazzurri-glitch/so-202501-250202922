
# Laporan Praktikum Minggu 3
Topik: Manajemen File dan Permission di Linux



---

## Identitas
- **Nama**  : Muhammad Maulidana Nerazzuri
- **NIM**   :250202922
- **Kelas** : 1IKRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.   

Mahasiswa mampu:
1. Menggunakan perintah `ls`, `pwd`, `cd`, `cat` untuk navigasi file dan direktori.
2. Menggunakan `chmod` dan `chown` untuk manajemen hak akses file.
3. Menjelaskan hasil output dari perintah Linux dasar.
4. Menyusun laporan praktikum dengan struktur yang benar.
5. Mengunggah dokumentasi hasil ke Git Repository tepat waktu.


---

## Dasar Teori
1. Struktur Sistem File Linux
Linux menggunakan struktur sistem file berbentuk pohon (hierarki), dengan direktori root (/) sebagai akar. Semua file dan direktori lainnya bercabang dari root ini. Pemahaman struktur ini penting untuk navigasi dan pengelolaan file.

2. Hak Akses (Permissions) File
Setiap file dan direktori di Linux memiliki hak akses yang menentukan siapa yang bisa membaca, menulis, atau mengeksekusi file. Hak akses dibagi menjadi tiga kategori:

• Owner (pemilik file)

• Group (grup pemilik file)

• Others (pengguna lain)

Hak akses ditampilkan dalam bentuk simbolik (misalnya rwxr-xr--) atau numerik (misalnya 754).

4. Perintah Dasar Manajemen File

Perintah dasar yang digunakan dalam manajemen file di Linux meliputi:

• ls, cd, pwd – untuk navigasi direktori

• cp, mv, rm, mkdir – untuk mengelola file dan folder

• touch – untuk membuat file kosong

4. Perintah Manajemen Permission

Perintah yang digunakan untuk mengatur hak akses file/direktori:

chmod – mengubah permission file/direktori

chown – mengubah kepemilikan file/direktori

chgrp – mengubah grup pemilik file/direktori

5. Mode Permission: Simbolik vs Numerik

Permission dapat diatur dalam dua mode:

Simbolik: Contoh chmod u+x file.sh (menambah izin eksekusi untuk user)

Numerik: Contoh chmod 755 file.sh (7=rwx untuk user, 5=r-x untuk group, 5=r-x untuk others)

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
