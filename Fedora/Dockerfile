FROM fedora:29
MAINTAINER Yves Schumann <yves@eisfair.org>

ENV WORK_DIR=/data/work

# Mount point for development workspace
RUN mkdir -p ${WORK_DIR}
VOLUME ${WORK_DIR}

RUN yum update -y

RUN yum install -y \
    autoconf \
    automake \
    cmake \
    curl \
    gcc-c++ \
    git \
    less \
    make \
    mc \
    openssh-clients \
    openssl-devel \
    patch \
    pkg-config \
    wget
