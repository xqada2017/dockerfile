FROM debian:12

ENV TINI_VERSION v0.19.0

ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/local/bin/tini

RUN set -eux; \
        \
    chmod +x /usr/local/bin/tini;

ENTRYPOINT [ "tini", "--" ]

# CMD [ "/bin/bash", "-c", "tail -f /dev/null" ]


###
# Build command:
#   docker build --network host -t xqada2017/tini:0.19.0 ./
###
