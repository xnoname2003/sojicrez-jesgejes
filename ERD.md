---
## Entity Relationship Diagram Sistem Penjualan Kripik Isal
<img width="450" alt="image" src="https://github.com/user-attachments/assets/fa8a98be-47a5-4561-8206-e2db64836140" />

---
## Tabel Relasi Sistem Penjualan Kripik Isal
<img width="450" alt="image" src="https://github.com/user-attachments/assets/377c7579-391a-4bc8-b326-ab1c1da10b8d" />

---
## Penjelasan Relasi Antar Tabel
).

| No | Entitas 1           | Entitas 2           | Tipe Relasi   | Penjelasan                                                                 |
|----|---------------------|---------------------|---------------|----------------------------------------------------------------------------|
| 1  | Trx_User            | Ms_Pelanggan        | One-to-One    | Setiap user yang berperan sebagai pelanggan memiliki satu data profil pelanggan |
| 2  | Trx_User            | Ms_Admin            | One-to-One    | Setiap user yang berperan sebagai admin memiliki satu data profil admin   |
| 3  | Trx_User            | Ms_Role             | Many-to-One   | Setiap user memiliki satu role, misalnya admin atau pelanggan             |
| 4  | Trx_Alamat          | Ms_Pelanggan        | Many-to-One   | Pelanggan bisa memiliki banyak alamat                                     |
| 5  | Trx_Alamat          | Ms_Provinsi         | Many-to-One   | Alamat terhubung ke satu provinsi                                         |
| 6  | Trx_Alamat          | Ms_Kota             | Many-to-One   | Alamat terhubung ke satu kota                                             |
| 7  | Trx_Alamat          | Ms_Kecamatan        | Many-to-One   | Alamat terhubung ke satu kecamatan                                        |
| 8  | Trx_Alamat          | Ms_Kelurahan        | Many-to-One   | Alamat terhubung ke satu kelurahan                                        |
| 9  | Trx_Foto_Produk     | Ms_Produk           | Many-to-One   | Satu produk bisa memiliki banyak foto                                     |
| 10 | Trx_Layanan_Ekspedisi | Ms_Ekspedisi      | Many-to-One   | Satu ekspedisi bisa punya banyak layanan                                  |
| 11 | Trx_Keranjang       | Ms_Pelanggan        | Many-to-One   | Pelanggan bisa memiliki banyak item keranjang                             |
| 12 | Trx_Keranjang       | Ms_Produk           | Many-to-One   | Setiap item keranjang mengacu ke satu produk                              |
| 13 | Trx_Keranjang       | Trx_Checkout        | Many-to-One   | Item keranjang bisa dihubungkan ke satu transaksi checkout (nullable)     |
| 14 | Trx_Checkout        | Ms_Pelanggan        | Many-to-One   | Pelanggan bisa melakukan banyak checkout                                  |
| 15 | Trx_Checkout        | Ms_Ekspedisi        | Many-to-One   | Setiap transaksi checkout menggunakan satu ekspedisi                      |
| 16 | Trx_Checkout        | Ms_Admin            | Many-to-One   | Admin sebagai updater transaksi (pada kolom `updated_by`)                 |
| 17 | Trx_Payment         | Trx_Checkout        | One-to-One    | Setiap transaksi hanya memiliki satu pembayaran                           |
| 18 | Trx_Payment         | Ms_Payments         | Many-to-One   | Pembayaran dilakukan menggunakan salah satu metode dari Ms_Payments       |
| 19 | Trx_Ulasan          | Ms_Pelanggan        | Many-to-One   | Pelanggan dapat memberikan beberapa ulasan                                |
| 20 | Trx_Ulasan          | Ms_Produk           | Many-to-One   | Produk bisa memiliki banyak ulasan                                        |
| 21 | Trx_Komplain        | Ms_Pelanggan        | Many-to-One   | Pelanggan dapat mengajukan banyak komplain                                |
| 22 | Trx_Komplain        | Trx_Checkout        | Many-to-One   | Komplain berhubungan dengan satu transaksi checkout                       |
| 23 | Trx_Komplain_Chat   | Trx_Komplain        | Many-to-One   | Satu komplain dapat memiliki banyak pesan chat                            |
| 24 | Trx_Komplain_Chat   | Ms_Admin            | Many-to-One   | Chat dapat dikirim oleh admin (nullable)                                  |
| 25 | Trx_Komplain_Chat   | Ms_Pelanggan        | Many-to-One   | Chat dapat dikirim oleh pelanggan (nullable)                              |

