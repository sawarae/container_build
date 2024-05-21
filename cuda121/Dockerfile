FROM nvidia/cuda:12.1.0-devel-ubuntu22.04
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    sudo wget screen unzip less nano
WORKDIR /opt

RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
    sh Miniconda3-latest-Linux-x86_64.sh -b -p /opt/miniconda3 && \
    rm -r Miniconda3-latest-Linux-x86_64.sh

ENV PATH /opt/miniconda3/bin:$PATH

# for cv2
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y ffmpeg libsm6 libxext6

RUN pip install --upgrade pip && \
    conda update -n base -c defaults conda

WORKDIR /workspace

CMD ["/bin/bash"]