# [autn/bagisto-nginx](https://github.com/autn/bagisto-nginx)

![docker hub](https://img.shields.io/docker/cloud/build/autn/bagisto-nginx.svg?style=flat-square)
![docker hub](https://img.shields.io/docker/pulls/autn/bagisto-nginx.svg?style=flat-square)
![docker hub](https://img.shields.io/docker/stars/autn/bagisto-nginx.svg?style=flat-square)

## Please open pull requests and issues on [https://github.com/autn/bagisto-nginx](https://github.com/autn/bagisto-nginx)

## Overview

This is a Dockerfile/image to build a container for nginx, php-fpm and nodejs, with the ability to pull website code from git when the container is created, as well as allowing the container to push and pull changes to the code to and from git. The container also has the ability to update templated files with variables passed to docker in order to update your code and settings. There is support for lets encrypt SSL configurations, custom nginx configs, core nginx/PHP variable overrides for running preferences, X-Forwarded-For headers and UID mapping for local volume support.

You can use this image for:

- Bagisto project
- Laravel project (Backend)
- Laravel project with Frontend (using nvm, yarn)

If you have improvements or suggestions please open an issue or pull request on the GitHub project page.

### Versioning

| Docker Tag | Git Release | Nginx Version | PHP Version | Alpine Version |
|-----|-------|-----|--------|--------|
| latest/0.1 | Master Branch |1.18.0 | 7.4.9 | 3.12 |

### Links

- [https://github.com/autn/bagisto-nginx](https://github.com/autn/bagisto-nginx)
- [https://hub.docker.com/r/autn/bagisto-nginx](https://hub.docker.com/r/autn/bagisto-nginx)

## Quick Start

To pull from docker hub:

```BASH
docker pull autn/bagisto-nginx:latest
```

### Running

To simply run the container:

```BASH
sudo docker run -d autn/bagisto-nginx
```

Docker compose:

```BASH
services:

  web_server:
    image: autn/bagisto-nginx:latest
    volumes:
      - ./src:/var/www/app
    working_dir: /var/www/app/
    ports:
      - '${WEB_PORT}:443'
    environment:
      - PHP_MEM_LIMIT=4048M
      - COMPOSER_MEMORY_LIMIT=4048M
    ...
```

You can then browse to ```https://<DOCKER_HOST>``` to view the default install files. To find your ```DOCKER_HOST``` use the ```docker inspect``` to get the IP address (normally 172.17.0.2)

For more detailed examples and explanations please refer to [richarvey/nginx-php-fpm the documentation](https://github.com/richarvey/nginx-php-fpm/blob/master/README.md#documentation).
