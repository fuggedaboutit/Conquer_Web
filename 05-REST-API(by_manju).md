# Rest API

## 🤔 What is Rest API?

<br>

REST는 `REpresentational State Transfer` 의 약자로 웹이 HTTP를 제대로 사용하지 못하고 있는 상황을 보고 HTTP의 장점을 최대한 활용할 수 있는 아키텍처로 REST를 소개했고 이는 HTTP프로토콜의 의도에 맞게 디자인하도록 유도하고 있습니다.

그리고 이러한 **REST 기본 원칙을 성실히 지킨 서비스 디자인을 `RESTful` 이라고 합니다!**

> 예를 들어, ‘REST API’를 제공하는 웹 서비스를 ‘RESTful’하다고 할 수 있습니다.

<br>

다시 정리하면

REST는 <span style="color:orange; font-weight:bold;"> `**HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method를 통해 Resource를 처리하도록 설계된 아키텍쳐**` </span>이고,

REST API는 <span style="color:orange"> `**REST를 기반으로 서비스 API를 구현한 것**` </span>을 의미합니다!!

<br>

## 😮 REST의 특징

<br>

1. `Uniform(유니폼 인터페이스)`

   : URI로 지정한 리소스에 대한 조직을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일

2. `Stateless(무상태성)`

   : 작업을 위한 상태정보를 따로 저장하고 관리하지 않습니다. 세션, 쿠키 정보를 저장하고 관리하지 않기 때문에 API 서버는 들어오는 요청만 단순히 처리합니다. 따라서 서비스의 자유도가 높아지고 불필요한 정보를 관리하지 않음으로써 구현이 단순해집니다.

3. `Cacheable(캐시 가능)`

   : REST는 HTTP라는 기존 웹표준을 그대로 사용하기 때문에, 웹에서 사용하는 기존 인프라를 그대로 활용이 가능합니다. 따라서 HTTP가 가진 캐싱 기능이 적용 가능합니다. HTTP 프로토콜 표준에서 사용하는 Last-Modified태그나 E-Tag를 이용하면 캐싱 구현이 가능합니다.

4. `Self-descriptiveness (자체 표현 구조)`

   : REST API 메시지만 보고도 이를 쉽게 이해 할 수 있는 자체 표현 구조입니다.

5. `Client - Server 구조`

   : REST 서버는 API 제공, 클라이언트는 사용자 인증이나 컨텍스트(세션, 로그인 정보)등을 직접 관리하는 구조로 각각의 역할이 확실히 구분되기 때문에 클라이언트와 서버에서 개발해야 할 내용이 명확해지고 서로간 의존성이 줄어들게 됩니다.

6. `계층형 구조`
   : REST 서버는 다중 계층으로 구성될 수 있으며 보안, 로드 밸런싱, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있고 PROXY, 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있게 합니다.

<br>

## 😮 REST API의 구성

<br>

REST API는 **`Resource(자원)`, `Verb(행위)`, `Representation(표현)`** 의 세가지 요소로 구성됩니다. REST는 자체 표현 구조로 구성되어 REST API만으로도 HTTP내용을 이해할 수 있습니다!

![REST API 구성](https://user-images.githubusercontent.com/75834421/120059882-35c6a800-c08f-11eb-8ef4-22af6b313a7e.png)

<br>

> 💡 여기서 payload 란?
>
> `전송되는 데이터`를 의미합니다. 원래 데이터를 전송 할때는 헤더, 메타데이터, 에러 체크 비트등과 같은 다양한 요소들을 함께 보내서, 데이터 전송의 효율과 안전성을 높입니다.이 때 보내고자 하는 <span style="color: pink; font-weight:bold;"> 데이터 자체</span>가 바로 payload입니다!
>
> json 에서의 payload는 **"data"**
>
> ```json
> {
> 	"status" :
> 	"from": "localhost",
> 	"to": "http://melonicedlatte.com/chatroom/1",
> 	"method": "GET",
>
>   //payload
> 	"data":{ "message" : "There is a cutty dog!" }
> }
> ```

<br>

## 😮 REST API 설계 원칙

<br>

가장 중요한 원칙은 두가지로, <span style="color:orange; font-weight:bold">URI는 리소스를 표현</span> 하는데 집중하고 <span style="color:orange; font-weight:bold">행위에 대한 정의는 HTTP 요청 메서드</span>를 통해 하는 것이 RESTful API를 설계하는 중심 규칙입니다!

<br>

1.  <span style="background-color:#ffc048; font-weight:bold; color:black">URI는 리소스를 표현해야 한다!</span>

    : **`리소스 표현`** 에 중점을 두고 **`명사`** 를 사용합니다. 따라서 이름에 get 같은 행위에 대한 표현이 들어가서는 안됩니다!

    ```jsx
    //bad
    GET / getTodos / 1;
    GET / todos / show / 1;

    //good
    GET / todos / show / 1;
    ```

    <br>

2.  <span style="background-color:#ffc048; font-weight:bold; color:black">리소스에 대한 행위는 HTTP요청 메서드로 표현한다!</span>

    : HTTP요청 메서드는 클라이언트가 서버에게 요청의 종류와 목적(리소스에 대한 행위)을 알리는 방법입니다. 주로 쓰이는 **요청 메서드 5가지<span style="color:orange">(GET, POST, PUT, PATCH, DELETE)</span>가 있습니다**

    ![요청메서드종류](https://user-images.githubusercontent.com/75834421/120064367-be9d0e00-c0a6-11eb-851f-47363ae451d4.png)

    : 리소스에 대한 행위는 HTTP요청 메서드를 통해 표현하며 **URI에 표현하지 않아요!**

    ```jsx
    //bad
    GET /todos/delete/1

    //good
     DELETE /todos/1
    ```

    <br>

    요청 method에 따른 실습은 `C:\Users\wjdal\Documents\json-server-exam` 파일 참고!

[참고]

: 모던 자바스크립트 Deep Dive

: https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html

: https://meetup.toast.com/posts/92
