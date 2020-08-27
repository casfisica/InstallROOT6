# InstallROOT6

## Guide to install Cern root from surces at Debian based Linux

<par>
ROOT requires several external libraries in order to properly run, then it is mandatory to install them
</par>
- First Update and upgrade the distro
```bash
sudo apt-get update && sudo apt-get upgrade
```
- Install Prerequisites
```bash
apt-get install cmake git dpkg-dev make g++ gcc binutils libx11-dev libxpm-dev \
libxft-dev libxext-dev gfortran libssl-dev libpcre3-dev \
xlibmesa-glu-dev libglew1.5-dev libftgl-dev \
libfftw3-dev libcfitsio-dev graphviz-dev libavahi-compat-libdnssd-dev \
libldap2-dev python-dev libxml2-dev libkrb5-dev libgsl0-dev python3-pip\
r-base r-base-dev gsl-bin libgsl-dev ocaml libz3-dev
```
## Getting the code from github

<par>
Clone the code from the repository at GitHub
</par>

```bash
git clone http://root.cern.ch/git/root.git
```

## Getting External Dependencies (Optional)
<par>
R dependencies. First runn R
</par>

```bash
R
```

<par>
Inside the R terminal
</par>

```bash
install.packages(c('Rcpp','RInside','C50','xgboost','e1071','RSNNS'))
quit()
```

