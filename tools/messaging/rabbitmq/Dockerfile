# jamescarr/rabbitmq
#
# A docker container running rabbitmq 3.1.1
# version 0.1.1

FROM base

MAINTAINER James R. Carr <jame@zapier.com>

RUN apt-get install -y wget
RUN echo "deb http://www.rabbitmq.com/debian/ testing main" >> /etc/apt/sources.list
RUN wget http://www.rabbitmq.com/rabbitmq-signing-key-public.asc
RUN apt-key add rabbitmq-signing-key-public.asc
RUN apt-get update

# Create dirs that rabbitmq-server wants
RUN mkdir -p /var/lib/ /var/log
RUN apt-get install -y rabbitmq-server || true
RUN rabbitmq-plugins enable rabbitmq_management

EXPOSE 5672, 15672

CMD ["rabbitmq-server"]