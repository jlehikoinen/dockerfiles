# DOCKER-VERSION 1.3.1

# Base image
FROM centos:centos6

# Update OS
RUN yum update -y

# Install tar, wget & Java 7
RUN yum -y install tar
RUN yum -y install wget
RUN yum -y install java-1.7.0-openjdk.x86_64

# Set JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-1.7.0-openjdk.x86_64

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
