####################################
# Dockerfile to build NGINX image
####################################
# Base image
FROM ubuntu:16.04

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

RUN locale-gen en_US.UTF-8

ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN apt-get update \
    && apt-get install -y nginx curl zip unzip git software-properties-common supervisor sqlite3 \
    && add-apt-repository -y ppa:ondrej/php \
    && apt-get update \
    && apt-get install -y php7.1-fpm php7.1-cli php7.1-mcrypt php7.1-gd php7.1-mysql \
       php7.1-pgsql php7.1-imap php-memcached php7.1-mbstring php7.1-xml php7.1-curl \
       php7.1-bcmath php7.1-sqlite3 php7.1-xdebug \
    && apt-get -y --no-install-recommends install php-redis php7.1-bz2 php7.1-dba php7.1-enchant \
       php-gearman php-igbinary php-imagick php7.1-interbase php7.1-intl php7.1-ldap php-msgpack \
       php7.1-odbc php7.1-phpdbg php7.1-pspell php-raphf php7.1-recode php7.1-snmp php7.1-soap \
       php-ssh2 php7.1-sybase php7.1-tidy php7.1-xmlrpc php7.1-xsl php-yaml php-tideways php-xhprof php-zmq \
    && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && mkdir /run/php \
    && apt-get remove -y --purge software-properties-common \
    && apt-get -y autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* \
    && echo "daemon off;" >> /etc/nginx/nginx.conf \
    && ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log

COPY default /etc/nginx/sites-available/default
COPY php-fpm.conf /etc/php/7.1/fpm/php-fpm.conf
COPY xdebug.ini /etc/php/7.1/mods-available/xdebug.ini

# Add default page
COPY index.html /var/www/site/public

# Expose HTTP/HTTPS ports
EXPOSE 80 443

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY start-container /usr/local/bin/start-container
RUN chmod +x usr/local/bin/start-container

CMD ["start-container"]
