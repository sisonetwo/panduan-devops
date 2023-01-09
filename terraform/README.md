# Terraform

Terraform dikembangkan oleh HashiCorp yang merupakan tools infrastruktur as a code sebagai alat yang memungkinkan untuk membuat, mengubah, dan meningkatkan infrastuktur dengan aman dan dapat diprediksi. Terraform dikembangkan dalam bahasa Go. Terraform mendukung provision di berbagai provider cloud yang besar seperti AWS, GCP, Azure, bahkan DigitalOcean.

Referensi [Install Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli).

 ## Install Terraform di MAC OS

1. Download terraform di https://developer.hashicorp.com/terraform/downloads
 
    <img width="350" alt="Screen Shot 2022-05-11 at 14 37 11" src="terraform1.png">

2. Extract file terraform

    <img width="350" alt="Screen Shot 2022-05-11 at 14 37 11" src="terraform2.png">

3. install terraform di terminal dengan perintah :
   ```sh
   mv /Downloads/terraform /usr/local/bin/terraform
   ```

    <img width="350" alt="Screen Shot 2022-05-11 at 14 37 11" src="terraform2.png">


## AWS Provider

Untuk menggunakan Provider AWS, syarat utama yang dibutuhkan adalah menginstall AWS CLI. Instalasi AWS CLI dapat dilakukan dengan cara berikut:

Referensi [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

## AWS CLI di Mac OS
1. Download dan jalankan AWS CLI macOS pkg file. https://awscli.amazonaws.com/AWSCLIV2.pkg
2. Ikuti instruksi installasi.
3. Untuk mengkonfirmasi terinsall, dapat dilakukan dengan mengetikan command berikut di terminal.
   ```sh
   aws --version
   ```

## Menjalankan terraform

1. Inisialisasi provider
   ```sh
   terraform init
   ```
2. Melihat detail resource sebelum dibuat
   ```sh
   terraform plan
   ```
3. Apply resource
   ```sh
   terraform apply
   ```
