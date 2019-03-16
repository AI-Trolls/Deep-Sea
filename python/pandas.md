

## solved errors in pandas programming

- AttributeError: module 'pandas' has no attribute 'plotting'
  - someone said "because of PyQt4". But it was not for me.
  - or just upgrade
    ```python
    pip install --upgrade pandas
    ```
    - then, met new error, ImportError: cannot import name 'ensure_object' from 'pandas.core.dtypes.common' (C:\Anaconda3\lib\site-packages\pandas\core\dtypes\common.py)
      ```python
      pip install -U pandas_datareader
      ```
    - I regret using jupyter lab based on conda in windows
