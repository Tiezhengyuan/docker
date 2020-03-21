FROM ubuntu
MAINTAINER Tiezheng Yuan <tiezhengyuan@hotmail.com>

#samtools version 1.10
ENV VERSION=1.10

#dependency
RUN apt-get update && \
    apt-get install -y curl gcc make bzip2 autoconf && \
    apt-get install -y zlib1g zlib1g-dev libncurses5 libncurses5-dev  && \
    apt-get install -y libbz2-1.0 libbz2-dev liblzma5 liblzma-dev && \
    apt-get install -y libcurl4 libcurl4-openssl-dev openssl libssl-dev

#install samtools
RUN curl -L https://github.com/samtools/samtools/releases/download/$VERSION/samtools-$VERSION.tar.bz2 > /tmp/samtools-$VERSION.tar.bz2 && \
    cd /tmp && tar xfjv samtools-$VERSION.tar.bz2 && rm samtools-$VERSION.tar.bz2 && \
    cd samtools-$VERSION && ./configure && make && make prefix=/opt install && \
    cd /tmp && rm -rf samtools-$VERSION

#clean installation
RUN apt-get clean -y
#RUN apt-get purge -y curl gcc make bzip2 autoconf zlib1g-dev libncurses5-dev
#RUN libbz2-dev liblzma-dev libcurl4-openssl-dev libssl-dev
#RUN apt-get autoremove -y

ENV PATH /opt/bin:$PATH


WORKDIR /bioinfo

CMD ["/bin/bash", "samtools"]
