# DOCKER-VERSION 1.3.1

# Base image
FROM dockerfile/java:oracle-java7

# Variable
# ENV ES_PKG_NAME elasticsearch-1.4.0

# Install ElasticSearch
RUN wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.0.tar.gz -O elasticsearch.tar.gz && tar zxf elasticsearch.tar.gz && mv elasticsearch-* /opt/elasticsearch && rm -rf /tmp/*

# Copy ElasticSearch config file from host to container /opt
COPY elasticsearch.yml /opt/elasticsearch/config/elasticsearch.yml

# Expose needed ports
EXPOSE 9200
EXPOSE 9300

# Create a mountpoint for host or other containers
VOLUME /opt/elasticsearch/data

# Container can run as an executable
ENTRYPOINT ["/opt/elasticsearch/bin/elasticsearch"]
