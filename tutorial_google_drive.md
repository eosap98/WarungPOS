# Panduan Setup Google Drive (TERBARU - Perbaikan 401)

Ikuti tutorial ini jika Anda sebelumnya mendapatkan error 401 saat mengetes koneksi Google Drive.

---

## Langkah 1: Buat/Update Google Apps Script
1.  Buka [Google Apps Script](https://script.google.com/).
2.  Buka project Anda yang sebelumnya atau buat baru.
3.  **Gunakan kode terbaru ini** (Kode ini sudah mendukung fitur "Restore" dan perbaikan otentikasi):

```javascript
function doPost(e) {
  var data = JSON.parse(e.postData.contents);
  var folderName = "WarungPOS_Backup";
  var folders = DriveApp.getFoldersByName(folderName);
  var folder = folders.hasNext() ? folders.next() : DriveApp.createFolder(folderName);
  
  var fileName = data.table + ".json";
  var files = folder.getFilesByName(fileName);
  
  // LOGIKA RESTORE (Jika aplikasi minta data)
  if (data.action === "get") {
    if (files.hasNext()) {
      var content = files.next().getBlob().getDataAsString();
      return ContentService.createTextOutput(content).setMimeType(ContentService.MimeType.JSON);
    } else {
      return ContentService.createTextOutput("null").setMimeType(ContentService.MimeType.TEXT);
    }
  }
  
  // LOGIKA BACKUP (Simpan data)
  if (files.hasNext()) {
    files.next().setContent(JSON.stringify(data.data));
  } else {
    folder.createFile(fileName, JSON.stringify(data.data));
  }
  
  return ContentService.createTextOutput("Success").setMimeType(ContentService.MimeType.TEXT);
}
```

---

## Langkah 2: Deploy Ulang (Sangat Penting)
Jika Anda hanya mengubah kode tanpa melakukan "Deploy" ulang, perubahan tidak akan ngefek.
1.  Klik tombol **Deploy** > **New Deployment**.
2.  Select type: **Web App**.
3.  Execute as: **Me**.
4.  Who has access: **Anyone**.
5.  Klik **Deploy**.
6.  Salin **Web App URL** yang baru.

---

## Langkah 3: Setup di Aplikasi WarungPOS
1.  Pilih Tipe: `GOOGLE_DRIVE`.
2.  **Database URL**: Tempelkan URL Web App yang baru.
3.  **Secret Key**: **WAJIB DIKOSONGKAN**. (Jangan isi apapun di kolom Secret Key untuk Google Drive).
4.  Klik **Simpan**.

---

### Kenapa Muncul Error 401 Sebelumnya?
Error 401 muncul karena aplikasi mencoba mengirimkan kode "Authorization" ke Google, padahal Google Apps Script yang diset ke "Anyone" tidak membutuhkannya. Update aplikasi versi terbaru ini sudah secara otomatis menghilangkan kode tersebut khusus untuk Google Drive agar koneksi lancar.

> [!TIP]
> Sekarang Anda bisa menggunakan tombol **"Tarik Data (Restore)"** untuk mengambil kembali file `.json` yang ada di folder `WarungPOS_Backup` di Google Drive Anda ke HP baru.
