##############################################
# Dockerfile to build Apache HTTP server image
##############################################
# Base image
FROM httpd:alpine

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

# Add page for default site
COPY index.html /usr/local/apache2/htdocs/

# Add configuration for custom site [Comment for default site]
#COPY httpd.conf /usr/local/apache2/conf/httpd.conf

# Install PHP and helper packages
RUN  apk update && apk upgrade && \

    apk add libressl && \
    apk add curl openssl && \
    apk add apache2-proxy && \

    apk add php7 php7-apache2 php7-openssl php7-mbstring && \
    apk add php7-apcu php7-intl php7-mcrypt php7-json php7-gd php7-curl && \
    apk add php7-fpm php7-mysqlnd php7-pgsql php7-sqlite3 php7-phar && \

    # fix compatible with old scripts
    ln -s /usr/bin/php7 /usr/bin/php && \

    # install composer
    cd /tmp && curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer && \

    #clear cache
    rm -rf /var/cache/apk/*

# Expose HTTP/HTTPS ports
EXPOSE 80 443
