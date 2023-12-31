FROM debian:12

ENV REPO_MIRROR_URL "mirrors.ustc.edu.cn"
ENV ETCDCTL_API 3

RUN set -eux; \
        \
    cd /tmp; \
    rm -rf /etc/apt/sources.list; \
    sed -i "s/deb.debian.org/${REPO_MIRROR_URL}/g" /etc/apt/sources.list.d/debian.sources; \
    apt-get update; \
    apt-get -y install net-tools inetutils-ping procps curl; \
        \
    curl -fL -o "etcd-v3.5.9-linux-amd64.tar.gz" "https://github.com/etcd-io/etcd/releases/download/v3.5.9/etcd-v3.5.9-linux-amd64.tar.gz"; \
    tar -xvf etcd-*; \
    install -o root -g root -m 0755 etcd-*/etcd* /usr/local/bin/; \
    rm -rf ./*; \
        \
    apt-get autoremove -y; \
    apt-get clean -y; \
    rm -rf /var/lib/apt/lists/*; \
    rm -rf /tmp/*;

ENTRYPOINT [ "etcd" ]

# CMD [ "--logger=zap" ]


###
# Build Command:
#   docker build --network host -t xqada2017/etcd:3.5.9 ./
###
