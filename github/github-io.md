# Github.io

그냥 기본적인 style로 하면 매우 쉬운데,<br>
template 좀 이쁜거 써보려 하면 매우 귀찮아짐.<br>

#### gem(ruby)과 jekyll 기반이라는 것 알아주고 시작!

```bash
sudo apt-get install ruby ruby-bun
bundle install
```

```err
Bundler could not find compatible versions for gem "bundler":
  In Gemfile:
    bundler (~> 1.15)

  Current Bundler version:
    bundler (1.11.2)
```

처음부터 높은 버젼을 깔아주지 쪼잔쓰리...

```bash
gem install bundler -v '~> 1.15.0'
```

요구 조건에 맞는 수준으로 업!<br>
다시 undle install 했으나 똑같은 오류가 난다 ㅡㅡ<br>
승질이 난다 ㅡㅡ<br>

예전에 npm도 버젼 이슈를 겪었었는데, nvm으로 버젼관리를 했던 기억이 난다-<br>
ruby를 위한 [rvm](https://stackoverflow.com/questions/4373128/how-do-i-activate-a-different-version-of-a-particular-gem)도 존재한다.<br>

### RVM 설치부터 시작...
(난 도대체 무엇을 누리려고 이 먼길을 떠나는가...)

- requirements
    software-properties-common라는 것을 깔아야 한다네요
    ```bash
    sudo apt-get install software-properties-common
    ```
   그리고 ppa 추가해주고, 설치 강행! 
    ```bash
    sudo apt-add-repository -y ppa:rael-gc/rvm
    sudo apt-get update
    sudo apt-get install rvm
    ```
    rvm을 이용해 ruby 설치!!
    ```bash
    rvm install ruby
    ```
    restart를 권장하는데 난 귀차나서 안함
    ```
    source /etc/profile.d/rvm.sh
    ```
    로 활성화 하고! `rvm`으로 잘 실행되는지 확인!<br>
    확인 완료했으면, 이제 rvm을 이용해서 원하는 ruby 버젼 설치..!
    ```
    rvm install 1.15.4
    ```
    라고 했으나, 
    ```err
    Unknown ruby interpreter version (do not know how to handle): 1.15.4.
    ```
    라는 에러, 다른 버젼을 설치해보자
    ```bash
    rvm install 2.1
    ```
    ```err
    -2.1.10.tar.bz2.part: Permission denied
    ```
    아 진짜...
    ```bash
    sudo -i
    rvm install 2.1
    logout
    ```
    다시 local 유저로 돌아와서
    ```
    rvm use 2.1
    ```
    드디어ㅠㅠ 원하는 버젼 사용... 원하던걸 하기위해 돌아가보자;

### 다시 bundle install로
- bundle install
    bundle install은 bundler가 없다는 에러를   뱉어냈다.
    ```err
    /usr/lib/ruby/2.3.0/rubygems/dependency.rb:319:in `to_specs': Could not find 'bundler' (>= 0.a) among 6 total gem(
    ```
    2.1 버젼인데 2.3.0 폴더를 참조하고있는게 매우 의심스럽고 쯔증나지만- 일단은 속아주고 bundler 설치부터 해보자
    ```bash
    gem install rubygems-bundler
    ```
    ```
    Building native extensions.  This could take a while...
    ERROR:  Error installing rubygems-bundler:
    ERROR: Failed to build gem native extension.
    ```
    망할 설치도 안됨
    ```
    sudo -i
    gem install rubygems-bundler
    logout
    ```
    똑같은 에러^^ 

