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
libldap2-dev python3-dev libxml2-dev libkrb5-dev libgsl0-dev python3-pip \
r-base r-base-dev gsl-bin libgsl-dev ocaml libz3-dev libxpm-dev libxft-dev
```

## Getting External Dependencies (Optional)
<par>
R dependencies. First runn R
</par>

```
sudo R
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
sudo pip3 install scikit-learn numpy matplotlib scipy jupyter ipython metakernel
```

## Getting the code from github

<par>
Clone the code from the repository at GitHub
</par>

```bash
#git clone --branch latest-stable --depth=1 https://github.com/root-project/root.git
git clone http://root.cern.ch/git/root.git
cd root
```

## Compile and setup 

<par>
  Set the last stable version. At the time of the last modification to this document the lates version was v6-24-00-patches
</par>

```bash
git checkout v6-28-00-patches
```

<par>
Create a new folder for the installation, and compile. At the last line the 8 is the number of cores, you can change for yours.
</par>

```bash
mkdir v6-28-00-patches
cd v6-28-00-patches
cmake -Dr=ON -Dpython3=ON -Dhttp=ON ..
#Max threads
make -j $(grep -c processor /proc/cpuinfo)
#for single core or less than max use
#make -j @ #Where @ is the number of cores 
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
cd $ROOT_FOLDER_PATH/etc/notebook/kernels/
sudo jupyter kernelspec install root
cd $ROOT_FOLDER_PATH
```
