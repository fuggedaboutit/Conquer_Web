# 1.HTTP vs HTTPS

![image](https://user-images.githubusercontent.com/75282888/118450602-560d7300-b72f-11eb-87e9-83035068843a.png)

과거(대략 14년도 이전)에는 신용카드 번호와 같은 매우 예민한 정보를 다루는 이커머스사업자가 아닌 이상 굳이 HTTPS를 사용하지 않았다고 한다. 
하지만 구글에서 HTTPS로의 전환을 권고했고, HTTPS로 전환하는 사이트에게 **검색 노출 가산점**을 부여한다고 발표하자. 이에 따라 수많은 사이트들이 본격적으로 HTTPS로 전환하기 시작했다.



## 1.1. HTTP

![image](https://user-images.githubusercontent.com/75282888/118451460-3f1b5080-b730-11eb-8ff7-ae99b3060281.png)

0. Hypertext Transfer Protocol의 약자이다. 
1. HTTP는 서로 다른 시스템 간의 데이터 교환을 가능케 한다.
2. 대표적으로 서버에서 브라우저로 데이터를 보낼 때 흔히 사용되는 프로토콜이다.
3. 문제는 서버에서 브라우저로 전송되는 **데이터에 암호화가 걸려있지 않다**는 것이다.
4. 즉 정보가 해킹되기 쉽다는 얘기다.



## 1.2. HTTP (SSL과 TLS가 더해진)
![image](https://user-images.githubusercontent.com/75282888/118451119-de8c1380-b72f-11eb-82d2-fe489a3b2384.png)

0. Hypertext Transfer Protocol Secure의 약자이다.
1. HTTP의 보안 문제를 해결하기 위해 **SSL인증서**(Secure sockets layer certificate)을 사용한다.
2. SSL 인증서는 서버와 브라우저 사이 암호화된 보안망을 구축하는 것을 돕는다.
3. SSL인증서는 유저가 사이트에 제공하는 정보를 암호화한다. 데이터를 코드로 변환하는 방식을 사용한다.
4. 또한 HTTPS는 **TLS**(Transport Layer Security)프로토콜을 통해 암호화된다.
5. TLS는 데이터가 전송 도중 무단으로 수정되거나 도용되는 것을 예방한다.
6. 또한 TLS는 사용자에게 <u>현재 접속하고 있는 사이트가 해커가 만든 가짜 파싱 사이트가 아님</u>을 증명하는 인증을 제공합니다.







#### 참고자료

https://opentutorials.org/course/228/4894

https://seopressor.com/blog/http-vs-https/
https://medium.com/@audira98/http-vs-cheap-https-vs-expensive-https-e3b611f07dd2
