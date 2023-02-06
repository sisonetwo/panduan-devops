# Perkenalan Kubernetes

## Node ( VM di Kubernetes )

  1.  Melihat semua Node

      ```sh
      kubectl get node
      ```
    
    
  
  2. Melihat detail Node

      ```sh
      kubectl describe node namanode
       ```
    
## Pod ( unit terkecil yang bisa di deploy di Kubernetes Cluster / aplikasi kita yang running di K8s Cluster )

  1. Melihat semua Pod

      ```sh
      kubectl get pod
      ```

  2. Melihat detail Pod

      ```sh
      kubectl describe pod namapod
      ```
    
  3. Membuat Pod nginx

      ```sh
      apiVersion: v1
      kind: Pod
      metadata:
        name: nginx
      spec:
        containers:
          - name: nginx
            image: nginx
            ports:
              - containerPort: 80
      ```
     
     submit configuration yang sudah kita buat
     
     ```sh
     kubectl create -f filepod.yml
     ```
     
     melihat pod yang sudah berjalan
     
     ```sh
     kubectl get pod
     kubectl get pod -o wide
     kubectl desribe pod namapod
     ```
     
 4. Mengakses Pod

     ```sh
     kubectl port-forward namapod portakses:pod
     kubectl port-forward namapod 8080:80
     ```
     
  5. Mengahpus Pos

      ```sh
     kubectl delete pod namapod
     kubectl delete pod namapod1 namapod2 namapod3
     ```
     
  6. Mengapus Pod menggunakan Label
  
     ```sh
     kubectl delete pod -l key=value
     ```
     
  7. Menhapus semua Pod di Namespace
    
     ```sh
     kubectl delete pod --all --namespace namanamespace
     ```

## Label (untuk memberi tanda pada pod)

   1. Membuat Label
 
      ```sh
      apiVersion: v1
      kind: Pod
      metadata:
        name: nginx-with-label
        Labels:
          team: finance
          version: 1.4.5
          environment: production
      spec:
        containers:
          - name: nginx
            image: nginx
            ports:
              - containerPort: 80
      ```
     
      Jalan perintah
     
      ```sh
      kubectl create -f namefile.yaml
      ```  
    
   2. Melihat label

      ```sh
      kubectl get pod --show--labels
      ```
    
   3. Menambah atau mengubah Label di Pod
    
      ```sh
      kubectl label pod namapod key=value
      kubectl label pod nginx environment=development
      kubectl label pod nginx environment=qa --overwrite //sintaks edit label
      ```
    
   4. Mencari pod dengan label
    
      ```sh
      kubectl get pods -l key
      kubectl get pods -l key=value / kubectl get pods -l environment=qa
      kubectl get pods -l '!key'
      kubectl get pods -l key!=value
      kubectl get pods -l key 'key in (value1,value2)'
      kubectl get pods -l key 'key notin (value1, value2)'
      kubectl get pod -l key,key2=value
      ```
  
## Namespace

  1. Melihat daftar namespace
    
      ```sh
      kubectl get namespace
      kubectl get pod --namespace namanamespace
      ```
      
  2. Membuat namespace

      ```sh
      apiVersion: v1
      kind: namespace
      metadata:
        name: finance
      ```
      
     Jalankan dengan ketik
     
      ```sh
      kubectl create -f namafile.yaml
      ```
      
  3. Membuat pod dalam namespace

      ```sh
      kubectl create -f namafile.yaml --namespace finance
      ```
      
  4. Delete namespace

      ```sh
      kubectl delete namepsace namafile.yaml
      ```
    
