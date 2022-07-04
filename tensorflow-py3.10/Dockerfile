# https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/dockerfiles/dockerfiles/gpu.Dockerfile
# https://github.com/tensorflow/tensorflow/issues/25939
# Due to lack of possibility to dynamically choose python version.

ARG UBUNTU_VERSION=20.04
FROM ubuntu:${UBUNTU_VERSION}

# Let us install tzdata painlessly
ENV DEBIAN_FRONTEND=noninteractive

# Needed for string substitution
SHELL ["/bin/bash", "-c"]

# Pick up some TF dependencies
RUN apt-get update && \
    apt-get install -qq -y --no-install-recommends \
        build-essential \
        curl \
        pkg-config \
        software-properties-common \
        unzip

RUN add-apt-repository -y ppa:deadsnakes/ppa && \
    apt-get update && \
    apt-get install -qq -y --no-install-recommends \
        python3.10 \
        python3.10-distutils \
        python3.10-dev && \
    apt-get clean

# See http://bugs.python.org/issue19846
ENV LANG C.UTF-8

RUN curl -sS https://bootstrap.pypa.io/get-pip.py | python3.10
RUN python3.10 -m pip --no-cache-dir install -qq --upgrade pip setuptools wheel

# Some TF tools expect a "python" binary
RUN ln -s $(which python3.10) /usr/local/bin/python

# Options:
#   tensorflow
#   tensorflow-gpu
#   tf-nightly
#   tf-nightly-gpu
# Set --build-arg TF_PACKAGE_VERSION=1.11.0rc0 to install a specific version.
# Installs the latest version by default.
ARG TF_PACKAGE=tensorflow
ARG TF_PACKAGE_VERSION=2.9.0
RUN python3.10 -m pip install -qq --no-cache-dir ${TF_PACKAGE}${TF_PACKAGE_VERSION:+==${TF_PACKAGE_VERSION}}
