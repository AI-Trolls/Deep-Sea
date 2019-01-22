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