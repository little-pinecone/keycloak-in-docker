# keycloak-in-docker

[![keep_growing logo](readme-images/logo_250x60.png)](https://keepgrowing.in/)

## About this project

This simple project shows an example Docker configuration for Keycloak.

To learn how to set up a project like this one, check out the following articles:

* [Keycloak in Docker #1 – How to run Keycloak in a Docker container](https://keepgrowing.in/tools/keycloak-in-docker-1-how-to-run-keycloak-in-a-docker-container/)

## Getting started

First, [clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository)
this repository.

Then, start the `keycloak` and `keycloakdb` containers with the following command:

```shell
docker-compose -f docker-compose-keycloak.yml up -d
```

### Credentials

Below you'll find a list of default user accounts.

#### Keycloak admin

* username: `keycloak`
* password: `keycloak`

### Visit Keycloak

* Make sure that the `keycloak` container is up. For instance, you can run the `docker ps` command in your terminal:

![docker container list screenshot](readme-images/docker-container-list.png)

* Visit the [http://localhost:8024/auth](http://localhost:8024/auth) url:

![keycloak welcome screen screenshot](readme-images/welcome-screen.png)

* Choose the `Administration Console` option and log in as the Keycloak admin [`keycloak:keycloak`]:

![keycloak login screen screenshot](readme-images/keycloak-login.png)

## Features

* Dockerized Keycloak server and its PostgreSQL database

## Built With

* [Keycloak](https://www.keycloak.org/)
* [Docker Compose](https://docs.docker.com/compose/)
