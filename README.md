# deep-sea
Curation of everything

## 유용한 프로그램들
  - immortal
    - A nix cross-platform (OS agnostic) supervisor
    - 간단히 설명하면 프로그램이 꺼지면 다시 살려줌. ~이모텝이라는 이름이었어도 좋았을텐데~
    - installation
      - curl -s https://packagecloud.io/install/repositories/immortal/immortal/script.deb.sh | sudo bash
      - apt install immortal

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

## conda 용량 줄이기
- conda clean -tp

## 너무 많아서 골치아픈 python 도서관들
- [Fabricb](http://www.fabfile.org/) - execute shell commands remotely over SSH
- [spaCy](https://spacy.io) - Industrial-strength natural language processing in python

## 이것도 너무 많아 js
- masonry js

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
  
- conda create on offline environment
  ```bash
  conda create -n yourenvname --clone root
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
    
- 콘다 경로 변경
  ```
  whereis 명령어로 찾아서... 경로 변경
  activate 
  conda.sh
  ```
  - 위의 conda.sh 파일과 activate, ... 들의 path를 수정하였지만, 계속해서 문제가 발생해서 conda uninstall을 safely 진행하게 되었다.
  ```bash
  rm -rf ~/anaconda
  rm -rf ~/.anaconda/navigator
  rm -rf ~/.condarc ~/.conda ~/.continuum
  nano ~/.bash_profile # remove the anaconda directory from your `PATH` env var
  remove the shortcut from the applications folder
  ```
  내게 적용된 방법은
  ```bash
  rm -rf ~/anaconda
  rm -rf ~/.conda
  nano ~/.bash_profile # remove the anaconda directory from your `PATH` env var
  remove the shortcut from the applications folder
  ```
  이정도..?
  
- mongoDB
  - create collection
  ```mongodb
  db.createCollection("people", { autoIndexId: true } )
  ```
  - update specific fields
  ```mongo
  db.books.update(
   { _id: 1 },
   {
     $set: {
       item: "ABC123",
       "info.publisher": "2222",
       tags: [ "software" ],
       "ratings.1": { by: "xyz", rating: 3 }
     }
   }
   ```
  - save(insert) document (w/ mongoose)
)

  - error: YouCompleteMe unavailable: requires vim compiled with python
    ```bash
    apt-get install python-dev
    ```
    해도 안된다면,
    ```bash
    cd /tmp && git clone https://github.com/vim/vim.git && cd vim
    ./configure --enable-pythoninterp --prefix=/usr
    make && sudo make install
    ```
    make 과정에서 "you need to install a terminal library; for example ncurses"같은 error가 난다면,
    ```
    apt-get install libncurses5-dev libncursesw5-dev
    ```
    걍 태초부터 
    https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source

  - python no module named ujson, while it's already installed
    export PYTHONPATH=$PYTHONPATH:/usr/lib64/python2.7/site-packages
