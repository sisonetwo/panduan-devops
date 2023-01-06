## Instalasi Ansible


Ansible merupakan tool yang digunkaan untuk mensetup infrastruktur. Dimana kita dapat mencatat setiap melakukan konfigurasi ke beberapa server sekaligus. Misal saat pertama kali kita memasang Ubuntu Server di 10 mesin, maka kita akan melakuan apt-get update serta memasang beberapa komponen seperti PHP5 dan Apache2. Sebenarnya tidak akan menjadi masalah, bila kita hanya melakukan sedikit hal. Tapi tentunya tidak efektif. Dengan ansible, kita bisa melakukanya dalam satu langkah.

## Install di MAC OS

Instalasi di MAC OS, menggunakan pip. Untuk menjalankan pip kita harus memiliki python terlebih dahulu.
1. Pertama install PIP
```sh
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py --user
```

2. Install ansible dengan pip
```sh
pip install ansible
```
