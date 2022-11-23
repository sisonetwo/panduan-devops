## Instalasi Docker

# Install Docker dari installer
  1. Double click Desktop Instller.exe untuk menjalankan penginstal.
  
        > Jika Anda belum mengunduh penginstall (Docker Desktop Installer.exe) Anda bisa mendapatkannya dari Docker Hub. Biasanya mengunduh ke folder Unduhan Anda, atau    dapat menjalakannya dari bilah unduhan terbaru di bagian bawah browser web Anda.

  2. Saat diminta, pastikan opsi Gunakan WSL 2 alih-alih Hyper-V pada halaman Konfigurasi, dipilih atau tidak tergantung pada pilihan backend Anda.

        > Jika sistem Anda hanya mendukung salah satu dari dua opsi, Anda tidak akan dapat memilih backend mana yang akan digunakan.

  3. Ikuti instruksi penginstalan (accept the license, authorize the installer, and proceed with the install)
  4. Jika penginstalan berhasil, klik Tutup untuk menyelesaikan proses penginstalan. Jika dibutuhkan lakukan reboot/ restart

# Install Docker dari Command Line
  1. Setelah mengunduh file Docker Desktop Installer.exe, jalankan perintah berikut di command line windows anda :
      ```sh
      start /w "" "Docker Desktop Installer.exe" install
      ```
