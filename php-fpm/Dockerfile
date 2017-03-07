####################################
# Dockerfile to build PHP-FPM image
####################################
# Base image
FROM php:fpm

# Copy configuration
COPY php-fpm.conf /etc/php/7.1/fpm/php-fpm.conf
COPY xdebug.ini /etc/php/7.1/mods-available/xdebug.ini

# Assign working directory
WORKDIR /var/www/site/

CMD ["php", "-a"]