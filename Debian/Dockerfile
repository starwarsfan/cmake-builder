FROM debian:stretch
MAINTAINER Yves Schumann <yves@eisfair.org>

ENV WORK_DIR=/data/work \
    DEBIAN_FRONTEND=noninteractive \
    LC_ALL=en_US.UTF-8

# Mount point for development workspace
RUN mkdir -p ${WORK_DIR}
VOLUME ${WORK_DIR}

COPY Debian/stretch-backports.list /etc/apt/sources.list.d/
COPY Debian/testing.list /etc/apt/sources.list.d/

RUN apt-get update -y \
 && apt-get upgrade -y

RUN apt-get install -y \
    autoconf \
    automake \
    build-essential \
    ca-certificates \
    cmake \
    curl \
    g++-7 \
    git \
    less \
    locales \
    make \
    mc \
    openssh-client \
    pkg-config \
    wget

# Set locale to UTF8
RUN echo "${LC_ALL} UTF-8" > /etc/locale.gen \
 && locale-gen ${LC_ALL} \
 && dpkg-reconfigure locales \
 && /usr/sbin/update-locale LANG=${LC_ALL}
