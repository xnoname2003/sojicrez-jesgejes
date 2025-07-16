---
# Sequence Diagram

---
## A. **Sequence Diagram Admin**
1. **View Pending Payment**

Diagram ini menunjukkan interaksi antara admin dan sistem dalam menampilkan daftar pembayaran yang belum dikonfirmasi. Proses dimulai saat admin masuk ke dashboard, lalu sistem secara otomatis mengakses dan memproses permintaan untuk menampilkan daftar pesanan dengan status “Pending Payment”. Sistem kemudian mengambil data tersebut dari basis data dan mengembalikannya kepada admin dalam bentuk daftar pesanan yang menunggu konfirmasi pembayaran. Hal ini memungkinkan admin untuk melihat pesanan mana saja yang perlu segera diverifikasi dan diproses, menjadi bagian penting dari alur kerja administratif dalam sistem.

<img width="883" height="402" alt="ViewPendingPayment drawio" src="https://github.com/user-attachments/assets/de9bf478-f317-47df-9e98-812f83822498" />

2. **Verify Pending Payment**

Pada diagram ini, admin memilih salah satu pesanan dari daftar “Pending Payment” untuk melakukan verifikasi. Sistem menampilkan detail pembayaran beserta bukti pembayaran yang telah diunggah oleh pelanggan. Admin kemudian memverifikasi apakah pembayaran valid atau tidak. Jika valid, admin memberikan konfirmasi, dan sistem secara otomatis memperbarui status pesanan menjadi “Confirmed” atau “Processing” di database. Langkah ini penting untuk menjamin kelancaran proses selanjutnya seperti pengemasan dan pengiriman.

<img width="883" height="401" alt="verifyPendingPayment drawio" src="https://github.com/user-attachments/assets/d517ba42-f1d8-4ad7-96cc-a2ce6076a786" />

---
## B. **Sequence Diagram Pelanggan**
1. **Registrasi**

Diagram ini menggambarkan proses awal seorang pengguna baru untuk menjadi pelanggan sistem. Pelanggan mengisi formulir registrasi yang mencakup data seperti username, email, dan password. Sistem akan memvalidasi input tersebut dan memastikan tidak ada data duplikat. Setelah validasi berhasil, sistem menyimpan data ke dalam database dan memberikan konfirmasi bahwa akun berhasil dibuat. Proses ini menjadi pintu gerbang utama untuk seluruh aktivitas pelanggan di sistem penjualan online.

<img width="604" height="431" alt="Registrasi Pelanggan" src="https://github.com/user-attachments/assets/b86bbd36-ddf9-42f4-88d6-7e767924f2e8" />

2. **Login**

Pada diagram ini, pelanggan yang telah terdaftar memasukkan username dan password pada form login. Sistem melakukan proses otentikasi dengan mencocokkan data input terhadap data di database. Jika cocok, sistem mengizinkan akses dan mengarahkan pelanggan ke dashboard atau halaman utama. Jika tidak, sistem memberikan notifikasi kesalahan. Sequence ini memastikan hanya pengguna terdaftar yang dapat mengakses fitur-fitur khusus pelanggan seperti pembelian dan pelacakan pesanan.

<img width="664" height="432" alt="Login Pelanggan" src="https://github.com/user-attachments/assets/e6502ada-e173-4594-8066-0f48f40682e2" />

3. **Tambah Produk ke Keranjang**

Pelanggan memilih produk dari katalog dan menambahkan produk tersebut ke dalam keranjang belanja. Sistem akan mencatat ID produk, kuantitas, dan ID pelanggan ke dalam tabel Keranjang. Jika produk yang sama sudah ada, sistem akan memperbarui jumlahnya, bukan menambahkan baris baru. Interaksi ini memungkinkan pelanggan menyusun daftar belanja sebelum memproses pembayaran, dan menyederhanakan langkah pembelian berikutnya.

<img width="739" height="523" alt="MenambahProdukkeKeranjang drawio" src="https://github.com/user-attachments/assets/0e292352-313d-459e-9e03-2558ff450c8c" />

4. **Proses Checkout**

Saat pelanggan memutuskan untuk membeli produk dalam keranjang, ia melakukan proses checkout. Sistem akan menampilkan ringkasan isi keranjang, total harga, dan pilihan metode pengiriman serta pembayaran. Setelah pelanggan mengisi data yang dibutuhkan dan menyetujui pesanan, sistem mencatat transaksi ke dalam entitas Pesanan, kemudian menghasilkan invoice. Ini adalah titik transisi dari proses perencanaan pembelian ke tahap pembayaran aktual.

<img width="924" height="431" alt="CheckOutProcess drawio" src="https://github.com/user-attachments/assets/a4918188-345e-461f-ae92-242da97b76f6" />

5. **Proses Pembayaran**

Dalam diagram ini, pelanggan memilih metode pembayaran (transfer bank). Pelanggan diwajibkan melakukan transfer sesuai nominal total belanja dan menyimpan bukti pembayaran. Sistem akan menunggu proses unggah bukti sebelum status pesanan berubah. Proses ini penting karena menjadi validasi bahwa pelanggan telah menyelesaikan kewajiban pembayaran dan admin dapat melanjutkan proses pengiriman.

<img width="965" height="383" alt="PaymentProcess drawio" src="https://github.com/user-attachments/assets/3f26cd7d-35ab-47ec-94c5-bb88bbb69bd8" />

