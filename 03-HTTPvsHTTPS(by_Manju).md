# HTTP vs HTTPS

## 🤔 What is HTTP?

<br>

- **`Hypertext Transfer Protocol`** 의 약자로 **server측에서 client 브라우저로 웹페이지를 처리, 렌더링 및 전달** 하는데 사용되는 프로토콜, 즉 통신 규약을 의미합니다!. 따라서 HTTP는 웹이 표시되는 수단이라고도 할 수 있습니다.

  => 통신 규약이므로 client가 server에 요청하거나 server가 응답을 줄때 지켜야하는 규칙이라고 생각하면 됨(대화의 규칙!)

  > 👀 Hypertext : 참조(하이퍼링크)를 통해 독자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  >
  > 👀 www. = world wide web

<br>

- `브라우저는 client가 보는 화면`입니다. 이 브라우저에서 client, 즉 사용자가 웹사이트에서 상호작용을 수행하려고 할 때, (검색, 저장, 작성 등 뭐든 하려고 할 때) 생기는 게 바로 요청, **`request`** 입니다. 이러한 요청이 있어야 응답, **`response`** 도 생길 수 있습니다!

  ex) 검색창에 뭔가를 검색했을 때, 요청에 대한 응답이 SERP(search engine results page)에 나오는 것

<br>

- 요청과 응답 모두 data 이므로 통신 규약인 HTTP는 **`data가 네트워크를 통해 전송되는 방법`** 이라고도 할 수 있습니다!

<br>

- 점점 더 네트워크상으로 처리되는 일이 많아지면서 개인 정보나 결제 정보 같은 보안이 필요한 data를 주고 받는 경우가 더 많아지고 있습니다 => HTTP의 치명적인 문제가 바로 ❗❗ **HTTP를 통한 data 송수신은 제3자도 너무 쉽게 볼 수 있을 만큼 노출이 되어 있습니다** ❗❗

<br>

## 🤔 What is HTTPS?

<br>

