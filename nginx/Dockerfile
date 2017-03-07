####################################
# Dockerfile to build NGINX image
####################################
# Base image
FROM nginx:alpine

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

# Add page for default site
#COPY index.html /usr/share/nginx/html

# Add configuration for custom site [Comment for default site]
RUN rm /etc/nginx/conf.d/default.conf
COPY site.conf /etc/nginx/conf.d/default.conf

# Add config
COPY nginx.conf /etc/nginx/nginx.conf

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log

# Expose HTTP/HTTPS ports
EXPOSE 80 443

ENTRYPOINT ["/usr/sbin/nginx"]