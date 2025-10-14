
# Laporan Praktikum Minggu 1
Topik: Arsitektur Sistem Operasi 

---

## Identitas
- **Nama**  : Muhammad Maulidana Nerazzuri 
- **NIM**   : 250202922
- **Kelas** : 1IKRA 

---

## Tujuan
Mahasiswa mampu:
1. Menjelaskan peran sistem operasi dalam arsitektur komputer.
2. Mengidentifikasi komponen utama OS (kernel, system call, device driver, file system).
3. Membandingkan model arsitektur OS (monolithic, layered, microkernel).
4. Menggambarkan diagram sederhana arsitektur OS menggunakan alat bantu digital (draw.io / mermaid).

---

## Dasar Teori
Konsep Kernel dan Ruang Alasat

**Kernel:** Merupakan inti dari sistem operasi, program yang selalu berjalan selana komputer aktif, bertindak sebagai 
perantara antara aplikasi (software) dan perangkat keras (hardware). 
Mode Operasi:

**User Mode (Ruang Pengguna):** Tempat aplikasi biasa berjalan, Akses ke hardware terbatas.

**Kernel Mode (Ruang Kernel):** Tempat kernel berjalan. Memiliki akses penuh dan tak terbatas hardware.

**Panggilan Sistem (Syston Calls):** Mekanisme utama bagi aplikasi di User Mode untuk meminta layanan dari kernel (misalnya, meminta akses 1/0, manajemen memori, atau membuat proses baru).

2. Arsitektur Kernel

**Monolitik Kernel:** Semua layanan inti 50 (manajemen proses, senori, device driver, file system) terintegras dalam satu address space kernel.

*Keuntungan:* Sangat cepat karena semua fungsi berada di satu tempat.modularites).

