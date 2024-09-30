FROM nvidia/cuda:12.4.1-cudnn-devel-ubuntu22.04
RUN apt-get update && apt-get install -y \
    sudo \
    wget \
    screen \
    nano
WORKDIR /opt

RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    sh Miniconda3-latest-Linux-x86_64.sh -b -p /opt/miniconda3 && \
    rm -r Miniconda3-latest-Linux-x86_64.sh

ENV PATH /opt/miniconda3/bin:$PATH

RUN pip install --upgrade pip && \
    conda update -n base -c defaults conda && \
    conda create -n py312 python=3.12 && \
    conda init && \
    echo "conda activate py312" >> ~/.bashrc

ENV CONDA_DEFAULT_ENV py312 && \
    PATH /opt/conda/envs/py312/bin:$PATH


WORKDIR /

CMD ["/bin/bash"]