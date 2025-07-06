# Flowchart Sistem Informasi Penjualan Kripik Isal

Proses dalam sistem penjualan Kripik Isal diawali dari satu titik permulaan yaitu start, yang kemudian bercabang kedua aktor utama: Pelanggan dan Admin. Masing-masing memiliki alur tugas dan tanggung jawab berbeda dalam ekosistem ini.

## 1. Sisi Pelanggan
Pertama, pelanggan memulai dengan melihat katalog produk yang tersedia di platform. Katalog ini berisi daftar produk keripik lengkap dengan deskripsi, harga, varian, dan ukuran. Setelah melihat katalog, pelanggan diarahkan untuk melakukan login ke sistem. Di sini, terdapat keputusan bercabang: jika pelanggan belum memiliki akun, maka akan diarahkan untuk terlebih dahulu melakukan registrasi. Proses registrasi mencakup pengisian data diri seperti email, username, dan password untuk membuat akun baru. Setelah akun berhasil dibuat, pelanggan kembali ke proses login.

Jika pelanggan berhasil login, maka mereka bisa langsung menambahkan produk ke keranjang belanja, yaitu memilih produk dari katalog dan menentukan jumlah yang diinginkan. Setelah semua produk yang diinginkan masuk ke keranjang, pelanggan melanjutkan dengan melakukan checkout. Di tahap ini, pelanggan meninjau ulang pesanan dan mengisi informasi penting seperti alamat pengiriman.

Setelah checkout, pelanggan melanjutkan ke tahap pembayaran, dimana sistem hanya mendukung metode transfer bank. Pelanggan wajib melakukan pembayaran melalui transfer bank sesuai nominal yang ditentukan. Setelah melakukan transfer, pelanggan harus mengunggah bukti pembayaran ke sistem untuk diverifikasi oleh admin.

Setelah bukti dikirim, pelanggan dapat melacak status pesanan mereka, mulai dari proses verifikasi, pengemasan, hingga pengiriman. Ketika pesanan diterima di alamat tujuan, pelanggan menandai pesanan sebagai diterima. Selanjutnya, pelanggan diberi opsi untuk memberikan ulasan dan rating, yaitu penilaian dalam bentuk bintang dan komentar terhadap produk maupun layanan. 

Setelah memberi ulasan, sistem memberikan pertanyaan: “Apakah terdapat komplain?” Jika tidak ada komplain, maka proses berakhir. Namun jika ada komplain, pelanggan dapat mengajukan komplain melalui fitur yang disediakan, misalnya karena produk rusak, tidak sesuai, atau keterlambatan pengiriman. Setelah proses komplain diajukan atau ditutup, maka alur dari sisi pelanggan berakhir di titik end.

## 2. Sisi Admin
Dari sisi admin, proses juga dimulai dari titik start, lalu admin diarahkan untuk melakukan login ke sistem menggunakan kredensial yang sesuai. Setelah berhasil masuk, admin menjalankan fungsi utama, yaitu mengelola produk. Ini mencakup aktivitas seperti menambah produk baru, memperbarui deskripsi, mengubah harga atau stok, serta menghapus produk yang tidak lagi tersedia.

Selanjutnya, admin juga bertanggung jawab dalam mengelola pesanan yang masuk dari pelanggan. Di dalam pengelolaan pesanan ini, admin melakukan pengecekan atas setiap transaksi, status pembayaran, dan informasi pelanggan. Salah satu langkah penting dalam proses ini adalah memverifikasi pembayaran, dimana admin mencocokkan bukti transfer yang diunggah pelanggan dengan catatan pembayaran di sistem. Jika valid, pembayaran akan diterima dan pesanan masuk ke tahap selanjutnya.

Setelah verifikasi, admin akan memperbarui status pesanan, misalnya dari “menunggu pembayaran” menjadi “sedang diproses” atau “dikirim”. Admin juga bertanggung jawab untuk menginput data pengiriman, termasuk memilih ekspedisi, mencatat nomor resi, dan memverifikasi bahwa barang telah dikirim ke alamat pelanggan.

Kemudian, admin memiliki tugas tambahan dalam mengelola feedback dan komplain dari pelanggan. Jika terdapat komplain yang diajukan melalui sistem, admin wajib menangani dan memberikan tanggapan atau solusi yang sesuai. Jika tidak ada komplain yang diterima, proses ini bisa dilewati. 

Terakhir, admin dapat menjalankan proses mencetak laporan penjualan, yaitu rekapitulasi data transaksi, pesanan, dan statistik penjualan dalam rentang waktu tertentu. Laporan ini berguna untuk keperluan manajemen dan evaluasi bisnis. Setelah semua tugas diselesaikan, proses admin juga berakhir pada titik end.

![Flowchart Kripik Isal APBO drawio](https://github.com/user-attachments/assets/31c4d10c-edef-4bcd-b153-7a7bb3cabcaf)
