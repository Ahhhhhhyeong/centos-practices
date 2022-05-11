0. 작업계정 = root / 작업 디렉토리 = /root

1. tomcat8.5, tomcat9 다운로드
	* ``[root@localhost ~]#wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.62/bin/apache-tomcat-9.0.62.tar.gz --no-check-certificate``

2. tomcat9 압축 풀기
	* ``[root@localhost ~]# tar xvfz apache-tomcat-9.0.62.tar.gz``

3. 설치 
	* ``[root@localhost ~]# tar xvfz apache-tomcat-8.5.65.tar.gz``
	* 더존 설치 디렉토리 만들기
		* ``[root@localhost ~]#mkdir /usr/local/douzone ``
	* ``[root@localhost ~]# ln -s /usr/local/douzone/tomcat8.5 /usr/local/douzone/tomcat-9.0`` -> 링크 만들기
	
4. 설정(/etc/profile, 생략)

5. 포트 확인
    * ``[root@localhost ~]# vi /usr/local/douzone/tomcat/conf/server.xml``
		- 8080 open 확인

6. 실행
   - ``[root@localhost ~]# /usr/local/douzone/tomcat/bin/catalina.sh start``
   - ``[root@localhost ~]# ps -ef | grep tomcat``
   - ``[root@localhost ~]# ps -ef | grep java``

7. 브라우저로 접근 하기
	- ``http://192.168.80.131:8080``
	- 참고) firewalld 실행 유무 확인 해 보기(iptable)
		- ```[root@localhost ~][root@localhost ~]# ps -ef | grep firewalld```
		- 만약 실행 시, ```[root@localhost ~][root@localhost ~]# systemctl stop firewalld```

8. 중지 시키기
	- ```[root@localhost ~]# /usr/local/douzone/tomcat/bin/catalina.sh stop```

9. 서비스 등록 하기
	* ```/usr/lib/systemd/system/tomcat.service``` -> 파일 생성
	* ```[root@localhost ~]# systemctl enable tomcat```

10. tomcat 서비스 실행/중지/재실행
  * ```[root@localhost ~]# systemctl start tomcat```
  * ```[root@localhost ~]# systemctl stop tomcat```
  * ```[root@localhost ~]# systemctl restart tomcat```

11. tomcat manager 설정
	
	```shell
	====================================================================
	1) tomcat-users.xml 설정
    	vi /usr/local/douzone/tomcat/conf/tomcat-users.xml
	====================================================================
	<tomcat-users>
	. . .
	. . . 
	<role rolename="manager"/>
	<role rolename="manager-gui" />
	<role rolename="manager-script" />
	<role rolename="manager-jmx" />
	<role rolename="manager-status" />
	<role rolename="admin"/>
	<user username="admin" password="manager" roles="admin,manager,manager-gui, manager-script, manager-jmx, manager-status"/>

	</tomcat-users>
	========================================================
	2) /usr/local/douzone/tomcat/webapps/manager/META-INF/context.xml
	========================================================
	주석 처리
	<Context>
	....
	</Context>

	새로 다음내용 추가
	<Context antiResourceLocking="false" privileged="true" docBase="${catalina.home}/webapps/manager">
	<Valve className="org.apache.catalina.valves.RemoteAddrValve"
			allow="^.*$" />
	</Context>

	======================================================== 
	```
12. tomcat 재시작   
   * ```[root@localhost ~]# systemctl stop tomcat```
   * ```[root@localhost ~]# ps -ef | grep tomcat```
   * ```[root@localhost ~]# systemctl start tomcat```

13. http://192.168.10.41/manager


---
> kill -9 pid : 프로세스 강제종료


### tomcat manager 용도
``` shell
[root@localhost webapps]# ls -la
합계 4
drwxr-x---.  7 root root   81  3월 31 23:34 .
drwxr-xr-x.  9 root root  220  5월 10 15:59 ..
drwxr-x---.  3 root root  223  5월 10 15:59 ROOT
drwxr-x---. 15 root root 4096  5월 10 15:59 docs
drwxr-x---.  7 root root   99  5월 10 15:59 examples
drwxr-x---.  6 root root   79  5월 10 15:59 host-manager
drwxr-x---.  6 root root  114  5월 10 15:59 manager

```
> tomcat 의 webapps 폴더 안의 디렉토리    
> manager 프로그램이 파일을 webapps 디렉토리 안으로 배포해줌    
> > 배포 관리 역할을 한다.    
**deployment**   
* 자동화 하는 어플리케이션 => Jenkins
* CI/CD
