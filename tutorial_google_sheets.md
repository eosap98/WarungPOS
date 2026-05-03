# Panduan Google Sheets WarungPOS (v2 - FIX)

Ikuti panduan ini jika sebelumnya data Anda tidak muncul di Google Sheets. Masalah utama biasanya karena nama kolom di Google Sheets tidak sesuai dengan data dari aplikasi.

---

## Langkah 1: Siapkan File Google Sheets (WAJIB)
Buka [Google Sheets](https://sheets.new/) Anda dan buat 4 tab (sheet) dengan header (baris pertama) sebagai berikut:

### Tab 1: `products`
Isi baris pertama dengan nama kolom ini (huruf kecil semua):
`id`, `name`, `category`, `price`, `hpp`, `barcode`, `stock`, `isactive`, `issynced`

### Tab 2: `transactions`
Isi baris pertama dengan nama kolom ini:
`id`, `cashierid`, `cashiername`, `subtotal`, `taxrate`, `tax`, `grandtotal`, `paymentmethod`, `cashreceived`, `change`, `note`, `isreturned`, 'returnreason' , `ordertype`, `issynced`, `createdat`

### Tab 3: `users`
Isi baris pertama dengan nama kolom ini:
`id`, `username`, `passwordHash`, `role`, `fullName`, `isActive`, `isSynced`

### Tab 4: `branches`
Isi baris pertama dengan nama kolom ini:
`id`, `name`, `address`, `phone`, `isSynced`

---

## Langkah 2: Setting di SheetDB.io
1.  Buka [SheetDB](https://sheetdb.io/).
2.  Klik **"Create New API"**.
3.  Tempelkan URL Google Sheets Anda.
4.  **PENTING**: Klik ikon ⚙️ (Settings) pada API tersebut di dashboard SheetDB.
5.  Pastikan opsi **"Cast values to specific types"** diaktifkan (jika ada).

---

## Langkah 3: Perbaikan di Aplikasi
1.  Buka aplikasi WarungPOS > Pengaturan Database.
2.  Klik **Disconnect (Putuskan Koneksi)** dulu.
3.  Pilih kembali `GOOGLE_SHEETS`.
4.  Masukkan API URL baru dari SheetDB.
5.  Klik **Simpan**.
6.  Klik **Sinkronisasi Sekarang**.

---

### Kenapa Status Menjadi Offline Saat Keluar?
Saya sudah memperbaiki masalah ini. Sekarang status **Online/Offline** akan tetap tersimpan dan muncul dengan benar setiap kali Anda membuka menu pengaturan database.

> [!TIP]
> Jika data tetap tidak muncul, pastikan Anda tidak menggunakan spasi pada nama tab/sheet di Google Sheets. Nama tab harus persis: `products`, `transactions`, `users`, `branches`.
