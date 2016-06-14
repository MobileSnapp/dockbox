# Apache HTTP server container for Dockbox

[![forthebadge](http://forthebadge.com/images/badges/built-by-developers.svg)](http://www.mobilesnapp.com)

Dockbox helps you run your PHP development environment on Docker. It provides all the virtual development environments that you would normally need for your PHP development. Dockbox is a tool that controls Docker for you (using Docker Compose official commands).

## Usage

    $ docker run -d -p 80:80 mobilesnapp/dockbox-apache
    
With all the options:
 
    $ docker run -d -p 80:80 \
        -v /home/user/app:/var/www/site \
        -e PHP_ERROR_REPORTING='E_ALL & ~E_STRICT' \
        mobilesnapp/dockbox-apache

-v [local path]:/var/www/site maps the container's webroot to a local path
-p [local port]:80 maps a local port to the container's HTTP port 80
-e PHP_ERROR_REPORTING=[php error_reporting settings] sets the value of error_reporting in the php.ini files.

With SSL options

    $ docker run -d -p 80:80 -p 443:443 \
        -v /home/user/app:/var/www/site \
        -e PHP_ERROR_REPORTING='E_ALL & ~E_STRICT' \
        mobilesnapp/dockbox-apache

## Access apache logs

Apache is configured to log both access and error log to STDOUT. So you can simply use docker logs to get the log output:

    docker logs -f container-id
    
## Configuration

.htaccess-Enabled in webroot (mod_rewrite with AllowOverride all)

## Author

MobileSnapp (support@mobilesnapp.com)
