ARG BASE_IMAGE="runpod/pytorch:2.1.0-py3.10-cuda11.8.0-devel-ubuntu22.04"

FROM ${BASE_IMAGE}

USER root
RUN apt-get update && \
   apt-get install -y  --no-install-recommends  \
    curl \
    gcc \
    git \
    gosu \
    git-lfs \
    htop \
    libgl1 \
    libglib2.0-0 \
    ncdu \
    tree \
    openssh-client \
    openssh-server \
    psmisc \
    rsync \
    screen \
    sudo \
    tmux \
    unzip \
    vim \
    ldap-utils \
    nvtop \
    wget \
    cm-super \
    texlive \
    texlive-latex-extra \
    texlive-fonts-recommended \
    dvipng \

# install Miniforge
RUN wget -O /tmp/Miniforge3.sh "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh" && \
    bash /tmp/Miniforge3.sh -b -p "/opt/conda" &&  rm /tmp/Miniforge3.sh
RUN . /opt/conda/etc/profile.d/conda.sh
# make conda install writable
RUN chmod -R 777 /opt/conda

# setup ssh
RUN ssh-keygen -A
RUN service ssh start
EXPOSE 22

COPY base/.bashrc /tmp/.bashrc
RUN cat /tmp/.bashrc >> /root/.bashrc && rm /tmp/.bashrc
