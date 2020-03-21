# Dockerfile to build container images for sequence aligner bowtie2

FROM ubuntu
MAINTAINER Tiezheng Yuan <tiezhengyuan@hotmail.com>

# install dependencies first
RUN apt-get update 
RUN apt-get install -y libsys-hostname-long-perl apt-utils wget unzip python 


# Install bowtie1
WORKDIR /bioinfo
         
RUN wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.4.1/bowtie2-2.4.1-linux-x86_64.zip && \
    unzip bowtie2-2.4.1-linux-x86_64.zip
RUN cp -p bowtie2-2.4.1-linux-x86_64/bowtie2* /usr/bin
ENV PATH "/bowtie2-2.4.1-linux-x86_64:$PATH"

#clean 
RUN apt-get clean

# Set default working path
WORKDIR /bioinfo

CMD ["/bin/bash", "bowtie"]

