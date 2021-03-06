# Borgmatic Container
![](https://img.shields.io/github/stars/frutti93/docker-borgmatic)
[![](https://img.shields.io/docker/stars/frutti93/borgmatic?link=https://hub.docker.com/r/frutti93/borgmatic)](https://img.shields.io/docker/stars/frutti93/borgmatic?link=https://hub.docker.com/r/frutti93/borgmatic&link=https://hub.docker.com/r/frutti93/borgmatic)
[![](https://img.shields.io/docker/pulls/frutti93/borgmatic?link=https://hub.docker.com/r/frutti93/borgmatic)](https://img.shields.io/docker/pulls/frutti93/borgmatic?link=https://hub.docker.com/r/frutti93/borgmatic&link=https://hub.docker.com/r/frutti93/borgmatic)
![](https://img.shields.io/github/workflow/status/frutti93/docker-borgmatic/build%20latest)
![](https://img.shields.io/github/workflow/status/frutti93/docker-borgmatic/build%20tagged)

## Description
This is a fork of [docker-borgmatic](https://github.com/b3vis/docker-borgmatic) by [b3vis](https://github.com/b3vis) providing multiarch builds on [DockerHub](https://hub.docker.com/r/frutti93/borgmatic).

Find the images here: https://hub.docker.com/r/frutti93/borgmatic

**ATTENTION**: So far I only tested the base version, but the others should work as well. If you happen to test one of the others and stumble into a bug, let me know and I will try to fix it.

This image comes in the three flavours:
1. [base](./base/README.md) (vanilla), with docker log
2. [msmtp](./msmtp/README.md), with e-mail notifications
3. [ntfy](./ntfy/README.md), with push notifications

### Usage
General instructions can be found in the base image [README](./base/README.md).
