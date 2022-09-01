# Installation of conda environment and dependencies for QuickFixR

*Please find more info on: https://github.com/JacobAgerbo/QuickFixR*

I base this tutorial on conda and therefore miniconda should be installed prior the tutorial, please see link:
*https://docs.conda.io/en/latest/miniconda.html*

First thing we need to do is, creating a conda environment. 

For this you will a config file with all dependencies. This file has already been made and can be downloaded. It is called **Metabolomics.yml**.


```
conda env create -f Metabolomics.yml
```

This environment has installed R (>4.1) with several packages, but a few more is needed. 
These packages are not yet to be found on condas channels and therefore we will install them in R

Launch conda environment and subsequently R, by typing:

```
conda activate Metabolomics #activating the environment
R #starting R
```

Now install dependencies

```
dependencies <- c("boral","ggboral", "pbkrtest", "ggiraph", "hilldiv")
installed_packages <- dependencies %in% rownames(installed.packages())
if (any(installed_packages == FALSE)) {
  install.packages(dependencies[!installed_packages])}
#BiocManager
installed_packages <- dependencies %in% rownames(installed.packages())
if (any(installed_packages == FALSE)) {
BiocManager::install(dependencies[!installed_packages])}
#Github
installed_packages <- dependencies %in% rownames(installed.packages())
if (installed_packages[2] == FALSE) {
  remotes::install_github("mbedward/ggboral")}
```

Now please install my R package *QuickFixR* 

```
devtools::install_github("JacobAgerbo/QuickFixR")
```

After this you should be golden! And should be able launch the shiny app simply by typing:

```
QuickFixR::QuickFix()
```
