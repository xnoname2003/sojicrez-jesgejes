# Use Case Diagram

## 1. Use Case Diagram Admin
Pada sistem penjualan Kripik Isal, aktor admin berperan sebagai pengelola utama seluruh proses operasional sistem. Aktivitas dimulai dengan login, yang memberikan akses penuh ke fitur backend sistem. Admin dapat mengelola produk, termasuk menambah, memperbarui, atau menghapus informasi produk.
Melalui fitur data pesanan, admin dapat memantau dan mengelola semua transaksi yang dilakukan oleh pelanggan. Use case ini memiliki relasi include dengan data pelanggan, karena setiap pesanan terkait dengan identitas pemesan. Admin kemudian menjalankan proses pesanan, yang mencakup konfirmasi pembayaran, pembaruan status pesanan, dan pengelolaan transaksi manual (misalnya dari WhatsApp).
Pada tahap proses pengiriman, admin bertanggung jawab untuk menyiapkan barang dan mengatur ekspedisi. Tugas ini terhubung langsung ke fitur kelola ekspedisi, dimana admin dapat mencatat nama ekspedisi, nomor resi, dan status pengiriman.
Admin juga dapat mengakses kelola ulasan, yaitu memberikan respons terhadap ulasan yang ditulis oleh pelanggan secara publik. Jika terdapat komplain dari pelanggan, admin masuk ke fitur tanggapi komplain, dimana mereka dapat melihat rincian pengaduan komplain ini bisa berupa klarifikasi, penggantian produk, atau diskusi lanjutan dengan pelanggan melalui sistem. Hal ini bertujuan menjaga reputasi layanan dan meningkatkan kepercayaan pelanggan.
Sebagai bagian dari evaluasi bisnis, admin juga dapat menggunakan fitur kelola hasil penjualan untuk menghasilkan laporan transaksi, menganalisis data penjualan, dan mencetak laporan dalam bentuk Excel atau PDF. Semua aktivitas ini ditutup dengan logout dari sistem secara aman.

![Revisi Use Case Admin drawio](https://github.com/user-attachments/assets/2b2534ab-f4a4-4b15-a43e-a07293f6c8ca)

## 2. Use Case Diagram Pelanggan
Aktor pelanggan merupakan pengguna utama yang menggunakan sistem untuk melakukan pembelian produk Kripik Isal. Proses dimulai dengan registrasi akun, dimana pelanggan mengisi informasi seperti username, email, dan password. Setelah registrasi, pelanggan dapat login ke dalam sistem dan memperoleh akses ke fitur utama.
Setelah masuk, pelanggan bisa melakukan pemesanan produk, yaitu melihat katalog, memilih varian, menentukan jumlah, dan menambah produk ke keranjang belanja. Setelah itu, pelanggan diarahkan ke proses pembayaran, yang memiliki relasi include ke bukti pembayaran. Di tahap ini, pelanggan diminta untuk melakukan transfer bank dan mengunggah bukti pembayaran sebagai validasi transaksi.
Setelah melakukan pembayaran, pelanggan dapat memantau status pesanan, yang saling terhubung dengan fitur lacak pesanan. Fitur ini memungkinkan pelanggan mengetahui proses pesanan, mulai dari diproses hingga pengiriman. Setelah pesanan diterima, pelanggan memasuki tahapan penerimaan pesanan, lalu diberikan opsi untuk memberikan ulasan dan rating terhadap produk, baik berupa komentar maupun penilaian dalam bentuk bintang.
Jika pelanggan menemui kendala atau ketidakpuasan terhadap produk atau layanan, mereka dapat menggunakan fitur ajukan komplain. Use case ini memungkinkan pelanggan untuk menyampaikan keluhan mereka secara langsung melalui sistem, seperti produk rusak, keterlambatan pengiriman, atau perbedaan barang. Data komplain ini akan dijawab oleh admin untuk ditindaklanjuti. Terakhir, pelanggan dapat logout untuk keluar dari sistem dengan aman.

![Revisi Use Case Pelanggan drawio](https://github.com/user-attachments/assets/86d55833-cef6-473e-adda-6f913658c1bb)

## 3. Use Case Diagram Admin dan Pelanggan
Use case gabungan menyatukan seluruh aktivitas dari pelanggan dan admin dalam satu diagram yang terintegrasi. Diagram ini memperlihatkan bagaimana dua aktor utama saling berinteraksi dengan sistem secara timbal balik. Pelanggan memulai dengan registrasi, login, pemesanan produk, melakukan pembayaran, dan mengunggah bukti pembayaran. Selanjutnya, admin menangani verifikasi pembayaran dan memproses pesanan hingga pengiriman.
Setelah barang diterima, pelanggan memberikan ulasan atau mengajukan komplain, yang kemudian ditangani oleh admin melalui fitur tanggapi komplain dan kelola ulasan. Diagram ini menampilkan hubungan logis antara fungsi-fungsi pelanggan dan admin, dengan login dan logout sebagai titik pertemuan di awal dan akhir aktivitas. 

![Revisi Use Case Gabungan drawio](https://github.com/user-attachments/assets/3bd38b2e-87fd-4ab8-9f7a-ec4b0550fe33)
