ARG LOGSTASH_VERSION="7.17.10"
FROM arm64v8/logstash:${LOGSTASH_VERSION}

# Install the logstash-input-http_poller plugin
RUN logstash-plugin install logstash-input-http_poller
RUN logstash-plugin install logstash-codec-csv
RUN logstash-plugin install logstash-filter-csv
