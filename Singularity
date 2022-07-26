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

  # Installs dependencies for gdal
  apt-get update && apt-get install -y gdal-bin libgdal-dev python-pip

  pip install numpy==1.12.1
  export PATH=$PATH:/usr/include/gdal
  
  export CPLUS_INCLUDE_PATH=/usr/include/gdal && export C_INCLUDE_PATH=/usr/include/gdal && pip install gdal==2.1.3

  # Installs dependencies for GFlow
  apt-get update && apt-get install -y openmpi-bin libhypre-dev petsc-dev git make wget
  
  # gdal_calc
  wget https://download.osgeo.org/gdal/2.1.1/gdal-2.1.1.tar.gz --no-check-certificate
  mv gdal-2.1.1.tar.gz /usr/include/
  cd /usr/include/
  tar xzvf gdal-2.1.1.tar.gz
  rm gdal-2.1.1.tar.gz
  export PATH=$PATH:/usr/include/gdal-2.1.1/swig/python/scripts/
  
  # Cleans up apt-get downloads
  rm -rf /var/lib/apt/lists/*
  
  # Builds GFlow 
  git clone https://github.com/cysearch/GFlow /opt/GFlow
  cd /opt/GFlow
  make
  cd

%runscript
  echo "welcome to singularity container running ubuntu-16.10 yakkery yak for GFlow"
