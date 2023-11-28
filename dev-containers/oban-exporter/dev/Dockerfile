ARG ELIXIR_VERSION=1.15.6
ARG ERLANG_VERSION=26.1.1
ARG UBUNTU_VERSION=jammy-20230126
FROM hexpm/elixir:${ELIXIR_VERSION}-erlang-${ERLANG_VERSION}-ubuntu-${UBUNTU_VERSION}
LABEL org.opencontainers.image.source=https://github.com/twozeronine/docker-images

# for phx.new
ARG PHOENIX_VERSION="1.7.2"
RUN apt-get update
RUN apt-get -y install --no-install-recommends \
    curl \
    unzip
RUN curl -sSL https://github.com/devcontainers/features/archive/refs/heads/main.zip -o /tmp/features-main.zip
RUN unzip /tmp/features-main.zip -d /tmp
RUN INSTALLZSH=false \
    CONFIGUREZSHASDEFAULTSHELL=false \
    INSTALLOHMYZSH=false \
    INSTALLOHMYZSHCONFIG=false \
    UPGRADEPACKAGES=true \
    USERNAME=vscode \
    UID=1000 \
    GID=1000 \
    NONFREEPACKAGES=false \
    /bin/bash /tmp/features-main/src/common-utils/install.sh
RUN VERSION=latest \
    && /bin/bash /tmp/features-main/src/github-cli/install.sh
RUN apt-get -y autoremove
RUN apt-get -y clean
RUN rm -rf /var/lib/apt/lists/* /tmp/*
# Phoenix
RUN su vscode -c  "mix local.hex --force"
RUN su vscode -c  "mix local.rebar --force"
RUN su vscode -c  "mix archive.install hex phx_new 1.7.2"