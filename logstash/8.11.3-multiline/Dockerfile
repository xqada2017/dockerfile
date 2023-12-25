FROM docker.elastic.co/logstash/logstash:8.11.3

USER 0

RUN set -sux; \
    /usr/share/logstash/bin/logstash-plugin install logstash-filter-multiline

USER 1000


###
# Build Command:
#   docker build --network host -t xqada2017/logstash:8.11.3-multiline ./
###
