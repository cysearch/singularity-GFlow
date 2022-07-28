BootStrap: docker
From: ubuntu:16.10

%labels
  Author Cysearch

%help
  This container runs GFlow software (see https://github.com/gflow/GFlow/)

%post
  # Configures default locale
  echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
  locale-gen en_US.utf8
  /usr/sbin/update-locale LANG=en_US.UTF-8
  export LC_ALL=en_US.UTF-8
  export LANG=en_US.UTF-8

  # Configures old releases sources.list
  echo "## old releases sources.list for ubuntu 16.10 "yakkety yak"
deb http://old-releases.ubuntu.com/ubuntu/ yakkety main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ yakkety-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ yakkety-security main restricted universe multiverse
" > /etc/apt/sources.list


  # https://github.com/precice/tutorials/issues/20
  # https://github.com/precice/precice/issues/526
  # Installs dependencies for GFlow, and bash utilities for calculations
  apt-get update && apt-get install -y mpich libhypre-dev git make wget bc dos2unix
  
  wget https://download.open-mpi.org/release/open-mpi/v2.1/openmpi-2.1.1.tar.gz --no-check-certificate
  
  tar xf openmpi-2.1.1.tar.gz
  
  cd openmpi-2.1.1
  
  ./configure
  
  make
  
  apt-get update && apt-get install -y petsc-dev
  
  #wget https://ftp.mcs.anl.gov/pub/petsc/release-snapshots/petsc-3.8.4.tar.gz --no-check-certificate
  
  #tar xf petsc-3.8.4.tar.gz
  
  #rm petsc-3.8.4.tar.gz
  
  #cd petsc-3.8.4
  
  #ln -s /usr/bin/python3 /usr/bin/python && python ./configure -with-cc=mpicc --with-cxx=mpicxx --with-fc=mpif90
  
  #make
  
  #cd
  
  # Installs dependencies for gdal
  apt-get update && apt-get install -y gdal-bin libgdal-dev python-pip

  pip install numpy==1.12.1
  export PATH=$PATH:/usr/include/gdal
  export CPLUS_INCLUDE_PATH=/usr/include/gdal && export C_INCLUDE_PATH=/usr/include/gdal && pip install gdal==2.1.3


  
  # gdal_calc
  wget https://download.osgeo.org/gdal/2.1.1/gdal-2.1.1.tar.gz --no-check-certificate
  mv gdal-2.1.1.tar.gz /usr/include/
  cd /usr/include/
  tar xzvf gdal-2.1.1.tar.gz
  rm gdal-2.1.1.tar.gz
  
  # Cleans up apt-get downloads
  rm -rf /var/lib/apt/lists/*
  
  # Builds GFlow 
  git clone https://github.com/cysearch/GFlow /opt/GFlow
  cd /opt/GFlow
  make
  cd

%environment
  export PATH=$PATH:/usr/include/gdal-2.1.1/swig/python/scripts
  echo "


Welcome to singularity container running ubuntu-16.10 yakkery yak for GFlow !

"