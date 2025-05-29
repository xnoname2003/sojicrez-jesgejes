---
## ERD Sistem Informasi Keripik Isal
<img width="450" alt="image" src="https://github.com/user-attachments/assets/07458e00-f3c1-4aec-a728-248eafd2c0b2" />

---
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
- Relasi Foto Produk (Trx_Foto_Produk)
- Relasi Layanan Ekspedisi (Trx_Layanan_Ekspedisi)
- Relasi Keranjang (Trx_Keranjang)
- Relasi Checkout (Trx_Checkout)
- Relasi Payment (Trx_Payment)
- Relasi Ulasan (Trx_Ulasan)
- Relasi Komplain (Trx_Komplain)
- Relasi Komplain Chat (Trx_Komplain_Chat)
