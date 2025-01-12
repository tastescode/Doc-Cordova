# Doc-Cordova
Panduan Instalasi CORDOVA di linux

# Dokumentasi Instalasi Apache Cordova di Ubuntu

Panduan ini akan membantu Anda untuk menginstal **Apache Cordova** di sistem berbasis Linux (misalnya Ubuntu). Anda akan belajar cara menginstal semua dependensi yang diperlukan seperti **Node.js**, **Java Development Kit (JDK)**, **Android SDK**, dan **Apache Cordova** itu sendiri.

---

## 1. Persiapan Sistem

Sebelum memulai instalasi, pastikan sistem Anda sudah terhubung dengan internet dan memiliki **akses root** atau kemampuan untuk menjalankan perintah dengan `sudo`.

### 1.1. Memperbarui Sistem
   Pastikan sistem operasi Anda diperbarui. Jalankan perintah berikut untuk memeriksa versi dan pembaruan sistem:
   ```bash
   sudo apt update && sudo apt upgrade

## 2. Instalasi Node.js

Cordova memerlukan Node.js yang terinstal di sistem. Untuk menginstal Node.js, ikuti langkah-langkah berikut:
2.1. Instal Node.js dari Repositori Resmi Ubuntu

Gunakan perintah berikut untuk menginstal Node.js versi terbaru yang tersedia di repositori Ubuntu:
```bash
sudo apt install nodejs
sudo apt install npm

2.2. Verifikasi Instalasi Node.js

Pastikan Node.js terinstal dengan benar dengan memeriksa versinya:
```bash
node -v
npm -v

3. Instalasi Apache Cordova

Setelah Node.js terinstal, Anda bisa menginstal Cordova menggunakan npm (Node Package Manager).
3.1. Instal Cordova secara Global

Untuk menginstal Cordova secara global di sistem, jalankan perintah berikut:
```bash
sudo npm install -g cordova

3.2. Verifikasi Instalasi Cordova

Setelah instalasi selesai, periksa apakah Cordova terinstal dengan benar:
cordova -v

Jika Cordova terinstal dengan benar, perintah ini akan menampilkan versi Cordova yang terinstal.
4. Instalasi Java Development Kit (JDK)

Cordova memerlukan Java Development Kit (JDK) untuk mengembangkan aplikasi Android. Biasanya, JDK 8 atau yang lebih baru digunakan untuk membangun aplikasi Android.
4.1. Instal JDK (OpenJDK)

Gunakan perintah berikut untuk menginstal OpenJDK 11 (atau versi lainnya jika diperlukan):

sudo apt install openjdk-11-jdk

4.2. Verifikasi Instalasi JDK

Setelah JDK terinstal, pastikan versi JDK sudah benar dengan menjalankan perintah:

java -version

5. Instalasi Android SDK

Untuk mengembangkan aplikasi Android, Anda juga perlu menginstal Android SDK dan alat terkait.
5.1. Instal SDK Android Tools

Anda bisa menginstal Android SDK melalui SDK Command Line Tools. Ikuti langkah-langkah berikut:

    Unduh Android SDK Command Line Tools dari situs resmi Android:
        Android Command Line Tools

    Ekstrak file SDK ke Direktori yang Diinginkan: Misalnya, jika Anda mengunduhnya ke direktori ~/Downloads, ekstrak dengan:

mkdir -p ~/Android/Sdk
unzip commandlinetools-linux-*.zip -d ~/Android/Sdk/cmdline-tools

Menambahkan Path SDK ke File .bashrc atau .zshrc: Edit file konfigurasi shell untuk menambahkan path SDK ke variabel lingkungan:

nano ~/.bashrc

atau

nano ~/.zshrc

Tambahkan baris berikut:

export ANDROID_SDK_ROOT=~/Android/Sdk
export ANDROID_HOME=$ANDROID_SDK_ROOT
export PATH=$PATH:$ANDROID_SDK_ROOT/platform-tools:$ANDROID_SDK_ROOT/emulator:$ANDROID_SDK_ROOT/cmdline-tools/latest/bin

Simpan dan Muat Ulang File Konfigurasi: Simpan perubahan dengan CTRL + O, kemudian keluar dengan CTRL + X. Jalankan perintah berikut untuk memuat ulang file konfigurasi:

source ~/.bashrc

atau

    source ~/.zshrc

5.2. Instal SDK Platform dan Alat yang Diperlukan

Gunakan sdkmanager untuk menginstal platform Android dan alat yang diperlukan:

sdkmanager "platform-tools" "build-tools;33.0.0" "platforms;android-33"

Untuk memeriksa apakah SDK sudah terinstal, jalankan:

sdkmanager --list

6. Pengaturan Emulator Android (Opsional)

Jika Anda ingin menjalankan aplikasi di emulator Android, pastikan Android Virtual Device (AVD) sudah terkonfigurasi dengan benar.
6.1. Membuat AVD Baru

Gunakan perintah berikut untuk membuat emulator Android:

avdmanager create avd --name "MyAVD" --package "system-images;android-33;google_apis;x86_64"

6.2. Jalankan Emulator

Untuk menjalankan emulator, gunakan perintah berikut:

emulator -avd MyAVD

7. Membuat dan Menjalankan Aplikasi Cordova
7.1. Membuat Aplikasi Baru

Gunakan perintah berikut untuk membuat proyek Cordova baru:

cordova create nama_aplikasi com.example.app NamaAplikasi
cd nama_aplikasi

7.2. Menambahkan Platform Android

Setelah membuat proyek, tambahkan platform Android:

cordova platform add android

7.3. Membangun Aplikasi

Setelah platform ditambahkan, bangun aplikasi dengan perintah:

cordova build android

7.4. Menjalankan Aplikasi di Emulator atau Perangkat Fisik

Jalankan aplikasi di perangkat fisik atau emulator menggunakan perintah:

cordova run android

8. Menangani Masalah Umum
8.1. Variabel Lingkungan ANDROID_HOME atau ANDROID_SDK_ROOT Tidak Ditemukan

Pastikan variabel lingkungan diatur dengan benar dalam file .bashrc atau .zshrc. Jika Anda menggunakan sudo, pastikan variabel tersebut juga dikenali oleh root.
8.2. Perangkat Tidak Terhubung

Jika perangkat Android fisik tidak terdeteksi, pastikan USB Debugging diaktifkan di perangkat dan perangkat terhubung dengan benar melalui kabel USB. Jalankan:

adb devices

9. Kesimpulan

Dengan mengikuti langkah-langkah di atas, Anda akan memiliki Cordova terinstal di sistem dan siap untuk membangun serta menjalankan aplikasi Android. Dokumentasi ini mencakup seluruh proses instalasi, dari pengaturan lingkungan hingga menjalankan aplikasi. Jika ada masalah lebih lanjut atau kesalahan dalam proses ini, beri tahu saya dan kita dapat mencari solusi lebih lanjut!
