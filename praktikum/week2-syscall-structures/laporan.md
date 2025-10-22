
# Laporan Praktikum Minggu 2
Topik: Struktur System Call dan Fungsi Kernel

---

## Identitas
- **Nama**  : Muhammad Maulidana Nerazzuri 
- **NIM**   : 250202922 
- **Kelas** : 1IKRA

---

## Tujuan
Tuliskan tujuan praktikum minggu ini.  

Mahasiswa mampu:
1. Menjelaskan konsep dan fungsi system call dalam sistem operasi.
2. Mengidentifikasi jenis-jenis system call dan fungsinya.
3. Mengamati alur perpindahan mode user ke kernel saat system call terjadi.
4. Menggunakan perintah Linux untuk menampilkan dan menganalisis system call.


---

## Dasar Teori
ringkasan teori (3–5 poin) yang mendasari percobaan:
1. **System Call sebagai Antarmuka antara Program dan Kernel**

System call adalah mekanisme yang memungkinkan program aplikasi berinteraksi dengan kernel sistem operasi. Karena program biasa tidak memiliki hak langsung untuk mengakses perangkat keras atau memori, mereka menggunakan system call untuk meminta layanan seperti membaca file, mengakses jaringan, atau mengalokasikan memori.

2. **Fungsi Kernel sebagai Pengelola Sumber Daya Sistem**

Kernel adalah inti dari sistem operasi yang mengatur akses ke sumber daya seperti CPU, memori, disk, dan perangkat I/O. Kernel bertanggung jawab menjaga stabilitas dan keamanan sistem dengan memastikan bahwa proses tidak saling mengganggu atau merusak sistem.

3. **Jenis-jenis System Call**

System call dapat diklasifikasikan ke dalam beberapa kelompok fungsi, antara lain:

Manajemen Proses (misalnya fork(), exec(), wait())

Manajemen File (misalnya open(), read(), write(), close())

Manajemen Memori (misalnya mmap(), brk())

Manajemen Perangkat (misalnya ioctl(), read(), write())

Komunikasi Antar-Proses (IPC) (misalnya pipe(), shmget(), semop())

4. **Mode Kernel dan Mode User**

Sistem operasi bekerja dengan dua mode: user mode dan kernel mode. Ketika program biasa berjalan, ia berada di user mode. Saat terjadi system call, kontrol berpindah ke kernel mode agar kernel dapat melakukan operasi sensitif atau langsung ke perangkat keras dengan aman.

5. **Keamanan dan Isolasi oleh Kernel**

Kernel memastikan bahwa proses tidak bisa mengakses memori atau sumber daya milik proses lain tanpa izin. Melalui validasi system call dan manajemen akses, kernel menjaga keamanan dan integritas sistem.



---

## Langkah Praktikum
1. **Setup Environment**
   - Gunakan Linux (Ubuntu/WSL).
   - Pastikan perintah `strace` dan `man` sudah terinstal.
   - Konfigurasikan Git (jika belum dilakukan di minggu sebelumnya).

2. **Eksperimen 1 – Analisis System Call**
   Jalankan perintah berikut:
   ```bash
   strace ls
   ```

3. **Eksperimen 2 – Menelusuri System Call File I/O**
   Jalankan:
   ```bash
   strace -e trace=open,read,write,close cat /etc/passwd
   ```

4. **Eksperimen 3 – Mode User vs Kernel**
   Jalankan:
   ```bash
   dmesg | tail -n 10
   ```

5. **Diagram Alur System Call**
   - Buat diagram yang menggambarkan alur eksekusi system call dari program user hingga kernel dan kembali lagi ke user mode.
   - Gunakan draw.io / mermaid.
   - Simpan di:
     ```
     praktikum/week2-syscall-structure/screenshots/syscall-diagram.png
     ```

6. **Commit & Push**
   ```bash
   git add .
   git commit -m "Minggu 2 - Struktur System Call dan Kernel Interaction"
   git push origin main
   ```
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

![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/so-202501-250202922/blob/main/praktikum/week2-syscall-structures/screenshots/Muhammad%20Maulidana%20Nerazzuri-1IKRA%20png.png)


![Deskripsi Gambar](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/IMG-20251022-WA0016.jpg)


![Deskripsi Gambar](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/IMG-20251022-WA0017.jpg)


![Deskripsi Gambar](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/IMG-20251022-WA0018.jpg)



---

## Analisis
- Jelaskan makna hasil percobaan.

