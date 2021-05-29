풀스택으로 웹 개발을 해본다면, 반드시 이 에러를 마주하게 될 것입니다.

<img width="500" alt="스크린샷 2021-05-30 오전 5 30 23" src="https://user-images.githubusercontent.com/53216594/120084143-efae2a80-c108-11eb-81a2-bf6bf673c0c2.png">
<img width="500" alt="스크린샷 2021-05-30 오전 5 30 51" src="https://user-images.githubusercontent.com/53216594/120084147-f177ee00-c108-11eb-9f9b-bc47319fec60.png">

위의 에러는 CORS Error로, 각각 http://localhost:3000, https://localhost:3001라는 origin에서 서버에다가   
어떠한 리소스를 요청했을 때 발생한 에러입니다. 대체 왜 이러한 에러가 발생한 것일까요?

<br>

우리가 접속하는 많은 웹 사이트에 자바스크립트 파일이 포함되어 있을 것입니다.   
그런데 만약 자바스크립트에서 다른 서버에 데이터를 무차별적으로 요청하고 받아올 수 있게 되면 어떻게 될까요?

특정 소셜 미디어에 로그인이 된 상태로, 다른 탭을 열어서 이상한 악성 사이트에 접속하게 되어 버렸다고 가정해 봅시다.   
이 경우 악성 사이트의 자바스크립트는 브라우저에 심어져 있는 쿠키의 정보를 요청하는 등의 방법을 통해 계정 정보에 접근 할 수 있고   
메세지나 포스팅 등의 정보도 통제할 수 있게 되어버립니다.   
만약 은행 정보라면 더욱 끔찍한 상황이겠죠?   

이러한 이유로 서로 다른 origin을 가진 클라이언트와 서버간의 리소스 교환을 통제함으로써 자바스크립트에서 함부로 데이터를   
요청할 수 없도록 할 필요가 있습니다.

<br>

## SOP(Same-Origin Policy) - 동일 출처 정책
SOP(Same-Origin Policy)은 어떤 origin에서 불러온 문서나 스크립트가 다른 origin에서 리소스를 불러오는 것을 제한하는 내용을 담고 있습니다.   
이러한 SOP 정책으로 인해서 CORS Error가 발생하게 되는 것입니다.   

그렇다면 앞의 CORS error를 다시 살펴보면 http://localhost:3000 라는 origin에서 이와 다른 origin을 가진 서버에 요청을 했기 때문에 발생한 것입니다.   
그 밑의 것 역시 마찬가지입니다. https://localhost:3001 라는 origin에서 이와 다른 origin을 가진 서버에 요청을 했기 때문에 발생한 것입니다.   

그런데 다른 origin으로부터 리소스를 요청해야하는 경우는 반드시 생기기 때문에 항상 SOP를 지키면서 데이터를 교환하는 것은 사실상 불가능합니다.   
풀스택으로 웹 개발을 하는 단계에서 바로 CORS error를 마주하게 될 것입니다.   
예를들어 프론트엔드에서 3000번 포트를 사용하고 있는데, 백엔드 서버를 만들면 3000번이 아닌 다른 포트를 이용해야하므로 이 둘의 origin은 달라져 버립니다.   

> origin이 다르다 = Protocol, host(domain), port 중에서 하나라도 다르면 origin이 다른 것이라고 합니다.

그래서 서로 다른 origin간에도 리소스 교환이 가능하도록 SOP의 예외 조항인 CORS 조항이 만들어집니다.   

> Generally, reading information from another origin is forbidden.
> However, an origin is permitted to use some kinds of resources retrieved from other origins.
> For example, an origin is permitted to execute script, render images, and apply style sheets from any origin.
> Likewise, an origin can display content from another origin, such as an HTML document in an HTML frame.
> Network resources can also opt into letting other origins read their information, for example, using Cross-Origin Resource Sharing.
> RFC 6454 - 3.4.2 Network Access

## CORS

Cors 는 Cross Origin Resource Sharing의 약자로서, http header를 통해 브라우저에게 다른 origin과도 리소스에 접근하고 교환할 수 있도록 해주는 체제입니다.   
서로 다른 origin을 가지고 있더라도 서버가 올바른 CORS header를 포함하고 있는 경우에 한정해서 다른 origin을 가진 리소스를 교환할 수 있게 됩니다.   

여기까지 따라왔다면 앞의 CORS error의 내용을 이해할 수 있게 됩니다.   
cors error의 내용을 보면 NO 'Access-Control-Allow-Origin' header is present on the requested resourse라는 문구가 있습니다.   
이것을 해석해보면 requested resourse, 즉 요청된 리소스(서버 측)에 'Access-Control-Allow-Origin'이라는 header가 표시되지 않았다고 하고 있습니다.   

앞서 서버가 올바른 CORS header를 포함하고 있는 경우에 한정해서 서로 다른 origin끼리 리소스를 교환할 수 있다고 했는데,   
"서버가 올바른 CORS header('Access-Control-Allow-Origin')를 표시하고 있지 않으니 CORS를 하려면 서버 측에 올바른 header를 표시해!"라는 의미입니다.   

CORS와 관련해서 마지막으로 짚고 넘어가고 싶은 점이 있는데, 바로 Cors Error가 마치 서버 측에서 보낸 에러같지만 사실 이것은 브라우저에서 발생한 에러라는 것입니다.   
자바스크립트에서 XMLHttpRequest 또는 Fetch를 통해 요청이 이루어졌다고 가정해봅시다.   
브라우저는 해당 http요청이 CORS 정책의 검증을 해야하는지 판단합니다. 만약 안전하지 않은 cross-origin request라고 판단한 경우, CORS검증을 하도록 서버에 요청을 하게 됩니다.   
(이 요청을 Preflight Request이라고 하는데 조금 뒤에 자세하게 나옵니다.)
브라우저는 서버에게서 받은 응답을 살피고 CORS검증에 실패했다면 CORS error를 발생시킵니다.   
즉 브라우저가 response object가 적절한 header를 가지고 있는지 살피고, 그렇지 않다면 Server로 부터의 응답을 block 하는 것입니다.

