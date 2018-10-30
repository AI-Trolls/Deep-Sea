- mongodb 이전하기 (db 데이터를 dump로 만들기)
  - 모든 db, collection을 옮기는 경우
    ```bash
    mongodump --port 27017
    mongorestore -h 127.0.0.1 ~/dump/
    ```
  - 원하는 collection만 옮기는 경우 (db만은 안되는 듯)
    ``` bash
    mongoexport -h 127.0.0.1:27017 -d _dbName -c _collectionName -o _filename.json
    mongoimport -h 127.0.0.1:27017 -d _dbName -c _collectionName --file _filename.json
    ```
    
- pymongo.errors.ServerSelectionTimeoutError: IP:PORT: [Errno 111] connection refused
+ Failed to restart mongod.service: Unit mongod.service not found (by sudo service mongod restart)
+ Failed to excute operation: No such file or dictionary (by sudo systemctl enable mongod)
  - 위의 3개의 error가 나타난다. 가장 위의 error를 먼저 만났고, 그 error를 고치기 위해 mongo service를 다루는 과정에서 나머지 2개의 error를 만났다.
+ exception in initAndListen: IllegalOperation: Attempted to create a lock file on a read-only directory: /data/db, terminating
  - mongod를 kill하고 다시 실행하는 과정에서 /data/db가 root의 권한으로 되어있어서 접근이 불가능한 것으로 보였다.
    ```bash
    chown -R $USER /data/db
    ```
  - 재설치 시도
  
- mongodb 재설치하기
