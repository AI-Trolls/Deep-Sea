- csv 파일 열고, row 수 계산하고, dict로 변환 (column 수에 따라 수정 필요)

```python
import csv

file_path = 'something.csv'

with open(file_path) as csv_file:
    csv_reader = csv.reader(csv_file, delimiter='###')
    row_count = sum(1 for row in csv_reader)
    print(row_count)
    
    for idx, row in enumerate(csv_reader):
        print(row)
        csv_dict = {rows[0]:rows[1] for rows in csv_reader}
```
