FROM alpine:20201218 as downloads
RUN apk add --no-cache git=2.29.2-r wget=1.20.3-r2 \
    && git clone https://bitbucket.org/orserang/supermassa.git \
    && git clone https://github.com/guilherme-pereira/vcf2sm.git \
    && wget https://github.com/Cristianetaniguti/poly_containers/raw/master/poly_genocalls/subset.vcf \
    && wget https://bootstrap.pypa.io/get-pip.py -O get-pip.py


FROM rocker/rstudio:4.0.3
COPY --from=downloads /supermassa/src/* /scripts/
COPY --from=downloads /vcf2sm/* /scripts/
COPY --from=downloads /subset.vcf /opt/
COPY --from=downloads /get-pip.py /
ENV PATH="/scripts:${PATH}"
ARG CRAN_REPO=https://packagemanager.rstudio.com/all/__linux__/focal/latest

# Installing python2 and matplotlib for supermassa
RUN apt-get update && apt-get install --no-install-recommends -y \
        git=1:2.25.1-1ubuntu3 \
        libgit2-dev=0.28.4+dfsg.1-2 \
        libfontconfig1-dev=2.13.1-2ubuntu3 \
        libxml2-dev=2.9.10+dfsg-5 \
        libharfbuzz-dev=2.6.4-1ubuntu4 \
        libfribidi-dev=1.0.8-2 \
        python2=2.7.17-2ubuntu4 \
        python-tk=2.7.18-1 \
        python-is-python2=2.7.17-4 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && python /get-pip.py && pip install \
        matplotlib==2.0.2 \
        numpy==1.16.6

# Install R packages
RUN install2.r --error --deps TRUE -r ${CRAN_REPO} \
        remotes \
        devtools \
        fitPoly \
        BiocManager \
    && installGithub.r lvclark/polyRAD
