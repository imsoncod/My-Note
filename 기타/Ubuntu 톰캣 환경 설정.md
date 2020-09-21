# Ubuntu 톰캣 환경 설정

<br>

## 테스팅 환경

* Ubuntu 18.04

<br>

## JRE, JDK 설치

* sudo apt-get install openjdk-8-jre

* sudo apt-get install openjdk-8-jdk
  
<br>

## JAVA 환경변수 설정

* sudo nano /etc/profile

  * Ctrl + O
  
  * Enter
  
  * 맨 아래에 입력
  
    ```
    export JAVA_HOME=/usr/lib/jvm/java-9-openjdk-amd64
    export PATH=$JAVA_HOME/bin/:$PATH
    export CLASS_PATH=$JAVA_HOME/lib:$CLASS_PATH
    ```

  * Ctrl + X
  
* source /etc/profile

* sudo reboot now

* echo $JAVA_HOME

* $JAVA_HOME/bin/javac -version

<br>

## 톰캣 설치 및 포트설정

* sudo apt-get install tomcat8

* sudo /usr/share/tomcat8/bin/version.sh

* sudo ufw allow 8080/tcp

* sudo service tomcat8 start / stop

<br>

## 톰캣 webapps 접근 권한 설정

* sudo su (관리자 권한 흭득)

* chmod -R 777 /var/lib/tomcat8/webapps/

* chown -R tomcat8:tomcat8 /var/lib/tomcat8/webapps/

* service tomcat8 stop

* service tomcat8 start
