FROM frutti93/borgmatic:latest as builder
LABEL mainainer='frutti93'
RUN apk upgrade --no-cache \
    && apk add --no-cache \
    alpine-sdk \
    python3-dev \
    py3-pip \
    openssl-dev \
    libffi-dev \
    && pip3 install --upgrade pip \
    && pip3 install --upgrade ntfy[pid,emoji,xmpp,telegram,instapush,slack,rocketchat]

FROM frutti93/borgmatic:latest
LABEL mainainer='frutti93'
VOLUME /root/.config/ntfy
COPY --from=builder /usr/lib/python3.8/site-packages /usr/lib/python3.8/
COPY --from=builder /usr/bin/ntfy /usr/bin/
