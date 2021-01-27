# Docker란?

도커를 간단히 정의하면 '컨테이너 기반의 오픈소스 가상화 플랫폼' 입니다.

이미지와 컨테이너를 이해하면 도커를 조금 더 쉽게 이해할 수 있습니다.

<br>

## 이미지와 컨테이너

이미지는 컨테이너를 실행하기 위한 파일 및 설정값을 저장하고 있습니다. 

예를들어 Flask 이미지로 컨테이너를 실행하면 어디서든 Docker만 설치하여 쉽게 Flask 서버를 구동할 수 있습니다.

하나의 이미지로 여러개의 컨테이너를 생성할 수 있고 작동시킬 수 있습니다.

따라서 컨테이너를 독립적인 하나의 프로세스로 볼 수 있습니다.

![image](https://user-images.githubusercontent.com/48934537/105995623-97c8ce00-60ec-11eb-8f8c-373c02ac0850.png)

위 사진을 보면 도커의 특징을 한 눈에 알 수 있습니다.

<br>

## 이미지 만들고 컨테이너 실행하기

1. Dockerfile 작성

   Dockerfile을 Build하면 도커 이미지를 생성할 수 있습니다.

   아주 간단한 예시로 Dockerfile을 작성해 보겠습니다.

   ```dockerfile
   FROM python:3.7 #실행 환경을 정의합니다 ex)ubuntu:18.04
   
   #필요한 명령어를 실행합니다
   RUN apt-get update -y
   RUN pip3 install flask
   RUN pip3 install pandas
   
   COPY ./ ./ #현재 경로에 있는 모든 파일을 컨테이너 안으로 복사합니다
   
   EXPOSE 5000 #5000번 포트를 개방합니다
   
   CMD python index.py #index.py를 실행합니다
   ```
   
2. Dockerfile을 빌드하여 이미지를 생성합니다.

   ```python
   #도커 이미지를 생성합니다
   docker build --tag myimage:test .
   
   #생성한 이미지를 확인합니다.
   docker images
   ```

3. 이미지로 컨테이너를 생성하고 실행합니다.

   ```python
   #컨테이너를 생성합니다
   docker create --name mycontainer -p 5000:5000 myimage:test
   
   #컨테이너를 실행합니다
   docker start mycontainer
   
   #실행중인 컨테이너를 확인합니다
   docker ps
   
   #모든 컨테이너를 확인할수도 있습니다
   docker ps -a
   ```
