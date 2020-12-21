## Why should you use this docker images?

* If you do not want to install all software needed for the Polyploids Training Workshop
* Run every software via RStudio in your browser
* Use cluster to run the workshop analysis

## Where will you run the analysis?

* [Personal computer with Linux](#linux-system-personal-computer)
* [Personal computer with Windows]()
* [Mac system personal computer]()
* [Cluster with Linux]()

## Linux system personal computer

### Genotype calls 

Docker hub image: [cristaniguti/poly_genocalls]()

**Contains:**

* R
* RStudio
* Python 2.7
* SuperMASSA
* VCF2SM
* polyRAD
* fitPoly

**How to run:**

Use this instructions to install docker for [ubuntu](https://docs.docker.com/engine/install/ubuntu/). Or search your distribution [here](https://docs.docker.com/engine/install/).

```{bash, eval=FALSE}
# Use VCF2SM
docker run -v $(pwd):/opt cristaniguti/poly_genocalls python /scripts/vcf2sm/VCF2SM.py -i /opt/example.vcf -o NewPlusOldCalls.headed_poly.vcf -S /scripts/supermassa/src/SuperMASSA.py -I hw -a RA/AA -r 1:84 -d 15 -D 500 -M 4:6 -f 4 -p 0.80 -n 0.90 -c 0.75 -t 1

# Access the RStudio
docker run -p 8787:8787 -v $(pwd):/home/rstudio/ -e DISABLE_AUTH=true cristaniguti/poly_genocalls
```

Keep this terminal open and search for `http://localhost:8787/` or `http://127.0.0.1:8787/` in your browser. Feel free to choose another port different than 8787. You can also run the VCF2SM using the RStudio terminal, just do not forget the path of the script inside the container: `/scripts/SuperMASSA.py` and `/scripts/VCF2SM.py`.

### Linkage Mapping and Haplotype Reconstruction:

**Contains:**

* R
* RStudio
* Julia
* MAPpoly
* polymapR
* PolyOrigin

**How to run:**

```{bash, eval=FALSE}

```

### QTL mapping

**Contains:**

* R
* RStudio
* QTLpoly
* diaQTL
* GWASpoly

**How to run:**

```{bash, eval=FALSE}

```