# Metabolomics Analysis 

Dear all 

**Thank you for attending!** 

## Pre-processing of data, using MZmine3
Please see documentation [here](https://mzmine.github.io/mzmine_documentation/workflows/lcmsworkflow/lcms-workflow.html)

## *In silico* classification using SIRIUS:CSI-FingerID
Please see documentation [here](https://boecker-lab.github.io/docs.sirius.github.io/)

## Multivariate analysis with QuickFixR

First things first!
**Open Terminal**

* Go to Applications
* Open System Tools > MATE Terminal

Now Terminal should open, and we need to launch our environment.
First, we can our possible environments in conda.

```
conda env list
```

Here you see a list of environments, including the “Metabolomics” environment. This needs to be activated.

```
conda activate Metabolomics
```
**Easy!**
Now we can use R and all the dependencies in the environment.
First thing, launch **R**

```
R
```

Now you are in the R program and can launch this code to open my package for multivariate analysis called “QuickFixR”.
First we load the package and set our browser options

```
library(QuickFixR)
options(browser="firefox")
```

Now launch the software! **After the command, a browser window will open with an user-interface for your multivariate analysis**.

```
QuickFix()
```

## If you would like more commandline-based R

Please find a markdown [**here**](https://github.com/JacobAgerbo/HF_Course_Bilbao)
