#########
FROM ubuntu:20.04
## Pre requirements
########
ENV DEBIAN_FRONTEND noninteractive
#ENV LC_ALL en_GB.UTF-8
#ENV LANG en_GB.UTF-8
#ENV LANGUAGE en_GB:en
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
RUN apt update && \
    apt upgrade -y && \
    apt install -y \
        python3 \
        python3-pip \
        ncbi-blast+ \
        prodigal \
        mash \
        mummer \
    && apt -y autoremove && apt autoclean && rm -rf /var/lib/apt/lists/*

RUN pip3 --version
# Upgrade pip3
RUN pip3 install --upgrade pip==22.2.2
# Install python package for getting the assembly stats and fastani
## Install drep
########
RUN pip3 install -U drep
RUN pip3 install -U assembly-stats

# Install fastani
RUN apt-get update && apt-get install -y autoconf \
	libgsl-dev \
	zlib1g-dev \
	g++ \
	make \
	wget \
    && apt -y autoremove && apt autoclean && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/ParBLiSS/FastANI/archive/refs/tags/v1.33.tar.gz &&\
	tar -xzf v1.33.tar.gz &&\
	rm v1.33.tar.gz &&\
	cd FastANI-1.33 &&\
	./bootstrap.sh &&\
	./configure &&\
	make
ENV PATH="${PATH}:/FastANI-1.33"



