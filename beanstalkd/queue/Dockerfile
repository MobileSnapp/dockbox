##########################################
# Dockerfile for Beanstalkd console image
###########################################
# Base image
FROM phusion/baseimage:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

ENV DEBIAN_FRONTEND noninteractive
ENV PATH /usr/local/rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

# Install beanstalkd
RUN apt-get update
RUN apt-get install -y beanstalkd
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

VOLUME /var/lib/beanstalkd/data

# Expose port
EXPOSE 11300

CMD ["/usr/bin/beanstalkd"]
