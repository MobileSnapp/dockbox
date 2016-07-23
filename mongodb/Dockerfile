##################################
# Dockerfile for MongoDB image
##################################
# Base image
FROM mongo:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

RUN usermod -u 1000 mongodb
RUN chown -R `id -u` /data/db

#VOLUME /data/db /data/configdb

# Expose port
EXPOSE 27017

CMD ["mongod"]


