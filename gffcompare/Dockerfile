# Dockerfile to build container images for gffcompare

FROM ubuntu
MAINTAINER Tiezheng Yuan <tiezhengyuan@hotmail.com>

# Set default working path
WORKDIR /bioinfo

RUN apt-get update
RUN apt-get install -y \
    apt-utils \
    build-essential \
    gcc-multilib \
    make \
    git



# Install gffcompare 
WORKDIR /bioinfo
RUN git clone https://github.com/gpertea/gclib && \
    git clone https://github.com/gpertea/gffcompare && \
    cd gffcompare && \
    make release && \
    cp gffcompare /usr/bin/
ENV PATH "/gffcompare:$PATH"

# Cleanup
RUN apt-get clean
#RUN apt-get remove --yes --purge build-essential gcc-multilib apt-utils

CMD ["/bin/bash", "gffcompare"]
