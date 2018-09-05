FROM python:3.6

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

COPY conda_demo/pip/requirements.txt ./
RUN pip install --no-cache-dir ipython