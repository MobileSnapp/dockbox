####################################
# Dockerfile to build Node image
####################################
# Base image
FROM node:alpine

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

# Install extentions and tools
RUN apt-get update && apt-get install -y \
        git \
        npm \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install gulp and bower with NPM
RUN npm install -g \
    gulp \
    bower \
    grunt-cli

# Link the global gulp to be used locally
RUN npm link gulp
