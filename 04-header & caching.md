# Header & Caching

## Prologue

브라우저에 URL(Uniform Resoucre Locator)를 입력하고 제출 시 벌어지는 과정.

1. URL 입력 
2. 브라우저는 DNS(Domain name server)를 통해 IP address를 탐색
3. 브라우저는 HTTP request를 서버에게 전송
4. 서버는 HTTP response를 브라우저에게 응답 전송
5. 브라우저는 HTML을 렌더링 프로세스 시작
6. 브라우저는 HTML에 embeded 돼있는 부수적인 object들에 따른 HTTP request를 재차 전송 (Images, css, javascript). 3~5번 step을 재차 반복
7. 페이지 로드 완료 시, 비동기적인 요청들을 HTTP request를 서버에게 전송

## Header

> Header
>
> a line of text serving to indicate what the passage below it is about

> '머리말'
>  
> 책이나 논문 따위의 첫머리에 **내용**이나 **목적** 따위를 간략하게 적은 글.


HTTP 통신 간 오가는 HTTP Message(request와 response)에 대해  
내용이나 목적을 설명해주는 내용이 바로 **Header**입니다. 

다른 명칭으로는 web meta data라고도 할 수 있습니다.

#### Request 대표적 헤더

User-Agent
- 클라이언트가 자신의 application 이름을 넣는 곳

Referer
- 서버에서 참고하는 추가 정보
- 클라이언트가 요청을 보낼 때 보고 있던 페이지의 URL을 보낸다.

Authroization
- 특별한 클라이언트에만 통신을 허가할 떄 인증 정보를 서버에게 전달


![image](https://user-images.githubusercontent.com/77006427/120074654-c5dd0f80-c0d8-11eb-8294-a35cf8eb8fba.png)


#### Response 대표적 헤더

Content-Type
- 파일 종류를 지정

Content-Length
- 바디 크기

Content-Encoding
- 압축이 이루어진 경우 압축 형식

Date
- 문서 날짜

![image](https://user-images.githubusercontent.com/77006427/120074680-eb6a1900-c0d8-11eb-9287-fe110e6954e4.png)

CSR (Content Security Policy)
- 브라우저가 게시할 수 있는 컨테츠의 종류를 제한


현재 추가되고 있는 최신 헤더
Feature Policy
- 사용되는 브라우저 기능을 제한


※ 등록된 모든 Header를 볼 수 있는 곳:   
[IANA 사이트](https://www.iana.org/assignments/message-headers/message-headers.xhtml)


## Cache


> Cache
>
> a collection of items of the same type stored in a hidden or inaccessible place.
> store away in hiding or for future use.
>
> 저장하다 / 은닉하다

반복적으로 사용되는 동일한 데이터를 저장하여, 더 빠르게 사용자에게 제공 할 수 있는 메카니즘을 **캐시**라고 합니다.


>컨텐츠가 변경되지 않았을 때 로컬에 저장된 파일을 재사용함으로써 불필요한 다운로드 횟수를 
>절감하고 성능을 높이는 작업
>
> 2.8 cache - real world http p88 中


### 갱신 일자에 따른 캐시
브라우저에서 HTTP resonpse에 명시된 Last Modified를 If-Modified-Since 헤더에 넣어 서버에게 요청합니다.

해당 컨텐츠의 변경 일시와 비교하여 차이가 없을 떄, response status code에 따라 cache된 데이터를 사용하느냐 안하느냔 판가름이 납니다.


<p align="center">
    <img 
    src="https://user-images.githubusercontent.com/77006427/120097465-8f040980-c16b-11eb-86d8-3624eaf12b7c.jpg"
    width=400 height=600
    />
</p>

### Expires 헤더에 따른 캐시

지정한 Expire 헤더에 기한(날짜와 시간)을 기입.

> Expires: Fri, 05 Aug 2016 00:52:00 GMT

클라이언트는 지정된 기한 내라면 캐시를 강제로 이용.

유효기간이 지날 시 캐시가 신선하지 않다고 인식하게 됩니다.

기한을 길게 설정했다면, 최신 컨텐츠가 즉각 반영이 되지 않는 에로사항이 있습니다.

※ 캐시 최대수명을 1년으로 설정하자라는 가이드라인이 제시되어있습니다.

<p align="center">
    <img 
    src="https://user-images.githubusercontent.com/77006427/120097473-9c20f880-c16b-11eb-9360-78d2bd46dfc9.jpg"
    width=400 height=600
    />
</p>

### Etag (entity tag)
파일의 해시값(혹은 고유 식별할 수 있는 값)을 통해 비교하여 캐시를 사용하는지의 여부를 판단합니다.

URL을 통해 처음 접속 할 시 HTTP response에 Etag를 첨부하여 보내줍니다.

재차 같은 URL에 접속시, Etag를 If-Non-Match 헤더에 값을 보내, 컨텐츠가 변경이 됬는지 알 수 있습니다.



<p align="center">
    <img 
    src="https://user-images.githubusercontent.com/77006427/120097485-a6db8d80-c16b-11eb-827a-37fd8b17994c.jpg"
    width=400 height=600
    />
</p>

### Cache-Control

캐시 제어에 대한 방법들을 명시해주는 헤더입니다.

※ expire 보다 우선되서 처리됩니다.

대표적으로

### public
같은 컴퓨터를 사용하는 복수의 사용자간 캐시 재사용을 허간한다.
### private
같은 컴퓨터를 사용하는 다른 사용자 간 캐시를 재사용하지 않는다.
같은 URL에서 사용자마다 다른 컨텐츠가 돌아오는 경우에 이용한다.

#### max-age=n
캐시의 신선도를 초단위로 설정.

86400(하루)로 설정한다면 해당 기한 내에 서버에 문의하지 않고 캐시를 이용.
그 이후에는 서버에서 304 status 코드를 반환 할 시에만 캐시를 사용합니다.
#### no-cache
캐시가 유효한지 매번 문의한다. (max-age=0 과 동일)
#### no-store
캐시하지 않는다.

<p align="center">
    <img 
    src="https://user-images.githubusercontent.com/77006427/120097495-b3f87c80-c16b-11eb-887c-353a2aa34ffb.jpg"
    width=600 height=600
    />
</p>

※ cache-flow가 정의 되어있지 않으면, cache가 기능이 안되는건 아닙니다. 브라우저가 자동적으로 해당 페이제 맞춰 caching을 어떻게 할것인지 자동을 설정해줍니다. 

자동으로 설정되는 방식이 궁금하시다면, 출처에 기입된 Heuristic Freshness 글을 참고해주세요!



References
- [What Happens when you type in a URL](https://wsvincent.com/what-happens-when-url/)
- [opentutorials HTTP](https://opentutorials.org/module/3621) 
- [opentutorials CACHE](https://opentutorials.org/module/3830)
- [MDN http caching](https://developer.mozilla.org/ko/docs/Web/HTTP/Caching)
- [google developer http caching](https://web.dev/http-cache/)
- [Heuristic Freshness](https://www.mnot.net/blog/2017/03/16/browser-caching#heuristic-freshness)
- [Real World HTTP](https://www.hanbit.co.kr/store/books/look.php?p_code=B7009240426)
- [HTTP headers for the responsible developer](https://www.youtube.com/watch?v=Mjqf2kkFLy8)
- [HTTP Headers: The State of the Web](https://www.youtube.com/watch?v=Mjqf2kkFLy8)