# keycloak-in-docker

[![keep_growing logo](readme-images/logo_250x60.png)](https://keepgrowing.in/)

## About this project

This simple project shows an example Docker configuration for Keycloak.

To learn how to set up a project like this one, check out the following articles:

* [Keycloak in Docker #1 – How to run Keycloak in a Docker container](https://keepgrowing.in/tools/keycloak-in-docker-1-how-to-run-keycloak-in-a-docker-container/)
* [Keycloak in Docker #2 – How to import a Keycloak realm](https://keepgrowing.in/tools/keycloak-in-docker-2-how-to-import-a-keycloak-realm/)
* [Keycloak in Docker #3 – How to customise Keycloak themes](https://keepgrowing.in/tools/keycloak-in-docker-3-how-to-customise-keycloak-themes/)

## Getting started

First, [clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository)
this repository.

Then, start the `keycloak` and `keycloakdb` containers with the following command:

```shell
docker-compose -f docker-compose-keycloak.yml up -d
```

Make sure that the `keycloak` container is up. For instance, you can run the `docker ps` command in your terminal:

![docker container list screenshot](readme-images/docker-container-list.png)

The `keycloak` service has a default realm imported from the
[keycloak/realms/realm-export.json](keycloak/realms/realm-export.json) file that specifies all the default users.
 Information about the import can be found in the container logs when the service is started for the first time:  

![imported realm info in container logs screenshot](readme-images/imported-realm-in-logs.png)

### Credentials

Below you'll find a list of default user accounts.

#### Keycloak admin

* username: `keycloak`
* password: `keycloak`

#### Default users

* usernames: `christina`, `hanna`, `carlo`, `noel`
* password: `test`
* realm role: `user`

### Visit Keycloak

* Visit the [http://localhost:8024/auth](http://localhost:8024/auth) url:

![keycloak welcome screen screenshot](readme-images/welcome-screen.png)

* Select the `Administration Console` option and log in as the Keycloak admin [`keycloak:keycloak`]:

![keycloak login screen screenshot](readme-images/keycloak-login.png)

* As an admin you can see a list of users associated with the `Example-Realm` realm by clicking the `View all users` button on the
  [http://localhost:8024/auth/admin/master/console/#/realms/Example-Realm/users](http://localhost:8024/auth/admin/master/console/#/realms/Example-Realm/users) page.
* What's more, you can log in as any user associated with the `Example-Realm` realm by clicking the `Sign in` button on the
  [http://localhost:8024/auth/realms/Example-Realm/account](http://localhost:8024/auth/realms/Example-Realm/account) page.
* The realm roles are available under the [http://localhost:8024/auth/admin/master/console/#/realms/Example-Realm/roles](http://localhost:8024/auth/admin/master/console/#/realms/Example-Realm/roles) url.

## Features

* Dockerized Keycloak server and its PostgreSQL database
* Default Example-Realm is imported when the `keycloak` container starts
* Keycloak themes are customized for the Login and Account types:

![customised login page screenshot](readme-images/login-customised.png)

![customised account page screenshot](readme-images/account-customised.png)

## Deploying to production

The Keycloak theme caching is disabled to allow for fast and convenient theme editing. Remember to re-enable caching in 
production as it will significantly impact performance. To do this, remove the 
`- ./keycloak/scripts/disable-theme-cache.cli:/opt/jboss/startup-scripts/disable-theme-cache.cli` volume from the
[docker-compose-keycloak.yml](docker-compose-keycloak.yml) file.

## Built With

* [Keycloak](https://www.keycloak.org/)
* [Docker Compose](https://docs.docker.com/compose/)
