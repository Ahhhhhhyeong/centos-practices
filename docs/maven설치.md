0. 작업 디렉토리
   /root

1. 다운로드
  ``` # wget https://dlcdn.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.tar.gz ```
   

2. 압축 풀기
   # tar cxfz apache-maven-3.8.5-bin.tar.gz
   
3. 설치
   # mv apache-maven-3.8.5 /usr/local/douzone/maven3.8
   # ln -s /usr/local/douzone/maven3.8 /usr/local/douzone/maven

4. 설정(/etc/profile)

# maven
export PATH=$PATH:/usr/local/douzone/maven/bin
 
