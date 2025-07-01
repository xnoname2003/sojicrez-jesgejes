---
## Entity Relationship Diagram Sistem Penjualan Kripik Isal
<img width="450" alt="image" src="https://github.com/user-attachments/assets/33a52cb6-a2f0-4d90-906f-8d1606907f85" />

---
## Tabel Relasi Sistem Penjualan Kripik Isal
<img width="450" alt="image" src="https://github.com/user-attachments/assets/6eb70d41-ce18-4a1c-9245-b759c569e556" />

---
## Penjelasan Relasi Antar Tabel

| No | Entitas 1            | Entitas 2            | Tipe Relasi    | Penjelasan                                                                 |
|----|----------------------|----------------------|----------------|---------------------------------------------------------------------------|
| 1  | Trx_User             | Ms_Role              | Many-to-One    | Setiap user memiliki satu role tertentu.                                  |
| 2  | Ms_Pelanggan         | Trx_User             | One-to-One     | Setiap pelanggan adalah satu user (unik), referensi dari Trx_User.        |
| 3  | Ms_Admin             | Trx_User             | One-to-One     | Setiap admin adalah satu user (unik), referensi dari Trx_User.            |
| 4  | Trx_Alamat           | Ms_Pelanggan         | Many-to-One    | Satu pelanggan bisa punya banyak alamat.                                  |
| 5  | Trx_Alamat           | Ms_Provinsi          | Many-to-One    | Alamat merujuk ke satu provinsi.                                          |
| 6  | Trx_Alamat           | Ms_Kota              | Many-to-One    | Alamat merujuk ke satu kota.                                              |
| 7  | Trx_Alamat           | Ms_Kecamatan         | Many-to-One    | Alamat merujuk ke satu kecamatan.                                         |
| 8  | Trx_Alamat           | Ms_Kelurahan         | Many-to-One    | Alamat merujuk ke satu kelurahan.                                         |
| 9  | Trx_Foto_Produk      | Ms_Produk            | Many-to-One    | Satu produk bisa punya banyak foto.                                       |
| 10 | Trx_Layanan_Ekspedisi| Ms_Ekspedisi         | Many-to-One    | Satu ekspedisi bisa punya banyak layanan.                                 |
| 11 | Trx_Keranjang        | Trx_User             | Many-to-One    | Satu user bisa punya banyak item keranjang.                               |
| 12 | Trx_Keranjang        | Ms_Produk            | Many-to-One    | Setiap item keranjang merujuk ke satu produk.                             |
| 13 | Trx_Keranjang        | Trx_Checkout         | Many-to-One    | Item keranjang bisa dikaitkan dengan satu transaksi checkout.             |
| 14 | Trx_Checkout         | Trx_User             | Many-to-One    | Satu user bisa memiliki banyak transaksi checkout.                         |
| 15 | Trx_Checkout         | Ms_Ekspedisi         | Many-to-One    | Satu transaksi checkout menggunakan satu ekspedisi.                        |
| 16 | Trx_Checkout         | Trx_User (updated_by)| Many-to-One    | Transaksi bisa diubah oleh satu user (admin atau sistem).                 |
| 17 | Trx_Payment          | Trx_Checkout         | One-to-One     | Satu pembayaran terkait dengan satu transaksi checkout.                   |
| 18 | Trx_Payment          | Ms_Payments          | Many-to-One    | Satu metode pembayaran bisa digunakan di banyak transaksi.                |
| 19 | Trx_Ulasan           | Trx_User             | Many-to-One    | Satu user bisa memberi banyak ulasan.                                     |
| 20 | Trx_Ulasan           | Ms_Produk            | Many-to-One    | Ulasan diberikan untuk satu produk tertentu.                              |
| 21 | Trx_Komplain         | Trx_User             | Many-to-One    | Satu user bisa membuat banyak komplain.                                   |
| 22 | Trx_Komplain         | Trx_Checkout         | Many-to-One    | Komplain dikaitkan dengan satu transaksi checkout.                         |
| 23 | Trx_Komplain_Chat    | Trx_Komplain         | Many-to-One    | Banyak chat bisa dikaitkan ke satu komplain.                              |
| 24 | Trx_Komplain_Chat    | Trx_User             | Many-to-One    | Pesan chat dikirim oleh satu user (null jika anonim/sistem).              |

