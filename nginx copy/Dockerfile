####################################
# Dockerfile to build NGINX image
####################################
# Base image
FROM nginx:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

# Add config
ADD nginx.conf /etc/nginx/

# Add page for default site
COPY index.html /usr/share/nginx/html

# Add configuration for custom site [Comment for default site]
#RUN rm /etc/nginx/conf.d/default.conf
#COPY site.conf /etc/nginx/conf.d/default.conf

# Expose web and SSL ports.
EXPOSE 80 443

# Set the default command to execute
CMD service nginx start