---
## Tabel Master dan Relasi Sistem Penjualan Kripik Isal

### 1. Table Master
- Master Pelanggan (Ms_Pelanggan)
  ``` sql
  CREATE TABLE Ms_Pelanggan (
    idPelanggan CHAR(6) PRIMARY KEY,
    username VARCHAR(50),
    email VARCHAR(100),
    password VARCHAR(255),
    no_hp BIGINT,
    nama_pelanggan VARCHAR(100),
    foto_pelanggan VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;

  ```
  | Nama Atribut     | Tipe Data        | Keterangan                      |
  |------------------|------------------|---------------------------------|
  | idPelanggan      | char(6) (PK)     | ID unik pelanggan               |
  | username         | varchar(50)      | Username pelanggan              |
  | email            | varchar(100)     | Email pelanggan                 |
  | password         | varchar(255)     | Password pelanggan              |
  | no_hp            | bigint           | Nomor telepon pelanggan         |
  | nama_pelanggan   | varchar(100)     | Nama lengkap pelanggan          |
  | foto_pelanggan   | varchar(255)     | Foto profil pelanggan           |
  | created_at       | timestamp        | Waktu pembuatan akun pelanggan  |

- Master Admin (Ms_Admin)
  ``` sql
  CREATE TABLE Ms_Admin (
    idAdmin CHAR(6) PRIMARY KEY,
    username VARCHAR(50),
    email VARCHAR(100),
    password VARCHAR(255),
    no_hp BIGINT,
    nama_admin VARCHAR(100),
    foto_admin VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut   | Tipe Data       | Keterangan                     |
  |----------------|------------------|--------------------------------|
  | idAdmin        | char(6) (PK)     | ID unik admin                  |
  | username       | varchar(50)      | Username admin                 |
  | email          | varchar(100)     | Email admin                    |
  | password       | varchar(255)     | Password admin                 |
  | no_hp          | bigint           | Nomor telepon admin            |
  | nama_admin     | varchar(100)     | Nama lengkap admin             |
  | foto_admin     | varchar(255)     | Foto profil admin              |
  | created_at     | timestamp        | Waktu pembuatan akun admin     |
  
- Master Produk (Ms_Produk)
  ``` sql
  CREATE TABLE Ms_Produk (
    idProduk CHAR(6) PRIMARY KEY,
    nama_produk VARCHAR(100),
    deskripsi VARCHAR(255),
    varian_rasa VARCHAR(100),
    ukuran ENUM('50','75','125','250','500'),
    harga INT,
    mfg_date DATE,
    exp_date DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut   | Tipe Data            | Keterangan                                      |
  |----------------|----------------------|-------------------------------------------------|
  | idProduk       | char(6) (PK)         | ID unik produk                                  |
  | nama_produk    | varchar(100)         | Nama produk                                     |
  | deskripsi      | varchar(255)         | Deskripsi produk                                |
  | varian_rasa    | varchar(100)         | Varian rasa produk                              |
  | ukuran         | enum                 | Ukuran produk dalam gram ('50', '75', '125', '250', '500') |
  | harga          | int                  | Harga produk                                    |
  | mfg_date       | date                 | Tanggal produksi produk                         |
  | exp_date       | date                 | Tanggal kadaluarsa produk                       |
  | created_at     | timestamp            | Waktu pembuatan produk                          |

- Master Ekspedisi (Ms_Ekspedisi)
  ``` sql
  CREATE TABLE Ms_Ekspedisi (
    idEkspedisi CHAR(6) PRIMARY KEY,
    nama_ekspedisi VARCHAR(100),
    kode_ekspedisi VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data        | Keterangan                     |
  |------------------|------------------|--------------------------------|
  | idEkspedisi      | char(6) (PK)     | ID unik ekspedisi              |
  | nama_ekspedisi   | varchar(100)     | Nama ekspedisi                 |
  | kode_ekspedisi   | varchar(255)     | Kode ekspedisi                 |
  | created_at       | timestamp        | Waktu pembuatan ekspedisi      |

- Master Payments (Ms_Payments)
   ``` sql
  CREATE TABLE Ms_Payments (
    idPayment CHAR(6) PRIMARY KEY,
    nama_payment VARCHAR(100),
    va_payment VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut   | Tipe Data        | Keterangan                         |
  |----------------|------------------|------------------------------------|
  | idPayment      | char(6) (PK)     | ID unik metode pembayaran          |
  | nama_payment   | varchar(100)     | Nama jasa pembayaran               |
  | va_payment     | varchar(255)     | Rekening atau virtual account pembayaran |
  | created_at     | timestamp        | Waktu pembuatan pembayaran         |


---
### 2. Table Relasi
- Relasi Alamat (Trx_Alamat)
  ``` sql
  CREATE TABLE Trx_Alamat (
    idTrxAlamat CHAR(6) PRIMARY KEY,
    idPelanggan CHAR(6),
    nama_lengkap VARCHAR(255),
    no_hp BIGINT,
    provinsi VARCHAR(100),
    kota VARCHAR(100),
    kecamatan VARCHAR(100),
    kode_pos INT,
    nama_jalan VARCHAR(255),
    detail_lainnya VARCHAR(255),
    tandai ENUM('rumah','kantor'),
    isAlamatPribadi BOOLEAN DEFAULT FALSE,
    isAlamatUtama BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data          | Keterangan                                   |
  |------------------|--------------------|----------------------------------------------|
  | idTrxAlamat      | char(6) (PK)       | ID unik alamat                               |
  | idPelanggan      | char(6) (FK)       | ID unik pelanggan                            |
  | nama_lengkap     | varchar(255)       | Nama lengkap penerima paket                   |
  | no_hp            | bigint             | No telepon penerima                          |
  | provinsi         | varchar(100)       | Provinsi penerima                            |
  | kota             | varchar(100)       | Kota penerima                                |
  | kecamatan        | varchar(100)       | Kecamatan penerima                           |
  | kode_pos         | int                | Kode pos penerima                            |
  | nama_jalan       | varchar(255)       | Nama jalan penerima                          |
  | detail_lainnya   | varchar(255)       | Detail lainnya alamat penerima               |
  | tandai           | enum               | Tandai alamat sebagai apa (rumah/kantor)    |
  | isAlamatPribadi  | boolean            | Validasi sebagai alamat pribadi              |
  | isAlamatUtama    | boolean            | Validasi sebagai alamat utama                |
  | created_at       | timestamp          | Waktu pembuatan alamat                       |
  
- Relasi Foto Produk (Trx_Foto_Produk)
  ``` sql
  CREATE TABLE Trx_Foto_Produk (
    idTrxFotoProduk CHAR(6) PRIMARY KEY,
    idProduk CHAR(6),
    img_produk VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idProduk) REFERENCES Ms_Produk(idProduk) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data        | Keterangan                   |
  |------------------|------------------|------------------------------|
  | idTrxFotoProduk  | char(6) (PK)     | ID unik foto produk          |
  | idProduk         | char(6) (FK)     | ID unik produk               |
  | img_produk       | varchar(255)     | Gambar produk                |
  | created_at       | timestamp        | Waktu pembuatan gambar produk|

- Relasi Layanan Ekspedisi (Trx_Layanan_Ekspedisi)
  ``` sql
  CREATE TABLE Trx_Layanan_Ekspedisi (
    idTrxLayananEkspedisi CHAR(6) PRIMARY KEY,
    idEkspedisi CHAR(6),
    nama_layanan_ekspedisi VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idEkspedisi) REFERENCES Ms_Ekspedisi(idEkspedisi) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut           | Tipe Data        | Keterangan                     |
  |-----------------------|------------------|--------------------------------|
  | idTrxLayananEkspedisi | char(6) (PK)     | ID unik layanan ekspedisi      |
  | idEkspedisi           | char(6) (FK)     | ID unik ekspedisi              |
  | nama_layanan_ekspedisi| varchar(255)     | Nama layanan ekspedisi         |
  | created_at            | timestamp        | Waktu pembuatan layanan ekspedisi |

- Relasi Keranjang (Trx_Keranjang)
  ``` sql
  CREATE TABLE Trx_Keranjang (
    idTrxKeranjang CHAR(6) PRIMARY KEY,
    idPelanggan CHAR(6),
    idProduk CHAR(6),
    idTrxCheckout CHAR(6),
    jumlah INT,
    harga_unit DECIMAL(10,2),
    subtotal DECIMAL(10,2),
    isCheckedOut BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE,
    FOREIGN KEY (idProduk) REFERENCES Ms_Produk(idProduk) ON DELETE CASCADE,
    FOREIGN KEY (idTrxCheckout) REFERENCES Trx_Checkout(idTrxCheckout) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut    | Tipe Data        | Keterangan                            |
  |-----------------|------------------|-------------------------------------|
  | idTrxKeranjang  | char(6) (PK)     | ID unik keranjang                   |
  | idPelanggan     | char(6) (FK)     | ID unik pelanggan                   |
  | idProduk       | char(6) (FK)     | ID unik produk                      |
  | idTrxCheckout   | char(6) (FK)     | ID unik Checkout                    |
  | jumlah         | int              | Jumlah produk                      |
  | harga_unit     | decimal(10,2)    | Harga per produk                   |
  | subtotal       | decimal(10,2)    | Total harga_unit * jumlah          |
  | isCheckedOut   | boolean          | Validasi tombol checkout ditekan   |
  | created_at     | timestamp        | Waktu pembuatan keranjang          |

- Relasi Checkout (Trx_Checkout)
  ``` sql
  CREATE TABLE Trx_Checkout (
    idTrxCheckout CHAR(6) PRIMARY KEY,
    idPelanggan CHAR(6),
    idEkspedisi CHAR(6),
    no_order CHAR(19) UNIQUE NOT NULL,
    status ENUM('pending','confirmed','processing','shipped','delivered','cancelled') DEFAULT 'pending',
    subtotal DECIMAL(12,2),
    discount_amount DECIMAL(10,2) DEFAULT 0,
    total_amount DECIMAL(12,2),
    isPurchaseWithSistem BOOLEAN DEFAULT TRUE,
    no_resi VARCHAR(100),
    updated_by CHAR(6),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE,
    FOREIGN KEY (idEkspedisi) REFERENCES Ms_Ekspedisi(idEkspedisi) ON DELETE CASCADE,
    FOREIGN KEY (updated_by) REFERENCES Ms_Admin(idAdmin) ON DELETE SET NULL
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut        | Tipe Data          | Keterangan                                                                                 |
  |---------------------|--------------------|--------------------------------------------------------------------------------------------|
  | idTrxCheckout       | char(6) (PK)       | ID unik Checkout                                                                           |
  | idPelanggan         | char(6) (FK)       | ID unik pelanggan                                                                         |
  | idEkspedisi         | char(6) (FK)       | ID unik ekspedisi                                                                         |
  | no_order            | char(19)           | Nomor unik Pesanan                                                                        |
  | status              | enum               | Status Pesanan ('pending', 'confirmed', 'processing', 'shipped', 'delivered', 'cancelled')|
  | subtotal            | decimal(12,2)      | Subtotal pesanan                                                                         |
  | discount_amount     | decimal(10,2)      | Harga diskon (default = 0)                                                               |
  | total_amount        | decimal(12,2)      | Total harga (subtotal - discount_amount)                                                 |
  | isPurchaseWithSistem| boolean            | Validasi pembelian melalui sistem                                                        |
  | no_resi             | varchar(100)       | Nomor resi pengiriman pesanan                                                        |
  | updated_by          | char(6) (FK)       | Pesanan diupdate oleh admin                                                              |
  | created_at          | timestamp          | Waktu pembuatan pesanan                                                                   |
  | updated_at          | timestamp          | Waktu update pesanan                                                                      |

- Relasi Payment (Trx_Payment)
  ``` sql
  CREATE TABLE Trx_Payment (
    idTrxPayment CHAR(6) PRIMARY KEY,
    idTrxCheckout CHAR(6),
    idPayment CHAR(6),
    amount DECIMAL(12,2) NOT NULL,
    status ENUM('pending','paid','failed','refunded') DEFAULT 'pending',
    payment_proof VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idTrxCheckout) REFERENCES Trx_Checkout(idTrxCheckout) ON DELETE CASCADE,
    FOREIGN KEY (idPayment) REFERENCES Ms_Payments(idPayment) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut    | Tipe Data        | Keterangan                                      |
  |-----------------|------------------|-------------------------------------------------|
  | idTrxPayment    | char(6) (PK)     | ID unik pembayaran                              |
  | idTrxCheckout   | char(6) (FK)     | ID unik Checkout                                |
  | idPayment       | char(6) (FK)     | ID unik metode pembayaran                        |
  | amount          | decimal(12,2)    | Total harga                                     |
  | status          | enum             | Status pembayaran ('pending', 'paid', 'failed', 'refunded') |
  | payment_proof   | varchar(255)     | Bukti pembayaran                                |
  | created_at      | timestamp        | Waktu pembuatan pembayaran                       |
  | updated_at      | timestamp        | Waktu update pembayaran                          |

- Relasi Ulasan (Trx_Ulasan)
  ``` sql
  CREATE TABLE Trx_Ulasan (
    idTrxUlasan CHAR(6) PRIMARY KEY,
    idPelanggan CHAR(6),
    idProduk CHAR(6),
    rating INT COMMENT '1 to 5',
    isi_ulasan TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE,
    FOREIGN KEY (idProduk) REFERENCES Ms_Produk(idProduk) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut  | Tipe Data      | Keterangan             |
  |---------------|----------------|------------------------|
  | idTrxUlasan   | char(6) (PK)   | ID unik ulasan         |
  | idPelanggan   | char(6) (FK)   | ID unik pelanggan      |
  | idProduk      | char(6) (FK)   | ID unik produk         |
  | rating        | int            | Rating produk          |
  | isi_ulasan    | text           | Isi ulasan             |
  | created_at    | timestamp      | Waktu pembuatan ulasan |

- Relasi Komplain (Trx_Komplain)
  ``` sql
  CREATE TABLE Trx_Komplain (
    idTrxKomplain CHAR(6) PRIMARY KEY,
    idPelanggan CHAR(6),
    idTrxCheckout CHAR(6),
    judul_komplain VARCHAR(100),
    status ENUM('baru','diproses','selesai') DEFAULT 'baru',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE,
    FOREIGN KEY (idTrxCheckout) REFERENCES Trx_Checkout(idTrxCheckout) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut    | Tipe Data        | Keterangan                 |
  |-----------------|------------------|----------------------------|
  | idTrxKomplain   | char(6) (PK)     | ID unik komplain           |
  | idPelanggan     | char(6) (FK)     | ID unik pelanggan          |
  | idTrxCheckout   | char(6) (FK)     | ID unik Checkout           |
  | judul_komplain  | varchar(100)     | Judul komplain             |
  | status          | enum             | Status komplain            |
  | created_at      | timestamp        | Waktu pembuatan komplain   |
  | updated_at      | timestamp        | Waktu update komplain      |

- Relasi Komplain Chat (Trx_Komplain_Chat)
  ``` sql
  CREATE TABLE Trx_Komplain_Chat (
    idTrxKomplainChat CHAR(6) PRIMARY KEY,
    idTrxKomplain CHAR(6),
    idAdmin CHAR(6),
    idPelanggan CHAR(6),
    isi_pesan TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idTrxKomplain) REFERENCES Trx_Komplain(idTrxKomplain) ON DELETE CASCADE,
    FOREIGN KEY (idAdmin) REFERENCES Ms_Admin(idAdmin) ON DELETE CASCADE,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data      | Keterangan                    |
  |------------------|----------------|-------------------------------|
  | idTrxKomplainChat| char(6) (PK)   | ID unik komplain chat          |
  | idTrxKomplain    | char(6) (FK)   | ID unik komplain               |
  | idAdmin          | char(6) (FK)   | ID unik admin                  |
  | idPelanggan      | char(6) (FK)   | ID unik pelanggan              |
  | isi_pesan        | text           | Isi pesan komplain             |
  | created_at       | timestamp      | Waktu pembuatan komplain chat  |
  | updated_at       | timestamp      | Waktu update komplain chat     |
