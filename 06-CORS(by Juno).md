# CORS (Cross-Origin Resource Sharing)

<br/>

<p align="center"><img src="https://blog.container-solutions.com/hubfs/CORS.jpg"/></p>

<br/>

## **1. 😅 첫 만남**

<br/>

&nbsp; 리액트를 사용한 프로젝트를 만들어보고자 하였고 코로나 관련 API를 사용하기로 하였다.

두곳의 API를 사용하기로 하였고 그중 국내 현황은 [굿바이코로나](https://api.corona-19.kr/) 에서 키를 발급받고 postman에 테스트를 해보았다.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHbCer%2FbtqURufOH9K%2FusjZX4CSZn68IYPmGoHAK1%2Fimg.png"/></p>

<br/>

&nbsp; api 데이터 테스트를 해보니 문제가 없이 나오는걸 확인하였다. 이후 react에서 데이터를 불러보았습니다.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbZ0pnc%2FbtqUYGZ4ruc%2FJP8iC8fSSnOYCeSfTxUsk0%2Fimg.png"/></p>

<br/>

<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">두근두근</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNi79A%2FbtqUSqqJ1qm%2F7oOiRPgKUh8vIXH80OlLTk%2Fimg.jpg"/></p>

<br/>

<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">두근두근</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcI5Jyw%2FbtqUYGsdCjD%2FlsAIDqmXc3pNxujXKIMeQK%2Fimg.jpg"/></p>

<p align="center">sigh..</p>

<br/>

&nbsp; 이러한 문제의 원인과 해결을 위해 웹생태계의 다른 출처로 리소스 요청을 제한하는 것과 관련된 두가지 정책인

**CORS**와 **SOP**에대해서 알아보도록 하겠습니다.

<br/>

## **2. 🙄 SOP(Same-Origin Policy) ?**

<br/>

&nbsp; 자바스크립트(`XMLHttpRequest`)로 다른 웹페이지에 접근할때 같은 출처의 페이지만 접근가능하다. 이때의 정책이 **동일 출처 정책(SOP)** 이다.

**SOP**는 어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는것을 제한하는 중요한 보안청잭이다.

여기서 동일 출처의 기준은 요청과 응답의 **프로토콜**, **호스트**, **포트** 세개가 모두 같다는것이다.

하지만 포트는 기본 포트번호가 정해져있기 때문에 생략이 가능합니다.

[참고문서](https://tools.ietf.org/html/rfc2616#section-3.2.2)

> 3.3.2 http URL
>
> …  
> If the port is empty or not given, port 80 is assumed. The semantics are that the identified resource is located at the server listening for TCP connections on that port of that host, and the Request-URI for the resource is abs_path (section 5.1.2).  
> …

<br/>

<p align="center"><img src="https://evan-moon.github.io/static/e25190005d12938c253cc72ca06777b1/6af66/uri-structure.png"/></p>

<br/>

- https://baegofda.kr - 기본 도메인
- https://baegofda.kr/bookmark - 프로토콜, 호스트, 포트가 동일하니 O
- http://baegofda.kr - 프로토콜이 다르니 X
- https://api.baegofda.kr - 호스트가 다름 X
- https://baegofda.kr:8080 - 포트까지 동일해야하나 **대부분**은 포트가 달라도 생략이 가능하여 같다고 인식힌다. (예외 : **<span style="color : red;">IE</span>**)

<br/>

<p align="center"><img src="https://evan-moon.github.io/static/a21288d9ab75a6714b1f5a752d171ce4/c08c5/ie_is_trash.jpg"/></p>

**<p align="center">이젠 안녕 ~!</p>**

<br/>

하지만 **SOP**를 우회에서 서로 다른 도메인간에 통신을 할수있게 해줄 무언가가 필요했고 때문에 만든 해결책이 JSONP, ReverseProxy, FlashSocket등이 있다.

<br/>

## **3. 🤔 CORS(Cross-OriginResource Sharing) ?**

<br/>

&nbsp; **CORS** 즉, **교차 출처 자원 공유**는 웹브라우저에서 외부 도메인 서버와 통신하기위한 방식을 표준화한 스펙이다.

서버와 클라이언트가 정해진 헤더를 통해 서로 요청이나 응답에 반응할지 말지 결정하는 방식이다.

<br/>

### **3-1. 👍 CORS의 등장 배경**

---

<br/>

&nbsp; 크로스도메인 이슈를 해결하는 표준의 필요성이 대두되며 W3C에서 권장사항으로 CORS사양을 발표하였다.

> 현재 화발하게 유지 관리되는 사양은 **WHATWG**의 **Fetch Living Standard**이다.
>
> [참고문서](https://fetch.spec.whatwg.org/)

<br/>

&nbsp; 또한 crsf, xss와 같은 해커들의 공격에 대응하기 위해서라도 등장이 필요한 시점이였다.

<br/>

### **3-2.🙏 CORS의 시나리오**

---

<br/>

&nbsp; 먼저 request에 **Origin** 이라는 헤더가있고 response에 **Access-Control-Allow-Origin** 이라는 헤더가있는데 이 두가지가 같을 경우 같은출처라고 인식한다는 것을 알고 갑시다.

<br/>

#### **3-2-1. Preflight Request**

<br/>

&nbsp; **프리플라이트(Preflight Request)** 가장 일반적으로 마주치는 시나리오이다.

JS에서 Fetch로 요청을하면 options을 통해 예비요청을 보내고 본요청을 보내며 헤더에 출처를 같이 보냅니다.

> access-control-request-method : GET  
> access-control-request-headers: content-type  
> origin

이후 서버는 response에 **Access-Control-Allow-Origin**으로 응답합니다.

<br/>

<p align="center"><img src="https://beomy.github.io/assets/img/posts/browser/cors_preflight_request.png"/></p>

<br/>

```js
const headers = new Headers({
  "Content-Type": "text/xml",
});
fetch("https://evanmoon.tistory.com/rss", { headers });
```

<br/>

```http
OPTIONS https://evanmoon.tistory.com/rss

Accept: */*
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9,ko;q=0.8,ja;q=0.7,la;q=0.6
Access-Control-Request-Headers: content-type
Access-Control-Request-Method: GET
Connection: keep-alive
Host: evanmoon.tistory.com
Origin: https://evan-moon.github.io
Referer: https://evan-moon.github.io/2020/05/21/about-cors/
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: cross-site
```

<br/>

&nbsp; 위와같이 요청을 보면 단순 **Origin**에 대한 정보 뿐만아니라 예비요청이후 본요청때 같이 보낼 정보가 포함되있음을 볼 수 있다.

이 예비요청에 **Access-Control-Request-Headers** 를 사용하여 자신이 본 요청에서 **Content-Type** 헤더를 사용할 것을 알려주거나,

**Access-Control-Request-Method**를 사용하여 이후 **GET** 메소드를 사용할 것을 서버에게 미리 알려주고 있는 것이다.

```http
OPTIONS https://evanmoon.tistory.com/rss 200 OK

Access-Control-Allow-Origin: https://evanmoon.tistory.com
Content-Encoding: gzip
Content-Length: 699
Content-Type: text/xml; charset=utf-8
Date: Sun, 24 May 2020 11:52:33 GMT
P3P: CP='ALL DSP COR MON LAW OUR LEG DEL'
Server: Apache
Vary: Accept-Encoding
X-UA-Compatible: IE=Edge
```

<br/>

&nbsp; 이 부분은 서버사이드 영역이 아닌 브라우저 영역에서 판단하기 때문에 서버는 200대의 성공코드를 반환하나

브라우저에서는 에러를 보여준다.

<br/>

#### **3-2-2. Simple Request**

<br/>

&nbsp; 이 시나리오는 예비요청이 없으며 본요청만 있고, 직접 볼수는 없다.

<br/>

<p align="center"><img src="https://evan-moon.github.io/static/d8ed6519e305c807c687032ff61240f8/6af66/simple-request.png"/></p>

<br/>

&nbsp; 여기에는 조건이 존재하는데

- 메소드는 get, head,post중 하나여야된다.

- accept, accept-language, content-language, content-type, DPR,Downlink,Save-Data, Viewport-Width, Width를 제외한 헤더를 사용하면안된다.  
  (이부분 때문에 인증관련의 jwt사용이 불가하다.)

- ontent-type를 사용하는 경우 application/x-www-form-urlencoded, multipart/form-data, text/plain만 허용된다.
  (현재는 Rest API를 사용하며 application/json을 사용하나 여기에는 해당하지 않기에 실질적으로 이부분은 보기 힘들다.)

<br/>

#### **3-2-3. Credentialed Request**

<br/>

&nbsp; **CORS**도 보안정책이나 여기서 보안을 더 강화 할 수 있다.

Fetch나 비동기는 기본적으로 쿠키를 담지 않기때문에 아래의 **credentials**옵션을 통하여 인증 보안을 강화한다.

- same-origin (기본값) : 같은 출처 간 요청에만 인증 정보를 담을 수 있다.

- include : 모든 요청에 인증 정보를 담을 수 있다.

- same-origin (기본값) : 모든 요청에 인증 정보를 담지 않는다.

<br/>

```js
fetch("https://evan-moon.github.io/feed.xml", {
  credentials: "include", // Credentials 옵션 변경!
});
```

<br/>

또한

- Access-Control-Allow-Origin에는 \*(와일드카드)를 사용할수없으며 명시적 url을 사용해야함

- 응답헤더에는 Access-Control-Allow-Credentials:가 존재해야한다.

<br/>

## **4. 🎉 결론**

<br/>

&nbsp; 서버사이드에서는 Access-Control-Allow-Origin이 내려올수있도록 세팅해줘야한다.

webpack dev server로 리버스 프록싱하여 우회가능하나 로컬에서만 가능하니 가장 좋은 방법은 서버개발자에게 요청한다.

[참고](https://evan-moon.github.io/2020/05/21/about-cors/)

[참고 : 우아테코톡](https://www.youtube.com/watch?v=7iGIfcEsc2g)

[추천 - 리액트 & nodejs(with CORS)](https://velog.io/@wlsdud2194/cors)
