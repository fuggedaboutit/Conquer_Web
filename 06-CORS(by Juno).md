# CORS (Cross-Origin Resource Sharing)

<br/>

<p align="center"><img src="https://blog.container-solutions.com/hubfs/CORS.jpg"/></p>

<br/>

## **1. ๐ ์ฒซ ๋ง๋จ**

<br/>

&nbsp; ๋ฆฌ์กํธ๋ฅผ ์ฌ์ฉํ ํ๋ก์ ํธ๋ฅผ ๋ง๋ค์ด๋ณด๊ณ ์ ํ์๊ณ  ์ฝ๋ก๋ ๊ด๋ จ API๋ฅผ ์ฌ์ฉํ๊ธฐ๋ก ํ์๋ค.

๋๊ณณ์ API๋ฅผ ์ฌ์ฉํ๊ธฐ๋ก ํ์๊ณ  ๊ทธ์ค ๊ตญ๋ด ํํฉ์ [๊ตฟ๋ฐ์ด์ฝ๋ก๋](https://api.corona-19.kr/) ์์ ํค๋ฅผ ๋ฐ๊ธ๋ฐ๊ณ  postman์ ํ์คํธ๋ฅผ ํด๋ณด์๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FHbCer%2FbtqURufOH9K%2FusjZX4CSZn68IYPmGoHAK1%2Fimg.png"/></p>

<br/>

&nbsp; api ๋ฐ์ดํฐ ํ์คํธ๋ฅผ ํด๋ณด๋ ๋ฌธ์ ๊ฐ ์์ด ๋์ค๋๊ฑธ ํ์ธํ์๋ค. ์ดํ react์์ ๋ฐ์ดํฐ๋ฅผ ๋ถ๋ฌ๋ณด์์ต๋๋ค.

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbZ0pnc%2FbtqUYGZ4ruc%2FJP8iC8fSSnOYCeSfTxUsk0%2Fimg.png"/></p>

<br/>

<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">๋๊ทผ๋๊ทผ</p>
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
<p align="center">๋๊ทผ๋๊ทผ</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>
<p align="center">.</p>

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcI5Jyw%2FbtqUYGsdCjD%2FlsAIDqmXc3pNxujXKIMeQK%2Fimg.jpg"/></p>

<p align="center">sigh..</p>

<br/>

&nbsp; ์ด๋ฌํ ๋ฌธ์ ์ ์์ธ๊ณผ ํด๊ฒฐ์ ์ํด ์น์ํ๊ณ์ ๋ค๋ฅธ ์ถ์ฒ๋ก ๋ฆฌ์์ค ์์ฒญ์ ์ ํํ๋ ๊ฒ๊ณผ ๊ด๋ จ๋ ๋๊ฐ์ง ์ ์ฑ์ธ

**CORS**์ **SOP**์๋ํด์ ์์๋ณด๋๋ก ํ๊ฒ ์ต๋๋ค.

<br/>

## **2. ๐ SOP(Same-Origin Policy) ?**

<br/>

&nbsp; ์๋ฐ์คํฌ๋ฆฝํธ(`XMLHttpRequest`)๋ก ๋ค๋ฅธ ์นํ์ด์ง์ ์ ๊ทผํ ๋ ๊ฐ์ ์ถ์ฒ์ ํ์ด์ง๋ง ์ ๊ทผ๊ฐ๋ฅํ๋ค. ์ด๋์ ์ ์ฑ์ด **๋์ผ ์ถ์ฒ ์ ์ฑ(SOP)** ์ด๋ค.

**SOP**๋ ์ด๋ค ์ถ์ฒ์์ ๋ถ๋ฌ์จ ๋ฌธ์๋ ์คํฌ๋ฆฝํธ๊ฐ ๋ค๋ฅธ ์ถ์ฒ์์ ๊ฐ์ ธ์จ ๋ฆฌ์์ค์ ์ํธ์์ฉํ๋๊ฒ์ ์ ํํ๋ ์ค์ํ ๋ณด์์ ์ฑ์ด๋ค.

์ฌ๊ธฐ์ ๋์ผ ์ถ์ฒ์ ๊ธฐ์ค์ ์์ฒญ๊ณผ ์๋ต์ **ํ๋กํ ์ฝ**, **ํธ์คํธ**, **ํฌํธ** ์ธ๊ฐ๊ฐ ๋ชจ๋ ๊ฐ๋ค๋๊ฒ์ด๋ค.

ํ์ง๋ง ํฌํธ๋ ๊ธฐ๋ณธ ํฌํธ๋ฒํธ๊ฐ ์ ํด์ ธ์๊ธฐ ๋๋ฌธ์ ์๋ต์ด ๊ฐ๋ฅํฉ๋๋ค.

[์ฐธ๊ณ ๋ฌธ์](https://tools.ietf.org/html/rfc2616#section-3.2.2)

> 3.3.2 http URL
>
> โฆ  
> If the port is empty or not given, port 80 is assumed. The semantics are that the identified resource is located at the server listening for TCP connections on that port of that host, and the Request-URI for the resource is abs_path (section 5.1.2).  
> โฆ

<br/>

<p align="center"><img src="https://evan-moon.github.io/static/e25190005d12938c253cc72ca06777b1/6af66/uri-structure.png"/></p>

<br/>

- https://baegofda.kr - ๊ธฐ๋ณธ ๋๋ฉ์ธ
- https://baegofda.kr/bookmark - ํ๋กํ ์ฝ, ํธ์คํธ, ํฌํธ๊ฐ ๋์ผํ๋ O
- http://baegofda.kr - ํ๋กํ ์ฝ์ด ๋ค๋ฅด๋ X
- https://api.baegofda.kr - ํธ์คํธ๊ฐ ๋ค๋ฆ X
- https://baegofda.kr:8080 - ํฌํธ๊น์ง ๋์ผํด์ผํ๋ **๋๋ถ๋ถ**์ ํฌํธ๊ฐ ๋ฌ๋ผ๋ ์๋ต์ด ๊ฐ๋ฅํ์ฌ ๊ฐ๋ค๊ณ  ์ธ์ํ๋ค. (์์ธ : **<span style="color : red;">IE</span>**)

<br/>

<p align="center"><img src="https://evan-moon.github.io/static/a21288d9ab75a6714b1f5a752d171ce4/c08c5/ie_is_trash.jpg"/></p>

**<p align="center">์ด์   ์๋ ~!</p>**

<br/>

ํ์ง๋ง **SOP**๋ฅผ ์ฐํ์์ ์๋ก ๋ค๋ฅธ ๋๋ฉ์ธ๊ฐ์ ํต์ ์ ํ ์์๊ฒ ํด์ค ๋ฌด์ธ๊ฐ๊ฐ ํ์ํ๊ณ  ๋๋ฌธ์ ๋ง๋  ํด๊ฒฐ์ฑ์ด JSONP, ReverseProxy, FlashSocket๋ฑ์ด ์๋ค.

<br/>

## **3. ๐ค CORS(Cross-OriginResource Sharing) ?**

<br/>

&nbsp; **CORS** ์ฆ, **๊ต์ฐจ ์ถ์ฒ ์์ ๊ณต์ **๋ ์น๋ธ๋ผ์ฐ์ ์์ ์ธ๋ถ ๋๋ฉ์ธ ์๋ฒ์ ํต์ ํ๊ธฐ์ํ ๋ฐฉ์์ ํ์คํํ ์คํ์ด๋ค.

์๋ฒ์ ํด๋ผ์ด์ธํธ๊ฐ ์ ํด์ง ํค๋๋ฅผ ํตํด ์๋ก ์์ฒญ์ด๋ ์๋ต์ ๋ฐ์ํ ์ง ๋ง์ง ๊ฒฐ์ ํ๋ ๋ฐฉ์์ด๋ค.

<br/>

### **3-1. ๐ CORS์ ๋ฑ์ฅ ๋ฐฐ๊ฒฝ**

---

<br/>

&nbsp; ํฌ๋ก์ค๋๋ฉ์ธ ์ด์๋ฅผ ํด๊ฒฐํ๋ ํ์ค์ ํ์์ฑ์ด ๋๋๋๋ฉฐ W3C์์ ๊ถ์ฅ์ฌํญ์ผ๋ก CORS์ฌ์์ ๋ฐํํ์๋ค.

> ํ์ฌ ํ๋ฐํ๊ฒ ์ ์ง ๊ด๋ฆฌ๋๋ ์ฌ์์ **WHATWG**์ **Fetch Living Standard**์ด๋ค.
>
> [์ฐธ๊ณ ๋ฌธ์](https://fetch.spec.whatwg.org/)

<br/>

&nbsp; ๋ํ crsf, xss์ ๊ฐ์ ํด์ปค๋ค์ ๊ณต๊ฒฉ์ ๋์ํ๊ธฐ ์ํด์๋ผ๋ ๋ฑ์ฅ์ด ํ์ํ ์์ ์ด์๋ค.

<br/>

### **3-2. ๐ CORS์ ์๋๋ฆฌ์ค**

---

<br/>

&nbsp; ๋จผ์  request์ **Origin** ์ด๋ผ๋ ํค๋๊ฐ์๊ณ  response์ **Access-Control-Allow-Origin** ์ด๋ผ๋ ํค๋๊ฐ์๋๋ฐ ์ด ๋๊ฐ์ง๊ฐ ๊ฐ์ ๊ฒฝ์ฐ ๊ฐ์์ถ์ฒ๋ผ๊ณ  ์ธ์ํ๋ค๋ ๊ฒ์ ์๊ณ  ๊ฐ์๋ค.

<br/>

#### **3-2-1. Preflight Request**

<br/>

&nbsp; **ํ๋ฆฌํ๋ผ์ดํธ(Preflight Request)** ๊ฐ์ฅ ์ผ๋ฐ์ ์ผ๋ก ๋ง์ฃผ์น๋ ์๋๋ฆฌ์ค์ด๋ค.

JS์์ Fetch๋ก ์์ฒญ์ํ๋ฉด options์ ํตํด ์๋น์์ฒญ์ ๋ณด๋ด๊ณ  ๋ณธ์์ฒญ์ ๋ณด๋ด๋ฉฐ ํค๋์ ์ถ์ฒ๋ฅผ ๊ฐ์ด ๋ณด๋๋๋ค.

> access-control-request-method : GET  
> access-control-request-headers: content-type  
> origin

์ดํ ์๋ฒ๋ response์ **Access-Control-Allow-Origin**์ผ๋ก ์๋ตํฉ๋๋ค.

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

&nbsp; ์์๊ฐ์ด ์์ฒญ์ ๋ณด๋ฉด ๋จ์ **Origin**์ ๋ํ ์ ๋ณด ๋ฟ๋ง์๋๋ผ ์๋น์์ฒญ์ดํ ๋ณธ์์ฒญ๋ ๊ฐ์ด ๋ณด๋ผ ์ ๋ณด๊ฐ ํฌํจ๋์์์ ๋ณผ ์ ์๋ค.

์ด ์๋น์์ฒญ์ **Access-Control-Request-Headers** ๋ฅผ ์ฌ์ฉํ์ฌ ์์ ์ด ๋ณธ ์์ฒญ์์ **Content-Type** ํค๋๋ฅผ ์ฌ์ฉํ  ๊ฒ์ ์๋ ค์ฃผ๊ฑฐ๋,

**Access-Control-Request-Method**๋ฅผ ์ฌ์ฉํ์ฌ ์ดํ **GET** ๋ฉ์๋๋ฅผ ์ฌ์ฉํ  ๊ฒ์ ์๋ฒ์๊ฒ ๋ฏธ๋ฆฌ ์๋ ค์ฃผ๊ณ  ์๋ ๊ฒ์ด๋ค.

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

&nbsp; ์ด ๋ถ๋ถ์ ์๋ฒ์ฌ์ด๋ ์์ญ์ด ์๋ ๋ธ๋ผ์ฐ์  ์์ญ์์ ํ๋จํ๊ธฐ ๋๋ฌธ์ ์๋ฒ๋ 200๋์ ์ฑ๊ณต์ฝ๋๋ฅผ ๋ฐํํ๋

๋ธ๋ผ์ฐ์ ์์๋ ์๋ฌ๋ฅผ ๋ณด์ฌ์ค๋ค.

<br/>

#### **3-2-2. Simple Request**

<br/>

&nbsp; ์ด ์๋๋ฆฌ์ค๋ ์๋น์์ฒญ์ด ์์ผ๋ฉฐ ๋ณธ์์ฒญ๋ง ์๊ณ , ์ง์  ๋ณผ์๋ ์๋ค.

<br/>

<p align="center"><img src="https://evan-moon.github.io/static/d8ed6519e305c807c687032ff61240f8/6af66/simple-request.png"/></p>

<br/>

&nbsp; ์ฌ๊ธฐ์๋ ์กฐ๊ฑด์ด ์กด์ฌํ๋๋ฐ

- ๋ฉ์๋๋ get, head,post์ค ํ๋์ฌ์ผ๋๋ค.

- accept, accept-language, content-language, content-type, DPR,Downlink,Save-Data, Viewport-Width, Width๋ฅผ ์ ์ธํ ํค๋๋ฅผ ์ฌ์ฉํ๋ฉด์๋๋ค.  
  (์ด๋ถ๋ถ ๋๋ฌธ์ ์ธ์ฆ๊ด๋ จ์ jwt์ฌ์ฉ์ด ๋ถ๊ฐํ๋ค.)

- content-type๋ฅผ ์ฌ์ฉํ๋ ๊ฒฝ์ฐ application/x-www-form-urlencoded, multipart/form-data, text/plain๋ง ํ์ฉ๋๋ค.
  (ํ์ฌ๋ Rest API๋ฅผ ์ฌ์ฉํ๋ฉฐ application/json์ ์ฌ์ฉํ๋ ์ฌ๊ธฐ์๋ ํด๋นํ์ง ์๊ธฐ์ ์ค์ง์ ์ผ๋ก ์ด๋ถ๋ถ์ ๋ณด๊ธฐ ํ๋ค๋ค.)

<br/>

#### **3-2-3. Credentialed Request**

<br/>

&nbsp; **CORS**๋ ๋ณด์์ ์ฑ์ด๋ ์ฌ๊ธฐ์ ๋ณด์์ ๋ ๊ฐํ ํ  ์ ์๋ค.

Fetch๋ ๋น๋๊ธฐ๋ ๊ธฐ๋ณธ์ ์ผ๋ก ์ฟ ํค๋ฅผ ๋ด์ง ์๊ธฐ๋๋ฌธ์ ์๋์ **credentials**์ต์์ ํตํ์ฌ ์ธ์ฆ ๋ณด์์ ๊ฐํํ๋ค.

- same-origin (๊ธฐ๋ณธ๊ฐ) : ๊ฐ์ ์ถ์ฒ ๊ฐ ์์ฒญ์๋ง ์ธ์ฆ ์ ๋ณด๋ฅผ ๋ด์ ์ ์๋ค.

- include : ๋ชจ๋  ์์ฒญ์ ์ธ์ฆ ์ ๋ณด๋ฅผ ๋ด์ ์ ์๋ค.

- omit : ๋ชจ๋  ์์ฒญ์ ์ธ์ฆ ์ ๋ณด๋ฅผ ๋ด์ง ์๋๋ค.

<br/>

```js
fetch("https://evan-moon.github.io/feed.xml", {
  credentials: "include", // Credentials ์ต์ ๋ณ๊ฒฝ!
});
```

<br/>

๋ํ

- Access-Control-Allow-Origin์๋ \*(์์ผ๋์นด๋)๋ฅผ ์ฌ์ฉํ ์์์ผ๋ฉฐ ๋ช์์  url์ ์ฌ์ฉํด์ผํจ

- ์๋ตํค๋์๋ Access-Control-Allow-Credentials:๊ฐ ์กด์ฌํด์ผํ๋ค.

<br/>

## **4. ๐ ๊ฒฐ๋ก **

<br/>

&nbsp; ์๋ฒ์ฌ์ด๋์์๋ Access-Control-Allow-Origin์ด ๋ด๋ ค์ฌ์์๋๋ก ์ธํํด์ค์ผํ๋ค.

webpack dev server๋ก ๋ฆฌ๋ฒ์ค ํ๋ก์ฑํ์ฌ ์ฐํ๊ฐ๋ฅํ๋ ๋ก์ปฌ์์๋ง ๊ฐ๋ฅํ๋ ๊ฐ์ฅ ์ข์ ๋ฐฉ๋ฒ์ ์๋ฒ๊ฐ๋ฐ์์๊ฒ ์์ฒญํ๋ค.

[์ฐธ๊ณ ](https://evan-moon.github.io/2020/05/21/about-cors/)

[์ฐธ๊ณ  : ์ฐ์ํ์ฝํก](https://www.youtube.com/watch?v=7iGIfcEsc2g)

[์ถ์ฒ - ๋ฆฌ์กํธ & nodejs(with CORS)](https://velog.io/@wlsdud2194/cors)
