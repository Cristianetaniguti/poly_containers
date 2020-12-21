## Why should you use docker images?

* If you do not want to install all software needed for the Polyploid Training Workshop
* You want to run every software via RStudio in your web browser
* You want to use a cluster to run the analysis

All images will run on top of your OS kernel, so they are cross-platform enabled, do not need any configuration, and are ready to go.

## What will you find in this repository?

* [Docker installation instructions](#installing-docker)

* Self-contained images of the following software:

    * [SuperMASSA/VCF2SM]()
    * [polyRAD]()
    * [fitPoly]()
    * [MAPpoly]()
    * [polymapR]()
    * [PolyOrigin]()
    * [QTLpoly]()
    * [polyqtlR]()
    * [diaQTL]()
    * [GWASpoly]()

* Instructions for running the images on the following platforms:

    * [Personal computer with Linux]()
    * [Personal computer with Windows]()
    * [Personal computer with Mac]()
    * [Cluster with Linux]()

## Installing Docker

**Linux users:** use the following instructions to [Install Docker on Ubuntu](https://docs.docker.com/engine/install/ubuntu/), or find your distribution [here](https://docs.docker.com/engine/install/).

**Windows users:** download the [Docker Desktop Installer for Windows](https://desktop.docker.com/win/stable/Docker%20Desktop%20Installer.exe) and follow the [Installation instructions for Windows](https://docs.docker.com/docker-for-windows/install/).

**Mac users:** download the [Docker Desktop Installer for Mac](https://desktop.docker.com/mac/stable/Docker.dmg) and follow the [Installation instructions for Mac](https://docs.docker.com/docker-for-mac/install/).

**Cluster users**: most computing clusters already have Docker or Singularity installed - you can jump to the next session, download and run the images. If your cluster does not have any image rendering system, please contact your system administrator.

## Genotype calling software

* Docker Hub image: [cristaniguti/poly_genocalls](https://hub.docker.com/repository/docker/cristaniguti/poly_genocalls)

### Image contents

* Ubuntu 20.04
* R 4.0.3
* RStudio 1.3
* Python 2.7
* SuperMASSA
* VCF2SM
* polyRAD
* fitPoly

### Running instructions

**Download the container image:** open a terminal and run: `docker pull cristaniguti/poly_genocalls`

Then start the image by running the following commands:

```{bash, eval=FALSE}
# Use VCF2SM
docker run -v $(pwd):/opt cristaniguti/poly_genocalls python /scripts/vcf2sm/VCF2SM.py -i /opt/example.vcf -o /opt/NewPlusOldCalls.headed_poly.vcf -S /scripts/supermassa/src/SuperMASSA.py -I hw -a RA/AA -r 1:84 -d 15 -D 500 -M 4:6 -f 4 -p 0.80 -n 0.90 -c 0.75 -t 1

# Access the RStudio
docker run -p 8787:8787 -v $(pwd):/home/rstudio/ -e DISABLE_AUTH=true cristaniguti/poly_genocalls
```

Keep this terminal open and access `http://localhost:8787/` or `http://127.0.0.1:8787/` in your web browser. Feel free to choose another port different than 8787. You can also run the VCF2SM using the RStudio terminal, but do not forget the path of the scripts inside the container: `/scripts/SuperMASSA.py` and `/scripts/VCF2SM.py`.

**Warning:** container images can be large depending on their content. If you do not plan to use the images soon and want to free up some storage space, please open a terminal and run `rm -rf poly_genocalls`.

## Linkage Mapping and Haplotype Reconstruction

* Docker Hub image: [cristaniguti/poly_maphaplo](https://hub.docker.com/repository/docker/cristaniguti/poly_maphaplo)

### Image contents

* Ubuntu 20.04
* R 4.0.3
* RStudio 1.3
* Julia
* MAPpoly
* polymapR
* PolyOrigin

### Running instructions

**Download the container image:** open a terminal and run: `docker pull cristaniguti/poly_maphaplo`

Then start the image by running the following commands:

```{bash, eval=FALSE}

```

**Warning:** container images can be large depending on their content. If you do not plan to use the images soon and want to free up some storage space, please open a terminal and run `rm -rf poly_maphaplo`.

## QTL mapping

* Docker Hub image: [cristaniguti/poly_qtlmap](https://hub.docker.com/repository/docker/cristaniguti/poly_qtlmap)

### Image contents

* Ubuntu 20.04
* R 4.0.3
* RStudio 1.3
* QTLpoly
* diaQTL
* GWASpoly

### Running instructions

**Download the container image:** open a terminal and run: `docker pull cristaniguti/poly_qtlmap`

Then start the image by running the following commands:

```{bash, eval=FALSE}

```

**Warning:** container images can be large depending on their content. If you do not plan to use the images soon and want to free up some storage space, please open a terminal and run `rm -rf poly_qtlmap`.
