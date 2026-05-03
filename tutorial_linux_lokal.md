# Tutorial Setup Server Linux Sendiri (Tanpa VPS)

Jika Anda ingin menggunakan PC/Laptop sendiri sebagai server database untuk WarungPOS (tanpa menyewa VPS), ikuti langkah-langkah di bawah ini.

---

## 1. Persiapan Sistem
Anda bisa menggunakan Laptop bekas atau PC yang tidak terpakai.
*   **OS**: Ubuntu Server atau Ubuntu Desktop (disarankan versi 22.04 LTS atau yang lebih baru).
*   **Koneksi**: Pastikan PC Server dan HP Android berada dalam **satu jaringan WiFi** yang sama.

---

## 2. Instalasi Lingkungan (Database & Node.js)
Buka terminal di Linux Anda dan jalankan perintah berikut:

### Install MySQL
```bash
sudo apt update
sudo apt install mysql-server -y
```

### Install Node.js (Sebagai Backend API)
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
```

---

## 3. Membuat Backend API Sederhana
Kita butuh API kecil untuk menerima data dari aplikasi.

1. Buat folder baru: `mkdir warungpos-server && cd warungpos-server`
2. Inisialisasi: `npm init -y`
3. Install library: `npm install express body-parser`
4. Buat file `server.js`: `nano server.js`

Isi file `server.js` dengan kode ini:
```javascript
const express = require('express');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

app.use(bodyParser.json({ limit: '50mb' }));

// Endpoint untuk menerima data sync
app.post('/sync/:table', (req, res) => {
    const table = req.params.table;
    const data = req.body;
    
    console.log(`Menerima ${data.length} data untuk tabel: ${table}`);
    
    // Di sini Anda bisa menambahkan kode untuk menyimpan ke MySQL
    // Untuk tes, kita kembalikan sukses saja
    res.status(200).send({ message: "Data received" });
});

app.listen(port, '0.0.0.0', () => {
    console.log(`Server berjalan di http://localhost:${port}`);
});
```
5. Jalankan server: `node server.js`

---

## 4. Cara Menghubungkan HP ke Server Lokal

Ada dua cara agar HP bisa mengakses server di PC Anda:

### Cara A: Melalui WiFi Lokal (Hanya di Dalam Toko)
1. Cek IP Lokal PC Anda: Ketik `hostname -I` di terminal Linux. (Misal muncul: `192.168.1.15`)
2. Di aplikasi WarungPOS, masukkan URL: `http://192.168.1.15:3000/`
3. Pastikan Firewall Linux mengizinkan port 3000: `sudo ufw allow 3000`

### Cara B: Melalui Internet (Agar Bisa Diakses dari Mana Saja)
Karena Anda tidak punya VPS, Anda bisa menggunakan **Ngrok** atau **Cloudflare Tunnel**.

**Menggunakan Ngrok:**
1. Install Ngrok di Linux.
2. Jalankan: `ngrok http 3000`
3. Ngrok akan memberikan URL publik seperti: `https://abcd-1234.ngrok-free.app`
4. Masukkan URL tersebut ke pengaturan di aplikasi WarungPOS.

---

## 5. Setup di Aplikasi WarungPOS

*   **Tipe Database**: `LINUX`
*   **Database URL**: Masukkan IP Lokal (Cara A) atau URL Ngrok (Cara B).
*   **Secret Key**: (Bebas, karena di kode `server.js` di atas kita belum mengaktifkan pengecekan token).

---

## Keuntungan Setup Ini:
1. **Gratis**: Tidak perlu bayar sewa bulanan VPS.
2. **Privasi**: Data benar-benar ada di dalam gedung/rumah Anda sendiri.
3. **Kapasitas**: Tergantung harddisk PC Anda (bisa sangat besar).

> [!WARNING]
> Jika menggunakan Cara A (WiFi Lokal), sinkronisasi hanya akan jalan saat HP Anda terhubung ke WiFi toko. Jika Anda keluar toko dan menggunakan paket data, sinkronisasi akan tertunda sampai Anda kembali ke WiFi toko. Gunakan Cara B (Ngrok) jika ingin sinkronisasi tetap jalan di mana saja.
