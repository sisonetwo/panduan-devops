## Management Container

Menampilkan semua container 

```sh
docker container ls
docker container ls -a
docker ps
docker ps -a
```

Menampilkan container dengan filter

```sh
docker ps --filter "label=env=testing"
docker ps -a --filter "label=env=testing"
docker ps -a --filter "name =postgres"
```

Start, Stop, Pause Containers

```sh
docker container stop my_db
docker container start my_db
docker container pause my_db
```

Menghapus container

```sh
docker container rm my_db
docker container rm -f my_db
docker container prune
docker container rm $(docker container ls -a --filter "label=env=testing" -q)
```

## management Images

Mempilkan Image

```sh
docker image ls
docker images
dpcker images postgres
```

menghapus docker image

```sh
docker rmi httpd
docker rmi $(docker images postgres)
```

Backup & Restore image

```sh
docker image save -o Downloads/backup-postgres.tar postgres:9.6
docker image save -o Downloads/backup-postgres.tar $(docker images -q)
docker image save -o Download/docker-images.tar $(docker images --format {{.Repository}}:{{.Tag}})
docker image load -i backup-postgres.tar
```

## Menjalankan container command

menjalankan container

```sh
docker run --name ubuntu_bash -d -i -t ubuntu:21.04
docker exec ubuntu_bash bash -c "mkdir -p /contoh && echo 'Halo, sedang belajar docker' > /contoh/test.txt"
docker exec ubuntu_bash ls -a /contoh
```

menajalakan interactive command

```sh
docker exec -it ubuntu_bash bash
docker exec -i -t -w /contoh -u root ubuntu_bash bash

```
