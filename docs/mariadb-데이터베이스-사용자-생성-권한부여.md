> ```# mysql -p  (DBA 권한으로 접속)```   

1. webdb database 생성
MariaDB [none]> create database webdb;

2. linux 서버 local 접속 계정 webdb 생성
    1. user 생성   
   ``` MariaDB [none]> create user 'webdb'@'localhost' identified by 'webdb';```

    2. 권한 부여   
    ```MariaDB [none]> grant all privileges on webdb.* to 'webdb'@'localhost';```

    3. 새 변경사항 적용   
    ```MariaDB [none]> flush privileges;```

    4. 테스트   
    ```# mysql -u webdb -D webdb -p```

=====================================================================


3. 특정 IP(windows 192.168.80.31)의 접속 계정 webdb 생성 
    1. user 생성   
    ```MariaDB [none]> create user 'webdb'@'192.168.80.31' identified by 'webdb';```

    2. 권한 부여   
    ```MariaDB [none]> grant all privileges on webdb.* to 'webdb'@'192.168.80.31';```

    3. 새 변경사항 적용   
    ```MariaDB [none]> flush privileges;```

    4. Windows의 Workbench 에서 연결 테스트 
