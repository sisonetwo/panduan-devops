# Installing Kubernetes dengan Kubeadm

1. Siapkan 3 buah instance di aws dengan terraform pada file main.tf 
  
    ```sh
    terraform apply
    ```
    
2. Ubah file hosts sesuai IP Public masing-masing

3. Install kubernetes dengan ansible 

    ```sh
    ansible-playbook -i hosts 01_user.yml 02_install_k8s.yml 03_master.yml 04_join.yml
    ```
