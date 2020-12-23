# Node.js

<br>

## Node.js 란?

Node.js는 브라우저 밖에서 실행할 수 있는 Javascript 실행환경입니다.

과거 Javascript는 브라우저에서만 사용(버튼 Event, 사용자 입력 등) 되었지만 현재는 다양한 개발 분야에서 사용되고 있습니다.

<br>

## Node.js의 특징

1.크롬에서 사용되는 V8 엔진을 사용합니다.

2.단일 쓰레드 이벤트 루프 기반이며 I/O를 비동기식 처리합니다.

3.방대한 모듈 시스템을 갖추고 있습니다. (기본 / 써드파티 / 사용자 정의)

<br>

## Node.js의 Event Processing Model

![image](https://user-images.githubusercontent.com/48934537/103023340-1c29ad80-4591-11eb-9f5e-df517af17007.png)

이벤트는 Event Queue에 담겨 순서대로 처리됩니다. 매 이벤트를 처리하며 순환되는 Event Loop는 싱글 쓰레드이며 한 번에 하나의 이벤트만 처리할 수 있습니다. 하지만 파일, 네트워크 등의 I/O요청이 있는경우 작업의 정도가 무겁기 때문에 무작정 끝나기만을 기다릴수는 없습니다. 여기서 **비동기**개념이 적용됩니다. 

Event Loop는 I/O요청을 멀티쓰레드인 Worker에게 던집니다. 그리고 다른 작업을 수행합니다. Worker는 작업이 끝나면 Callback함수를 호출하여 Event Loop에게 작업이 끝났음을 알립니다.

<br>

## 동기(Blocking) vs 비동기(Non-Blocking)

**동기식** I/O에서는 디스크에 파일쓰기 요청이 들어오면 작업을 하는동안 cpu는 휴식?을 취하고 작업이 끝나면 다음 작업을 수행합니다. 하지만 **비동기식** I/O에서는 Worker에게 작업을 넘기고 cpu가 쉬지 않고 바로 다음 작업을 수행합니다. **즉, CPU의 효율면에서 많은 차이가 발생하게 됩니다.**

<br>

## 간단한 비동기 이해 - readFileSync()와 readFile()

readFileSync() : 동기식

```javascript
//Test.txt
//Hello World

const fs = require("fs");

const file = fs.readFileSync("Test.txt", "UTF-8");
console.log("Data : " + file);

//결과 - Text.txt파일의 데이터를 읽는 작업을 끝낸 후 출력작업을 수행합니다.(동기식)
//Data : Hello World
```

readFile() : 비동기식

```javascript
//Test.txt
//Hello World

const fs = require("fs");

const callback = (err, file) => {
    console.log("Data : " + file);
}
fs.readFile("Test.txt", "UTF-8", callback);

console.log("I/O작업중입니다.");

//결과 - Text.txt파일의 데이터를 읽는 작업을 Worker에게 던지고 하단의 출력 작업을 수행합니다.(비동기식)
//I/O작업중입니다. <- 하단의 출력 작업이 먼저 수행되었습니다.
//Data : Hello World <- I/O작업이 끝나고 callback 함수가 실행된 것입니다.
```

동기식 코드에서 함수(readFileSync -> readFile)만 바꾸어 비동기식으로 구현하고 console.log(file)로 출력해보면 undefined가 뜨게됩니다. 이는 I/O작업이 진행중인데 file을 출력하려고 시도했기 때문입니다.
