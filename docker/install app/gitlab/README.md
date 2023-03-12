## Configuration for Docker Compose

We will start work on the installation by creating a dedicated directory in which we will store data and Gitlab configuration.

```sh
mkdir gitlab
```

For convenience, we will also set an environment variable that will contain the path to our Gitlab directory:

```sh
export GITLAB_HOME=$(pwd)/gitlab
```

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
