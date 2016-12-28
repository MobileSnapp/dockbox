####################################
# Dockerfile to build NGINX image
####################################
# Base image
FROM nginx:latest

# Remove the default Nginx configuration file
RUN rm /etc/nginx/conf.d/default.conf
RUN rm /etc/nginx/conf.d/example_ssl.conf
#RUN rm -v /etc/nginx/nginx.conf

# Copy custom site 
# Comment it if using PHP
COPY index.html /usr/share/nginx/html

# Copy a configuration file from the current directory
# NOTE: Add configuration for static site
# Comment it if using PHP
ADD site.conf /etc/nginx/

# NOTE: Add configuration for PHP
# Comment it if using static site
#ADD nginx.conf /etc/nginx/

# Append "daemon off;" to the beginning of the configuration
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

RUN chown -R www-data:www-data /var/lib/nginx

# Assign working directory
WORKDIR /var/www/site/

# Expose ports
EXPOSE 80
EXPOSE 443

# Set the default command to execute
# when creating a new container
CMD service nginx start

# Define default command.
#CMD ["nginx"]