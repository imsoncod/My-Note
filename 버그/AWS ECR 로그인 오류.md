# AWS ECR 로그인 오류

<br>

## 문제

  ![image](https://user-images.githubusercontent.com/48934537/105946549-cde55e00-60aa-11eb-8315-3889f29db9c2.png)

  Docker 이미지 푸시를 위해 위 사진에서 첫 번째 명령어를 실행하였습니다.

  ```javascript
  Error saving credentials: error storing credentials - err: exit status 1, 
  out: `Error spawning command line “dbus-launch --autolaunch=ec28bc26405efa4865362c9554dade0a 
  --binary-syntax --close-stderr”: Child process exited with code 1`
  ```

  그런데, 이런 에러가 발생하였습니다.

<br>

## 해결

  ```javascript
  sudo apt install gnupg2 pass
  ```

  ![image](https://user-images.githubusercontent.com/48934537/105946968-962ae600-60ab-11eb-9c05-0adb8cb8ef61.png)

  해결했습니다!