*Kerugian:* Kesalahan pada satu driver dapat merusak seluruh sisten (kurang stabil). Contoh: Linux (dengan

**Mikrokernel:** Hanya fungsi-fungsi yang sangat esensial (seperti manajemen komunikasi antarses proses dan manajemen senori tingkat rendah) yang ada di ruang kernel. Layanan 50 lainnya (file system, driver) berjalan sebagai server di User Mode.

*Keuntungan:* Lebih stabil dan anan karena kegagalan server tidak merusak kernel,

*Kerugian:* Komunikasi antar-proses (IPC) melalui pesan menyebabkan overhead kiner ja yang lebih lambat.

**Hibrida Kernel:** Menggabungkan elemen monolitik dan mikrokernel, menempatkan beberapa layanan kunci (driver atau file system) di ruang kernel untuk meningkatkan kinerja, namun mempertahankan struktur modular. Contoh: Windows NT/XP/7/10/11.

3. Manajemen Proses dan Penjadwalan

**Proses dan Utas (Threads):** Proses adalah program yang sedang dieksekusi dan merupakan unit alokasi sunter daya. Utas adalah unit eksekusi CPU dalam suatu proses (lightweight process).

**Penjadwalan CPU (CPU Scheduling):** Kernel bertanggung jawab untuk menilih proses mana yang akan mendapatkan Jatah CPU. Tujuannya adalah memaksimalkan utilisasi CPU dan neminimalkan waktu tunggu, Algoritma dasarnya meliputi: FCFS (First-Come, First-Served), SJF (Shortest Job First), dan Round Robin.

**Pergantian Konteks (Context Switching):** Proses menyiapan status CPU (konteks) dari proses yang sedang berjalan, menuat status CPU dari proses baru, yang nemungkinkan 50 beralih antar proses secara cepat. Manajemen Menori Utana


4. Manajemen Memori Utama

**Memori Virtual (Virtual Memory):** Konsep di mana setiap proses meniliki ilusi ruang alamat nenori sendiri yang besar dan berurutan, seskipun awmori fisik (RAM) terbatas dan terfragmentasi.

**Paging:** Teknik utana dalan Virtual Memory. Menori dibagi menjadi blok-blok berukuran tetap (frame) dan ruang alamat virtual dibagi menjadi bluk berukuran sama (page). Kernel menggunakan tabel halanan untuk nenetakan alamat virtual ke alanat fisik,

**Proteksi Memori:** Kernel memastikan satu proses tidak dapat mengakses atau nengubah memori yang dialokasikan untuk proses lain, sehingga mencegah kerusakan sistem.

5. Sistem Berkas dan Manajemen I/O

**Sistem Berkas (File System):** Struktur logis yang digunakan kernel untuk mengelola dan mengatur penyimpanan data pada perangkat storage (disk/SSD)

**Device Driver:** Modul kernel yang memungkinkan kernel berkomunikasi dengan perangkat hardware tertentu (misalnya: keyboard, mouse, printer). Driver ini menerjemahkan permintaan I/O generik dari kernel ke perintah spesifik hardware

**Akses I/O:** Kernel menyediakan System Call yang seragam untuk operasi I/O, menyembunyikan detail kompleks hardware di balik sebuah lapisan abstraksi hardware 

---

## Langkah Praktikum
1. Langkah-langkah yang dilakukan.

Pertama, saya membuat source code hello.c.
Kedua, saya mengkompilasinya menggunakan GCC.
Ketiga, saya memuat modul kernel menggunakan perintah insmod

2. Perintah yang dijalankan.

gcc, make, sudo, git clone, insmod, dmesg

3. File dan kode yang dibuat.

kode C untuk modul kernel, Makefile, atau shell script

4. Commit message yang digunakan.

GitHub 

---

## Kode / Perintah
Tuliskan potongan kode atau perintah utama:
```bash
uname -a
lsmod | head
dmesg | head
ps -ef | head
top
cat /proc/cpuinfo
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/1000136675.png)

---

## Analisis
- Jelaskan makna hasil percobaan.

| Memahami Hubungan Antar-Komponen Utama|
| :--- | 
| Membedakan Ruang Akses (Mode)|  
| Verifikasi Fungsionalitas Konkret| 


- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).

| Hasil Percobaan | Teori |
| :--- | :--- |
|Hubungan dengan Fungsi Kernel (Pengelola Sumber Daya) | Fungsi utama Kernel adalah menjadi Pengelola Sumber Daya (Resource Manager), mengontrol dan mengalokasikan hardware seperti CPU, memori, dan perangkat I/O. Kernel berjalan di Kernel Mode dengan hak akses penuh |
| Hubungan dengan System Call (Gerbang Keamanan) | System Call adalah satu-satunya mekanisme formal yang memungkinkan kode dari User Mode meminta layanan atau mengakses sumber daya yang dikontrol oleh Kernel Mode. System Call berfungsi sebagai API Kernel dan merupakan lapisan keamanan |
| Hubungan dengan Arsitektur OS (Monolitik/Hibrida)| Arsitektur Linux adalah Hibrida Monolitik, yang berarti inti Kernel sudah mengandung banyak layanan (seperti File System dan Scheduler), namun memiliki kemampuan modular untuk memuat Device Drivers dan modul lain kapan saja tanpa reboot |

- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

| Hasil di Linux | Hasil di Windows |
| :--- | :--- |
|Penekanan pada Transparansi dan Modularitas. Sistem memberikan akses yang relatif terbuka untuk memuat kode dan melihat operasi Kernel |  Penekanan pada Stabilitas dan Abstraksi. Sistem menyembunyikan operasi Kernel di balik lapisan API, mengutamakan stabilitas dan konsistensi untuk program-program pihak ketiga|


---

## Kesimpulan
- dapat memahami operasi sistem
- mengetahui macam-macam arsitektur sistem operasi dan kernel 

---

## Quiz
1. Sebutkan 3 fungsi utama sistem operasi 

  manajemen sumber daya (resource manager),penyedia antarmuka (interface provider), pengelola program (program manager)

2. Jelaskan perbedaan kernel mode dan user mode 

| Fitur | Kernel Mode | User Mode|
| :--- | :--- | :--- |
| **Hak Akses** | Hak akses penuh ke hardware (CPU,memori,disk,port I/O) dan ke semua data di sistem| Hak akses terbatas tidak dapat mengakses hardware atau memori sistem secara langsung|
| **Kode yang berjalan** | Kernel (inti sistem operasi), Device Drivers penting, dan kode yang menangani interrupt.| Semua aplikasi (browser, word processor, game, shell terminal), serta library standar|
| **Kegagalan (crash)**|Sangat fatal. Jika kode di Kernel Mode gagal, seluruh sistem akan crash (Blue Screen of Death atau Kernel Panic.  | Tidak fatal. Jika aplikasi di User Mode gagal, hanya aplikasi tersebut yang akan ditutup (di-crash), sementara sistem operasi tetap berjalan|
| **Peralihan** | Hanya dapat diakses melalui System Calls (Panggilan Sistem) yang diinisiasi oleh aplikasi, atau melalui Hardware Interrupts (Interupsi Perangkat Keras) | Mode default ketika aplikasi berjalan|
| **Tujuan** |Menjalankan tugas penting dan krusial yang memerlukan kontrol penuh atas hardware (Manajemen Memori, Penjadwalan Proses) |Menjalankan aplikasi pengguna dengan aman dan terisolasi dari sistem inti|

3.Sebutkan contoh operasi sistem dengan monilithic dan microkernel 

   Linux,UNIX Tradisional,Mach,QNX,Haiku
   

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini? **belajar membuat diagram di Draw io, mempelajari arsitektur sistem operasi dan kernel**
- Bagaimana cara Anda mengatasinya? **BELAJAR DAN SABAR**


belajar membuat diagram di Draw io, mempelajari arsitektur sistem operasi dan kernel**


---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
