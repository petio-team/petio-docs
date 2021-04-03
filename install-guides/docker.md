---
description: >-
  If you notice any mistakes that need to be corrected, please reach out on
  Discord!
---

# Docker

We will go over how to install Petio using [Docker](https://docs.docker.com/engine/) or [Docker Compose](https://docs.docker.com/compose/). We assume you have installed Docker and/or Docker Compose. 

{% hint style="info" %}
**NOTE:** This guide will not walk you through how to install or configure any of these two services.
{% endhint %}

### Docker CLI

```text
docker run --rm \
    --name petio \
    -p 7777:7777 \
    -e TZ="Etc/UTC" \
    --user 1000:1000 \
    -v /<host_folder_config>:/app/api/config \
    ghcr.io/petio-team/petio
```

```text
docker run --rm \
    --name mongo \
    -e TZ="Etc/UTC" \
    --user 1000:1000 \
    -v /<host_folder_db>:/data/db \
    mongo
```

### Docker Compose

There are two ways you can install Petio using Docker Compose. You can either download the `docker-compose.yml` from the repo and place it in a folder where you will run `docker-compose` from or you can add it to an existing `docker-compose.yml`.

To download the Docker Compose file you run the following command:

```bash
curl -OL https://github.com/petio-team/petio/raw/master/docker-compose.yml -o /path/to/location
```

Below you can find an example for the `docker-compose.yml`. In this example, `petio` and `mongo` are on a custom docker network called `petio-network`

```yaml
version: '3'

networks:
    petio-network:
        driver: bridge

services:
    petio:
        image: ghcr.io/petio-team/petio:latest
        container_name: 'petio'
        hostname: petio
        ports:
            - '7777:7777'
        networks:
            - petio-network
        user: '1000:1000'
        depends_on:
            - mongo
        environment:
            - TZ=Etc/UTC
        volumes:
            - ./config:/app/api/config
            - ./logs:/app/logs

    mongo:
        image: mongo:latest
        container_name: 'mongo'
        hostname: mongo
        ports:
            - '27017:27017'
        networks:
            - petio-network
        user: '1000:1000'
        volumes:
            - ./db:/data/db
```

Once you configure the services, you need to spin up the container using `docker-compose up -d`. 

Once the container is spun up, you can navigate to `http://<hostname>:7777` to start [configuring Petio](../configuration/first-time-setup.md).

