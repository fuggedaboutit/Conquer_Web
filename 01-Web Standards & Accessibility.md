# Web Standards and Acessibility

## Web Standards

---

>**표준**
>
>여러 가지 다양한 것들이 섞여 있는 범주에서 가장 일반적이거나 평균적인 것.
> 
> 국립국어원 정의
  
#### 웹 표준이 없었을 때, 90s
- 제각각 다르게 제작된 Browser 들로 인해 개발자들에게 고통 부여
- 사용자들에게 공통적인 정보를 각각의 브라우저들이 제공하지 아니함
- 기준이 없기에 서로 상이하게 발전이 됨.
- 사용자가 제일 많은 곳의 브라우저의 독단적인 결정권이 쥐어짐.


위에 언급된 문제들을 해결 하기 위해 제작된 것이 웹 표준 명세서입니다.

표준의 명세서일 뿐, 따르지 않으면 작동이 되지는 않습니다. 

다만 모두가 참고 할 수 있는 가이드라인을 제시하여, 
공통체로서 WEB을 발전시키는 지향점을 목표로 웹 표준을 준수 할려고 하고있습니다.

더불어 더욱 더 좋은 표준을 세워, 웹이 가질 수 있는 최대의 잠재력을 끌어올리려는 노력을 하고있습니다.

---

#### 그럼 대체 누가 웹 표준을 제공 하나요? 😵

웹 표준은 커뮤니티를 통해 세워집니다.

단 한 곳의 커뮤니티가 아닌,   
아래와 같은 단체들이  
상호가 수많은 소통 과 합의를 거쳐 세워집니다.

웹 표준에 기여하는 커뮤니티들을 통 틀어,  
'Standards Development Organizations'라고 명칭합니다.
**※ A.K.A SDOs**


SDOs의 주측이 되는 기관은 아래와 같습니다.
- Internet Engineering Task Force (IETF)
- World Wide Web Consortium (W3C)
- Web Hypertext Application Technology Working Group (WHATWG)
- ECMA TC39

각 기관들이 지향하는 책임과 관심사는 다르지만,  
웹 표준을 세우는 일에는 모두 공동체로 서로 교류하며,  

- 더 옳은 방향은 무엇인가? 
- 지혜로운 방법은 무엇인가?
- 근거와 사유가 올바른가?

협력체로서 Web의 표준을 함께 만들어갑니다.

이렇게 세워진 표준은 누구에게도 로열티를 받지 않으며, 
Web에 종사하는 모든 사람에게 **대가 없이** 정보를 제공합니다.

위의 언급 된 기관이에도, 다른 기관들도 존재하며,  
표준을 어떻게 따라야하는가에 집중적으로 도와줄려는 목적을 가진,  
인큐베이팅 기관들도 있습니다. (Web incubator community group [A.K.A WHYCG](https://wicg.io/))


#### 표준을 어디서 어떻게 참고 할 수 있을까요?

시작은 가볍게, 대부분의 웹 개발자들이 참고하는 공신력 있는[Mozila Developer Networks](https://developer.mozilla.org/ko/)을 추천드립니다.

각각의 브라우저들과의 호환성표를 제공하기에,  
표준을 알아가는데 있어, 현재 필요한 부분들을 찾아서 적용 할 수 있습니다.

##### **요약된 표준 정리 공식 문서는 없을까요?**

아쉽지만, 요약본은 없습니다. 다만 필요한 부분들을 빠르게 찾을 수 있는 페이지는 W3C에서 제공하고있습니다. 
[퀵 네비게이션 링크](https://www.w3.org/WAI/WCAG21/quickref/)


표준은 방대합니다.  

표준을 다 지킨다는 것은,

대다수가 공증한 믿을 수 있는 약속을 지킨다는 것입니다.

<p align="center">
    <img 
        src="https://user-images.githubusercontent.com/77006427/119230570-c9f8b280-bb57-11eb-9c88-ad76784a60b4.gif"
    />
</p>

>개인적인 탁's 사견
>
>표준을 지키지 못했다는 죄책감보다는  
>지킬려는 의지와 목표를 가지며 
>발전하는 방향이 좋은 방향이지 않을까 😂
>


## Web Accessibiility 

> access
> 
> - a means of approaching or entering a place.
> - obtain, examine, or retrieve (data or a file).
> 
>
> accessibiltiy
> - the quality of being able to be reached or entered.
>
> - Oxford disctionary

> 접근성
>
> 닿을 수 있는 도달 할 수 있는 상태의 척도

일반 사용자들 뿐만 아니라,  
물리적으로 불편함을 가진 분들에게도,  
웹에 존재하는 contents를 차별없이 모두가 누릴 수 있는냐?에 관한 것이  
바로 Web accessibility입니다.

현실에서 접근성의 예시)

- 지하철 계단
<p align="center">
    <img 
        src="https://user-images.githubusercontent.com/77006427/119254952-0974dc80-bbf4-11eb-9479-1b123e2a7059.png"
    />
</p>

- 버스 계단
<p align="center">
    <img 
        src="https://user-images.githubusercontent.com/77006427/119254984-32956d00-bbf4-11eb-9ade-28205bf2bef6.png"
    />
</p>


Web에서 접근성의 예시)

- 시각장애인
<p align="center">
    <img 
        src="https://user-images.githubusercontent.com/77006427/119255166-1d6d0e00-bbf5-11eb-9ad6-9aca1fc4c385.png"
    />
</p>
  
- 청각장애인
<p align="center">
    <img 
        src="https://user-images.githubusercontent.com/77006427/119255136-f6164100-bbf4-11eb-8ec1-ca428461e17b.png"
    />
</p>

웹이 등장한 이 후, 특정 불편함을 겪지 않는 사람에게도 혁신이 왔다고 가정 하면,
물리적으로 불편한 사람에게는 새로운 새상이 왔습니다.

주변의 사람들로의 도움으로만 접할 수 있는 정보를,  
보다 쉽게 접근하고 체험 할 수 있기에,  

주변에 도와주는 사람이 없어도,  
더욱 세상에 다 가갈 수 있게 해준 것이 WEB이라는 장소입니다.

Semantic MarkUp을 쓰는 이유는, 의미가 없는 element에 의미를 부여 해, 뜻을 내포시키자라는 목적도 있지만, 

한발 더 나아가서, 보다 쉽게 접근성을 높이기 위한 구분을 해주는 목적도 있습니다.

접근성을 어떻게 구축하느냐? 어디서 부터 시작해야되느냐?

[W3C WAI 가 제공하는 가이드라인](https://www.w3.org/WAI/standards-guidelines/wcag/)을 살펴보면서 부터 시작가능합니다.

접근성을 부여하는 것은 여러가지 방법이 존재합니다. 

우리가 첫 걸음을 걷기 위해, 할 수 있는 step은 바로 
[aria-label](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute)에 그냥저냥의 내용을 적는게 아닌,   


aria-label에 만 적는 내용에 접근하면,  
해당 컨텐츠를 표현 할 수 있는 설명을 적어주는 습관부터   
시작하는게 첫 발자국이 될 수 있지 않을까 싶습니다.


References: 
- [Web Standards Keys](https://www.keycdn.com/blog/web-standards)
- [Web Standards Guide](https://www.smashingmagazine.com/2019/01/web-standards-guide/) 
- [Wiki Web Standards](https://en.wikipedia.org/wiki/Web_standards) 
- [Creating an Accessible Digital Future](https://www.youtube.com/watch?v=Wb2X9kYEvXc) 
- [Screenreader](https://webaim.org/techniques/screenreader/) 
- [WAI/standards-guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/) 