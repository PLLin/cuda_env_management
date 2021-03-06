FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04

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

WORKDIR /usr/local/cuda/lib64/
RUN cp libcufft.so libcufft.so.10.0
RUN cp libcurand.so libcurand.so.10.0
RUN cp libcusolver.so libcusolver.10.0
RUN cp libcusparse.so libcusparse.10.0
RUN cp libcusolver.so libcusolver.so.10.0
RUN cp libcusparse.so libcusparse.so.10.0
RUN cp libcudart.so libcudart.so.10.0

WORKDIR /usr/lib/x86_64-linux-gnu/
RUN cp libcublas.so libcublas.so.10.0

ENV LD_LIBRARY_PATH="/usr/local/cuda/lib64:${LD_LIBRARY_PATH}"

RUN TZ=Asia/Taipei \
    && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
    && echo $TZ > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata 

RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && locale-gen
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8  