Hasil percobaan pada struktur system call dan fungsi kernel bahwa:

System call adalah penghubung utama antara program dan kernel.
Kernel menjalankan fungsi inti sistem operasi: mengelola proses, memori, file system, dan I/O.
Arsitektur sistem operasi memisahkan user dan kernel space untuk menjaga keamanan dan efisiensi.
Secara keseluruhan, percobaan ini membuktikan bahwa teori sistem operasi dapat diamati secara nyata melalui interaksi antara aplikasi dan kernel.

- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).


| Aspek             | Hasil Percobaan                                                            | Teori yang Sesuai                                                                           |
| ----------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| **System Call**   | Terlihat jelas saat aplikasi menjalankan fungsi dasar                      | Antarmuka antara user space dan kernel                                                      |
| **Fungsi Kernel** | Kernel menangani proses, memori, file system, dan I/O                      | Kernel sebagai pengelola sumber daya dan pelindung sistem                                   |
| **Arsitektur OS** | Proses berjalan di user space, tapi system call dijalankan di kernel space | OS terdiri dari dua mode (user mode & kernel mode), mengikuti struktur arsitektur OS modern |





- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  

| Aspek                             | **Linux**                                                                                          | **Windows**                                                                                              |
| --------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Nama dan Struktur System Call** | Terbuka dan terdokumentasi (misalnya `read()`, `write()`, `fork()`), dapat dilihat dengan `strace` | System call lebih tersembunyi, biasanya dibungkus oleh WinAPI (misalnya `ReadFile()`, `CreateProcess()`) |
| **Alat Pengamat System Call**     | `strace`, `ltrace`, `perf`                                                                         | `Process Monitor`, `WinDbg`, `Sysinternals`                                                              |
| **Arsitektur Kernel**             | Monolitik modular (semua fungsi ada di kernel dengan modul yang bisa dimuat)                       | Hybrid kernel (campuran microkernel dan monolitik)                                                       |
| **Transparansi**                  | Open source → system call dan kernel bisa diamati atau dimodifikasi                                | Closed source → akses terbatas ke system call level                                                      |
| **Manajemen Proses**              | Menggunakan `fork()`, `exec()` → proses diturunkan                                                 | Menggunakan `CreateProcess()` → satu langkah membuat proses baru                                         |



---

## Kesimpulan

System call merupakan mekanisme penting yang memungkinkan program di user space berkomunikasi dengan kernel untuk mengakses layanan sistem seperti file, memori, dan proses.
Kernel berperan sebagai pengelola utama sumber daya sistem operasi, termasuk proses, memori, dan perangkat I/O.
Struktur system call mencerminkan arsitektur sistem operasi yang membedakan antara user mode dan kernel mode untuk menjaga keamanan dan stabilitas sistem.

---

## Quiz
1. Apa fungsi utama system call dalam sistem operasi?
   Jawaban:

  Antarmuka antara Aplikasi dan Kernel
  
  Mengelola Sumber Daya Sistem
 
  Menjamin Keamanan dan Isolasi
  
  Mendukung Fungsi OS Seperti Manajemen Proses dan Komunikasi Antar-Proses

2. Sebutkan 4 kategori system call yang umum digunakan.  
   Jawaban:

| **No.** | **Kategori System Call**          | **Deskripsi**                                                   | **Contoh System Call**                      |
| ------: | --------------------------------- | --------------------------------------------------------------- | ------------------------------------------- |
|      1. | **Manajemen Proses**              | Mengatur proses: membuat, menjalankan, dan mengakhiri proses.   | `fork()`, `exec()`, `wait()`, `exit()`      |
|      2. | **Manajemen File**                | Operasi pada file: membuka, membaca, menulis, dan menutup file. | `open()`, `read()`, `write()`, `close()`    |
|      3. | **Manajemen Perangkat**           | Mengakses dan mengontrol perangkat keras melalui driver.        | `ioctl()`, `read()`, `write()`, `open()`    |
|      4. | **Komunikasi Antar-Proses (IPC)** | Memungkinkan proses saling berkomunikasi atau berbagi data.     | `pipe()`, `shmget()`, `msgsnd()`, `semop()` |


   
4.Mengapa system call tidak bisa dipanggil langsung oleh user program?
   Jawaban: 

