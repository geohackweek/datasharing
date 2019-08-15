FROM python:3.7

RUN apt-get update -yqq \
  && apt-get install -yqq --no-install-recommends \
    software-properties-common \
    apt-utils

RUN apt-get update -yqq \
    && DEBIAN_FRONTEND=noninteractive apt-get install -yqq --no-install-recommends \
    build-essential \
    python3.7 \
    python3.7-dev \
    python-pip \
    git \
    wget \
    vim \
    asciinema \
  && apt-get -q clean

RUN useradd -mUs /bin/bash -G staff bob
RUN useradd -mUs /bin/bash -G staff sandy

RUN chmod -R g+w /usr/local/ && chown -R root:staff /usr/local/

USER sandy
WORKDIR /home/sandy

RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh && \
    bash miniconda.sh -b -p $HOME/miniconda && \
    export PATH="$HOME/miniconda/bin:$PATH" && \
    conda config --set always_yes yes --set changeps1 no --set show_channel_urls true && \
    conda update --quiet conda && \
    conda config --add channels conda-forge --force && \
    conda config --set channel_priority strict && \
    conda init bash

ENV color_prompt=yes

USER root
WORKDIR /