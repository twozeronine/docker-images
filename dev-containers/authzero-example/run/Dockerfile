ARG UBUNTU_VERSION=jammy-20220428

FROM ubuntu:${UBUNTU_VERSION}
LABEL org.opencontainers.image.source=https://github.com/twozeronine/docker-images
RUN apt-get update -y \
    && apt-get -y install --no-install-recommends \ 
    locales \
    && locale-gen en_US.UTF-8 \
    # Clean UP
    && apt-get -y autoremove \
    && apt-get -y clean \
    && rm -rf /var/lib/apt/lists/*
ENV LANG=C.UTF-8