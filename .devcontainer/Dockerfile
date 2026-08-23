FROM fedora:40

# Install common development tools used in Codespaces.
RUN dnf -y update && dnf -y install \
    bash \
    bash-completion \
    ca-certificates \
    curl \
    findutils \
    git \
    gzip \
    hostname \
    iproute \
    jq \
    less \
    procps-ng \
    shadow-utils \
    sudo \
    tar \
    unzip \
    util-linux \
    wget \
    which \
    zip \
    && dnf clean all

# Create a non-root user for VS Code / Codespaces.
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8