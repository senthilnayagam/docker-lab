# ElasticSearch 0.90.0
#
# VERSION               0.0.1

FROM       fgrehm/openjdk7
MAINTAINER Fabio Rehm "fgrehm@gmail.com"

RUN apt-get install -y wget

RUN wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-0.90.0.deb -O /tmp/elasticsearch.deb -q

RUN dpkg -i /tmp/elasticsearch.deb

RUN rm /tmp/elasticsearch.deb

RUN apt-get remove -y wget

RUN apt-get clean

EXPOSE 9200