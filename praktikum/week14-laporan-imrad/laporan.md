
# Laporan Praktikum Minggu 4
Topik: Manajemen Proses dan User di Linux

---

## Identitas
- **Nama**  : Muhammad Maulidana Nerazzuri 
- **NIM**   : 250202922
- **Kelas** : 1IKRA

---

## Tujuan

Tujuan dari praktikum ini adalah untuk memahami lebih dalam bagaimana sistem operasi Linux mengelola proses dan pengguna. Melalui kegiatan praktikum, saya belajar bagaimana cara menampilkan dan memantau proses yang sedang berjalan, termasuk memahami status dari setiap proses yang ada di sistem. Selain itu, saya juga mempelajari bagaimana membuat dan mengatur user serta group menggunakan perintah dasar seperti adduser, passwd, id, dan groups. Praktikum ini juga memberikan pemahaman tentang bagaimana cara menghentikan atau mengontrol proses tertentu melalui PID dengan menggunakan perintah seperti kill atau top. Dari keseluruhan kegiatan, saya dapat memahami hubungan antara manajemen user dengan keamanan sistem, di mana pengaturan hak akses dan pengelolaan akun pengguna memiliki peran penting dalam menjaga stabilitas serta keamanan sistem operasi secara keseluruhan.

---

## Dasar Teori

1. Manajemen Proses di Linux
Dalam Linux, setiap program yang dijalankan disebut proses, dan masing-masing punya ID unik yang disebut PID. Sistem operasi bertugas untuk mengatur jalannya proses-proses ini agar tidak saling mengganggu. Melalui perintah seperti ps, top, dan kill, saya bisa melihat proses yang sedang aktif, memantau kinerjanya, dan menghentikan proses tertentu jika diperlukan.

2. Manajemen User dan Group
Linux adalah sistem operasi multi-user, artinya beberapa pengguna bisa memakai sistem secara bersamaan. Karena itu, penting untuk mengatur akun user dan grup agar setiap pengguna memiliki hak akses sesuai kebutuhannya. Perintah seperti adduser, passwd, id, dan groups digunakan untuk membuat akun, mengatur kata sandi, dan menampilkan informasi pengguna.

3. Hak Akses dan Keamanan Sistem
Setiap file dan folder di Linux punya pengaturan izin seperti read, write, dan execute. Pengaturan ini menentukan siapa saja yang bisa mengakses atau mengubah file tersebut. Dengan manajemen hak akses yang baik, sistem bisa tetap aman dan terhindar dari penyalahgunaan oleh pengguna yang tidak berwenang.

---

## Langkah Praktikum
1. Menyiapkan lingkungan Linux dan membuat folder kerja praktikum/week4-proses-user.2. Menjalankan perintah whoami, id, dan groups untuk melihat identitas user.
2. Menampilkan proses menggunakan ps aux dan top, kemudian menyimpan tangkapan layar hasil top.
3. Menjalankan proses sleep 1000 &, mencari PID dengan ps, lalu menghentikannya menggunakan kill .
4. Menjalankan pstree untuk melihat hierarki proses dan mengidentifikasi proses induk sistem.
5. Menyimpan hasil praktikum dan melakukan git add, commit, dan push.

---

## Kode / Perintah
```bash
whoami
id
groups
sudo adduser praktikan
sudo passwd praktikan
ps aux | head -10
top -n 1
sleep 1000 &
ps aux | grep sleep
kill <PID>
pstree -p | head -20
```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/week4.Muhammad%20Maulidana%20Nerazzuri.png)

---

## Analisis
Analisis Hasil Percobaan

Pada percobaan ini, saya menguji bagaimana Linux mengelola user dan proses. Perintah whoami, id, dan groups menunjukkan identitas pengguna yang sedang login, termasuk UID, GID, serta grup yang dimiliki. Hasil tersebut membuktikan bahwa Linux bersifat multi-user, dimana setiap user memiliki hak akses yang berbeda. Saat menambahkan user baru dengan adduser, sistem otomatis membuat direktori home dan menyiapkan akun sehingga user baru dapat digunakan untuk login.
Pada bagian pengelolaan proses, perintah ps dan top menampilkan proses yang sedang berjalan lengkap dengan PID, nama user, penggunaan CPU, memori, dan perintah yang dijalankan. Dari sini terlihat bahwa kernel melakukan manajemen proses dan pembagian sumber daya. Proses sleep yang dijalankan di background dapat dihentikan menggunakan kill <PID>, dan setelah dicek kembali dengan ps, proses tersebut sudah tidak muncul lagi, sehingga dapat disimpulkan bahwa sistem menerima sinyal penghentian proses.
Melalui perintah pstree, saya mengamati struktur hierarki proses. Tampak bahwa setiap proses memiliki proses induk, dan seluruhnya bermuara pada init atau systemd sebagai proses pertama saat sistem menyala. Hal ini sesuai dengan konsep arsitektur proses di Linux.

