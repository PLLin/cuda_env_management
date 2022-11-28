FROM ubuntu:20.04

RUN apt -y update
RUN DEBIAN_FRONTEND=noninteractive apt install -y \
        build-essential \
        cmake \
        libprotobuf-dev \
        libpq-dev \
        protobuf-compiler \
        libzbar0 \
        libgl1 \
        libsm6 \
        libxext6 \
        libxrender-dev \
        tzdata \
        locales \
        libncurses5-dev \
        libgdbm-dev \
        libnss3-dev \
        libssl-dev \
        libreadline-dev \
        libffi-dev \
        wget \
        zlib*

WORKDIR /build
RUN wget https://www.python.org/ftp/python/3.6.9/Python-3.6.9.tgz
RUN tar -xzf Python-3.6.9.tgz
RUN cd Python-3.6.9 && ./configure --prefix=/usr/local/python36 --with-openssl && make && make install
RUN cd /build && rm -rf ./*
RUN ln -s -f /usr/local/python36/bin/python3.6 /usr/bin/python3
RUN ln -s -f /usr/local/python36/bin/pip3.6 /usr/bin/pip3

RUN TZ=Asia/Taipei \
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
    && echo $TZ > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && locale-gen
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
ENV CMAKE_ARGS="-DONNX_USE_PROTOBUF_SHARED_LIBS=ON"
