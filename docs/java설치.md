## Java Centos에 설치

0. 작업계정 = root / 작업 디렉토리 = /root

1. Java JDK 다운로드
	* 다운로드 사이트에서 다운로드
	* jdk-11.0.15_linux-x64_bin.tar.gz 다운로드

2. 리눅스 서버에 sftp로 접속
	* jdk-11.0.15_linux-x64_bin.tar.gz를 C드라이브에 둔다
	* sftp root@192.168.10.41
	* put jdk-11.0.15_linux-x64_bin.tar.gz
	
3. 압축 풀기   
	*  ```[root@localhost ~]#tar xvfz jdk-11.0.15_linux-x64_bin.tar.gz```
 
4. 더존 설치 디렉토리 만들기
	*  ```[root@localhost ~]# mkdir /usr/local/douzone```

5. 설치 디렉토리로 파일 옮기기
	*  ```[root@localhost ~]# mv jdk-11.0.15 /usr/local/douzone/```   
	* 확인 ```[root@localhost ~]# ls -l /usr/local/douzone/```
	* 자바 버전 확인
		*  ```[root@localhost ~]# /usr/local/douzone/jdk-11.0.15/bin/java --version```

6. 링크 파일 생성
	* ```[root@localhost ~]# ln -s /usr/local/douzone/jdk-11.0.15  /usr/local/douzone/java```

7.	PATH 설정(/etc/profile)
	* ```shell
		# java
		export JAVA_HOME=/usr/local/douzone/java
		export CLASSPATH=$JAVA_HOME/lib/tools.jar
		export PATH=$PATH:$JAVA_HOME/bin 
		``` 


8.	현재 shell 환경에 적용하기
	* ```[root@localhost ~]# source /etc/profile```

9.	확인
	* ```shell  
		[root@localhost ~]#java --version
		java 11.0.15 2022-04-19 LTS
		Java(TM) SE Runtime Environment 18.9 (build 11.0.15+8-LTS-149)
		Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.15+8-LTS-149, mixed mode)
		#
	```