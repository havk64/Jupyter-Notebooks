
# Installs Jupyter Notebook and iRkernel kernel from the current branch

# Using Jupyter official image from docker as start point:
FROM jupyter/notebook

MAINTAINER Alexandro de Oliveira <alexandro.oliveira@holbertonschool.com>

# Retrieve recent R binary from CRAN using Secure APT:
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 && \
    echo "deb http://cran.rstudio.com/bin/linux/ubuntu trusty/">>/etc/apt/sources.list && \
    apt-get update -qq && \
    DEBIAN_FRONTEND=noninteractive apt-get install -yq --force-yes --no-install-recommends \
        r-base r-base-dev && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*

# Set default CRAN repo
RUN echo 'options("repos"="http://cran.rstudio.com")' >> /usr/lib/R/etc/Rprofile.site

# Install IRkernel
RUN Rscript -e "install.packages(c('rzmq','repr','IRkernel','IRdisplay'), repos = c('http://irkernel.github.io/', getOption('repos')))" -e "IRkernel::installspec()"
