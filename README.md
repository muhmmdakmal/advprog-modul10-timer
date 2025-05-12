## AdvProg - Tutorial Module 10
<h2>
Nama   : Muhammad Akmal Abdul Halim

Kelas  : B

NPM    : 2306245125
</h2>

## Experiment 1.2: Understanding how it works.
![experiment1.2](img/experiment1.2.png)

Urutan ini terjadi karena cara eksekusi kode asinkron dalam Rust. Ketika saya menambahkan println!("Akmal's Komputer: hey hey"); dalam fungsi main() yang berada di luar task asynchronous, perintah ini dieksekusi secara langsung dan segera dalam alur utama program.

Perintah spawner.spawn(async {...}) hanya mendaftarkan tugas asinkron untuk dijalankan nanti oleh executor, bukan langsung menjalankannya. Setelah pendaftaran, program saya mencetak "hey hey", kemudian memanggil executor.run() yang baru mulai menjalankan tugas asinkron yang telah didaftarkan sebelumnya.

Dalam tugas asinkron tersebut, program mencetak "howdy!", menunggu selama 2 detik karena TimerFuture::new(Duration::new(2, 0)).await, dan akhirnya mencetak "done!". Inilah mengapa "hey hey" muncul terlebih dahulu, diikuti "howdy!" dan "done!" dengan jeda waktu di antaranya.