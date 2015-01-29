# DOCKER-VERSION 1.3.1

# Base image
FROM dockerfile/java:oracle-java7

# Vars
ENV LOGSTASH_CONF_URL http://hitu1.trrt.me/misc

# Install LogStash
RUN cd /tmp && \
    wget https://download.elasticsearch.org/logstash/logstash/logstash-1.4.2.tar.gz && \
    tar xzvf ./logstash-1.4.2.tar.gz && \
    mv ./logstash-1.4.2 /opt/logstash && \
    rm ./logstash-1.4.2.tar.gz

# Install contrib plugins
RUN /opt/logstash/bin/plugin install contrib

# COPY logstash.conf /etc/logstash.conf
ADD $LOGSTASH_CONF_URL/logstash.conf /etc/logstash.conf

# Expose port for clients (not needed?)
# EXPOSE 5000

# Container can run as an executable
ENTRYPOINT ["/opt/logstash/bin/logstash"]
