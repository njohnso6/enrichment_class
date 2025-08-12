# Docker inheritance 
# this is a ubuntu image with R, Rstudio and bioC
FROM bioconductor/bioconductor_docker:RELEASE_3_16

# Update apt-get
RUN apt-get update \
 	&& apt-get install -y nano git vim \
 	## Install the python package magic wormhole to send files
 	&& pip install magic-wormhole \
 	## Remove packages in '/var/cache/' and 'var/lib' 
	## to remove side-effects of apt-get update
 	&& apt-get clean \
 	&& rm -rf /var/lib/apt/lists/*

# Install required CRAN packages
RUN R -e 'install.packages(c("kableExtra","vioplot","gplots","eulerr","tweenr","bit"))'

# Install required Bioconductor package
RUN R -e 'BiocManager::install(c("getDEE2","DESeq2","fgsea","clusterProfiler","mitch","biomaRt","org.Mm.eg.db","enrichplot"))'

# Clone the repository that contains the research code and execute it
RUN git clone https://github.com/markziemann/enrichment_recipe.git

COPY requirements.txt /tmp/pip-tmp/
RUN python3 -m pip --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt

# Set the container working directory
ENV DIRPATH /enrichment_recipe
WORKDIR $DIRPATH

# Copy this datafile into the container for easy access
COPY AMvsEM_deseq2_results.csv /enrichment_recipe/data/

# Set environment variable to use host's X11 display
ENV DISPLAY=:0


CMD ["ls", "-l", "/data"]

