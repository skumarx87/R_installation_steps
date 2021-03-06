# Jupyter Notebook Installation with Miniconda
```
mkdir -p  /usr/bigdata
mkdir softwares
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh -b -p /usr/bigdata/Miniconda3
export PATH=/usr/bigdata/Miniconda3/bin:$PATH
/usr/bigdata/Miniconda3/bin/conda create -n pythonML -y
source activate pythonML
pip install notebook
nohup jupyter notebook --ip=0.0.0.0 &
```

# R_installation_steps
```

export PATH=/usr/bigdata/tools/bin:$PATH
export LD_LIBRARY_PATH=/usr/bigdata/tools/lib:$LD_LIBRARY_PATH
export CFLAGS="-I/usr/bigdata/tools/include"
export LDFLAGS="-L/usr/bigdata/tools/lib"

yum -y groupinstall "Development Tools"
yum -y install xz xz-devel libcurl-devel bzip2-devel zlib-devel readline-devel xorg-x11-server-devel libX11-devel libXt-devel

cd $HOME

wget http://ftp.cs.stanford.edu/pub/exim/pcre/pcre2-10.37.tar.gz

tar -zxvf pcre2-10.37.tar.gz
cd pcre2-10.37
./configure --prefix=/usr/bigdata/tools
make -j 24
make install

cd $HOME

wget https://cran.r-project.org/src/base/R-4/R-4.1.2.tar.gz
tar -zxvf R-4.1.2.tar.gz
cd R-4.1.2

./configure --prefix=/usr/bigdata/R-4.1.2 --enable-R-shlib --with-x=yes --with-readline --enable-memory-profiling
make
make install

./R
install.packages('IRkernel')
install.packages('plotly')
IRkernel::installspec(user = TRUE)
```
