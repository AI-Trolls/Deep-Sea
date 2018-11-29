## set-centos-wo-yum

회사 내부의 개발망 같은 경우, yum을 이용하지 못하는 경우가 많아서 정리해둠-
wget은 파일을 미리 받아서 전송해놓으면 될듯
이상적으로는 docker image 하나 잘 만들어 놓는게 좋음

## Install GCC from source
```bash
wget http://ftp.mirrorservice.org/sites/sourceware.org/pub/gcc/releases/gcc-7.3.0/gcc-7.3.0.tar.gz

tar zxf gcc-7.3.0.tar.gz
cd gcc-7.3.0

./contrib/download_prerequisites
./configure --disable-multilib --enable-languages=c,c++

make -j 4
make install

gcc --version
```

## conda

```bash
wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh
bash Anaconda-latest-Linux-x86_64.sh
```
To make the changes take effect, close and then <u>re-open</u> your Terminal window ! <br/>
and test by
```bash
conda list
```

```
conda install -c conda-forge nodejs
```
를 실행하였음.
그러나, "CondaHTTPError: HTTP 000 CONECTION FAILED for url <https://conda.anaconda.orf/conda-forge/linux-64/nodejs-10.4.1-0.tar.bz2"라는 오류가 발생함. 하지만 윈도우 컴퓨터에서는 됨.


## nvm
https://github.com/creationix/nvm#manual-install

1. 아래를 실행!
```bash
export NVM_DIR="$HOME/.nvm" && (
  git clone https://github.com/creationix/nvm.git "$NVM_DIR"
  cd "$NVM_DIR"
  git checkout `git describe --abbrev=0 --tags --match "v[0-9]*" $(git rev-list --tags --max-count=1)`
) && \. "$NVM_DIR/nvm.sh"
```

2. add these lines to ~/.bashrc, ~/.profile, or ~/.zshrc
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

## mongoDB

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/ 이걸로 하면 댐

```bash
pip2 install -r buildscripts/requirements.txt
python2 buildscripts/scons.py all
python2 buildscripts/scons.py --prefix=/opt/mongo install
```

dependencies for mongoDB
```bash
yum install libcurl-devel
```

Most people should now use pip install setuptools (possibly with sudo).
Some may need to (re)install the python-setuptools package via their package manager (apt-get install, yum install, etc.).

pip install Cheetah3
yum install python-cheetah
sudo pip3 install --upgrade typing

## forever (node)
```bash
npm install -g forever


```
