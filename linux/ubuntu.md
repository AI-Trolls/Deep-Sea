## Linux | Ubuntu

### 기본 명령어
- 남은 용량 보기
  - df -h : 깔끔하게 정리해서 보여줌
    
- /home 디렉토리 바꾸기
  ```
  vi /etc/passwd
  username:x: ... ::/home/username:/binbash
  username:x: ... ::/newdir/home/chanranhari:/binbash
  ```

### 개척
- 리눅스 운영체제 bit 확인 방법 (Linux OS bit)
  ```bash
  getconf LONG_BIT
  ```
  결과가 64면 64bit 결과가 32면 32bit
  ```bash
  grep . /etc/*-release
  ```


- 계정 생성
  adduser의 경우 명령어 실행시 기본 계정정보를 같이 생성해주지만 <- 가 편함
  useradd의 경우 계정만 생성하며 기타 다른 정보를 수동으로 생성 및 설정해주어야 한다. 
  /etc/passwd 에서 확인 및 수정
  
- sudo 권한
  $ sudo vi /etc/sudoers
  계정명 ALL=(ALL:ALL) ALLL
  
## Matplotlib 에서 한글 깨짐 linux/ubuntu 따라서 폰트 설치 및 적용
- 폰트 설치
  ```bash
  sudo apt-get install fonts-nanum*
  sudo fc-cache -fv
  sudo cp new_font.ttf /usr/share/fonts/
  sudo fc-cache -fv
  ```
- 로컬 영역에 추가 및 캐시 삭제
  ```bash
  sudo cp /usr/share/fonts/truetype/nanum/Nanum* /usr/local/lib/python3.4/dist-packages/matplotlib/mpl-data/fonts/ttf/
  rm -rf /home/ubuntu/.cache/matplotlib/*
  ```
- conda 콘다 영역에 한글 폰트 추가 및 캐시 삭제
  ```bash
  sudo cp /usr/share/fonts/truetype/nanum/Nanum* /home/{user_id}/anaconda3/envs/{env_name}/lib/python3.5/site-packages/matplotlib/mpl-data/fonts/ttf/
  rm -rf /home/ubuntu/.cache/matplotlib/*
  ```
- 사용 가능한 ttf 폰트 목록 확인
  ```bash
  import matplotlib
  import matplotlib.font_manager
  matplotlib.font_manager.fontManager.ttflist
  ```
- python 코드에 적용
  ```bash
  font_fname = '/usr/share/fonts/truetype/nanum/NanumGothic.ttf'
  font_name = font_manager.FontProperties(fname=font_fname).get_name()

  rc('font', family=font_name)
  print(font_name)
  ```
## mongoDB 설치하기
  ```bash
  sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
  
  echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list # for Ubuntu 14.04 (Trusty)
  #echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list # for Ubuntu 16.04(Xenial)
  #echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list # for Ubuntu 18.04 (Bionic)

  sudo apt-get update
  sudo apt-get install -y mongodb-org
  ```