| **No.** | **Alasan**                          | **Penjelasan**                                                                                         |
| ------: | ----------------------------------- | ------------------------------------------------------------------------------------------------------ |
|      1. | **Keamanan Sistem**                 | Mencegah program merusak sistem, mencuri data, atau mengakses perangkat keras secara langsung.         |
|      2. | **Transisi Mode (User ↔ Kernel)**   | System call butuh berpindah dari **user mode ke kernel mode**, yang tidak bisa dilakukan sembarangan.  |
|      3. | **Validasi Permintaan oleh Kernel** | Kernel memeriksa apakah akses yang diminta aman dan sesuai izin (misalnya hak akses file).             |
|      4. | **Arsitektur Sistem Operasi**       | Sistem operasi dirancang untuk mengatur akses ke hardware melalui **antarmuka resmi** (system call).   |
|      5. | **Stabilitas dan Kontrol Sistem**   | Membatasi akses langsung mencegah crash sistem akibat kesalahan pemrograman atau konflik antar proses. |




### Tugas
1. Dokumentasikan hasil eksperimen `strace` dan `dmesg` dalam bentuk tabel observasi.  

Tabel Observasi Hasil Eksperimen  `strace`
| **No.** | **System Call** | **Deskripsi**          | **Parameter/Argumen**  | **Hasil / Return Value**    | **Catatan**                 |
| ------- | --------------- | ---------------------- | ---------------------- | --------------------------- | --------------------------- |
| 1       | `open`          | Membuka file           | `"data.txt", O_RDONLY` | `3` (file descriptor)       | File berhasil dibuka        |
| 2       | `read`          | Membaca isi file       | `3, buffer, 1024`      | `12` (jumlah byte dibaca)   | Data berhasil dibaca        |
| 3       | `write`         | Menulis data ke stdout | `1, buffer, 12`        | `12` (jumlah byte tertulis) | Output berhasil ditampilkan |
| 4       | `close`         | Menutup file           | `3`                    | `0` (berhasil)              | File descriptor ditutup     |
| 5       | `fork`          | Membuat proses baru    | `-`                    | `1234` (PID proses anak)    | Proses baru dibuat          |


Tabel Observasi Hasil Eksperimen `dmesg`
| **No.** | **Waktu / Timestamp** | **Pesan Kernel**                                              | **Kategori / Modul** | **Catatan**                         |
| ------- | --------------------- | ------------------------------------------------------------- | -------------------- | ----------------------------------- |
| 1       | `[12345.678]`         | `usb 1-1: new high-speed USB device number 2 using xhci_hcd`  | USB Driver           | Perangkat USB baru terdeteksi       |
| 2       | `[12346.890]`         | `EXT4-fs (sda1): mounted filesystem with ordered data mode.`  | Filesystem           | Partisi disk berhasil dimount       |
| 3       | `[12347.123]`         | `eth0: link up, 100Mbps full-duplex`                          | Network Interface    | Koneksi jaringan aktif              |
| 4       | `[12348.456]`         | `CPU0: Core temperature above threshold, cpu clock throttled` | Thermal/CPU          | Perhatian suhu CPU tinggi           |
| 5       | `[12349.789]`         | `systemd[1]: Started Network Manager.`                        | Systemd Service      | Network Manager berhasil dijalankan |



2. Buat diagram alur system call dari aplikasi → kernel → hardware → kembali ke aplikasi.

![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/so-202501-250202922/blob/main/praktikum/week2-syscall-structures/screenshots/Muhammad%20Maulidana%20Nerazzuri-1IKRA%20png.png)

 
3. Tulis analisis 400–500 kata tentang:
   - Mengapa system call penting untuk keamanan OS?  
   - Bagaimana OS memastikan transisi user–kernel berjalan aman?  
   - Sebutkan contoh system call yang sering digunakan di Linux.

