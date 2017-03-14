##########################################
# Dockerfile for Beanstalkd console image
###########################################
# Base image
FROM debian:wheezy

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

# Install beanstalkd
ADD install.sh install.sh
RUN chmod +x install.sh && ./install.sh && rm install.sh

# Expose port
EXPOSE 11300

CMD ["beanstalkd", "-p", "11300"]