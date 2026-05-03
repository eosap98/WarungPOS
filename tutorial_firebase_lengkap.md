# Panduan Lengkap Setup Firebase untuk WarungPOS

Ikuti langkah-langkah di bawah ini untuk mengaktifkan fitur Cloud Sync menggunakan Firebase.

---

## Langkah 1: Membuat Project Firebase
1.  Buka [Firebase Console](https://console.firebase.google.com/).
2.  Klik tombol **"Add Project"**.
3.  Masukkan nama project (misal: `WarungPOS-Online`).
4.  Klik **Continue**.
5.  (Opsional) Google Analytics bisa dimatikan jika tidak perlu, lalu klik **Create Project**.
6.  Tunggu proses selesai dan klik **Continue**.

---

## Langkah 2: Mengaktifkan Realtime Database
1.  Di menu samping kiri, cari menu **Build** dan pilih **Realtime Database**.
2.  Klik tombol **"Create Database"**.
3.  Pilih lokasi database (disarankan **Singapore - asia-southeast1** agar lebih cepat dari Indonesia). Klik **Next**.
4.  Pilih **"Start in test mode"** agar aplikasi bisa langsung mengirim data tanpa ribet urusan izin di awal. Klik **Enable**.
5.  **PENTING**: Salin **URL Database** yang muncul di bagian atas (contoh: `https://warungpos-online-default-rtdb.asia-southeast1.firebasedatabase.app/`).

---

## Langkah 3: Mengambil Kunci Rahasia (Database Secret)
Agar data aman, aplikasi butuh "kunci" untuk bisa masuk ke database Anda.

1.  Klik ikon gerigi ⚙️ (Project Settings) di pojok kiri atas, di samping teks "Project Overview".
2.  Pilih menu **Project Settings**.
3.  Pilih tab **Service Accounts**.
4.  Klik menu **Database Secrets** di kolom sebelah kiri.
5.  Di sana akan ada daftar secret key. Klik **Show** pada salah satu kunci, lalu klik **Copy**.

---

## Langkah 4: Memasukkan ke Aplikasi WarungPOS
Sekarang, buka HP Anda dan masuk ke aplikasi:

1.  Buka menu **Pengaturan**.
2.  Cari tombol **"Pengaturan Database Remote (Cloud)"**.
3.  Ubah **Tipe Database** menjadi `FIREBASE`.
4.  **Database URL**: Tempelkan URL dari Langkah 2.
5.  **Secret Key**: Tempelkan kunci rahasia dari Langkah 3.
6.  Klik **Simpan Pengaturan**.

---

## Langkah 5: Uji Coba Sinkronisasi
1.  Klik tombol **"Sinkronisasi Sekarang"**.
2.  Kembali ke browser Anda di Firebase Console (bagian Realtime Database).
3.  Jika berhasil, Anda akan melihat data baru muncul berwarna merah secara otomatis dengan folder seperti `products`, `transactions`, dsb.

---

### Tips Keamanan (Setelah Berhasil):
Jika sinkronisasi sudah jalan, sangat disarankan untuk mengubah **Rules** di Firebase agar lebih aman.
1. Masuk ke tab **Rules** di Realtime Database.
2. Ubah kodenya menjadi:
```json
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
```
*Dengan rule ini, hanya aplikasi yang punya "Secret Key" yang bisa mengakses data Anda.*
