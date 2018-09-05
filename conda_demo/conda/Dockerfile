FROM continuumio/miniconda3:latest

RUN apt-get update -yqq \
  && apt-get install -yqq --no-install-recommends \
    software-properties-common

# -- Install Python dependencies
RUN DEBIAN_FRONTEND=noninteractive apt-get install -yqq --no-install-recommends \
    build-essential \
    git \
    wget \
    vim \
  && apt-get -q clean

WORKDIR /usr/src/app

COPY conda_demo/conda/environment.yml ./

RUN conda update conda --yes && \
    conda config --set show_channel_urls true && \
    conda config --add channels conda-forge --force