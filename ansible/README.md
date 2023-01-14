## Instalasi Ansible


Ansible merupakan tool yang digunkaan untuk mensetup infrastruktur. Dimana kita dapat mencatat setiap melakukan konfigurasi ke beberapa server sekaligus. Misal saat pertama kali kita memasang Ubuntu Server di 10 mesin, maka kita akan melakuan apt-get update serta memasang beberapa komponen seperti PHP5 dan Apache2. Sebenarnya tidak akan menjadi masalah, bila kita hanya melakukan sedikit hal. Tapi tentunya tidak efektif. Dengan ansible, kita bisa melakukanya dalam satu langkah.

## Install ansible di linux ubuntu

1. Jalankan command berikut di Terminal

    ```sh
    sudo apt update
    sudo apt install software-properties-common
    sudo add-apt-repository --yes --update ppa:ansible/ansible
    sudo apt install ansible
    ```

2. Jalankan command berikut

   ```sh
   sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
   $ sudo apt update
   $ sudo apt install ansible
   ```

## Install di MAC OS

Instalasi di MAC OS, menggunakan pip. Untuk menjalankan pip kita harus memiliki python terlebih dahulu.
1. Pertama install dengan brew
  ```sh
  brew install ansible
  ```

2. Jika sudah selesai install, cek ansible yang sudah di install pake pc atau server dengan perintah :
  ```sh
  ansible --version
  ```


## Menjalankan Ansible

  ```sh
  ansible-playbook -i hosts `nama file`
  ```
