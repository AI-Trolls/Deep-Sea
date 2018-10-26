
- conda 용량 줄이기
  ```
  conda clean -tp
  ```
  
- conda create on offline environment
  ```bash
  conda create -n yourenvname --clone root
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
