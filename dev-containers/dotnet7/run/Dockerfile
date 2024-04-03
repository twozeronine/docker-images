ARG DOTNET_VERSION=7.0
ARG UBUNTU_VERSION=jammy-amd64

FROM mcr.microsoft.com/dotnet/sdk:${DOTNET_VERSION}-${UBUNTU_VERSION}
LABEL org.opencontainers.image.source=https://github.com/twozeronine/docker-images
RUN apt-get update -y \
    # Clean UP
    && apt-get -y autoremove \
    && apt-get -y clean \
    && rm -rf /var/lib/apt/lists/*
ENV LANG=C.UTF-8