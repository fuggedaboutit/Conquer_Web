# Semantic Markup

<br/>

&nbsp; 웹이 발전하며 데이터도 방대해지고 컨텐츠 또한 다양화 되었습니다.

때문에 자연스럽게 다양하고 많은 이용자들이 웹을 사용하며 인터넷 마케팅이 급속도로 발달되었습니다.

이에 따라 웹페이지가 가지는 내용이 중요하게 되며 **검색 엔진 최적화**와 **웹접근성**을 위해 발전이 이루어집니다.

해당 웹페이지를 파악하고 노출이 잘되기 위해 HTML 요소를 적절하게 사용한 시멘틱한 마크업을 알아봅시다.

<br/>

## Semantic ?

<br/>

&nbsp; Semantic이란 **'의미론적인'** 이라는 사전적 의미를 가지고있습니다.

웹을 공부하게되면 **시멘틱 웹**, **시멘틱 마크업**이라는 말을 들을 수 있습니다.

여기서의 **시멘틱 마크업**은 컴퓨터(브라우저)가 잘 이해할 수 있는 코드입니다.

<br/>

## Semantic Markup

<br/>

&nbsp; 프로그래밍언어는 이용자와 기계와의 약속입니다. HTML은 프로그래밍언어가 아니지만 이용자와 컴퓨터(브라우저)와의 약속입니다.

제목을 나타내기 위해선 `<h1>` 태그를, 문단을 나타내기 위해선 `<p>` 태그를 사용하자는 약속입니다. 기계는 약속을 잘지키니 저희만 약속을 잘 지키면 될 것입니다.

구체적으로 마크업을 할때는 의미에 맞는 요소를 사용하고 문서를 표현할 때는 구조화를 잘 해주자는 것입니다.

이렇게 잘 정의되어있는 표준대로 작성하게 되면 결국엔 기계뿐 아니라 사람도 이해하기 쉬운 코드가 될 것입니다.

<br/>

```html
<b>굵은</b> vs <strong>중요한</strong>
<br />
<i>기울어진</i> vs <em>강조하는</em>
<br />
<u>밑줄친</u> vs <ins>새롭게 추가된</ins>
<br />
<s>중간선이 있는</s> vs <del>삭제된</del>
```

<br/>

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb9OxNA%2Fbtq6zRD5OTA%2FKJhCEam2YYv5Zl6ZZzmPi0%2Fimg.png"/></p>

<br/>

&nbsp; 위의 코드는 화면에서 각각의 요소가 같은 모습으로 표현되지만 의미는 같지 않습니다.

`<b>`는 의미 없이 단순히 텍스트를 굵게 표현하는 태그지만, `<strong>`은 중요하다는 의미

`<i>`는 단순히 기울어진 글자를 표현하지만, `<em>`은 글자의 특정 부분을 강조하는 의미

`<u>`와 `<s>`는 단순히 글자에 선을 그은 것이나, `<ins>`와 `<del>`은 내용이 새롭게 추가되거나 삭제가 되었다는 의미를 지닙니다.

이와같이 단순 표현만이아닌 의미를 주기위해 적절한 태그를 사용하는것이 `시멘틱한 마크업`입니다.

<br/>

## HTML5 시멘틱 요소

<br/>

&nbsp; HTML5에는 요소를 정의하는 규칙들이 있습니다. 비슷한 성격의 요소들끼리 그룹화한 것이 **콘텐츠 모델**입니다.

> **💡 콘텐츠모델의 7 분류**
>
> 1. Metadata Content
> 2. Flow Content
> 3. Sectioning Content
> 4. Heading Content
> 5. Phrasing Content
> 6. Embedded Content
> 7. Interacitve Content
>
> [참고 : Content Model-MDN](https://developer.mozilla.org/ko/docs/Web/Guide/HTML/Content_categories)

<br/>

&nbsp; 이중에서 `Sectioning Content`, `구획 콘텐츠`와 기본 레이아웃 구조에 대해서 알아보겠습니다.

<br/>

[참고 : HTML5 Semantics](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

<br/>

## 기본 레이아웃과 구획 콘텐츠

<br/>

<p align="center"><img src="https://www.w3schools.com/html/img_sem_elements.gif"/></p>

<br/>

&nbsp; HTML5에서 추가된 구획 콘텐츠는 `<nav>`, `<aside>`, `<section>`, `<article>` 입니다.

- nav : 문서전체에서 사용되는 navigation역할을 합니다.

[참고 : nav - MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/nav)

- aside : 배너,사이드바와 같은 영역에 많이 사용됩니다.

[참고 : aside - MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/aside)

- section : 문서를 주제별로 구분짓기 위해 사용을 합니다. 하위요소로 `h1` ~ `h6`를 포함해야합니다.

[참고 : section - MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/section)

- article : 독립적이고 홀로 설 수 있는 내용에 사용됩니다. 하위요소로 `h1` ~ `h6`를 포함해야합니다.

[참고 : article - MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/article)

[참고 : 뉴스 - article 사용사례](https://byline.network/)

---

[참고 : 당근마켓](https://www.daangn.com/)
