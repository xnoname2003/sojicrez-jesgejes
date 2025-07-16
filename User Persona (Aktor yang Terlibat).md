# User Persona (Aktor yang Terlibat)

## 1. User Persona Admin
Admin bertugas sebagai pengelola utama sistem yang memiliki akses penuh untuk melakukan berbagai fungsi seperti login, mengelola user (termasuk pelanggan), mengelola produk, menangani penjualan baik melalui sistem maupun secara langsung, mengatur pengiriman, mengelola ulasan, menanggapi komplain, serta membuat laporan penjualan. Admin berperan penting dalam memastikan kelancaran operasional dan administrasi sistem.

![User Persona Admin](https://github.com/user-attachments/assets/3604f750-7cdc-46be-bf6f-add1ffcfd413)
 
## 2. User Persona Pelanggan
Pelanggan adalah pengguna akhir sistem yang berperan sebagai konsumen produk. Mereka dapat melakukan registrasi, login, mengelola akun pribadi, membuat pesanan, melakukan pembayaran, melacak pesanan, melihat riwayat pesanan, dan memberikan ulasan atau komplain. Pelanggan menjadi pusat dari proses transaksi penjualan dalam sistem ini.

<img width="1414" height="2000" alt="User Persona Pelanggan" src="https://github.com/user-attachments/assets/228e5a54-aded-4908-960a-b413f23e12ce" />

# Kondisi Objek Permasalahan
Berikut ini merupakan berbagai permasalahan yang dihadapi dalam penjualan Kripik Isal:
1. Pencatatan stok dan transaksi manual.
2. Tidak tahu performa penjualan harian.
3. Pesanan via WhatsApp rawan lupa dan tidak tercatat.
4. Tidak bisa tracking status pesanan dan pengiriman.
5. Tidak ada dokumentasi keluhan pelanggan.
6. Tidak ada manajemen produk otomatis.

# Solusi yang Ditawarkan
Berdasarkan permasalahan yang dijabarkan sebelumnya, solusi yang ditawarkan mencakup:
1. Mengembangkan sistem pencatatan digital otomatis untuk stok dan transaksi guna menggantikan metode manual berbasis buku tulis, sehingga seluruh transaksi tercatat secara sistematis dan dapat direkap secara real-time.
2. Menyediakan dashboard performa penjualan harian hingga tahunan agar pemilik usaha dapat memantau perkembangan bisnis dan tren penjualan secara visual.
3. Membuat sistem pemesanan digital terintegrasi yang memungkinkan pelanggan melakukan pesanan melalui platform resmi dan bukan hanya lewat WhatsApp, untuk menghindari kelalaian dan kehilangan pesanan.
4. Mengimplementasikan fitur tracking status pesanan dan pengiriman agar pelanggan dapat mengetahui posisi dan tahapan pesanan mereka secara transparan.
5. Menyediakan fitur dokumentasi dan tanggapan terhadap keluhan pelanggan melalui sistem live chat atau komplain online, yang langsung terintegrasi dengan sistem administrasi sistem.
6. Membangun fitur manajemen produk yang dinamis, dimana admin dapat menambahkan, mengubah, dan menghapus produk serta mengatur stok dan harga secara langsung melalui panel sistem.

# Functional Requirement
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
13. Admin dapat menambahkan, mengedit, dan menghapus data produk melalui panel kelola produk.
14. Admin dapat mengelola data pelanggan: melihat profil, menonaktifkan akun, dan memverifikasi pengguna baru.
15. Sistem mencatat riwayat transaksi dan status pembayaran pelanggan.
16. Pelanggan dapat memantau status pesanan melalui halaman “Your Orders.”
17. Setelah produk diterima, pelanggan dapat memberikan rating (1-5 bintang) dan menulis ulasan.
18. Admin dapat membahas ulasan pelanggan secara publik untuk menjaga reputasi toko.
19. Sistem menyediakan fitur komplain: pelanggan dapat membuat laporan keluhan terkait pesanan.
20. Admin dan pelanggan dapat berkomunikasi melalui chat pada fitur komplain untuk menyelesaikan masalah.
21. Admin dapat mencetak dan mengunduh laporan keuangan dan transaksi dalam format PDF atau Excel.
22. Sistem dapat menampilkan statistik penjualan dalam bentuk grafik atau tabel harian, mingguan, bulanan, dan tahunan.
23. Sistem menyediakan autentikasi login khusus untuk admin dan pelanggan, serta fitur logout dan pengaturan akun.
