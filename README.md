# deep-sea
Curation of everything

## Sub-files
- linux
  - [anaconda](linux/anaconda.md)
  - [centos](linux/centos.md)
  - [ubuntu](linux/ubuntu.md)
- python
  - [python](python/python.md)

## 유용한 프로그램들
  - immortal
    - A nix cross-platform (OS agnostic) supervisor
    - 간단히 설명하면 프로그램이 꺼지면 다시 살려줌. ~이모텝이라는 이름이었어도 좋았을텐데~
    - installation
      - curl -s https://packagecloud.io/install/repositories/immortal/immortal/script.deb.sh | sudo bash
      - apt install immortal
    - stop all services
      - immortalctl halt "*"

## 유용한 코드들
- [Quiver](https://github.com/keplr-io/quiver)
  - Interactive convnet features visualization for Keras
  - 연관 논문: http://yosinski.com/deepvis

## 읽어볼만한 자료들
- [Python 게임 서버 안녕하십니까? 몬스터 슈퍼리그 게임 서버 - SMARTSTUDY 박준철](https://www.slideshare.net/joongom/ndc2017-python)
  - Game Server: Flask
  - DB: SQLAlchemy

## 써볼만한 기능을 가진 사이트들
- [RegExr](https://regexr.com)
- [ETRI의 <s>공공</s> 인공지능 <s>오픈</s> API·DATA 서비스 포털](http://aiopen.etri.re.kr)
  - 장점: 한국어에 대한 수준 높은 언어 분석(형태소 분석), 어휘관계 분석, 질문 분석, 음성 인식 API 제공.
  - 단점: 키 발급받아야 사용가능하고, 그다지 공공·오픈 이라는 느낌이 들지 않음

## Linkes
- [Open Knowledge Labs](http://okfnlabs.org/)

## 변환
- ipynb (ipython notebook) to markdown
  - ` ipython nbconvert --to markdown mynotebook.ipynb `

## 잼나리 해보이는 곰국
- [How transferable are features in deep neural networks?](http://yosinski.com/media/papers/Yosinski__2014__NIPS__How_Transferable_with_Supp.pdf)
  - Jason Yosinski, Jeff Clune, Yoshua Bengio, and Hod Lipson
  - NIPS, 2014
- [CONVERGENT LEARNING: DO DIFFERENT NEURAL NETWORKS LEARN THE SAME REPRESENTATIONS?](https://arxiv.org/pdf/1511.07543.pdf)
  - Yixuan Li, Jason Yosinski, Jeff Clune, Hod Lipson, & John Hopcroft
  - ICLR, 2016

## 싱기방기 github
- [LambdaHack](https://github.com/LambdaHack/LambdaHack)
- [openage](https://github.com/SFTtech/openage) - age of empire 2 소스 코드 공개... ㅎㄷㄷ
- [codecombat](https://github.com/codecombat/codecombat) - 게임으로 배우는 코딩?!

## 너무 많아서 골치아픈 python 도서관들
- [Fabricb](http://www.fabfile.org/) - execute shell commands remotely over SSH
- [spaCy](https://spacy.io) - Industrial-strength natural language processing in python

## 이것도 너무 많아 js
- masonry js

## 리눅스에서 구글 드라이브 다운로드
  ```
  pip install gdown
  gdown https://drive.google.com/uc?id=file_id
  ```
  구글 드라이브 링크 복사해서, open -> uc 로 바꿔서 gdown 하면 됨!

## Anaconda install and init
  ```
  curl -O https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh --limit-rate 10M
  sha256sum Anaconda3-5.0.1-Linux-x86_64.sh
  bash Anaconda3-5.0.1-Linux-x86_64.sh
  source ~/.bashrc
  conda create --name tf36 python=3.6
  source activate tf36
  ```

## JupyterLab
  ```bash
  conda install -c conda-forge jupyterlab
  python3 -m pip install jupyterlab
  pipenv install jupyterlab
  pipenv shell
  
  jupyter lab --ip 0.0.0.0 --port 80
  ```

## pixiedust 설치 및 사용
  https://pixiedust.github.io/pixiedust/install.html
  ```bash
  pip install pixiedust
  pip3 install -U html5lib=="0.9999999"
  jupyter pixiedust install
  sudo update-alternatives --config java
  ```
  java9는 spark & scala를 위해 지원이 안되므로, sudo update-alternatives --config java를 통해 8로 낮추거나 재설치해야함

  jupyter에 nodejs가 없는 경우
  ```bash
  git clone https://github.com/notablemind/jupyter-nodejs.git
  cd jupyter-nodejs
  mkdir -p ~/.ipython/kernels/nodejs/
  npm install && node install.js
  npm run build
  npm run build-ext
  jupyter console --kernel nodejs
  ```

## conda install로 안되서 pip install로 설치하는데, conda에 적용 안되는 경우 (pip로 anaconda 환경에 설치)
  - `python -V`로 실행되는 python 경로 확인
    - 여기서 만약 source activate를 안한 상태라면, 기본 python path가 되어있을 것.
    - 해둔 상태라면, anaconda를 포함하는 경로가 나올 것 ex) anaconda3/env/tf35/bin/pip
    - 나의 경우 tf35라는 이름의 환경임. `anaconda3/env/tf35/bin/pip install tensorlayer` 이런식으로 설치하면 됨!

## Problem Solving
- Vim update
  ```bash
  # curl -L https://copr.fedorainfracloud.org/coprs/mcepl/vim8/repo/epel-7/mcepl-vim8-epel-7.repo -o /etc/yum.repos.d/mcepl-vim8-epel-7.repo
  # yum update vim*
  ```
- syntax highlighting for Vue (needs Vim 8)
  ```bash
  git clone https://github.com/posva/vim-vue.git ~/.vim/pack/plugins/start/vim-vue
  ```
  
- .vimrc for python [link](https://stackoverflow.com/questions/65076/how-to-setup-vim-autoindentation-properly-for-editing-python-files-py)
  ```bash
  set nu
  set expandtab
  set textwidth=120
  set tabstop=4
  set softtabstop=4
  set shiftwidth=4
  set autoindent
  ```
  
- tf.estimator package not installed
  ```bash
  pip install tensorflow-transform
  ```
  
- Error: libzmq.so.5: cannot open shared object file: No such file or directory
  ```
  zeromq 설치 및
  .bashrc에서 $LD_LIBRARY_PATH 에 해당 파일 path 추가
  ```

- Error:/lib64/libstdc++.so.6: version `GLIBCXX_3.4.21' not found (required by .../zmq.node)
  ```
  conda install libgcc
  면 끝나지만, 내 환경에서는 이것이 안됨ㅠ
  
  strings /usr/lib/libstdc++.so.6 | grep GLIBCXX
  로 확인해보니, GLIBCXX_3.4 ~ GLIBCXX_3.4.19 까지만 있고... 21버젼은 없는 상황.
  
  cd /tmp
  wget ftp://ftp.gwdg.de/pub/misc/gcc/releases/gcc-8.2.0/gcc-8.2.0.tar.gz
  tar -xvzf gcc-8.2.0.tar.gz
  cd gcc-8.2.0
  ./contrib/download_prerequisites
  mkdir objdir
  cd objdir
  ../configure --prefix=/opt/gcc-8.2.0
  make
  make install
  mv /usr/lib64/libstdc++.so.6 /usr/lib64/libstdc++.so.6.bak
  mv /opt/gcc-8.2.0/lib64/libstdc++.so.6 /usr/lib64/libstdc++.so.6
  mv /opt/gcc-8.2.0/lib64/libstdc++.so.6.0.16 /usr/lib64/libstdc++.so.6.0.16
  ```
  
- 설치 설치 설치...
  - node zmq (Error: Cannot find module 'zmq')
    - pip install pyzmq
    - conda install pyzmq
    - brew install zeromq
    - npm install zmq
      - error: 'class v8::object' has no member named 'ForceSet'
      - npm ERR! zmq@2.15.3 install: `node-gyp rebuild`
        ```
        brew install pkg-config
        ```
    - 해결됐다면, 당신은 축복받음. node 버젼이 10 이상인 경우 zmq와 문제가 생김. zmq에서 아직 해결 안함 ㅡㅡ
      따라서 node 버젼을 낮출 필요가 있음. nvm을 사용한다면, 
      ```
      nvm install 8.11.3
      nvm use 8.11.3
      ```
  - scikit-learn
    - no module named 'sklearn'
    - conda install cython
    - conda install scikit-learn
  - Linuxbrew
    ```bash
    git clone https://github.com/Linuxbrew/brew.git ~/.linuxbrew
    PATH="$HOME/.linuxbrew/bin:$PATH"
    export MANPATH="$(brew --prefix)/share/man:$MANPATH"
    export INFOPATH="$(brew --prefix)/share/info:$INFOPATH"
    ```
    
