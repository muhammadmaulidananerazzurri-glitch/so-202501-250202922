
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
queue = list_of_process_sorted_by_arrival()
quantum = Q

while queue not empty:
    p = queue.pop(0)
    execute_time = min(p.remaining, quantum)
    p.remaining -= execute_time
    current_time += execute_time

    if p.remaining > 0:
        queue.append(p)  # proses masih ada sisa → kembali ke antrian ready

    update_completion_turnaround_waiting_if_finish(p, current_time)


ready_queue = list_of_process_sorted_by_arrival()

while ready_queue not empty:
    p = select_process_with_highest_priority(ready_queue)
    current_time += p.burst
    p.remaining = 0
    update_completion_turnaround_waiting(p, current_time)
    ready_queue.remove(p)



```

---

## Hasil Eksekusi
Sertakan screenshot hasil percobaan atau diagram:
![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/Screenshot%20(13).png?raw=trues.png)

![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/Screenshot%20(14).png?raw=true.png)


![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/Screenshot%20(15).png?raw=true.png)


![Screenshot hasil](https://github.com/muhammadmaulidananerazzurri-glitch/praktikum-week1-intro-arsitektur-os-screenshot-/blob/main/Screenshot%20(16).png?raw=true.png)


---

## Analisis
- Jelaskan makna hasil percobaan.

| Algoritma   | Makna Hasil Percobaan                                                                               |
| ----------- | --------------------------------------------------------------------------------------------------- |
| Round Robin | Lebih adil, responsif, tapi rata-rata waktu tunggu & selesainya bisa lebih buruk untuk proses besar |
| Priority    | Lebih efisien untuk pekerjaan penting, tapi rawan ketidakadilan & starvation                        |

 
- Hubungkan hasil dengan teori (fungsi kernel, system call, arsitektur OS).

Hasil percobaan membuktikan bahwa mekanisme penjadwalan yang dilakukan kernel melalui system call dan interrupt secara langsung mempengaruhi performa sistem operasi pada level arsitektur, dan pilihan algoritma menentukan trade-off fairness, response time, throughput, dan risiko starvation.

 
- Apa perbedaan hasil di lingkungan OS berbeda (Linux vs Windows)?  



**1) Linux**

- RR di Linux jadi lebih smooth / lebih fair

      tidak pure RR keras 1 quantum kaku

      lebih stabil untuk banyak proses

      context switching lebih efisien

- Priority di Linux umumnya tidak menyebabkan kelaparan karena kernel Linux menerapkan:

      dynamic priority

      aging system

      balancing fairness

Hasil khas Linux pada percobaan:

      RR: waiting time lebih merata antar proses

      Priority: perbedaan waktu penyelesaian tidak terlalu ekstrem antar priority



---

## Kesimpulan


1. **Round Robin memberikan fairness lebih baik** karena setiap proses mendapatkan jatah waktu CPU secara merata. Namun performanya sangat dipengaruhi oleh ukuran quantum. Quantum terlalu kecil → banyak context switching → performa menurun, quantum terlalu besar → mirip FCFS.

2. **Priority Scheduling mampu menyelesaikan proses penting lebih cepat**, tetapi berpotensi menyebabkan *starvation* pada proses prioritas rendah jika tidak ditangani dengan mekanisme aging atau penyesuaian prioritas dinamis.

3. **Perbedaan pemilihan algoritma mempengaruhi waiting time, turnaround time, serta responsiveness sistem**, sehingga OS modern biasanya mengkombinasikan konsep fairness (mirip RR) + prioritas (Priority) agar sistem tetap responsif dan adil terhadap seluruh proses.


---

## Quiz
1. Apa perbedaan utama antara Round Robin dan Penjadwalan Prioritas?

Round Robin fokus ke keadilan pembagian waktu CPU, time slice tetap, semua proses diputar bergiliran.
Priority Scheduling fokus ke importance level → proses yang lebih penting dijalankan dulu, bukan sekedar antrian.

2. Apa pengaruh besar/kecilnya waktu kuantum terhadap kinerja sistem?  

 **Jika quantum terlalu kecil**

1. proses akan sering sekali dipreempt (dipotong)

2. context switching menjadi sangat banyak

3. overhead sistem meningkat

4. throughput cenderung turun

5. tapi respon untuk user / interaktif terasa sangat cepat (karena proses sering dapat giliran CPU walaupun sebentar)

*→ cocok untuk sistem interaktif / desktop / mobile UI*

**Jika quantum terlalu besar**

1. akan sangat jarang terjadi switching → overhead kecil

2. tapi perilaku RR jadi mirip FCFS

3. proses kecil/pendek akan menunggu lama sampai proses besar selesai kuantumnya

4. responsiveness memburuk, bisa terasa lambat

*→ cocok kalau proses rata-rata burst time nya besar dan latencynya tidak kritikal*

  
3. Mengapa algoritma Prioritas dapat menyebabkan kelaparan ?

Starvation terjadi karena proses prioritas rendah bisa terus “dikalahkan” oleh proses prioritas tinggi yang datang berulang-ulang sehingga tidak pernah dieksekusi.
    

---

## Refleksi Diri
Tuliskan secara singkat:
- Apa bagian yang paling menantang minggu ini?  
- Bagaimana cara Anda mengatasinya?  

---

**Credit:**  
_Template laporan praktikum Sistem Operasi (SO-202501) – Universitas Putra Bangsa_
