# Dockerfile to build container images for mRNA-seq pipeline
# including samtools, hisat2, stringtie and gffcompare

FROM ubuntu
MAINTAINER Tiezheng Yuan <tiezhengyuan@hotmail.com>

# install dependencies first
RUN apt-get update
RUN apt-get install -y curl gcc make bzip2 autoconf && \
    apt-get install -y zlib1g zlib1g-dev libncurses5 libncurses5-dev  && \
    apt-get install -y libbz2-1.0 libbz2-dev liblzma5 liblzma-dev && \
    apt-get install -y libcurl4 libcurl4-openssl-dev openssl libssl-dev

RUN apt-get update  && apt-get install -y \
    apt-utils \
    build-essential \
    gcc-multilib \
    wget \
    unzip\
    cmake \
    python \
    python-pip \
    python-dev \
    python2.7-dev \
    #python-numpy \
    #python-matplotlib \
    #hdf5-tools \
    #libhdf5-dev \
    #hdf5-helpers \
    libhdf5-serial-dev \
    libssh2-1-dev \
    icu-devtools \
    libssl-dev \
    libxml2-dev \
    #r-bioc-biobase \
    git \
    pigz

# Install samtools
WORKDIR /bioinfo
RUN wget https://github.com/samtools/samtools/releases/download/1.10/samtools-1.10.tar.bz2 && \
    tar -jxf samtools-1.10.tar.bz2 && \
    cd samtools-1.10 && \
    make && \
    make install && \
    cp samtools /usr/bin/

# Install hisat2
WORKDIR /bioinfo
RUN wget ftp://ftp.ccb.jhu.edu/pub/infphilo/hisat2/downloads/hisat2-2.1.0-Linux_x86_64.zip && \
    unzip hisat2-2.1.0-Linux_x86_64.zip
RUN cp -p hisat2-2.1.0/hisat2 hisat2-2.1.0/hisat2-* /usr/bin


# Install stringtie
WORKDIR /bioinfo
RUN wget http://ccb.jhu.edu/software/stringtie/dl/stringtie-2.1.1.Linux_x86_64.tar.gz && \
    tar zxf stringtie-2.1.1.Linux_x86_64.tar.gz && \
    cp ./stringtie-2.1.1.Linux_x86_64/stringtie /usr/bin/
    
# Download stringtie prepDE
WORKDIR /bioinfo
RUN wget http://ccb.jhu.edu/software/stringtie/dl/prepDE.py
    
# Install gffcompare 
WORKDIR /bioinfo
RUN git clone https://github.com/gpertea/gclib && \
    git clone https://github.com/gpertea/gffcompare && \
    cd gffcompare && \
    make release && \
    cp gffcompare /usr/bin/
ENV PATH "/gffcompare:$PATH"

# Cleanup
RUN rm -rf /bioinfo/hisat2-2.1.0
RUN rm -rf /bioinfo/samtools-1.10
RUN rm -rf /bioinfo/stringtie-2.1.1.Linux_x86_64
RUN apt-get clean
#RUN apt-get remove --yes --purge build-essential gcc-multilib apt-utils zlib1g-dev vim

# Set default working path
WORKDIR /bioinfo

CMD ["/bin/bash", "samtools", "hisat2", "stringtie"]