---
## Tabel Master dan Relasi Sistem Penjualan Kripik Isal

### 1. Table Master
- Master Role (Ms_Role)
  ``` sql
  CREATE TABLE Ms_Role (
    idRole CHAR(6) PRIMARY KEY,
    nama_role VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;

  ```
  | Nama Atribut | Tipe Data    | Keterangan           |
  | ------------ | ------------ | -------------------- |
  | idRole       | CHAR(6)      | Primary key          |
  | nama\_role   | VARCHAR(100) | Nama peran pengguna  |
  | created\_at  | TIMESTAMP    | Waktu pembuatan data |

- Master Pelanggan (Ms_Pelanggan)
  ``` sql
  CREATE TABLE Ms_Pelanggan (
    idPelanggan CHAR(6) PRIMARY KEY,
    idTrxUser CHAR(6) UNIQUE,
    nama_pelanggan VARCHAR(100),
    no_hp BIGINT,
    foto_pelanggan VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;

  ```
  | Nama Atribut    | Tipe Data    | Keterangan                                  |
  | --------------- | ------------ | ------------------------------------------- |
  | idPelanggan     | CHAR(6)      | Primary key                                 |
  | idTrxUser       | CHAR(6)      | Foreign key ke `Trx_User.idTrxUser`, UNIQUE |
  | nama\_pelanggan | VARCHAR(100) | Nama pelanggan                              |
  | no\_hp          | BIGINT       | Nomor HP                                    |
  | foto\_pelanggan | VARCHAR(255) | Lokasi foto pelanggan                       |
  | created\_at     | TIMESTAMP    | Waktu pembuatan data                        |

