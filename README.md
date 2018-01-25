# Changes for Summit at CU Research Computing.
I have modified the configure file to work on summit. 
* Its 'grep/sed' command for determining the version of the boost library was failing because of a leading space present in the version.h file.
## Installation in R.
As of Thu Jan 25 11:08:56 MST 2018

### the following modules must be loaded.
`ml` is a shortcut for `module load`.
    * ml intel
    * ml impi
    * ml boost
    * ml R

### Locally installing in R

A local install path must be set inside R. For us, your project space is encouraged, and I recommend creating an `R` directory: 
```
mkdir /projects/username@colostate.edu/R
```

```
$ R
.libPaths('/projects/username@colostate.edu/R)
```

The original repository uses devtools, but that may be insufficient to install dependencies on Summit. To try it, update the url in that command.

```
require(devtools)
devtools::install_github('meekrob/spp', build_vignettes = FALSE)
```

Preferably, download this package using `git clone` and the url of this repository, it should create a directory called spp. In the same directory, start `R`, and do
```
.libPaths('/projects/username@colostate.edu/R') # Set your local install path
install.packages("spp", repos=NULL) # Should install dependancies
```
This will also compile SPP, and may take a while.

### To run SPP
In R:
```
.libPaths('/projects/username@colostate.edu/R') # Set your local install path
require(spp)
```
If the require succeeds without reporting errors, the installation worked.

---
Original README
---

# ChIP-seq processing pipeline
An [R](https://www.r-project.org/) package for anlaysis of ChIP-seq and other functional sequencing data.
Please see [package homepage](http://compbio.med.harvard.edu/Supplements/ChIP-seq/) for details.

## Requirements
A unix-flavored OS with R and [Boost C++](https://www.boost.org/) installed.

## Installation
You can use modtools to install SPP:
```
require(devtools)
devtools::install_github('hms-dbmi/spp', build_vignettes = FALSE)
```
Alternatively, download a .tar.gz containing the [latest release](https://github.com/hms-dbmi/spp/releases) and use the standard R installation command, e.g.:
```
R CMD INSTALL spp_1.13.tar.gz
```

Note: if Boost libraries are installed in a non-standard location, please specify the location in a `BOOST_ROOT` environment variable prior to running the installation.
```
export BOOST_ROOT=/path/boost_1_58_0/
```
