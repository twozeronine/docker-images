ARG UBUNTU_VERSION=jammy-20230126

FROM ubuntu:${UBUNTU_VERSION}
RUN apt-get update -y \
    && apt-get -y install --no-install-recommends \ 
    locales \
    && locale-gen en_US.UTF-8 \
    # Clean UP
    && apt-get -y autoremove \
    && apt-get -y clean \
    && rm -rf /var/lib/apt/lists/*_* 
ENV LANG=C.UTF-8