FROM debian:12

ENV REPO_MIRROR_URL "mirrors.ustc.edu.cn"

RUN set -eux; \
        \
    rm -rf /etc/apt/sources.list; \
    sed -i "s/deb.debian.org/${REPO_MIRROR_URL}/g" /etc/apt/sources.list.d/debian.sources; \
    apt-get update; \
    apt-get install -y curl git xz-utils; \
    cd /tmp; \
        \
    curl -SL -O "https://github.com/upx/upx/releases/download/v4.2.1/upx-4.2.1-amd64_linux.tar.xz"; \
    tar -xvf upx-*.tar.xz; \
    mv upx*/upx /usr/local/bin/; \
    upx --version; \
    rm -rf /tmp/*; \
        \
    curl -SL -O "https://download.docker.com/linux/static/stable/x86_64/docker-20.10.17.tgz"; \
    tar -xvf docker-*.tgz; \
    install -o root -g root -m 0755 ./docker/docker /usr/local/bin; \
    rm -rf /tmp/*; \
        \
    curl -SL -O "https://dl.k8s.io/release/v1.26.3/bin/linux/amd64/kubectl"; \
    install -o root -g root -m 0755 ./kubectl /usr/local/bin; \
    rm -rf /tmp/*; \
        \
    apt-get remove -y xz-utils; \
    apt-get autoremove -y; \
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/*; \
    rm -rf /tmp/*;

CMD [ "/bin/bash" ]


###
# Build command:
#   docker build --network host -t xqada2017/cicd-tools:v1-docker ./
###
