- 문자열 리스트 (string list) 내에 존재하는 것인지, 중복 검사
    ```js
    let findDuplicates = (arr) => arr.filter((item, index) => arr.indexOf(item) != index)
    isExist = findDuplicates(_item)
    ```
    
    ```js
    isExist = this._arr.includes(_item)
    ```
