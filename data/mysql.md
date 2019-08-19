## MySQL 설치 in Ubuntu 16.04

```
apt-get install mysql-server
```

```
service mysql start
service mysql stop
```

### 그런데, /etc/mysql/my.conf 파일을 수정하자, 에러가 발생하며 실행이 안됨
(내가 원하던 datadir=/db/mysql/dir 이었음)
수정을 많이 했지만, 그 중에 datadir 에서 문제가 생긱는 것을 확인함(주석처리를 해봤을 때)

그 에러메세지는 아래와 같음.

[....] Restarting mysql (via systemctl): mysql.serviceJob for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl-xe" for details.

다양한 시도를 해봤으나 실패.
그러던 중 initialize를 보게 되고, 아래와 같이 시도함.

```
mysqld --initialize
```
permimssion denied 뜸. 뭔가 잘못된 것을 느낌.


### 해결 방법 루틴

0. /db/mysql/dir 폴더 지움
dir, mysql 폴더를 각각 지우고 빈 폴더로 다시 생성함

1. 일단, apparmor 문제부터 해결했음

    /etc/apparmor.d/usr/sbin.mysql 에서
    ```
    /etc/mysql/** r,
    ```
    이 있는지 확인하고,

    ```
    /db/mysql/dir/ r,
    /db/mysql/dir/** rwk,
    ```
    위 두줄을 추가함

2. 소유자/권한 문제 해결

    그리고, /db 위치에서,
    ```
    chmod -R 0771 mysql
    chown -R mysql:mysql mysql
    ```

3. mysqld --initialize 수행
    갑자기 에러없이 됨!

4. service mysql start 수행
    갑자기 에러없이 됨!

5. 행복

## 행복은 무슨 MySQL password 오류 나면서 접속이 안됨

안전모드로 들어가기 위해,
```
sudo mysqld_safe --skip-grant &
```
을 열심히 시도 했으나 계속해서 실패,

이유는 2가지 였다.

1. var/run/mysqld 폴더가 없었음. 생성해주고, chown로 mysql:mysql 설정해줌

2. --skip-grant-tables 로 바뀜

3. ```sudo mysqld_safe --skip-grant-tables &``` 로 안전모드를 돌입하고 나면,
```mysql -uroot myql```로 mysql로 진입!!!

4. query문을 통해서 패스워드 변경
        ```mysql
        mysql> update user set password=password('원하는비밀번호입력') where user='root';
        mysql> flush privileges;
        mysql> quit
        ```
5. mysql 서비스 재시작!

### mysql을 윈도우 10에 설치한 우분투에 설치하기
- 설치 명령어는 간단쓰-
    ```bash
    sudo apt-get update
    sudo apt-get install mysql-server
    ```
- 설치가 아래와 같은 에러도 중단됨ㅠ
    ```bash
    cannot open /proc/net/unix: No such file or directory
    cannot stat file /proc/1/fd/5: operation not permitted
    cannot stat file /proc/1493/fd/7: operation not permitted
    ```
    아래의 이 한줄로 해결! (다행)
    ```bash
    sudo service mysql start sudo dpkg --configure -a
    ```
- 비밀번호를 설정을 해야함!
    ```
    UPDATE mysql.user SET Password = PASSWORD('password') WHERE User = 'root';
    ```
    그런데 에러..
    ```
    ERROR 1054 (42S22): Unknown column 'Password' in 'field list'
    ```
    아래 명령어로 바뀐듯!
    ```
    use mysql;
    show tables;
    update user set authentication_string=password('1111') where user='root';
    ```
    
### Errors
- ERROR 1045 (28000): Access denied for user 'chanranhari'@'localhost' (using password: NO)
    - `mysql -u root -p`로 root로 접속!
- InternalError: (1130, "Host '127.0.0.1' is not allowed to connect to this MySQL server")
    - `grant all privileges on *.* to 'root'@'%' identified by 'PASSWORD' with grant option;`
        - PASSWORD 채워줄 것! 와... 
    
