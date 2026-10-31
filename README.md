# BudgetKu Android

Versi awal proyek Android BudgetKu berdasarkan file HTML yang diberikan. Aplikasi dibungkus dengan Capacitor sehingga dapat dibangun menjadi APK Android.

## Fitur yang sudah ada
- Dashboard pemasukan, saldo tersisa, dan anggaran bulanan
- Kategori konsumsi dan tabungan
- Catat dan hapus transaksi
- Pengelolaan akun (bank, e-wallet, tunai)
- Ringkasan alokasi dan pengeluaran
- Data lokal di perangkat (localStorage)
- Ekspor dan pemulihan cadangan JSON (ditambahkan pada versi upgrade ini)

## Yang dibutuhkan
- Komputer Windows/macOS/Linux
- Node.js versi LTS
- Android Studio dan Android SDK
- Koneksi internet saat memasang dependensi pertama kali

## Membuat proyek Android dan APK
Jalankan perintah berikut dari folder proyek ini:

```bash
npm install
npx cap add android
npx cap sync android
npx cap open android
```

Di Android Studio:
1. Tunggu Gradle Sync selesai.
2. Pilih menu **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
3. Setelah selesai, klik **locate** pada notifikasi untuk menemukan APK debug.
4. Pindahkan APK ke HP Android dan instal. Untuk distribusi pribadi, izinkan instalasi dari sumber tersebut bila Android memintanya.

Setiap kali mengubah `www/index.html`, jalankan `npx cap sync android` lalu build ulang APK.

## Catatan data dan privasi
- Data disimpan secara lokal pada WebView aplikasi; tidak ada sinkronisasi cloud atau akun pengguna pada versi ini.
- Menghapus data aplikasi atau menghapus aplikasi dapat menghilangkan data. Gunakan **Ringkasan > Cadangan data** secara berkala dan simpan file JSON di tempat aman.
- File cadangan berisi informasi keuangan pribadi. Jangan membagikannya sembarangan.
- Versi ini belum memiliki PIN/biometrik, enkripsi cadangan, atau sinkronisasi antarperangkat.

## Identitas aplikasi
- Nama: BudgetKu
- Application ID: `com.budgetku.personal`
- Platform: Android melalui Capacitor 7
