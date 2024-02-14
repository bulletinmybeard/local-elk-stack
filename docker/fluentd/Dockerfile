ARG FLUENTD_VERSION="1.16-1"
ARG GEM_ELASTICSEARCH_VERSION="7.17.10"
ARG GEM_FLUENT_PLUGIN_ELASTICSEARCH_VERSION="5.3.0"

FROM arm64v8/fluentd:v${FLUENTD_VERSION}

USER root

# Downgrade packages to make everything work with Elasticsearch/Kibana v7.x
RUN gem install elasticsearch -v "${GEM_ELASTICSEARCH_VERSION}"

# Install fluentd plugins
RUN gem install fluent-plugin-elasticsearch -v "${GEM_FLUENT_PLUGIN_ELASTICSEARCH_VERSION}"
RUN gem install \
    fluent-plugin-multi-format-parser \
    fluent-plugin-rewrite-tag-filter \
    fluent-plugin-grok-parser

# Install additional packages including bash shell (Alpine Linux)
RUN apk add --no-cache --update \
    bash \
    curl

USER fluent
