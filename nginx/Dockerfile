####################################
# Dockerfile to build NGINX image
####################################
# Base image
FROM nginx:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

# Add docker config
ADD nginx.conf /etc/nginx/

# Add configuration for custom site [Comment it for default site]
RUN rm /etc/nginx/conf.d/default.conf
ADD site.conf /etc/nginx/conf.d/

# Assign working directory
WORKDIR /var/www/site/

# Expose web and SSL ports.
EXPOSE 80 443

# Set the default command to execute
# when creating a new container
CMD service nginx start

# Define default command.
#CMD ["nginx"]