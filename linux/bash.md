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
