FROM alpine:3.15 as builder
LABEL mainainer='frutti93'
ARG BORG_VERSION=1.1.17
ARG BORGMATIC_VERSION=1.5.21
ARG RCLONE_VERSION=v1.57.0
ARG LLFUSE_VERSION=1.4.1
RUN apk upgrade --no-cache \
    && apk add --no-cache \
    alpine-sdk \
    python3-dev \
    py3-pip \
    openssl-dev \
    lz4-dev \
    acl-dev \
    linux-headers \
    fuse-dev \
    attr-dev \
    py3-wheel 
RUN ARCH=`uname -m` && \
    echo ${ARCH} &&\
    if [ "$ARCH" == "x86_64" ]; then \
        ARCHITECTURE="amd64"; \
    elif [ "$ARCH" == "aarch64" ]; then \
        ARCHITECTURE="arm64"; \
    elif [ "$ARCH" == "armv7l" ]; then \
        ARCHITECTURE="arm-v7"; \
    elif [ "$ARCH" == "armv6l" ]; then \
        ARCHITECTURE="arm"; \
    else \
       echo "unknown arch"; \
    fi \
    && echo ${ARCHITECTURE} \
    && cd /tmp \
    && wget -q https://downloads.rclone.org/${RCLONE_VERSION}/rclone-${RCLONE_VERSION}-linux-${ARCHITECTURE}.zip \
    && unzip -q rclone*.zip \
    && cd rclone-*-linux-${ARCHITECTURE} \
    && cp rclone /usr/bin \
    && chmod 755 /usr/bin/rclone
RUN pip3 install --upgrade pip \
    && pip3 install --upgrade \
    borgbackup==${BORG_VERSION} \
    borgmatic==${BORGMATIC_VERSION} \
    llfuse==${LLFUSE_VERSION}


FROM alpine:3.15
LABEL mainainer='frutti93'
COPY entry.sh /entry.sh
RUN apk upgrade --no-cache \
    && apk add --no-cache \
    tzdata \
    sshfs \
    python3 \
    openssl \
    fuse \
    ca-certificates \
    lz4-libs \
    libacl \
    postgresql-client \
    mariadb-client \
    curl \
    docker \
    && rm -rf /var/cache/apk/* \
    && chmod 755 /entry.sh
VOLUME /mnt/source
VOLUME /mnt/borg-repository
VOLUME /etc/borgmatic.d
VOLUME /root/.config/borg
VOLUME /mnt/rclone_config
VOLUME /root/.ssh
VOLUME /root/.cache/borg
COPY --from=builder /usr/lib/python3.9/site-packages \
                    /usr/lib/python3.9/
COPY --from=builder /usr/bin/borg \
                    /usr/bin/borgfs \
                    /usr/bin/borgmatic \
                    /usr/bin/generate-borgmatic-config \
                    /usr/bin/upgrade-borgmatic-config \
                    /usr/bin/rclone \
                    /usr/bin/

RUN ln -s /mnt/rclone_config/rclone.conf /usr/bin
CMD ["/entry.sh"]
