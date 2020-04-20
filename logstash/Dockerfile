ARG ELK_VERSION

# https://www.docker.elastic.co/
FROM docker.elastic.co/logstash/logstash:${ELK_VERSION}

# Delete logstash.conf example config from the base image
RUN rm -f /usr/share/logstash/pipeline/logstash.conf

# Install jdbc input plugin
RUN logstash-plugin install logstash-integration-jdbc

# Add mysql connector
COPY config/mysql-connector-java-8.0.19.jar /usr/share/logstash/logstash-core/lib/jars/

# Add last run files directory
RUN mkdir /usr/share/logstash/lastrun && \
    chmod 777 /usr/share/logstash/lastrun