6. **Buat Pesanan**

Sequence diagram Buat Pesanan menggambarkan alur saat pelanggan menyelesaikan pemesanan setelah memilih produk. Pelanggan mengirimkan detail pesanan ke sistem, seperti jumlah, alamat, dan metode pembayaran. Sistem kemudian memvalidasi data, mengecek ketersediaan produk, dan jika valid, sistem membuat data pesanan baru dengan status “Menunggu Pembayaran”. Setelah itu, sistem menampilkan nomor pesanan dan instruksi pembayaran kepada pelanggan, termasuk nominal dan rekening tujuan. Proses ini ditutup dengan sistem menunggu bukti pembayaran dari pelanggan untuk melanjutkan ke tahap verifikasi oleh admin.

<img width="965" height="473" alt="createOrder drawio" src="https://github.com/user-attachments/assets/faf86153-efee-47e2-82de-e5add8570f3e" />

7. **Upload Bukti Pembayaran**

Pelanggan yang telah melakukan pembayaran akan mengunggah foto bukti transfer ke sistem. Sistem akan menyimpan bukti ini dan mengaitkannya dengan PesananID terkait. Setelah bukti diterima, sistem akan memberi notifikasi kepada admin bahwa ada pembayaran yang harus diverifikasi. Tahapan ini memastikan adanya jejak digital atar transaksi keuangan dan menjadi dasar proses verifikasi di pihak admin.

<img width="895" height="401" alt="UploadBuktiPembayaran drawio" src="https://github.com/user-attachments/assets/f0bdd971-87cc-4ebf-94dc-8de14082b848" />

8. **Lihat Detail Produk**

Diagram ini menggambarkan alur interaksi saat pelanggan ingin melihat detail dari produk yang telah dibeli. Proses dimulai ketika pelanggan membuka halaman produk melalui antarmuka pengguna. Antarmuka pengguna kemudian mengirim permintaan getDetailProduk(ProdukID) ke Produk Controller. Controller akan meneruskan permintaan ini ke database dengan memanggil fungsi getProdukByID(ProdukID). Setelah data produk berhasil diperoleh, database mengembalikan informasi produk ke controller, yang kemudian meneruskannya ke antarmuka pengguna. Terakhir, informasi ini ditampilkan kepada pelanggan dalam bentuk tampilan detail produk.

<img width="894" height="401" alt="viewproductdetail drawio" src="https://github.com/user-attachments/assets/3dd2360e-7d86-4e8a-a32b-20a381d52765" />

9. **Kirim Ulasan**

Diagram ini menunjukkan proses saat pelanggan mengirimkan ulasan dan rating terhadap produk yang telah dibeli. Pelanggan memulai dengan menulis ulasan dan rating melalui antarmuka pengguna, yang kemudian mengirimkan data ulasan  (PelangganID, ProductID, Ulasan, Rating) ke Produk Controller melalui fungsi submitUlasan. Controller akan melakukan dua operasi ke database: pertama, menyimpan ulasan dengan insertUlasan(Data) dan mendapatkan UlasanID sebagai hasilnya; kedua, memperbarui rating produk melalui UpdateRatingProduk(ProdukID). Setelah kedua operasi berhasil, controller mengirim respons ke antarmuka pengguna berupa konfirmasi bahwa ulasan berhasil disimpan, lalu antarmuka menampilkan pesan terima kasih kepada pelanggan.

<img width="895" height="401" alt="submitReview drawio" src="https://github.com/user-attachments/assets/1d8dc2c4-eeba-42b5-b430-89756d584118" />

10. **Lihat Detail Pesanan**

Sequence diagram ini mendeskripsikan proses saat pelanggan ingin melihat detail dari suatu pesanan tertentu. Pelanggan menginisiasi dengan memilih detail pesanan di antarmuka pengguna. Permintaan getDetailPesanan(PesananID) dikirimkan ke Pesanan Controller, yang kemudian meneruskan ke database melalui fungsi getDetailPesananByID(PesananID). Database mengembalikan data lengkap mengenai pesanan tersebut, termasuk status dan rincian pengiriman. Controller meneruskan data ini ke antarmuka pengguna, yang kemudian menampilkan informasi kepada pelanggan.

<img width="894" height="401" alt="vieworderdetails drawio" src="https://github.com/user-attachments/assets/fd55a3a4-021c-44ca-91c1-2f437a51175b" />

11. **Lihat Riwayat Pesanan**

Diagram ini menjelaskan proses pelanggan saat mengakses riwayat pemesanan. Proses diawali saat pelanggan memilih opsi “lacak pesanan” pada antarmuka. Antarmuka pengguna mengirim permintaan getPesananByPelangganID(PelangganID) ke Pesanan Controller. Controller kemudian mengakses database melalui fungsi getPesananHistory(PesananID) untuk mengambil daftar seluruh pesanan yang pernah dilakukan pelanggan tersebut. Setelah data diperoleh, controller mengirimkan list pesanan kembali ke antarmuka pengguna, yang kemudian menampilkannya dalam bentuk riwayat pemesanan kepada pelanggan.

<img width="894" height="401" alt="vieworderHistory drawio" src="https://github.com/user-attachments/assets/fb041b04-72f1-459e-be41-f35e2cd67324" />
