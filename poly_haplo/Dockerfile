FROM rocker/rstudio:latest

# Download Julia
RUN apt update \
    && wget https://julialang-s3.julialang.org/bin/linux/x64/1.5/julia-1.5.3-linux-x86_64.tar.gz \
    && tar zxvf julia-1.5.3-linux-x86_64.tar.gz

# Include in path
ENV PATH=/julia-1.5.3/bin:$PATH

RUN julia -e 'using Pkg;pkg"add https://github.com/chaozhi/PolyOrigin.jl"'

RUN apt install -y libcurl4-gnutls-dev libssl-dev libftgl2 libglu1-mesa-dev libftgl2 libfreetype6-dev  gcc-8-base libgfortran5 libxml2-dev libnlopt-dev devscripts software-properties-common libgit2-dev zlib1g-dev pkg-config

RUN R -e "install.packages('candisc', repos='http://brieger.esalq.usp.br/CRAN/');\
          install.packages('mappoly', repos='http://brieger.esalq.usp.br/CRAN/');\
          install.packages('polymapR', repos='http://brieger.esalq.usp.br/CRAN/')"
