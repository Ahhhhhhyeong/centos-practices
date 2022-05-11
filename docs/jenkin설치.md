1. jenkins 설치
    * ```# wget https://get.jenkins.io/war-stable/2.332.3/jenkins.war --no-check-certificate ```

2. 이동
    * ```mv jenkins.war /usr/local/douzone/tomcat/webapps/```

3. font 에러 해결
    1. ```cd /usr/local/douzone/java/lib```
    2. ```vi fontconfig.properties```
    3. ```
        # 추가하기
        version=1
        sequence.allfonts=default
        ``` 

4. tomcat 종료 후 시작!