- Master Admin (Ms_Admin)
  ``` sql
  CREATE TABLE Ms_Admin (
    idAdmin CHAR(6) PRIMARY KEY,
    idTrxUser CHAR(6) UNIQUE,
    nama_admin VARCHAR(255),
    no_hp BIGINT,
    foto_admin VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut | Tipe Data    | Keterangan                                  |
  | ------------ | ------------ | ------------------------------------------- |
  | idAdmin      | CHAR(6)      | Primary key                                 |
  | idTrxUser    | CHAR(6)      | Foreign key ke `Trx_User.idTrxUser`, UNIQUE |
  | nama\_admin  | VARCHAR(255) | Nama admin                                  |
  | no\_hp       | BIGINT       | Nomor HP                                    |
  | foto\_admin  | VARCHAR(255) | Lokasi foto admin                           |
  | created\_at  | TIMESTAMP    | Waktu pembuatan data                        |

  
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

- Master Provinsi (Ms_Provinsi)
   ``` sql
  CREATE TABLE Ms_Provinsi (
    idProvinsi CHAR(6) PRIMARY KEY,
    nama_provinsi VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data    | Keterangan           |
  | ------------     | ------------ | -------------------- |
  | idProvinsi       | CHAR(6)      | Primary key          |
  | nama_provinsi    | VARCHAR(100) | Nama Provinsi        |
  | created_at       | TIMESTAMP    | Waktu pembuatan data |

- Master Kota (Ms_Kota)
   ``` sql
  CREATE TABLE Ms_Kota (
    idKota CHAR(6) PRIMARY KEY,
    nama_kota VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data    | Keterangan           |
  | ------------     | ------------ | -------------------- |
  | idKota           | CHAR(6)      | Primary key          |
  | nama_kota        | VARCHAR(100) | Nama Kota            |
  | created_at       | TIMESTAMP    | Waktu pembuatan data |

- Master Kecamatan (Ms_Kecamatan)
   ``` sql
  CREATE TABLE Ms_Kecamatan (
    idKecamatan CHAR(6) PRIMARY KEY,
    nama_kecamatan VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data    | Keterangan           |
  | ------------     | ------------ | -------------------- |
  | idKecamatan      | CHAR(6)      | Primary key          |
  | nama_kecamatan   | VARCHAR(100) | Nama Kecamatan       |
  | created_at       | TIMESTAMP    | Waktu pembuatan data |

- Master Kelurahan (Ms_Kelurahan)
   ``` sql
  CREATE TABLE Ms_Kelurahan (
    idKelurahan CHAR(6) PRIMARY KEY,
    nama_kelurahan VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data    | Keterangan           |
  | ------------     | ------------ | -------------------- |
  | idKelurahan      | CHAR(6)      | Primary key          |
  | nama_kelurahan   | VARCHAR(100) | Nama Kelurahan       |
  | created_at       | TIMESTAMP    | Waktu pembuatan data |

---
### 2. Table Relasi
- Relasi User (Trx_User)
   ``` sql
  CREATE TABLE Trx_User (
    idTrxUser CHAR(6) PRIMARY KEY,
    username VARCHAR(100) UNIQUE,
    email VARCHAR(100),
    password VARCHAR(255),
    idRole CHAR(6),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idRole) REFERENCES Ms_Role(idRole) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut | Tipe Data    | Keterangan                                 |
  |--------------|--------------|--------------------------------------------|
  | idTrxUser    | CHAR(6)      | Primary key                                |
  | username     | VARCHAR(255) | Username, harus unik (UNIQUE)              |
  | email        | VARCHAR(255) | Email                                      |
  | password     | VARCHAR(255) | Password (hash)                            |
  | idRole       | CHAR(6)      | Foreign key ke `Ms_Role.idRole`            |
  | created_at   | TIMESTAMP    | Waktu pembuatan data                       |

- Relasi Alamat (Trx_Alamat)
  ``` sql
  CREATE TABLE Trx_Alamat (
    idTrxAlamat CHAR(6) PRIMARY KEY,
    idPelanggan CHAR(6),
    nama_lengkap VARCHAR(255),
    no_hp BIGINT,
    idProvinsi CHAR(6),
    idKota CHAR(6),
    idKecamatan CHAR(6),
    idKelurahan CHAR(6),
    kode_pos INT,
    nama_jalan VARCHAR(255),
    detail_lainnya VARCHAR(255),
    tandai ENUM('rumah','kantor'),
    isAlamatPribadi BOOLEAN DEFAULT FALSE,
    isAlamatUtama BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idPelanggan) REFERENCES Ms_Pelanggan(idPelanggan) ON DELETE CASCADE,
    FOREIGN KEY (idProvinsi) REFERENCES Ms_Provinsi(idProvinsi) ON DELETE CASCADE,
    FOREIGN KEY (idKota) REFERENCES Ms_Kota(idKota) ON DELETE CASCADE,
    FOREIGN KEY (idKecamatan) REFERENCES Ms_Kecamatan(idKecamatan) ON DELETE CASCADE,
    FOREIGN KEY (idKelurahan) REFERENCES Ms_Kelurahan(idKelurahan) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut    | Tipe Data    | Keterangan                    |
  | --------------- | ------------ | ----------------------------- |
  | idTrxAlamat     | CHAR(6)      | Primary key                   |
  | idPelanggan     | CHAR(6)      | Foreign key ke `Ms_Pelanggan` |
  | nama_lengkap    | VARCHAR(255) | Nama penerima                 |
  | no_hp           | BIGINT       | Nomor HP                      |
  | idProvinsi      | CHAR(6)      | FK ke `Ms_Provinsi`           |
  | idKota          | CHAR(6)      | FK ke `Ms_Kota`               |
  | idKecamatan     | CHAR(6)      | FK ke `Ms_Kecamatan`          |
  | idKelurahan     | CHAR(6)      | FK ke `Ms_Kelurahan`          |
  | kode_pos        | INT          | Kode pos                      |
  | nama_jalan      | VARCHAR(255) | Alamat jalan utama            |
  | detail_lainnya  | VARCHAR(255) | Detail tambahan               |
  | tandai          | ENUM(...)    | Penanda alamat (rumah/kantor) |
  | isAlamatPribadi | BOOLEAN      | True jika pribadi             |
  | isAlamatUtama   | BOOLEAN      | True jika alamat utama        |
  | created_at      | TIMESTAMP    | Waktu pembuatan data          |
  
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
  idTrxUser CHAR(6),
  idProduk CHAR(6),
  idTrxCheckout CHAR(6),
  jumlah INT,
  harga_unit DECIMAL(10,2),
  subtotal DECIMAL(10,2),
  isCheckedOut BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE,
  FOREIGN KEY (idProduk) REFERENCES Ms_Produk(idProduk) ON DELETE CASCADE,
  FOREIGN KEY (idTrxCheckout) REFERENCES Trx_Checkout(idTrxCheckout) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut    | Tipe Data        | Keterangan                            |
  |-----------------|------------------|-------------------------------------|
  | idTrxKeranjang  | char(6) (PK)     | ID unik keranjang                   |
  | idTrxUser     | char(6) (FK)     | ID unik pelanggan melalui tabel `Trx_User`                   |
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
  idTrxUser CHAR(6),
  idEkspedisi CHAR(6),
  no_order CHAR(19) UNIQUE NOT NULL,
  status ENUM('pending','confirmed','processing','shipped','delivered','cancelled') DEFAULT 'pending',
  subtotal DECIMAL(12,2),
  discount_amount DECIMAL(10,2) DEFAULT 0,
  total_amount DECIMAL(12,2),
  isPurchaseWithSistem BOOLEAN DEFAULT TRUE,
  no_resi VARCHAR(100) COMMENT 'Nomor resi pengiriman',
  updated_by CHAR(6),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE,
  FOREIGN KEY (idEkspedisi) REFERENCES Ms_Ekspedisi(idEkspedisi) ON DELETE CASCADE,
  FOREIGN KEY (updated_by) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut        | Tipe Data          | Keterangan                                                                                 |
  |---------------------|--------------------|--------------------------------------------------------------------------------------------|
  | idTrxCheckout       | char(6) (PK)       | ID unik Checkout                                                                           |
  | idTrxUser         | char(6) (FK)       | ID unik pelanggan melalui tabel `Trx_User`                                                 |
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
  idTrxUser CHAR(6),
  idProduk CHAR(6),
  rating INT COMMENT '1 to 5',
  isi_ulasan TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE,
  FOREIGN KEY (idProduk) REFERENCES Ms_Produk(idProduk) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut  | Tipe Data      | Keterangan             |
  |---------------|----------------|------------------------|
  | idTrxUlasan   | char(6) (PK)   | ID unik ulasan         |
  | idTrxUser   | char(6) (FK)   | ID unik pelanggan melalui tabel `Trx_User`      |
  | idProduk      | char(6) (FK)   | ID unik produk         |
  | rating        | int            | Rating produk          |
  | isi_ulasan    | text           | Isi ulasan             |
  | created_at    | timestamp      | Waktu pembuatan ulasan |

- Relasi Komplain (Trx_Komplain)
  ``` sql
  CREATE TABLE Trx_Komplain (
  idTrxKomplain CHAR(6) PRIMARY KEY,
  idTrxUser CHAR(6),
  idTrxCheckout CHAR(6),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE,
  FOREIGN KEY (idTrxCheckout) REFERENCES Trx_Checkout(idTrxCheckout) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut    | Tipe Data        | Keterangan                 |
  |-----------------|------------------|----------------------------|
  | idTrxKomplain   | char(6) (PK)     | ID unik komplain           |
  | idTrxUser     | char(6) (FK)     | ID unik pelanggan melalui tabel `Trx_User`         |
  | idTrxCheckout   | char(6) (FK)     | ID unik Checkout           |
  | created_at      | timestamp        | Waktu pembuatan komplain   |
  | updated_at      | timestamp        | Waktu update komplain      |

- Relasi Komplain Chat (Trx_Komplain_Chat)
  ``` sql
  CREATE TABLE Trx_Komplain_Chat (
    idTrxKomplainChat CHAR(6) PRIMARY KEY,
    idTrxKomplain CHAR(6),
    idTrxUser CHAR(6),
    isi_pesan TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (idTrxKomplain) REFERENCES Trx_Komplain(idTrxKomplain) ON DELETE CASCADE,
    FOREIGN KEY (idTrxUser) REFERENCES Trx_User(idTrxUser) ON DELETE CASCADE
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
  ```
  | Nama Atribut     | Tipe Data      | Keterangan                    |
  |------------------|----------------|-------------------------------|
  | idTrxKomplainChat| char(6) (PK)   | ID unik komplain chat          |
  | idTrxKomplain    | char(6) (FK)   | ID unik komplain               |
  | idTrxUser          | char(6) (FK)   | ID unik admin atau pelanggan sesuai role                  |
  | isi_pesan        | text           | Isi pesan komplain             |
  | created_at       | timestamp      | Waktu pembuatan komplain chat  |
  | updated_at       | timestamp      | Waktu update komplain chat     |
