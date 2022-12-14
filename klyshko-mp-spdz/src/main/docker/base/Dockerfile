#
# Copyright (c) 2021 - for information on the respective copyright owner
# see the NOTICE file and/or the repository https://github.com/carbynestack/klyshko.
#
# SPDX-License-Identifier: Apache-2.0
#
FROM ubuntu:20.04

# Install prerequisites
ENV TZ=Europe/Berlin
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update && apt-get install -y --no-install-recommends \
    automake \
    build-essential \
    git \
    libboost-dev \
    libboost-filesystem-dev \
    libboost-thread-dev \
    libntl-dev \
    libsodium-dev \
    libssl-dev \
    libtool \
    m4 \
    python3 \
    texinfo \
    yasm \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# https://github.com/data61/MP-SPDZ
ARG MP_SPDZ_REPO="https://github.com/carbynestack/MP-SPDZ"
# v0.2.8
ARG MP_SPDZ_VERSION="add-prng-seed-option"

# Checkout MP-SPDZ repository at required version
RUN git clone --recurse-submodules ${MP_SPDZ_REPO} mp-spdz
WORKDIR mp-spdz
RUN git checkout ${MP_SPDZ_VERSION}
