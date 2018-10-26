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

## JSON
- JSONDecodeError:
  - json_str = json.loads(jsonString, strict=False)
  - If strict is false (True is the default), then control characters will be allowed inside strings. Control characters in this context are those with character codes in the 0–31 range, including '\t' (tab), '\n', '\r' and '\0'.

- UnicodeDecodeError: 'utf8' codec can't decode byte
  - str = unicode(str, errors='replace')
  - str = unicode(str, errors='ignore')

## mongodb
- mongodb find in python
  ```python
  import pymongo

  myclient = pymongo.MongoClient("mongodb://localhost:27017/")
  mydb = myclient["mydatabase"]
  mycol = mydb["customers"]

  x = mycol.find_one()

  print(x)
  '''
