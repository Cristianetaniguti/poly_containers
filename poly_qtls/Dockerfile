FROM rocker/rstudio:latest

RUN apt install -y libgit2-dev libfontconfig1-dev libxml2-dev 

RUN R -e "install.packages('devtools', repos='http://brieger.esalq.usp.br/CRAN/', dependencies=T);\
          devtools::install_github('https://github.com/guilherme-pereira/QTLpoly');\
          devtools::install_github('https://github.com/jendelman/diaQTL');\
          devtools::install_github('https://github.com/jendelman/GWASpoly')"