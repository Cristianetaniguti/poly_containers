FROM rocker/rstudio:latest

RUN apt install -y libgit2-dev libfontconfig1-dev libxml2-dev 

RUN R -e "install.packages('devtools', repos='http://brieger.esalq.usp.br/CRAN/', dependencies=T);\
          devtools::install_url('https://cran.r-project.org/src/contrib/Archive/SPA3G/SPA3G_1.0.tar.gz');\
          devtools::install_url('https://cran.r-project.org/src/contrib/Archive/varComp/varComp_0.2-0.tar.gz');\
          devtools::install_version('sommer', version = '3.6', repos = 'http://cran.us.r-project.org');\
          devtools::install_github('guilherme-pereira/qtlpoly', upgrade = FALSE);\
          install.packages('BGLR', repos='http://brieger.esalq.usp.br/CRAN/');\
          devtools::install_github('jendelman/diaQTL');\
          devtools::install_github('jendelman/GWASpoly')"
          
COPY ./subset.vcf /opt