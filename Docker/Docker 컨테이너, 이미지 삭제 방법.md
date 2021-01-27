# Docker 컨테이너, 이미지 삭제 방법

1.  컨테이너 선택 삭제

   ```javascript
   docker rm [컨테이너 이름]
   ```

2.  컨테이너 전체 삭제

   ```javascript
   docker rm `docker ps -a -q`
   ```

3.  이미지 선택 삭제

   ```javascript
   docker rmi [이미지 이름]
   
   docker rmi -f [이미지 이름] //컨테이너까지 강제 삭제
   ```

4. 이미지 전체 삭제

  ```javascript
  docker rmi `docker images -q`
  ```
