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
