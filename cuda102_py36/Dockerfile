FROM nvidia/cuda:10.2-devel-ubuntu18.04
RUN apt-get update && apt-get install -y \
    sudo \
    wget \
    screen
WORKDIR /opt

RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    sh Miniconda3-latest-Linux-x86_64.sh -b -p /opt/miniconda3 && \
    rm -r Miniconda3-latest-Linux-x86_64.sh

ENV PATH /opt/miniconda3/bin:$PATH

# for cv2
RUN apt-get install ffmpeg libsm6 libxext6  -y

RUN pip install --upgrade pip && \
    conda update -n base -c defaults conda && \
    conda create -n py36 python=3.6 && \
    conda init && \
    echo "conda activate py36" >> ~/.bashrc

ENV CONDA_DEFAULT_ENV py36 && \
    PATH /opt/conda/envs/py36/bin:$PATH

WORKDIR /workspace

CMD ["/bin/bash"]