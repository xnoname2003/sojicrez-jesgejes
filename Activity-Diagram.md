---
## Activity Diagram Penjualan Dengan Sistem

Proses penjualan dengan sistem dimulai ketika pelanggan mengunjungi website Kripik Isal. Pelanggan dapat langsung melihat dan memilih produk yang tersedia. Jika tertarik, pelanggan akan menambahkan produk ke keranjang. Pada titik ini, sistem akan meminta pelanggan untuk melakukan login atau mendaftar akun terlebih dahulu jika belum memiliki akun. Setelah berhasil login, pelanggan  dapat mengecek kembali isi keranjang sebelum melanjutkan ke proses checkout. Pada tahap checkout, pelanggan memilih metode pengiriman dan jenis pembayaran melalui transfer bank. Setelah konfirmasi checkout, sistem akan menampilkan invoice pembayaran beserta instruksi transfer.

Jika pelanggan melanjutkan pembayaran, maka bukti pembayaran harus diunggah ke dalam sistem. Setelah itu, admin akan menerima notifikasi bahwa ada pesanan baru yang menunggu verifikasi pembayaran. Admin kemudian memverifikasi bukti pembayaran dan mengubah status pesanan menjadi “Confirmed”. Selanjutnya, admin memproses pesanan tersebut dan menyiapkan produk dan memperbarui status pesanan menjadi “Processing”. Setelah barang dikirim, admin akan  memasukkan nomor resi pengiriman dan memperbarui status pesanan menjadi “Shipped”. Pelanggan dapat memeriksa status pesanan melalui menu “Your Orders”. Setelah produk diterima, pelanggan mengonfirmasi penerimaan dan sistem akan otomatis mengubah status pesanan menjadi “Delivered”. Setelah itu, pelanggan diberi opsi untuk memberikan rating dan ulasan terhadap produk serta layanan. Jika tidak ada keluhan, maka proses berakhir. Namun apabila terdapat masalah, pelanggan dapat mengajukan komplain melalui sistem dan admin akan menanggapinya secara langsung untuk menyelesaikan masalah tersebut. 

<img width="450" alt="image" src="https://github.com/user-attachments/assets/9216a164-2750-4748-8bd6-58e920fa15b8" />

---
## Activity Diagram Penjualan Tanpa Sistem

Dalam proses penjualan tanpa sistem, alur dimulai dari pelanggan yang datang langsung atau menghubungi admin untuk melakukan pembelian. Pelanggan kemudian memilih produk yang diinginkan, lalu melakukan pembayaran secara manual. Setelah itu, peran admin dimulai dengan mengonfirmasi pembayaran yang telah dilakukan pelanggan. Setelah pembayaran dikonfirmasi, admin menambahkan produk ke keranjang, lalu melanjutkan dengan proses checkout keranjang. Admin kemudian memilih metode pengiriman dan pembayaran, serta membuat pesanan sambil mengubah status pesanan menjadi “Delivered”. Produk lalu diantar atau dijemput oleh pelanggan. Akhirnya, pelanggan menerima produk dan aktivitas berakhir dengan status pesanan diterima.

Alur ini menunjukkan ketergantungan besar pada admin, karena hampir semua proses teknis dari checkout hingga pengiriman dilakukan manual oleh admin. Tidak ada sistem otomatis yang mendukung efisiensi proses ini.

<img width="450" alt="image" src="https://github.com/user-attachments/assets/b728487a-3d7a-4605-bd1d-a1d493afc7ac" />
