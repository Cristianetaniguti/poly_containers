FROM rocker/rstudio:latest

# Installing python2 and matplotlib for supermassa
RUN apt-get update \
    && apt install -y python2 python-tk curl \
    && curl https://bootstrap.pypa.io/get-pip.py --output get-pip.py \
    && python2 get-pip.py \
    && pip install matplotlib==2.0.2 numpy \
    && ln -s /usr/bin/python2 /usr/bin/python

# Install R packages
RUN apt install -y libgit2-dev libfontconfig1-dev libxml2-dev libharfbuzz-dev libfribidi-dev

RUN R -e "install.packages('devtools', repos='http://brieger.esalq.usp.br/CRAN/', dependencies=T);\
          install.packages('fitPoly', repos='http://brieger.esalq.usp.br/CRAN/', dependencies=T);\
          install.packages('BiocManager', repos='http://brieger.esalq.usp.br/CRAN/'); \
          BiocManager::install('pcaMethods');\
          devtools::install_github('lvclark/polyRAD')"

# Download supermassa and vcf2sm
RUN apt install -y git \
    && git clone https://bitbucket.org/orserang/supermassa.git \
    && git clone https://github.com/guilherme-pereira/vcf2sm.git \
    && mkdir /scripts \
    && cp supermassa/src/* /scripts \
    && cp vcf2sm/* /scripts

# It is not working - bugfix
ENV PATH=/scripts:$PATH 

COPY ./subset.vcf /opt