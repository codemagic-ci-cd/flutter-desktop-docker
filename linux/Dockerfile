FROM ubuntu:20.04

ENV PATH="/opt/flutter/bin:/opt/flutter/bin/cache/dart-sdk/bin:$PATH"
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
    && apt-get --yes install --reinstall ca-certificates \
    && apt-get --yes install --no-install-recommends \
        clang \
        cmake \
        curl \
        file \
        git \
        libglu1-mesa \
        libxinerama1 \
        libxcursor1 \
        libxrandr2 \
        ninja-build \
        unzip \
        xz-utils \
    && apt-get --purge autoremove \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/*

RUN git clone -b master https://github.com/flutter/flutter.git /opt/flutter

RUN flutter upgrade \
    && flutter config --enable-linux-desktop \
    && flutter precache --linux \
    && flutter doctor -v \
    && chown -R root:root /opt \
    && mkdir /opt/clone

WORKDIR /opt/clone
