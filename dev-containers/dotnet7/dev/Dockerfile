ARG DOTNET_VERSION=7.0
ARG UBUNTU_VERSION=jammy-amd64
FROM mcr.microsoft.com/dotnet/sdk:${DOTNET_VERSION}-${UBUNTU_VERSION}
LABEL org.opencontainers.image.source=https://github.com/twozeronine/docker-images

RUN DEBIAN_FRONTEND=nointeractive \
    && apt-get update \
    && apt-get -y install --no-install-recommends \
    curl \
    unzip \
    # features
    && curl -sSL https://github.com/devcontainers/features/archive/refs/heads/main.zip -o /tmp/features-main.zip \
    && unzip /tmp/features-main.zip -d /tmp \
    # features/common-utils
    && INSTALLZSH=false \
    CONFIGUREZSHASDEFAULTSHELL=false \
    INSTALLOHMYZSH=false \
    INSTALLOHMYZSHCONFIG=false \
    UPGRADEPACKAGES=true \
    USERNAME=vscode \
    UID=1000 \
    GID=1000 \
    NONFREEPACKAGES=false \
    /bin/bash /tmp/features-main/src/common-utils/install.sh \
    # features/github-cli
    && VERION=latest \
    && /bin/bash /tmp/features-main/src/github-cli/install.sh \
    # Clean Up
    && apt-get -y autoremove \ 
    && apt-get -y clean \ 
    && rm -rf /var/lib/apt/lists/* /tmp/*