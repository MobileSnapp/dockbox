# dockbox - PHP development environment with Docker

> Dockerized PHP development stack: Nginx, Apache2, PHP-FPM, HHVM, MySQL, MariaDB, PostgreSQL, MongoDB, Neo4j, RethinkDB, Minio, Redis, Memcached, Beanstalkd, RabbitMQ and Elasticsearch.

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://www.mobilesnapp.com)

### Dockerize your PHP development

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
5. Pre-configured NGINX for Laravel. (Setup for Symfony, Phalcon and Silex coming soon...)


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


## Requirements

* [Docker Engine](https://docs.docker.com/installation/)
* [Docker Compose](https://docs.docker.com/compose/)
* [Docker Machine](https://docs.docker.com/machine/) (Mac and Windows only)


## Web Configuration

Dockbox currently follows generic 'Zend/Laravel/Lumen' folder structure assuming that the hosting files are loacated under 'public' directory. Support for other framework (Symfony, Phalcon, Silex) coming soon.

```
Web root folder: '/var/www/site/public'
```

For Apache, default web configuration setup is available as dockbox default. Uncomment custom configuration in apache/Dockerfile for custom/generic (Zend/Laravel/Lumen) configuration.

## Database Configuration

Granting permisssion to database users

##### MySQL/MariaDB
```
'GRANT ALL PRIVILEGES ON * . * TO 'sitedb_user'@'localhost';'
```
More details: [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

##### PosgreSQL
```
'ALTER USER sitedb_user WITH SUPERUSER;'
```
More details: [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2)


## Installation and Usage

1. Clone dockbox inside your PHP project (Zend/Laravel/Lumen):
```
git clone https://github.com/MobileSnapp/dockbox.git
```

2. Your folder structure should look like this:
```
+ php-project
    + dockbox
```

3. Build the enviroment and run it using docker-compose:
Run NGINX (web server) and MySQL (database engine) to host a PHP web project:
```
docker-compose up -d nginx mysql
```
You can select your own combination of containers form the list below:
> nginx (PHP_FPM included), apache, hhvm, mariadb, mysql, postgres, mongo, minio, rethinkdb, redis, memcached, rabbitmq, beanstalkd, node, elasticsearch, neo4j, mailhog, selenium grid and more…!

**Note:** The data container will run automatically in most of the cases, so no need to specify them in the up command. It will setup the project folder and stop. 

Dockbox is setup to run management console with the following containers:
> mariadb, mysql, progres, rabbitmq, beanstalkd

*Comment 'links' section in 'docker-compose' file to detach the management console.*

4. Enter apache/nginx container, to execute commands like (Composer, PHPUnit …):
For apache: 
```
docker-compose exec dockbox-apache bash
```

For nginx:
```
docker-compose exec dockbox-nginx bash
```

Alternatively, for Windows PowerShell users: execute the following command to enter any running container:
```
docker exec -it {workspace-container-id} bash
```

5. Enter the node container, to execute commands like (Artisan, Gulp, …):
```
docker-compose exec dockbox-node bash
```

6. Update your project configurations:
DB_HOST=dockbox-mysql
REDIS_HOST=dockbox-redis
QUEUE_HOST=dockbox-rabbitmq

7.  Open your browser and visit localhost: http://localhost.


## Run Commands

Container  | Command   |
---------- | --------- |
apache                | docker-compose up -d apache                |
nginx                 | docker-compose up -d nginx                 |
hhvm                  | docker-compose up -d hhvm                  |
mariadb               | docker-compose up -d mariadb               |
mysql                 | docker-compose up -d mysql                 |
postgres              | docker-compose up -d postgres              |
mongo                 | docker-compose up -d mongo                 |
minio                 | docker-compose up -d minio                 |
rethinkdb             | docker-compose up -d rethinkdb             |
redis                 | docker-compose up -d redis                 |
memcached             | docker-compose up -d memcached             |
rabbitmq              | docker-compose up -d rabbitmq              |
beanstalkd            | docker-compose up -d beanstalkd            |
node                  | docker-compose up -d node                  |
elasticsearch         | docker-compose up -d elasticsearch         |
neo4j                 | docker-compose up -d neo4j                 |
mailhog               | docker-compose up -d mailhog               |      
docker registry       | docker-compose up -d docker-registry       |
selenium chrome node  | docker-compose up -d selenium-chrome-node  |
selenium firefox node | docker-compose up -d selenium-firefox-node |
 
**Note:** Selenium chrome/firefox node will bring up Selenium Hub container and attach to Selenium Hub.


## References

1. [Docker for php developers](http://www.newmediacampaigns.com/blog/docker-for-php-developers)
2. [PHP Web development with docker](http://mmenozzi.github.io/2016/01/22/php-web-development-with-docker/)
3. [webdevops docker](https://github.com/webdevops/Dockerfile)
4. [laradock](https://github.com/LaraDock/laradock)
5. [php-dockerized](https://github.com/kasperisager/php-dockerized)


## License

* Copyright 2017 [MobileSnapp Inc.](http://www.mobilesnapp.com)
* Distributed under the MIT License (hereby included)
