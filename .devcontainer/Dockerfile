FROM ubuntu:22.04

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
