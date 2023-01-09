# Install dan Konfigurasi Jenkins

## Install Jenkins

- [Referensi Install Jenkins](https://www.jenkins.io/doc/book/installing/)

1. Siapkan instance di AWS dengan ketentuan yang sesuai dengan minimum requirement penginstalan jenkins

    * Menggunakan Ubuntu Server 20.04 LTS (HVM), SSD Volume Type (Free Tier)

      ![img 1](https://user-images.githubusercontent.com/38523284/167793340-04b0bbc3-a8fa-4d11-96b1-397b969b7292.png)
      
    * Pilih tipe instance t2.medium dengan 2 vCPU dan 4GiB Memory

      ![img 2](https://user-images.githubusercontent.com/38523284/167793376-393ac4c1-5997-4879-9441-418d62144e75.png)
      
    * Edit network setting, pada segmen firewall pilih select existing security group kemudian pada security group, pilih allow all

      ![img 3](https://user-images.githubusercontent.com/10807163/211341819-afab6dbd-23d3-4223-b567-6ffc2073dc1c.png)
      
    * Ganti Configure Storage menjadi 20 GiB

      ![img 4](https://user-images.githubusercontent.com/38523284/167793443-fe960d2d-e38f-4786-9822-c85dfbc3ddae.png)

2. Login SSH menggunakan IPv4 yang terdapat pada detail instance

3. Masuk ke folder `devopsapril/ansible'

4. Kemudian ubah nomor IP yang terdapat di file hosts dengan menggunakan nano

5. Dilanjutkan menginstall docker terlebih dahulu

    ```sh
    ansible-playbook -i hosts install_docker.yml
    ```
    
6. Setelah selesai install docker, dilanjutkan menginstall jenkins dengan menggunakan sintaks berikut
    ```sh
    docker network create jenkins
    ```
7. Untuk menjalankan perintah Docker di dalam node Jenkins, unduh dan jalankan gambar docker:dind Docker menggunakan perintah run docker berikut:

    ```sh
    docker run \
    --name jenkins-docker \
    --rm \
    --detach \
    --privileged \
    --network jenkins \
    --network-alias docker \
    --env DOCKER_TLS_CERTDIR=/certs \
    --volume jenkins-docker-certs:/certs/client \
    --volume jenkins-data:/var/jenkins_home \
    --publish 2376:2376 \
    docker:dind \
    --storage-driver overlay2
    ```
    
8. Selanjutnya kita akan membuat Docker File, dengan mengeksekusi 2 langkah berikut

    ```sh
    nano Dockerfile
    ```
    
    Salin sintaks berikut dan masukan ke dalam Dockerfile setelah perintah nano
    
    ```sh
    FROM jenkins/jenkins:2.332.3-jdk11
    USER root
    RUN apt-get update && apt-get install -y lsb-release
    RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
    https://download.docker.com/linux/debian/gpg
    RUN echo "deb [arch=$(dpkg --print-architecture) \
    signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
    https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
    RUN apt-get update && apt-get install -y docker-ce-cli
    USER jenkins
    RUN jenkins-plugin-cli --plugins "blueocean:1.25.3 docker-workflow:1.28"
    ```
    
    Buat docker image baru dari Dockerfile ini dan tetapkan gambar tersebut dengan nama yang bermakna, mis. "myjenkins-blueocean:2.332.3-1":
    
    ```sh
    docker build -t myjenkins-blueocean:2.332.3-1 .
    ```
    
9. Setelah langkah membuat Dockerfile selesai, kita akan menjalankan/ run myjenkins-blueocean:2.332.3-1 image sebagai container di Docker

    ```sh
    docker run \
    --name jenkins-blueocean \
    --rm \
    --detach \
    --network jenkins \
    --env DOCKER_HOST=tcp://docker:2376 \
    --env DOCKER_CERT_PATH=/certs/client \
    --env DOCKER_TLS_VERIFY=1 \
    --publish 8080:8080 \
    --publish 50000:50000 \
    --volume jenkins-data:/var/jenkins_home \
    --volume jenkins-docker-certs:/certs/client:ro \
    myjenkins-blueocean:2.332.3-1 
    ```
    
10. Jalankan jenkins di browser dengan port sesuai yang tertera pada detail containernya, maka akan tampil laman berikut :
    ![img 5](https://user-images.githubusercontent.com/38523284/167792244-bdcf6cad-5247-4e56-a41e-7fa2a6c00079.png)
    
11. Saat pertama kali akses jenkins, anda wajib untuk memasukan administrator password yang dapat diakses dengan sintaks berikut

    ```sh
    docker exec -it jenkins-blueocean cat /var/jenkins_home/secrets/initialAdminPassword
    ```
    
12. Setelah memasukan administrator password kemudian akan masuk ke jendela Getting started

    * Pilih install suggested plugins pada segmen Customize Jenkins, kemudian tunggu sampai instalasi plugin selesai

      ![img 6](https://user-images.githubusercontent.com/38523284/167793753-984c0dfd-7af1-4900-819a-b9a46836ff94.png)
      
    * Selanjutnya pada Create First Admin User silahkan masukan username, password, full name, dan email address kemudian Save and Continue
      
      ![img 7](https://user-images.githubusercontent.com/38523284/167793883-51b159d0-680d-4f22-b62a-6b9c7c58303f.png)
      
    * Pada Instance Configuration langsung Save saja
    * Jenkins anda siap digunakan

      ![img 8](https://user-images.githubusercontent.com/38523284/167793994-87b67a7d-d13e-4eb8-9b3e-be1dfb07fce4.png)
