# Use Case Diagram

## Aktor yang Terlibat
### 1. Admin
Admin bertugas sebagai pengelola utama sistem yang memiliki akses penuh untuk melakukan berbagai fungsi seperti login, mengelola user (termasuk pelanggan dan admin lainnya), mengelola produk, menangani penjualan baik melalui sistem maupun secara langsung, mengatur pengiriman, menanggapi komplain, serta membuat laporan penjualan. Admin berperan penting dalam memastikan kelancaran operasional dan administrasi sistem.
     
### 2. Pelanggan
Pelanggan adalah pengguna akhir sistem yang berperan sebagai konsumen produk. Mereka dapat melakukan resgistrasi, login, mengelola akun pribadi, membuat dan mengelola pesanan, melakukan pembayaran, serta melihat riwayat pesanan dan memberikan ulasan. Pelanggan menjadi pusat dari proses transaksi penjualan dalam sistem ini.

## Functional Requirement
Adapun functional requirement dari sistem Kripik Isal adalah sebagai berikut:
1. Sistem menampilkan katalog produk (gambar, varian, rasa, ukuran, harga, dan deskripsi) kepada semua pengunjung, tanpa perlu login.
2. Pelanggan dapat melakukan registrasi akun dengan mengisi data diri (nama lengkap, email, nomor HP, dan password).
3. Setelah login, pelanggan dapat mengelola profil (ubah nama, email, foto, dan alamat pengiriman).
4. Pelanggan dapat menambahkan produk ke keranjang belanja dengan memilih ukuran dan jumlah yang diinginkan.
5. Sistem secara otomatis menghitung total belanja berdasarkan jumlah dan ukuran produk dalam keranjang.
6. Pelanggan dapat melakukan checkout dengan memilih ekspedisi dan metode pembayaran.
7. Tersedia pilihan metode pembayaran:
   - Transfer Bank (rekening/VA)
   - COD (Bayar di tempat untuk wilayah tertentu)
8. Jika memilih transfer, pelanggan dapat mengunggah bukti pembayaran (gambar).
9. Sistem menyimpan data checkout dan menghasilkan nomor pesanan (order ID) yang unik.
10. Admin menerima notifikasi untuk setiap pesanan masuk dan pembayaran yang perlu dikonfirmasi.
11. Admin dapat mengonfirmasi pembayaran, lalu memperbarui status pesanan dari pending → confirmed → processing → shipped → delivered.
12. Sistem memperbarui stok produk secara otomatis setelah transaksi dikonfirmasi.
13. Jika stok produk menipis, sistem memberi peringatan kepada admin untuk restock.
14. Admin dapat menambahkan, mengedit, dan menghapus data produk melalui panel kelola produk.
15. Admin dapat mengelola data pelanggan: melihat profil, menonaktifkan akun, dan memverifikasi pengguna baru.
16. Sistem mencatat riwayat transaksi dan status pembayaran pelanggan.
17. Pelanggan dapat memantau status pesanan melalui halaman “Your Orders.”
18. Setelah produk diterima, pelanggan dapat memberikan rating (1-5 bintang) dan menulis ulasan.
19. Admin dapat membahas ulasan pelanggan secara publik untuk menjaga reputasi toko.
20. Sistem menyediakan fitur komplain: pelanggan dapat membuat laporan keluhan terkait pesanan.
21. Admin dan pelanggan dapat berkomunikasi melalui chat pada fitur komplain untuk menyelesaikan masalah.
22. Admin dapat mencetak dan mengunduh laporan keuangan dan transaksi dalam format PDF atau Excel.
23. Sistem dapat menampilkan statistik penjualan dalam bentuk grafik atau tabel harian, mingguan, bulanan, dan tahunan.
24. Sistem menyediakan autentikasi login khusus untuk admin dan pelanggan, serta fitur logout dan pengaturan akun.

## Use Case Diagram
### 1. Use Case Diagram Admin
Pada sistem penjualan Kripik Isal, aktor Admin berperan sebagai pusat kendali dari seluruh proses operasional sistem. Admin memulai aktivitas dengan melakukan Login ke dalam sistem, yang membuka akses penuh ke berbagai fitur penting. Admin dapat Mengelola Produk, yaitu menambahkan produk baru, memperbarui deskripsi, varian, harga, dan ukuran kemasan, sesuai dengan data master produk. Melalui use case Data Pesanan yang memiliki dependensi terhadap Data Pelanggan, admin dapat melihat pesanan yang masuk sekaligus mengetahui detail pelanggan terkait, seperti alamat dan kontak. Selanjutnya, admin dapat menjalankan Proses Pesanan, termasuk konfirmasi pembayaran, mengubah status pesanan dari pending menjadi shipped atau delivered, serta menangani pesanan manual dari luar sistem (seperti WhatsApp).
Proses pengiriman dilakukan melalui use case Proses Pengiriman yang mencakup pengelolaan layanan ekspedisi (melalui relasi include ke Kelola Ekspedisi), seperti penambahan data ekspedisi, input nomor resi, dan bukti pengiriman. Admin juga bertugas pada use case Kelola Ulasan, yaitu merespons ulasan pelanggan secara publik sebagai bentuk pengelolaan reputasi. Selain itu, admin memantau kinerja bisnis melalui Kelola Hasil Penjualan dengan menghasilkan laporan keuangan dan grafik penjualan dalam format PDF atau Excel. Semua aktivitas ini berakhir dengan Logout untuk keluar dari sistem secara aman.

![Use Case Admin](https://github.com/user-attachments/assets/2f247568-1375-430c-abc9-3ad1d1336859)

### 2. Use Case Diagram Pelanggan
Aktor pelanggan merupakan pihak yang melakukan interaksi langsung terhadap sistem untuk kebutuhan pembelian produk. Proses dimulai dengan Registrasi Akun, yang mencakup input data diri seperti nama, email, nomor HP, dan password. Setelah berhasil Login, pelanggan dapat mengakses fitur Pemesanan Produk, yaitu melihat katalog, memilih varian dan ukuran produk, lalu menambahkannya ke keranjang. Tahap ini akan membawa pelanggan ke proses Pembayaran, yang memiliki hubungan langsung ke Bukti Pembayaran (melalui relasi include), dimana pelanggan dapat mengunggah foto bukti transfer jika tidak menggunakan COD. Setelah itu, pelanggan dapat memantau Status Pesanan yang saling terhubung dengan fitur Lacak Pesanan, yang memungkinkan mereka mengetahui apakah pesanan sedang diproses, dikirim, atau telah diterima.
Setelah produk diterima, pelanggan masuk ke tahap Peneriman Pesanan dan dapat melanjutkan dengan Ulasan dan Rating terhadap produk, mencakup pemberian Bintang (1-5) dan komentar tertulis yang dapat dibaca publik. Proses ini mencerminkan sistem dua arah antara pelanggan dan admin yang mendukung evaluasi dan peningkatan mutu layanan. Pelanggan juga dapat melakukan Logout untuk keluar dari sistem setelah aktivitas selesai.

![Use Case Pelanggan drawio](https://github.com/user-attachments/assets/931b4373-958b-4a56-8de7-819517cbeb06)

### 3. Use Case Diagram Gabung
![Use Case Gabungan](https://github.com/user-attachments/assets/0797c192-57ad-42c8-8c9a-18d8330cca0f)
