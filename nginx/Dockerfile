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
ADD site.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/site.conf /etc/nginx/sites-enabled

# Assign working directory
WORKDIR /var/www/site/

# Expose web and SSL ports.
EXPOSE 80
EXPOSE 443

# Set the default command to execute
# when creating a new container
CMD service nginx start

# Define default command.
#CMD ["nginx"]