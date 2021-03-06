########## ARMORY Base #################

FROM nvidia/cuda:10.0-cudnn7-runtime-ubuntu18.04 AS armory

RUN apt-get -y -qq update && \
    apt-get install -y wget vim build-essential git curl

# Install Conda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    echo 'alias ll="ls -al"' >> ~/.bashrc

ENV PATH=/opt/conda/bin:$PATH

RUN /opt/conda/bin/pip install \
    tensorflow-datasets==2.0.0 \
    jupyterlab==1.2.6 \
    boto3==1.11.13 \
    adversarial-robustness-toolbox==1.2.0 \
    Pillow==7.0.0 \
    pydub==0.23.1 \
    apache-beam==2.18.0 \
    pytest==5.3.5

RUN /opt/conda/bin/conda install -c conda-forge ffmpeg==4.2

WORKDIR /workspace
