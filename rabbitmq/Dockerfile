################################
# Dockerfile for RabbitMQ image
################################
# Base image
FROM rabbitmq:latest

# Author: MobileSnapp Inc.
MAINTAINER MobileSnapp <support@mobilesnapp.com>

RUN rabbitmq-plugins enable --offline rabbitmq_management

# Expose ports
EXPOSE 4369 5671 5672
EXPOSE 15672 25672

CMD ["rabbitmq-server"]