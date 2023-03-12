## Pre-requisites:

   - Ubuntu EC2 up and running with at least t2.medium(4GB RAM), 2GB will not work
   - Port 8081, 8085 is opened in security firewall rule
   - instance should have docker and docker-compose installed

Change Host Name to Nexus
    
```sh
sudo hostnamectl set-hostname Nexus
```
    
Perform System update
    
```sh
sudo apt-get update
```
    
Install Docker-Compose
```sh
sudo apt-get install docker-compose -y
```

Add current user to Docker group
```sh
sudo usermod -aG docker $USER
```

Create docker-compose.yml
this yml has all the configuration for installing Nexus on Ubuntu EC2.
sudo vi docker-compose.yml 

Now execute the compose file using Docker compose command to start Nexus Container
```sh
sudo docker-compose up -d 
```

Make sure Nexus 3 is up and running
```sh
sudo docker-compose logs --follow
```

Now to go to browser --> http://change to_nexus_publicdns_name:8081

Get admin password by executing below command
```sh
sudo docker exec -it ubuntu_nexus_1 cat /nexus-data/admin.password
```

source
https://www.coachdevops.com/2022/01/install-sonatype-nexus-3-using-docker.html
