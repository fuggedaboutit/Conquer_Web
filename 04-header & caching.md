# Header & Caching


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


References
- [HTTP headers for the responsible developer](https://www.youtube.com/watch?v=Mjqf2kkFLy8)
- [HTTP Headers: The State of the Web](https://www.youtube.com/watch?v=Mjqf2kkFLy8)
- [Real World HTTP](https://www.hanbit.co.kr/store/books/look.php?p_code=B7009240426)
- [opentutorials HTTP](https://opentutorials.org/module/3621) 
- [opentutorials CACHE](https://opentutorials.org/module/3830)