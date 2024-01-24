# Superset: Task 2

**Task:** Installation of Apache Superset on your Local-system, Explore about this and execute this task.

In this document we learn to install apache superset on our local system with the help of `docker compose`

## Prerequisites

* git
* docker

## Steps

1. Cloning superset repository

    ```bash
    git clone https://github.com/apache/superset.git
    ```

2. For the stable version of superset we need to checkout to `3.0.0` git branch

    ```bash
    cd superset
    git checkout 3.0.0
    ```

3. Setting environment variables
    Setting environment variables into file `./docker/.env` or `./docker/.env-non-dev`. Set values of some important variables like `SUPERSET_SECRET_KEY`.

    You can create a random secret using openssl CLI

    ```bash
    openssl rand -base64 42
    ```

4. Running a production instance of the superset

    ```bash
    # -d is optional either we want to run it in detached mode or not
    docker compose -d -f ./docker-compose-non-dev.yml up

    # or we can use custom superset image by providing a tag
    TAG=3.0.0 docker compose -d -f ./docker-compose-non-dev.yml up
    ```

5. Accessing superset
    Goto this [page](http://localhost:8088) at `http://localhost:8088`
    * username: admin
    * password: admin

6. Creating different users
    We can also create other users as well with the help of superset cli by login in into `superset_app` container

    ```bash
    docker exec -it superset_app /bin/bash
    ```

    After successfully login run below command and put information

    ```bash
    superset fab create-user
    ```

7. Creating a new Admin user
    Just like users we can also able to create a Admin user

    ```bash
    superset fab create-admin
    ```
