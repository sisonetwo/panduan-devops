## Configuration for Docker Compose

We will start work on the installation by creating a dedicated directory in which we will store data and Gitlab configuration.

```sh
mkdir gitlab
```

For convenience, we will also set an environment variable that will contain the path to our Gitlab directory:

```sh
export GITLAB_HOME=$(pwd)/gitlab
```

Perform System update
sudo apt-get update

Install Docker-Compose
sudo apt-get install docker-compose -y

In the next step, we create the docker-compose.yml file 

Containers are started using the command:

```sh
docker-compose up -d
```

To log in to GitLab for the first time, you need a temporary password, which is generated automatically during installation. We get the password using the command:

```sh
docker exec -it gitlab-ce grep 'Password:' /etc/gitlab/initial_root_password
```

GitLab launching
Our GitLab is available at: `http://localhost:8080`

The last change we will make is to change the password. To do this, go to the page: `ost:8080/-/profile/password/edit` 

##GitLab runner configuration

go to the address: `http://localhost:8080/admin/runners` and click the `Copy token` button

In the next step, it goes to the console and run the following command:

```sh
docker exec -it gitlab-runner gitlab-runner register --url "http://gitlab-ce" --clone-url "http://gitlab-ce"
```

we also need to allow access for containers launched from the runner to the virtual network in which GitLab operates

```sh
sudo vi gitlab/gitlab-runner/config.toml
```

Then we add new line to the end of the runner configuration: network_mode = “gitlab-network”

To check if the runner is available from the GitLab level, go to the following address:http://localhost:8080/admin/runners


source
https://www.czerniga.it/2021/11/14/how-to-install-gitlab-using-docker-compose/
