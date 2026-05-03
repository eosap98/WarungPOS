# 🏪 WarungPOS - Sistem Kasir Pintar & Modern

**WarungPOS** adalah aplikasi Point of Sale (POS) berbasis Android yang dirancang untuk memberikan solusi manajemen penjualan yang cepat, handal, dan estetik bagi UMKM. Dibangun dengan teknologi terkini untuk memastikan operasional bisnis Anda berjalan tanpa hambatan, baik secara offline maupun online. Download Aplikasi [Klik Disini](https://github.com/eosap98/WarungPOS/releases/download/V1.0/WPOS-KasirAndroid.apk)

---

## ✨ Fitur Utama

### 🛒 1. Kasir Digital (Point of Sale)
*   **Katalog Interaktif**: Tampilan produk dengan sistem kategori dan pencarian instan.
*   **Sistem Varian & Topping**: Mendukung varian produk (misal: Ukuran, Level Pedas, Topping) dengan penyesuaian harga otomatis.
*   **Diskon & Pajak**: Fleksibilitas dalam pemberian diskon per item dan perhitungan pajak (PPN) otomatis.
*   **Metode Pembayaran Lengkap**: Mendukung transaksi Tunai (Cash), QRIS (statis/dinamis), dan Transfer Bank.
*   **Jenis Pesanan**: Pilihan *Dine-In* (dengan nomor meja) atau *Take Away*.

### ⏳ 2. Manajemen Antrean (Waiting Menu)
*   **Kategorisasi Pesanan**: Pantau pesanan berdasarkan tipe (Semua, Dine-In, Take-Away).
*   **Detail Pesanan Instan**: Klik pada antrean untuk melihat detail item dan varian yang harus disiapkan.
*   **Status Real-time**: Indikator status pesanan (Memasak/Siap) untuk koordinasi dapur yang lebih baik.

### ☁️ 3. Sinkronisasi Remote & Multi-Device (Experimental)
*   **Mode Offline-First**: Aplikasi tetap berfungsi penuh tanpa koneksi internet. Data tersimpan aman di perangkat.
*   **Integrasi Google Sheets**: Gunakan Google Sheets sebagai database pusat untuk melihat laporan dari mana saja.
*   **Real-time Firebase**: Sinkronisasi data antar perangkat karyawan secara instan.
*   **Backup & Restore**: Keamanan data terjamin dengan fitur sinkronisasi otomatis (Experimental).

### 📊 4. Riwayat & Analisis Penjualan
*   **Filter Canggih**: Cari transaksi berdasarkan rentang tanggal atau metode pembayaran (Cash/QRIS/Transfer).
*   **Laporan Omzet**: Pantau total penjualan dan performa bisnis langsung dari aplikasi.
*   **Manajemen Retur**: Proses pengembalian barang yang tercatat dengan rapi.

### 🖨️ 5. Kustomisasi Struk & Hardware
*   **Desain Struk Profesional**: Tambahkan logo, QR Code sosial media, dan pesan footer pada struk.
*   **Dukungan Printer Thermal**: Kompatibel dengan printer Bluetooth ukuran 58mm dan 80mm.
*   **Scan Barcode**: Gunakan kamera perangkat untuk input produk lebih cepat.

### 🔐 6. Keamanan & Hak Akses (RBAC)
*   **Role Management**: Bedakan akses antara **Admin** (akses penuh ke pengaturan & laporan) dan **Staff** (hanya modul kasir).
*   **Proteksi Akun**: Keamanan login dan fitur ganti password yang terenkripsi.

---

## 🛠️ Teknologi (Tech Stack)
*   **Language**: Kotlin (Native Android)
*   **Architecture**: MVVM (Model-View-ViewModel) for Clean Code
*   **Local Database**: Room Persistence Library
*   **Networking**: Retrofit & Firebase SDK
*   **UI/UX**: Material Design 3 (Zinc Aesthetic)

---

## 📱 Persyaratan Perangkat
*   **Minimal**: Android 8.0 (Oreo) - API Level 26
*   **Rekomendasi**: Android 13+ untuk performa terbaik
*   **Layar**: Optimal untuk Smartphone & Tablet

---

## 📚 Panduan Pengguna
- [📖 Panduan Integrasi Google Sheets](https://github.com/eosap98/WarungPOS/blob/main/tutorial_google_sheets.md)
- [🔥 Setup Firebase & Remote Database](https://github.com/eosap98/WarungPOS/blob/main/tutorial_firebase_lengkap.md)
- [☁️ Panduan Remote Storage Google Drive](https://github.com/eosap98/WarungPOS/blob/main/tutorial_google_drive.md)
- [🖥️ Setup Server Linux/Lokal](https://github.com/eosap98/WarungPOS/blob/main/tutorial_linux_lokal.md)

---
Developed with ❤️ by **EOS AGENG**
