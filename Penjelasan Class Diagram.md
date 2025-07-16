---
# Class Diagram 

![classdiagram](https://github.com/user-attachments/assets/d3b800c4-43ca-4600-b266-43069243c24d)

---
# Penjelasan Class Diagram

## A. **Kategori Kelas**
1. **Class User (Superclass)**
Class User adalah superclass yang memiliki atribut umum seperti userID, username, email, passwordHash, dan role. Atribut ini menjadi dasar untuk dua subclass: Pelanggan dan Admin. Terdapat juga beberapa method seperti Login(), Logout(), UpdateProfile(), dan ValidateEmail() yang bersifat generik untuk semua jenis pengguna.

2. **Class Pelanggan**
Pelanggan memiliki atribut seperti PelangganID, nama, alamat, dan noHP. Pelanggan dapat melakukan sejumlah aktivitas penting seperti Registrasi_Akun(), Kelola_Keranjang(), Membeli_Produk(), Masukkan_Ulasan(), Masukkan_Rating(), Kelola_Pesanan(), Kelola_Pembayaran(), LihatRiwayatPembelian(), dan UpdateAlamat(). Pelanggan terhubung ke class-class seperti Keranjang, Pesanan, Pembayaran, dan KolomUlasan.

3. **Class Admin**
Admin bertanggung jawab atas manajemen sistem. Atributnya meliputi adminID, nama, dan noHP. Admin memiliki berbagai fungsi seperti Kelola_Pelanggan(), Kelola_Produk(), Kelola_KolomUlasan(), Kelola_Pembayaran(), KelolaLayananEkspedisi(), Tanggapi_Keluhan(), dan Buat_Laporan(). Admin juga berperan dalam mengelola komunikasi dengan pelanggan melalui Chat.

4. **Class Produk**
Menyimpan detail tentang produk seperti ProdukID, nama, varian, ukuran, harga, deskripsi, stok, dan foto. Produk bisa dihitung rating rata-ratanya melalui method HitungRataRating(). Produk memiliki relasi ke KolomUlasan, Keranjang, dan Pesanan.

5. **Class Pesanan**
Pesanan mencatat transaksi pembelian pelanggan. Atribut pentingnya termasuk PesananID, PelangganID, ProdukID, StatusOrder, TotalPesanan, TanggalOrder, MetodePembayaran, dan ShippingID. Method-method seperti MenaruhPesanan(), UpdateStatus(), BatalkanPesanan(), Tracking_Pembayaran(), Hitung_Total(), dan Konfirmasi_Pembayaran() mendukung pengelolaan siklus pesanan.

6. **Class Keranjang**
Class ini berfungsi menyimpan produk sementara sebelum dipesan. Mencakup atribut seperti KeranjangID, ProdukID, PelangganID, Kuantitas, dan CreatedAt. Fungsinya antara lain UpdateKeranjang(), MenambahProduk(), MengurangiProduk(), Checkout(), dan HitungTotal().

7. **Class Pembayaran**
Mencatat informasi pembayaran dengan atribut seperti PembayaranID, PesananID, PelangganID, ShippingID, TotalHarga, TanggalPembayaran, dan StatusOrder. Pembayaran juga memiliki method KonfirmasiPembayaran() dan SistemBayar().

8. **Class Kolom Ulasan**
Menampung ulasan dan rating dari pelanggan terhadap produk. Atributnya meliputi UlasanID, ProdukID, PelangganID, IsiUlasan, Rating, dan TanggalUlasan. Method-nya termasuk validasi_rating() dan getUlasanByProduk().

9. **Class Chat**
Digunakan untuk komunikasi terkait komplain antara pelanggan dan admin. Atribut seperti ChatID, AdminID, PelangganID, IsiPesan, CreatedAt, dan UpdatedAt menunjukkan sistem chat dua arah. Method-nya meliputi KirimPesan(), BalasPesan(), dan GetChatHistory().

10. **Class Layanan Ekspedisi**
Mewakili penyedia layanan pengiriman seperti JNE atau J&T. Mencakup atribut EkspedisiID, NamaLayanan, KodeEkspedisi, dan CreatedAt. Fungsinya seperti PilihEkspedisi() dan GetOngkosKirim().

11. **Class Laporan**
Digunakan oleh admin untuk menyusun laporan penjualan. Memiliki atribut ReportID, nama_produk, TanggalPembayaran, TanggalUlasan, dan TotalHarga. Laporan dapat diekspor melalui method ExportToPDF() dan ExportToExcel().

