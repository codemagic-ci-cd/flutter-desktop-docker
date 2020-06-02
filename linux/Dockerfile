FROM ubuntu:20.04

ENV PATH="/opt/flutter/bin:/opt/flutter/bin/cache/dart-sdk/bin:$PATH"

RUN apt-get update > /dev/null \
    && apt-get --yes install --reinstall ca-certificates \
    && DEBIAN_FRONTEND="noninteractive" apt-get --yes install --no-install-recommends \
        git \
        curl \
        unzip \
        clang \
        cmake \
        ninja-build \
    && apt-get --purge autoremove > /dev/null \
    && apt-get autoclean > /dev/null \
    && rm -rf /var/lib/apt/lists/*

RUN git clone -b master https://github.com/flutter/flutter.git /opt/flutter

RUN flutter upgrade \
    && flutter config --enable-linux-desktop \
    && flutter doctor -v \
    && chown -R root:root /opt \
    && mkdir /opt/clone

WORKDIR /opt/clone
