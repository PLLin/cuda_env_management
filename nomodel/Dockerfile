FROM ubuntu:18.04

RUN apt -y update \ 
    &&  DEBIAN_FRONTEND=noninteractive apt install -y \
        build-essential \
        cmake \
        libprotobuf-dev \
        libpq-dev \
        protobuf-compiler \
        python3-dev \
        python3-pip \
        libzbar0 \
        libgl1 \
        libsm6 \
        libxext6 \
        libxrender-dev \
        tzdata \
        locales

RUN TZ=Asia/Taipei \
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
    && echo $TZ > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && locale-gen
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
