# Express와 미들웨어

<br>

## Express란?

Express는 웹을 빠르고 편하게 개발할 수 있도록 도와주는 프레임워크입니다.

Express라는 뼈대에 여러 기능들을 붙여 하나의 완성품을 만들어낼 수 있습니다.

<br>

## Express의 특징

1.미들웨어

미들웨어는 서버가 클라이언트의 요청을 받고 응답을 하는 **중간 과정**에 거쳐가는 함수들입니다. (미들웨어에는 다양한 레벨이 있습니다)

![image](https://user-images.githubusercontent.com/48934537/103401521-7aa3ec80-4b8c-11eb-88f9-72cf3c492f90.png)

next()를 통해 다음 미들웨어로 현재의 요청을 넘길 수 있습니다. 즉, 미들웨어는 순차적으로 처리되며 순서가 중요합니다.

예를 들면, 인증된 요청만 받기 위해 인증미들웨어를 구현하거나 요청정보를 로깅하기 위해 로깅미들웨어를 구현할 수 있습니다.

다음은 로깅작업을 대신해주는 써드파티 미들웨어 **morgan**의 사용 코드입니다.

```javascript
const express = require('express')
const logger = require('morgan') //써드파티 미들웨어인 morgan을 사용합니다
const app = express()

//logger미들웨어를 설정합니다
app.use(logger)

//서버를 요청 대기 상태로 만들어줍니다
app.listen(4000, () => console.log('running'))
```

<br>

2.라우팅

라우팅은 클라이언트의 요청을 URL에 따라 적절한 핸들러 함수로 연결해주는 기능을 뜻하며 express는 이를 깔끔하게 관리할 수 있습니다.

다음은 라우팅을 설정하고 깔끔하게 분기시키는 작업입니다.

```javascript
var userRouter = require('./routes/user')
var boardRouter = require(./routes/board')

app.use('/user', userRouter) //user경로로 들어온 요청은 userRouter에서 처리합니다.
app.use('/board', boardRouter) //board경로로 들어온 요청은 boardRouter에서 처리합니다.
```

<br>

3.요청/응답 객체

요청/응답 객체를 통해 편리하게 클라이언트의 요청정보를 받고 다양한 형식으로 응답할 수 있습니다.

요청객체에서는 req.params, req.query, req.body등을 사용할 수 있습니다.

응답객체에서는 res.send(), res.status(), res.json()등을 사용할 수 있습니다.

다음은 요청으로부터 name파라미터를 받아 json형식으로 return해주는 코드입니다.

```javascript
app.get('/:name', (req, res) => {
  res.json({
    name : req.params.name
  })
})
```

<br>

## Express의 디렉토리 구조

node_modules : 프로젝트에서 사용할 모듈들이 담겨있는 디렉토리입니다.

public : js, css, image등 정적파일들을 저장해놓는 디렉토리입니다.

routes : 서버가 라우팅할 URL경로에 대한 로직들을 구현해놓는 디렉토리입니다.

app.js : 서버에 대한 설정을 담고있는 파일입니다.

package.json : 프로젝트가 어떤 모듈에 의존성을 갖고 있는지 명시해놓은 파일입니다. npm install을 통해 명시된 모듈들을 다운받을 수 있습니다.