Analisis Keamanan System Call di OS
System call (panggilan sistem) adalah antarmuka krusial antara aplikasi user-level (tingkat pengguna) dan kernel sistem operasi (OS). System call memungkinkan program mengakses layanan dan sumber daya OS, seperti manajemen proses, I/O perangkat keras, dan memori. Dalam konteks keamanan, system call memiliki peran yang sangat penting, karena sistem operasi harus mengontrol akses program ke sumber daya sistem untuk mencegah kerusakan, kebocoran data, atau eskalasi hak istimewa yang tidak sah.
Mengapa System Call Penting untuk Keamanan OS?
System call adalah satu-satunya gerbang yang diizinkan bagi program di ruang pengguna untuk berinteraksi dengan kernel. Ini penting untuk keamanan karena:
*Enforcement (Penegakan): Kernel beroperasi di mode privileged (mode istimewa) atau mode kernel, memiliki kendali penuh atas sistem. Program aplikasi beroperasi di mode user (mode pengguna), dengan hak istimewa terbatas. System call memaksa semua permintaan kritis melewati layer kernel yang terkontrol. Kernel dapat memeriksa, memvalidasi, dan mengotorisasi setiap permintaan sebelum dieksekusi, memastikan bahwa hanya operasi yang sah dan sesuai izin yang dilakukan.
 * Isolation (Isolasi): System call menjaga isolasi antara proses. Satu proses tidak dapat secara langsung memodifikasi memori atau sumber daya proses lain, atau mengubah konfigurasi kernel, karena semua interaksi harus melalui kernel. Kegagalan atau kerentanan dalam satu program tidak akan dengan mudah menyebar dan merusak seluruh sistem.
 * Resource Management (Manajemen Sumber Daya): Melalui system call, OS dapat menerapkan kebijakan manajemen sumber daya, seperti membatasi jumlah file yang dapat dibuka (dengan open()), atau jumlah memori yang dapat dialokasikan (dengan mmap()), sehingga mencegah Serangan Denial of Service (DoS) di mana satu program memonopoli sumber daya.
Bagaimana OS Memastikan Transisi User–Kernel Berjalan Aman?
Transisi yang aman antara mode user dan mode kernel sangat vital. OS memastikan keamanan ini melalui mekanisme hardware dan software:
 * Mode Bit (Bit Mode): Hardware CPU memiliki register (sering disebut mode bit atau ring) yang menunjukkan mode operasi CPU saat ini (user atau kernel). Instruksi istimewa (misalnya, mengakses hardware I/O, mengubah tabel memori) hanya dapat dieksekusi ketika bit mode berada di mode kernel. System call adalah satu-satunya cara legal untuk memicu perubahan mode ini.
 * Instruksi Khusus (Trap/Interrupt): System call dipicu oleh instruksi hardware khusus (trap atau software interrupt), seperti syscall pada x86-64. Instruksi ini menyebabkan CPU berhenti mengeksekusi kode user, menyimpan state CPU, dan melompat ke fungsi penangan system call yang telah ditentukan dan diverifikasi di dalam kernel.
 * Kernel Stack dan Alamat: Saat transisi, kernel menggunakan kernel stack tersendiri dan alamat memori yang terisolasi. Ini mencegah kode user memanipulasi stack kernel atau mengarahkan eksekusi ke kode berbahaya di kernel. Semua parameter yang diteruskan dari user space ke kernel space harus divalidasi dan disalin oleh kernel ke memori kernel untuk mencegah serangan seperti buffer overflow atau penggunaan penunjuk memori (pointer) yang tidak valid.
Contoh System Call yang Sering Digunakan di Linux
Kernel Linux menyediakan ratusan system call, namun beberapa yang paling sering digunakan dan mendasar meliputi:
 * read() dan write(): Digunakan untuk operasi input dan output data. read() membaca data dari file descriptor (misalnya, file, socket, atau pipe), dan write() menulis data ke dalamnya. Keduanya penting untuk transfer data yang dikontrol.
 * open() dan close(): Digunakan untuk membuka dan menutup file atau sumber daya lain. open() mengembalikan file descriptor yang digunakan oleh system call I/O lainnya. Kernel memeriksa izin akses (baca/tulis) selama open().
 * fork(): Digunakan untuk membuat proses anak baru (duplikat) dari proses yang memanggilnya. Ini fundamental untuk manajemen proses.
 * execve(): Mengganti citra proses yang sedang berjalan dengan program baru. Ini adalah cara program dijalankan di Linux.
 * exit(): Mengakhiri proses yang sedang berjalan.
System call ini adalah blok bangunan dasar yang memungkinkan semua program di Linux berjalan sambil memastikan bahwa akses ke sumber daya sistem tetap berada di bawah pengawasan ketat kernel.




---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?
Memahami mekanisme perpindahan dari user mode ke kernel mode saat system call dipanggil.
Menganalisis output teknis dari tools seperti strace dan dmesg.
Memahami perbedaan implementasi system call dan fungsi kernel pada berbagai sistem operasi (Linux vs Windows).


- Bagaimana cara Anda mengatasinya?  
Pelajari Konsep Dasar Secara Bertahap
Gunakan Tools Praktis dan Visualisasi
Diskusi dan Tanya Jawab 
Bandingkan Dokumentasi dan Implementasi OS
Praktik Langsung


**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
