# InstallROOT6

## Guide to install Cern root from surces at Debian based Linux

<par> The [instal.sh](./install.sh) script is generated automatically with the following commands in this file. It can install all if there is not a dependence problem</par>

<par>
ROOT requires several external libraries in order to properly run, then it is mandatory to install them
</par>
- First Update and upgrade the distro

```bash
sudo apt-get update && sudo apt-get upgrade
```
Install Prerequisites

```bash
sudo apt-get install cmake git dpkg-dev make g++ gcc binutils libx11-dev libxpm-dev \
libxft-dev libxext-dev gfortran libssl-dev libpcre3-dev \
xlibmesa-glu-dev libglew1.5-dev libftgl-dev \
libfftw3-dev libcfitsio-dev graphviz-dev libavahi-compat-libdnssd-dev \
libldap2-dev python-dev libxml2-dev libkrb5-dev libgsl0-dev python3-pip \
r-base r-base-dev gsl-bin libgsl-dev ocaml libz3-dev
```

## Getting External Dependencies (Optional)
<par>
R dependencies. First runn R
</par>

```
R
```

<par>
Inside the R terminal
</par>

```
install.packages(c('Rcpp','RInside','C50','xgboost','e1071','RSNNS'))
quit()
```

<par>
Install Python dependencies
</par>

```bash
pip install scikit-learn numpy matplotlib scipy jupyter ipython metakernel
```

## Getting the code from github

<par>
Clone the code from the repository at GitHub
</par>

```bash
git clone http://root.cern.ch/git/root.git
cd root
```

## Compile and setup 

<par>
  Set the last stable version. At the time this document was written the lates version is v6-22-00-patches
</par>

```bash
git checkout v6-22-00-patches
```

<par>
Create a new folder for the installation, and compile. At the last line the 8 is the number of cores, you can change for yours.
</par>

```bash
mkdir v6-20-00-patches 
cd v6-20-00-patches
cmake -Dr=ON -Dpython3=ON -Dhttp=ON ..
make -j 8
```

## Setup ROOT in your environment
<par>
  Set the path to root
</par>  

```bash
ROOT_FOLDER_PATH=$(pwd)
THISROOT_PATH="source "$ROOT_FOLDER_PATH"/bin/thisroot.sh"
echo $THISROOT_PATH >> ~/.bashrc
source ~/.bashrc
```

<par> 
Setup the pyrootModules
</par> 

```bash
cd $ROOT_PATH/v6-22-00-patches/etc/notebook/kernels/
jupyter kernelspec install root
```
