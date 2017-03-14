####################################
# Dockerfile to build HHVM image
####################################
# Base image
FROM hhvm/hhvm-proxygen:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

#RUN rm -rf /var/www
ADD index.html /var/www/public

# Setup FastCGI support using HHVM [Uncomment to use with Apache container]
#RUN /usr/share/hhvm/install_fastcgi.sh

EXPOSE 80
