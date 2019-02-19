- 압축/압축 해제 정리
  - *.zip
    ```bash
    $ zip -r file_name.zip file_or_dir
    $ unzip file_name.zip
    ```

  - *.tar
    ```
    $ tar -cf file_name.tar file_or_dir
    $ tar -xf file_name.tar
    ```

  - *.tgz
    ```
    tar -cvzpf file_name.tgz target_dir 
    tar -xvf file_name.tgz 
    ```


  - *.tar.gz
    ```
    $ tar zcf file_name.tar.gz file_or_dir
    $ tar xfz file_name.tar.gz
    ```

  - *.tar.bz2
    ```
    $ tar -jcf file_name.tar.bz2 file_or_dir
    $ tar -xfj [file_name.tar.bz2]
    ```

  - *.tar.xz (두번의 압축 풀기 과정)
    ```bash
    $ xz -d file_name.tar.xz
    $ tar -xf file_name.tar
    ```
