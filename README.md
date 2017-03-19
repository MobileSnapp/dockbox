# dockbox - Dockerize your PHP development

> Dockerized PHP development stack: Nginx, Apache2, PHP-FPM, HHVM, MySQL, MariaDB, PostgreSQL, MongoDB, Neo4j, RethinkDB, Minio, Redis, Memcached, Beanstalkd, RabbitMQ and Elasticsearch.

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://www.mobilesnapp.com)

Dockbox allows you to containerize your PHP application. 

Dockbox gives you everything you need for developing PHP applications locally. It provides an OS-agnostic and virtualized alternative to MNPP stack. Dockbox tries to keep download file size to a minimum by utilizing official docker images.

## Quick Setup

```
# Clone dockbox inside your PHP project (Laravel):
git clone https://github.com/MobileSnapp/dockbox.git

# Run your containers:
docker-compose up -d nginx mysql redis rabbitmq elasticsearch

# (For Laravel) Open your project’s .env file and set the following:
DB_HOST=dockbox-mysql
REDIS_HOST=dockbox-redis
QUEUE_HOST=dockbox-rabbitmq

# Open your browser and visit localhost: http://localhost.

```

## Features

1. Official and rated Docker images
2. Every software runs as a separate container
3. Easy to apply configurations inside containers.
4. Faster image and container builds.


## Supported Containers

#### Database Engines
- MySQL
- MariaDB
- PostgreSQL
- MongoDB
- Neo4j
- RethinkDB
- Minio

#### Cache Engines
- Redis
- Memcached

#### Web Servers/Compilers
- Apache2
- Nginx
- PHP (included in Apache2 container)
- PHP-FPM (included in Nginx container)
- HHVM

#### Message Queues
- Beanstalkd (includes console)
- RabbitMQ (includes console)

#### Management Consoles
- PhpMyAdmin (for MySQL/MariaDB)
- PgAdmin (for PostgreSQL)

#### Additional
- Elasticsearch
- Node
- Mailhog
- Selenium Grid
- Docker Registry


## Web Configuration

## Database Configuration



# License

* Copyright 2017 [MobileSnapp Inc.](http://www.mobilesnapp.com)
* Distributed under the MIT License (hereby included)