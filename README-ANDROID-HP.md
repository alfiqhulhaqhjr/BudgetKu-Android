# Membuat APK BudgetKu hanya dengan HP Android

Proyek ini memakai GitHub Actions untuk membangun APK di cloud, jadi HP hanya dipakai untuk mengunggah kode dan mengunduh APK. Tidak perlu memasang Android Studio di HP.

## Cara paling praktis (Termux + GitHub)
1. Buat akun GitHub jika belum punya, lalu buat repository baru bernama `budgetku-android` dan pilih **Private**.
2. Instal Termux dari F-Droid (bukan versi Play Store). Buka Termux dan jalankan:

   ```sh
   termux-setup-storage
   pkg update -y && pkg install git unzip -y
   ```

3. Ekstrak ZIP proyek ke folder Download menggunakan aplikasi pengelola berkas. Misalnya hasilnya ada di `Download/BudgetKu-Android`.
4. Di Termux jalankan (sesuaikan nama folder bila berbeda):

   ```sh
   cd ~/storage/downloads/BudgetKu-Android
   git init
   git add .
   git commit -m "BudgetKu Android initial"
   git branch -M main
   git remote add origin https://github.com/USERNAME/budgetku-android.git
   git push -u origin main
   ```

   Ganti `USERNAME` dengan username GitHub. Saat diminta password, GitHub memerlukan Personal Access Token (PAT), bukan password akun. Buat token dari GitHub Settings > Developer settings > Personal access tokens, dengan akses repository untuk repo tersebut. Jangan pernah kirim token kepada orang lain atau ke chat.

5. Di GitHub, buka repository > **Actions** > workflow **Build BudgetKu APK**. Jika workflow belum berjalan otomatis, pilih **Run workflow**.
6. Tunggu sampai status workflow hijau. Buka hasil run, cari **Artifacts**, lalu unduh `BudgetKu-debug-apk`.
7. Ekstrak ZIP artifact. Di dalamnya ada `app-debug.apk`. Ketuk file itu untuk memasang. Jika Android meminta izin, izinkan browser atau aplikasi Files memasang aplikasi dari sumber tersebut.

## Catatan
- APK ini adalah debug APK untuk penggunaan pribadi, bukan rilis Play Store.
- Data BudgetKu tersimpan lokal di aplikasi. Hapus data/uninstall dapat menghapus catatan; gunakan fitur cadangan JSON secara berkala.
- Untuk pembaruan kode: edit file, lalu `git add .`, `git commit -m "Update BudgetKu"`, dan `git push`. GitHub Actions akan membangun APK baru.