perbedaan hasil di lingkungan linux dan windows

Pada Linux, hasil percobaan menunjukkan bahwa proses dan user dapat dikelola langsung melalui terminal. Perintah seperti ps, top, dan kill memberikan informasi detail mengenai PID, penggunaan CPU, memori, hingga status proses. Struktur proses juga terlihat jelas dengan pstree, di mana setiap proses memiliki induk dan semuanya bermuara pada init atau systemd. Selain itu, pengelolaan user menggunakan UID, GID, dan permission berbasis user–group.

Sementara pada Windows, informasi proses biasanya diperoleh melalui Task Manager, bukan terminal. PID tetap ada, tetapi struktur hierarki proses tidak tampil sejelas Linux. Pengaturan user juga dilakukan melalui antarmuka grafis seperti User Account Control (UAC), bukan perintah terminal. Dengan kata lain, Linux lebih transparan dalam menampilkan detail proses dan hak akses, sedangkan Windows lebih berfokus pada kemudahan penggunaan melalui GUI.


---

## Kesimpulan
-Sistem Linux menerapkan konsep multiuser dan multitasking, yang memungkinkan beberapa pengguna dan proses berjalan secara bersamaan.

-Perintah whoami, id, dan groups digunakan untuk mengetahui identitas pengguna, sedangkan adduser dan passwd digunakan untuk menambah dan mengatur akun baru.


-Perintah ps, top, dan pstree berfungsi untuk memantau proses, sementara kill digunakan untuk menghentikan proses tertentu.


-Dari hasil percobaan, saya menyimpulkan bahwa pemahaman terhadap perintah-perintah tersebut sangat penting untuk mengelola sistem Linux dengan efektif, terutama dalam hal administrasi pengguna dan kontrol proses.


---

## Quiz
1. Apa fungsi dari proses init atau systemd dalam sistem Linux?

Berdasarkan hasil pemahaman saya, proses init atau systemd merupakan proses pertama yang dijalankan oleh kernel setelah sistem Linux berhasil melakukan booting. Proses ini berfungsi untuk memulai dan mengatur seluruh layanan (service) serta proses penting lainnya yang dibutuhkan oleh sistem agar dapat berjalan dengan normal.
 Dalam sistem Linux modern, systemd telah menggantikan peran init karena memiliki kemampuan untuk menjalankan proses secara paralel dan mengelola layanan dengan lebih efisien. Dapat dikatakan bahwa systemd bertindak sebagai induk dari semua proses yang ada di sistem Linux.

2. Perbedaan antara kill dan killall

Dari hasil praktikum, saya memahami bahwa perintah kill dan killall sama-sama digunakan untuk menghentikan proses, namun memiliki cara kerja yang berbeda. Perintah kill digunakan untuk menghentikan proses berdasarkan PID (Process ID) tertentu, sehingga pengguna harus mengetahui nomor PID dari proses yang ingin dihentikan.
Sementara itu, perintah killall digunakan untuk menghentikan semua proses yang memiliki nama yang sama, tanpa harus mengetahui PID-nya satu per satu. Contohnya, perintah killall firefox akan menghentikan seluruh proses dengan nama firefox. Jadi, dapat disimpulkan bahwa kill bersifat lebih spesifik, sedangkan killall bersifat lebih luas karena dapat menghentikan beberapa proses sekaligus berdasarkan nama proses.

3. Mengapa user root memiliki hak istimewa di sistem Linux?
 
user root memiliki hak istimewa di sistem Linux
Berdasarkan teori yang saya pelajari, user root memiliki hak istimewa karena berperan sebagai administrator utama sistem Linux. Pengguna root memiliki akses penuh terhadap seluruh file, direktori, konfigurasi, serta perintah sistem tanpa batasan. Hak istimewa ini diperlukan agar administrator dapat melakukan pengelolaan sistem secara menyeluruh, seperti instalasi perangkat lunak, pengaturan jaringan, manajemen pengguna, maupun pemeliharaan sistem.
 Namun demikian, hak istimewa pada akun root juga perlu digunakan dengan hati-hati, karena kesalahan perintah atau perubahan konfigurasi yang dilakukan oleh root dapat memengaruhi seluruh sistem operasi.
  

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
