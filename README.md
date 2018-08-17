# deep-sea
Curation of everything

### 유용한 코드들
- [Quiver](https://github.com/keplr-io/quiver)
  - Interactive convnet features visualization for Keras
  - 연관 논문: http://yosinski.com/deepvis

### 읽어볼만한 자료들
- [Python 게임 서버 안녕하십니까? 몬스터 슈퍼리그 게임 서버 - SMARTSTUDY 박준철](https://www.slideshare.net/joongom/ndc2017-python)
  - Game Server: Flask
  - DB: SQLAlchemy

### 써볼만한 기능을 가진 사이트들

- [RegExr](https://regexr.com)

- [ETRI의 <s>공공</s> 인공지능 <s>오픈</s> API·DATA 서비스 포털](http://aiopen.etri.re.kr)
  - 장점: 한국어에 대한 수준 높은 언어 분석(형태소 분석), 어휘관계 분석, 질문 분석, 음성 인식 API 제공.
  - 단점: 키 발급받아야 사용가능하고, 그다지 공공·오픈 이라는 느낌이 들지 않음

### 변환
- ipynb (ipython notebook) to markdown
  - ` ipython nbconvert --to markdown mynotebook.ipynb `

### 잼나리 해보이는 곰국
- [How transferable are features in deep neural networks?](http://yosinski.com/media/papers/Yosinski__2014__NIPS__How_Transferable_with_Supp.pdf)
  - Jason Yosinski, Jeff Clune, Yoshua Bengio, and Hod Lipson
  - NIPS, 2014
- [CONVERGENT LEARNING: DO DIFFERENT NEURAL NETWORKS LEARN THE SAME REPRESENTATIONS?](https://arxiv.org/pdf/1511.07543.pdf)
  - Yixuan Li, Jason Yosinski, Jeff Clune, Hod Lipson, & John Hopcroft
  - ICLR, 2016

### 싱기방기 github
- [LambdaHack](https://github.com/LambdaHack/LambdaHack)
- [openage](https://github.com/SFTtech/openage) - age of empire 2 소스 코드 공개... ㅎㄷㄷ
- [codecombat](https://github.com/codecombat/codecombat) - 게임으로 배우는 코딩?!

### 너무 많아서 골치아픈 python 도서관들
- [Fabricb](http://www.fabfile.org/) - execute shell commands remotely over SSH
- [spaCy](https://spacy.io) - Industrial-strength natural language processing in python

### Problem Solving
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
