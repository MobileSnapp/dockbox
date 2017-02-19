##############################################
# Dockerfile to build commons support image
##############################################
# Base image
FROM phusion/baseimage:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

RUN DEBIAN_FRONTEND=noninteractive
RUN locale-gen en_US.UTF-8

ENV LANGUAGE=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV LC_CTYPE=UTF-8
ENV LANG=en_US.UTF-8
ENV TERM xterm

# Install "software-properties-common" (for the "add-apt-repository")
RUN apt-get update && apt-get install -y \
    software-properties-common \
    supervisor \
&& apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Add the "PHP 7" ppa
RUN add-apt-repository -y \
    ppa:ondrej/php

# Install PHP-CLI 7, extentions and tools
RUN apt-get update && apt-get install -y \
        php7.1-cli \
        php7.1-common \
        php7.1-curl \
        php7.1-json \
        php7.1-xml \
        php7.1-mcrypt \
        php7.1-zip \
        php-memcached \
        php7.1-mcrypt \
        php7.1-mongodb \
        php7.1-mysql \
        php7.1-pgsql \
        php-redis \
        php7.1-sqlite3 \
        php7.1-bz2 \
        php7.1-dba \
        php7.1-bcmath \
        php7.1-enchant \
        php7.1-gd \
        php7.1-geoip \
        php7.1-gmp \
        php7.1-igbinary \
        php7.1-imap \
        php7.1-interbase \
        php7.1-intl \
        php7.1-ldap \
        php7.1-mbstring \
        php-msgpack \
        php7.1-odbc \
        php7.1-phpdbg \
        php7.1-pspell \
        php7.1-recode \
        php7.1-snmp \
        php7.1-soap \
        php7.1-ssh2 \
        php7.1-sybase \
        php7.1-tidy \
        php7.1-xmlrpc \
        php7.1-zip \
        php7.1-xsl \
        php7.1-opcache \
        php7.1-readline \
        php-gearman \
        php-imagick \
        php-raphf \
        php-yaml \
        php-tideways \
        php-xhprof \
        php-xdebug \
        php-zmq \
        php-apcu \
        php-apcu-bc \
        php-libsodium \
        php-dev \
        libcurl4-openssl-dev \
        libedit-dev \
        libssl-dev \
        libxml2-dev \
        libsslcommon2-dev \
        xz-utils \
        sqlite3 \
        libsqlite3-dev \
        cron \
        git \
        curl \
        zip \
        unzip \
        vim \
        nano \
        nodejs \
        nodejs-dev \
        npm \
        graphicsmagick \
        libgraphicsmagick1-dev \
        nano \
        wget \
        dialog \
        net-tools \
        pkg-config \
    && apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install gulp and bower with NPM
RUN npm install -g \
    gulp \
    bower \
    grunt-cli

# Link the global gulp to be used locally
RUN npm link gulp

# Add a symbolic link for Node
RUN ln -s /usr/bin/nodejs /usr/bin/node

# Add an alias for PHPUnit
RUN echo "alias phpunit='./vendor/bin/phpunit'" >> ~/.bashrc

# Install Composer
ENV COMPOSER_HOME /root/composer
RUN curl -s http://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/ \
    && echo "alias composer='/usr/local/bin/composer.phar'" >> ~/.bashrc
ENV PATH $COMPOSER_HOME/vendor/bin:$PATH

# Install mongodb extension
RUN pecl install mongodb
#RUN echo "extension=mongodb.so" >> /etc/php/7.1/cli/php.ini
RUN echo "extension=mongodb.so" >> `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"`

# Source the bash
RUN . ~/.bashrc

# Clean up, to free some space
RUN apt-get remove -y --purge software-properties-common \
    && apt-get -y autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /var/www/site