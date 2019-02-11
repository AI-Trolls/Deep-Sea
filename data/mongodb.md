- create collection
  ```mongodb
  db.createCollection("people", { autoIndexId: true, timestamps: { createdAt: 'createdDate',updatedAt: 'updatedDate' } )
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
   },
   {multi: true}
   );
   ```
- save(insert) document (w/ mongoose)


- 특정 field가 not null인 것 찾기
  ```mongodb
  db.cols.find( { field: { $ne: null } } );
  db.cols.find( { field: { $ne: '' } } ); //빈 스트링이었더니 이렇게 하는게 나에게는 맞
  ```
  not null인 field null로 만들기
  ```mongodb
  db.cols.update({field:{$ne:''}}, {$set: {{field: ''}}, {multi: true});
  ```

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
