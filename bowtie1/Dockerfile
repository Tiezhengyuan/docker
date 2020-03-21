# Dockerfile to build container images for sequence aligner bowtie1

FROM ubuntu
MAINTAINER Tiezheng Yuan <tiezhengyuan@hotmail.com>

# install dependencies first
RUN apt-get update 
RUN apt-get install -y apt-utils wget unzip python


# Install bowtie1
WORKDIR /bioinfo
RUN wget https://sourceforge.net/projects/bowtie-bio/files/bowtie/1.2.3/bowtie-1.2.3-linux-x86_64.zip && \
    unzip bowtie-1.2.3-linux-x86_64.zip
RUN cp -p bowtie-1.2.3-linux-x86_64/bowtie* /usr/bin
ENV PATH "/bowtie-1.2.3-linux-x86_64:$PATH"

#clean 
RUN apt-get clean

# Set default working path
WORKDIR /bioinfo

CMD ["/bin/bash", "bowtie"]