<br>

## CORS ERROR 해결 방법

#### 서버에서 Access-Control-Allow-Origin을 header로 넘겨주기

앞서 서버가 올바른 CORS header를 포함하고 있는 경우에 cors가 가능하다고 했으므로, 서버에서 해당 header를 넘겨주면 됩니다.   
어떤 환경에서 서버를 만들었느냐에 따라 조금씩 다르겠지만, Express를 사용해 서버를 만든 경우 어떻게 해결하는지 살펴보겠습니다.   
Node.js에서 Express를 이용해 서버를 만든 경우 cors library를 사용해서 header를 넘겨줄 수 있습니다.   

예를 들어 http://localhost:3000 에서 다른 origin의 서버로 요청하는 경우, 다음과 같이 쓸 수 있습니다.   

```javascript
//Server
const express = require('express');
const app = express();
const cors = require('cors');

app.use(cors({ origin: 'http://127.0.0.1:3000' }));

app.listen(5000);
```
이렇게 씀으로 인해서 서버에서 응답할 때 `http://127.0.0.1:3000`를 값으로 가진 `Access-Control-Allow-Origin` header를 전송하도록 지시하는 것입니다.   
만약 모든 url에 대해서 허용하고 싶으면 특정 url 대신에 * 를 넣어주면 됩니다.

<br>

#### CORS Preflight

만약 안전하지 않은 cross-origin request가 이루어지는 경우 브라우저는 서버에게 preflight request(사전 요청)이라는 것을 보냅니다.   
사전 요청은 말 그래도 본 요청을 보내기 전에 보내는 예비 요청입니다.   

> 안전한 cross-origin request
> method: GET, POST, HEAD
> Header: Accept, Accept-Language, Content-Language
> 값이 application/x-www-form-urlencoded나 multipart/form-data, text/plain인 Content-Type
> (출처: https://ko.javascript.info/fetch-crossorigin)

만약에 스크립트에 PUT요청이 있다고 가정해봅시다. 이때는 안전하지 않은 cross-origin request이므로 브라우저는 서버에 사전 요청을 보내게 됩니다.   
브라우저가 사전 요청을 보낼 때, header에 Access-Control-Request 및 Access-Control-Request 정보가 담깁니다.   

클라이언트가 PUT 메소드로 요청을 하고 싶고, Special-Request-Header라는 custom request header를 사용해서 서버에 요청을 하고 싶은 경우에 사전 요청은 다음과 같을 것입니다.

```javascript
Origin: https://....
Access-Control-Request-Method: PUT
Access-Control-Request-Headers: Special-Request-Header
......
```

그리고 서버는 사전 요청에 대해서 Access-Control-Allow-Methods, Access-Control-Allow-Headers를 담은 응답을 보내줄 것입니다.   

```javascript
Access-Control-Allow-Origin: https://...(client url)
Access-Control-Allow-Methods: GET, PUT, POST, DELETE
Access-Control-Allow-Headers: Special-Request-Header
Access-Control-Allow-Credentials: true
Access-Control-Max-Age: 240
......
```
이렇게 응답이 왔다면, 이것은 GET, PUT, POST, DELETE 메소드 그리고 request header가 Special-Request-Header인 경우 CORS를 허용하겠다는 것입니다.   
즉 브라우저는 사전 요청을 통해 CORS protocol이 cross-origin request를 허용하기 전, 어떠한 methods와 headers가 허용되어 있는지 확인을 하게 됩니다.   

만약 이떄 Access-Control-Allow-Methods에 PUT이 포함되어있지 않다면 CORS Error가 발생할 것이고, 이런 경우에는 서버에다가 PUT요청을 사용하는 것을 허락해주어야 합니다.

```javascript
//Server
const express = require('express');
const app = express();
const cors = require('cors');

app.use(cors({
  origin: 'http://127.0.0.1:3000',
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  allowedHeaders: ['Content-Type']
}));

app.listen(5000);
```
allowedHeaders를 설정하지 않으면 자동적으로 Access-Control-Request-Headers에 있는 값으로 설정될 것이기 떄문에, 보통 따로 설정해주지 않는다고 합니다.

<br>

#### Credentials

Credentials는 CORS와 쿠키에 관련된 내용을 담고 있습니다.   
기본적으로 CORS에서는 사용자가 요청하지 않는 한 쿠키를 요청과 함께 보내지 않습니다.   
쿠키를 보낼 수 있도록 하려면 먼저 요청을 할 때, 예를 들어 fetch를 하는 경우 fetch request에 credentials option을 포함시켜서 해당 쿠키가 안전하다는 것을 요청에 알려야합니다.

```javascript
fetch(url, { credentials: 'include' });
```

그리고 서버에서는 Access-Control-Allow-Credentials를 true로 해줌으로서 쿠키를 신임(?)하도록 합니다.   
이 역시 CORS library를 통해서 쉽게 할 수 있습니다.   

```javascript
//Server
const express = require('express');
const app = express();
const cors = require('cors');

app.use(cors({
  origin: 'http://127.0.0.1:3000',
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  allowedHeaders: ['Content-Type'],
  credentials: true
}));

app.listen(5000);
```

(reference: https://portswigger.net/web-security/cors/access-control-allow-origin   
https://blog.webdevsimplified.com/2021-05/cors/)
