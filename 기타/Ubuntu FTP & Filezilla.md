# Ubuntu FTP활성화 및 Filezilla서버 설치

<br>

## 테스팅 환경

* Ubuntu 18.04

<br>

## vsftpd(Very Secure FTP) 설치 및 설정 변경

* sudo apt-get install vsftpd

* sudo vi /etc/vsftpd.conf

  * 주석처리되어 있는 부분을 해제
  
    ```
    # Uncomment this to enable any form of FTP write command.
    write-enable=YES <---
    ...
    ...
    # You may override where the log file goes if you like. The default is shown
    # below.
    xferlog file=/var/log/vsftpd.log <---
    ```
 
  * :wq 저장하고 종료
 
* sudo service vsftpd restart 
  
<br>

## Filezilla 서버 설치

* sudo apt-get install filezilla
