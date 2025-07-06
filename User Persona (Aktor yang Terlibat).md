# User Persona (Aktor yang Terlibat)

## 1. User Persona Admin
Admin bertugas sebagai pengelola utama sistem yang memiliki akses penuh untuk melakukan berbagai fungsi seperti login, mengelola user (termasuk pelanggan), mengelola produk, menangani penjualan baik melalui sistem maupun secara langsung, mengatur pengiriman, menanggapi komplain, serta membuat laporan penjualan. Admin berperan penting dalam memastikan kelancaran operasional dan administrasi sistem.

![User Persona Admin](https://github.com/user-attachments/assets/3604f750-7cdc-46be-bf6f-add1ffcfd413)
 
## 2. User Persona Pelanggan
Pelanggan adalah pengguna akhir sistem yang berperan sebagai konsumen produk. Mereka dapat melakukan registrasi, login, mengelola akun pribadi, membuat pesanan, melakukan pembayaran, serta melihat riwayat pesanan, memberikan ulasan atau komplain. Pelanggan menjadi pusat dari proses transaksi penjualan dalam sistem ini.

![User Persona Pelanggan](https://github.com/user-attachments/assets/5bde449d-5f37-4a79-9667-cc3b63c8a752)

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
