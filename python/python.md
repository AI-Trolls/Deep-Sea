## Python
- python np array initialization with value and length
  - np.full((3, 5), 7, dtype=int)
    array([[7, 7, 7, 7, 7],
          [7, 7, 7, 7, 7],
          [7, 7, 7, 7, 7]])
          
- python print same line
  - print (word1, end=' ')
  
- python time to string
  - import time
    timestr = time.strftime("%Y%m%d-%H%M%S-%f) # %f: micro second

- Comparing a string to multiple items in Python
  ```python3
  accepted_strings = {'auth', 'authpriv', 'daemon'}
  if facility in accepted_strings:
      do_stuff()
  ```
  
  - python np array initialization with value and length
  - np.full((3, 5), 7, dtype=int)
    array([[7, 7, 7, 7, 7],
          [7, 7, 7, 7, 7],
          [7, 7, 7, 7, 7]])

- python으로 http 파일 서버 열기
  ```
  python3 -m http.server 3333
  ```

- python runtime timestamp print 
  ```python3
  import time
  start_time = time.time()
  main()
  print("--- %s seconds ---" % (time.time() - start_time))
  ```
  
- 문자열에서 특수문자 지우기 (string)
  ```python
  import re
  text = u'010-1566#7152'
  parse = re.sub('[-=.#/?:$}]', '', text)
  print parse
  ```

- Handling missing keys in Python dictionaries
  - get(key, default_value) 함수를 활용하여 해결
  - body_position_info라는 key에 해당하는 값이 있으면, return해주고, 아니면 -1을 리턴
  ```python
  if output_data.get('body_position_info', -1) == -1:
    continue
  ``` 
  
- 변수의 type 검사 (아래 예는 str인지)
  ```python
  if isinstance(variable, str):
  ```

## JSON
- JSONDecodeError:
  - json_str = json.loads(jsonString, strict=False)
  - If strict is false (True is the default), then control characters will be allowed inside strings. Control characters in this context are those with character codes in the 0–31 range, including '\t' (tab), '\n', '\r' and '\0'.

- UnicodeDecodeError: 'utf8' codec can't decode byte
  - str = unicode(str, errors='replace')
  - str = unicode(str, errors='ignore')
- Json file open
  ```python
  import json
  with open('data.json') as f:
    data = json.load(f)
  print(data)
  ```

## JSONL (JSON Line)
- python -m pip install json-lines
  ```python
  import json_lines

  with open('fileName.jsonl', 'rb') as f: # opening file in binary(rb) mode    
    for item in json_lines.reader(f):
      print(item) #or use print(item['X']) for printing specific data
  ```
  - 이유는 모르겠지만, no module named 'json_lines' 에러가 난다.
    따라서 그냥 파일을 읽고 라인 단위로 json.load를 해서 list에 결과를 append 하는 식으로 했다..

## pymongo (mongodb)
- ModuleNotFoundError: No module named 'pymongo' # pymongo 설치하기
  ```bash
  pip install pymongo
  ```
- mongodb find in python
  ```python
  import pymongo

  myclient = pymongo.MongoClient("mongodb://localhost:27017/")
  mydb = myclient["mydatabase"]
  mycol = mydb["customers"]

  x = mycol.find_one()

  print(x)
  ```
- mongodb find with for loop
  ```python
  _db = _client["_db_name"]
  _col = _db["_collection_name"]
  for doc in _col.find():
    print (doc)
  ```
  
## zmq
- bind -> connect로 바꿨을 때 생기는 오류
  ```
  File "zmq/backend/cython/socket.pyx", line 580, in zmq.backend.cython.socket.Socket.connect
  File "zmq/backend/cython/checkrc.pxd", line 25, in zmq.backend.cython.checkrc._check_rc
  zmq.error.ZMQError: Invalid argument
  ```
  - *를 못씀
