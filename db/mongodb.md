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
