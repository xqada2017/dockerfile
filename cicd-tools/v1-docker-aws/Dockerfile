FROM xqada2017/cicd-tools:v1-docker

RUN set -eux; \
        \
    cd /tmp; \
    apt-get update; \
    apt-get install -y zip less; \
        \
    curl -SL -O "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip"; \
    unzip awscli-*.zip; \
    ./aws/install; \
    rm -rf ./*; \
        \
    apt-get remove -y zip; \
    apt-get autoremove -y; \
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/*; \
    rm -rf /tmp/*;

CMD [ "/bin/bash" ]


###
# Build command:
#   docker build --network host -t xqada2017/cicd-tools:v1-docker-aws ./
###