- HTTPS는 `Hyper Text Transfer Protocol` Secure의 약자로 간단하게 HTTP에 **보안이 추가** 되었다고 이해 할 수 있습니다!

  ![HTTPS_example](https://user-images.githubusercontent.com/75834421/119218538-c6dfd100-bb1b-11eb-8f73-c3e50e5f23cf.png)

<br>

- HTTPS는 타사의 **보안인증서** 를 사용하여 연결을 보호하고 사이트가 합법적인지 확인합니다. 이 인증서를 **`SSL 인증서`**(또는 "cert")라고 합니다

  ![http_vs_https](https://user-images.githubusercontent.com/75834421/119217409-fa6b2d00-bb14-11eb-9f87-89b1ec424315.png)

<br>

## 😮 What is SSL or TLS?

<br>

- SSL이란 `Secure Socket layer`로 browser와 server사이의 교류를 암호화 함으로써 data의 노출을 막아줍니다

  > 넷스케이프 커뮤니케이션스사가 개발했고 현재 표준 정식 명칭은 **TLS**라고 합니다!

<br>

- TLS는 `Transport Layer Security`의 약자로 `전송 계층 보안`을 뜻하며 HTTPS로 주고 받는 data를 **암호화**하고 전자 메일 및 기타 **프로토콜을 보호** 하는 데 사용할 수 있습니다.

  > TLS는 다양한 종류의 보안 통신을 위한 프로토콜이고 HTTPS는 TLS위에 HTTP를 얹어서 보안된 HTTP 통신을 하는 프로토콜입니다. 즉, **다양한 역할을 하는 프로토콜이 있는데 그것들의 보안(security)에 관여하는 프로토콜이 TLS!**

<br>

- SSL을 기반한 기술로 데이터가 전송된 이후 변조되지 않고 통신이 실제 발신자와 잘 이루어 지도록 합니다. 여기서 SSL인증서로 서버가 신뢰할 수 있는지 판단하기 위해 공개키 서명 방식을 사용하는 이를 **`SSL/TLS Handshake`** 라고 합니다!!

  ![handshaking](https://user-images.githubusercontent.com/75834421/119219552-212f6080-bb21-11eb-967d-532570012884.png)

<br>

### 😮 정확히 어떤 방식으로 암호화되는 걸까?

<br>

![암호화방식](https://user-images.githubusercontent.com/75834421/119218384-f3471d80-bb1a-11eb-9314-dbf7ee472cc2.png)

<br>

### 😮 HTTPS의 또다른 장점!!

<br>

- **HTTPS로 전환하게 되면 `검색엔진 최적화(SEO)`에 있어서도 큰 혜택을 볼 수 있습니다!**
  => 지난 2014년 구글에서는 HTTP를 HTTPS로 바꾸라고 권고했고, HTTPS로의 전환을 장려하기 위해서 HTTPS를 사용하는 웹사이트에 대해서 검색 순위 결과에 약간의 가산점을 주겠다고 발표했습니다!

<br>

- SEO는 `Search Engine Optimization`의 약자로 `검색엔진최적화`를 뜻합니다. 다시말해, 검색자 (검색 유저)의 의도를 이해하고 이에 충실히 맞춰 웹 페이지의 콘텐츠를 제작하고, 이 페이지가 검색 결과 페이지에서 잘 노출 되도록 웹페이지의 태그와 링크 구조를 개선하여 자연 유입 트래픽을 늘리는 시책”이라고 할 수 있습니다.

<br>

- **`가속화된 모바일 페이지(AMP, Accelerated Mobile Pages)`를 만들고 싶을 때도 HTTPS 프로토콜을 사용**해야 합니다! 여기서 `AMP`란 모바일 기기에서 페이지를 볼 때 불필요한 HTML요소는 빼고 딱 필요한 결과만 잘 보이게끔 콘텐츠를 로딩하는 방법입니다!

  > 이것도 구글이 만든거라고 합니다😂😂

<br>

### 😮 그러면 http 에서 https로 전환하는 방법은??

<br>

👀 http에서 https로 전환할 때 `고려해야할 점`들이 있습니다.

<br>

1. **Inform Google About the Transition, and Mistakes to Avoid**
   => 사이트가 http에서 https로 전환된걸 구글에 알려주기!

2. **Choose the Right Security Certificate: SSL and Wildcard Certificates** => 다양한 SSL 인증서 중 적절한 것 잘 고르기!

3. **Make Sure All URLs Are Properly Updated Sitewide** => html파일 tag안에서 사용하는 모든 url들도 잘 보고 https에 맞게 변경하기!(relative Url 사용!)

4. **Don't Prevent Google From Crawling Your New HTTPS Site** => 구글이 크롤링 하는 걸 막지 않도록 해야 합니다! + 검색엔진이 우리의 웹사이트에 있는 페이지들을 인덱싱하는 것을 허용해야 합니다!!

<br>

[참고]

- HTTP vs HTTPS

  : <http://blog.wishket.com/http-vs-https-%EC%B0%A8%EC%9D%B4-%EC%95%8C%EB%A9%B4-%EC%82%AC%EC%9D%B4%ED%8A%B8%EC%9D%98-%EB%A0%88%EB%B2%A8%EC%9D%B4-%EB%B3%B4%EC%9D%B8%EB%8B%A4/>

  : <https://www.semrush.com/blog/what-is-https/>

- 다양한 프로토콜

  : <https://enter.tistory.com/141>

  : <https://m.blog.naver.com/xcripts/70122755291>

- TLS/SSL HandShake

  : <https://wangin9.tistory.com/entry/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-URL-%EC%9E%85%EB%A0%A5-%ED%9B%84-%EC%9D%BC%EC%96%B4%EB%82%98%EB%8A%94-%EC%9D%BC%EB%93%A4-5TLSSSL-Handshake#:~:text=%EC%9D%B8%EC%A6%9D%EC%84%9C%EB%A5%BC%20%ED%86%B5%ED%95%B4%20%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%EA%B0%80,SSL%2FTLS%20Handshake%20%EB%9D%BC%EA%B3%A0%20%ED%95%A9%EB%8B%88%EB%8B%A4.>

- SSL은 무엇이고 인증서란 무엇인가?

  : <https://wiki.kldp.org/HOWTO/html/SSL-Certificates-HOWTO/x70.html>
