# Dockerfile to build container images for variants calling
# including samtools, bcftools

FROM ubuntu
MAINTAINER Tiezheng Yuan <tiezhengyuan@hotmail.com>

# install dependencies first
RUN apt-get update
RUN apt-get install -y curl wget gcc make bzip2 autoconf && \
    apt-get install -y zlib1g zlib1g-dev libncurses5 libncurses5-dev  && \
    apt-get install -y libbz2-1.0 libbz2-dev liblzma5 liblzma-dev && \
    apt-get install -y libcurl4 libcurl4-openssl-dev openssl libssl-dev

# Install samtools
WORKDIR /bioinfo
RUN wget https://github.com/samtools/samtools/releases/download/1.10/samtools-1.10.tar.bz2 && \
    tar -jxf samtools-1.10.tar.bz2 && \
    cd samtools-1.10 && \
    make && \
    make install && \
    cp samtools /usr/bin/

# Install bcftools
WORKDIR /bioinfo
RUN wget https://github.com/samtools/bcftools/releases/download/1.10.2/bcftools-1.10.2.tar.bz2 && \
    tar -jxf bcftools-1.10.2.tar.bz2 && \
    cd bcftools-1.10.2 && \
    make && \
    make install && \
    cp bcftools /usr/bin/

# Cleanup
RUN rm -rf /bioinfo/samtools-1.10
RUN rm -rf /bioinfo/bcftools-1.10.2
RUN apt-get clean


# Set default working path
WORKDIR /bioinfo

CMD ["/bin/bash", "samtools", "bcftools"]
