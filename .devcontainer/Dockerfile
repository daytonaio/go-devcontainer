FROM ubuntu:22.04
ARG USERNAME=daytona
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

RUN set -eux; \
    apt-get update; \
    apt-get install -y --no-install-recommends \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        netbase \
        wget \
# https://bugs.debian.org/929417
        sudo \
        tzdata \
        zsh \
# daytona specific
        protobuf-compiler \
        libprotobuf-dev  \
        openjdk-11-jdk; \
    rm -rf /var/lib/apt/lists/*

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m -s /bin/zsh $USERNAME \
    # Add sudo support. We can omit if we're not going to support adding
    # software after building the container.
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME