- 현재 폴더 이하 파일 갯수 세기
  ```
  find . -type f | wc -l
  ```
  watch 명령어로 업데이트 하면서 보기
  ```
  watch -n 1 'find . -type f | wc -l'
  ```

- for loop
  ```bash
  N=40
  for i in $(seq 1 $N)
    do echo $i
  done
  ```

- while loop
  ```bash
  i=0
  N=40
  while true
    do i=$(expr $i + 1)
    echo $i
    if [[ "$i" -eq $N ]]
      then break
    fi
  done
  ```
