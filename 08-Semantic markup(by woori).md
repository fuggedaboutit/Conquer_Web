# Semantic Markup

## Semantic Markup 이란 무엇인가?

마크업 언어(markup language)는 태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어의 한 종류입니다.

그리고 사전적인 정의에 따르면 semantic은 '의미론적'이라는 뜻을 가지고 있습니다.   
의미론은 '단어나 문장의 정확한 해석'이라고 합니다.   
따라서 단어를 의미론적으로 사용한다는 것은 단어가 의미에 맞고 적절하게 사용되었다는 것입니다.   
반대로 단어의 사용법이 잘못됐거나 잘못된 목적에 사용하게 되었을 때 단어를 의미론적으로 사용하지 않았다고 말합니다.   

많은 HTML 태그는 의미론적 의미를 갖고 있습니다. 그 말인즉슨, 태그 그 자체만으로 opening tag, 그리고 closing tag 사이에 있는 내용이 어떤 정보를 담고 있는지 식별이 가능하다는 것입니다.   
예를 들어서 브라우저가 h1 heading 태그를 마주친다면, h1 요소를 포함하는 섹션 안에서 가장 중요한 제목을 구성한다는 의미로 그 태그를 해석할 수 있는 것입니다.   
h1 의 semantic meaning 은 웹 페이지나 섹션의 가장 중요한 헤더를 식별하는 것입니다.   

Semantic Markup을 사용할 때 지켜야할 것이 두가지 있습니다.   

1. Semantic markup에서 HTML요소는 의도된 목적에 따라서 사용되어야 한다.
2. Semantic markup은 내용과 표현의 분리가 필요하다. (Semantic markup requires the separation of content and presentation)

<br>

## HTML 요소를 올바르게 사용하는 법

우리는 브라우저에 요소에 관한 정보를 전달할 때는 HTML tags를 사용하면서 semantic markup을 쓸 수 있게됩니다.   
semantic markup 상에서 HTML tags는 단순히 사람이 읽을 수 있는 포멧으로 콘텐츠를 보여주는 역할을 하는 것이 아닙니다.   
HTML tags 그 자체만으로서 `기계(브라우저, 컴퓨터, 스마트폰 또는 다른 스마트 장치)`에 `콘텐츠의 의미`를 전달하게 됩니다.   

sematic markup을 제대로 작성하기 위해서는 인간과 기계가 모두 markup을 읽어낼 수 있도록 올바르게 HTML tags를 작성해야 합니다.

<br>

### Seperating Content and Presentation

과거에는 웹 페이지의 레이아웃과 스타일을 정의하기 위해 markup을 사용하는 것이 일반적이었습니다.   

Heading levels는 계층 구조를 고려해서 쓰여진 것이 아니라 웹 브라우저에 의해 적용된 스타일을 기반으로 사용되었고,   
tables를 사용할 때 데이터를 표로 그리기 위해서 사용한 것이 아니라 웹 페이지 레이아웃을 조정하기 위해 사용되었습니다.   
웹 페이지의 레이아웃을 정의하기 위한 목적으로 frameset과 같은 HTML tags가 몇 개 생기기도 했습니다.   

위와 같은 목적으로 HTML tags를 사용한다면 이것은 semantic markup이 아닙니다.   
semantic markup을 사용한다는 것은 눈에 보이는 비쥬얼을 위해서 HTML 요소를 선택하는 것이 아니라, 의미에 초점을 두고 선택이 이루어져야 합니다.   
따라서 semantic markup을 사용할 때 content와 presentation을 분리한다는 것은 content, 즉 요소가 담고 있는 의미가 눈에 보이는 외적인 요소와는 구분되어야 한다는 것입니다.   

이러한 두 가지 관행을 염두에 두고, 우리는 다음과 같은 방법으로 의미 마크업을 정의할 수 있다.

시맨틱 마크업(Semantic Markup)은 HTML과 같은 마크업 언어를 사용하여 마크업 요소의 적절한 선택을 통해 문서의 각 요소의 의미에 대한 정보를 전달하고 문서에 포함된 요소의 마크업과 시각적 표시 사이의 완전한 분리를 유지하는 것이다.

따라서 위의 내용을 고려하여 semantic markup을 다음과 같이 정의할 수 있습니다.   

> semantic markup은 HTML과 같은 마크업 언어를 사용하는 것입니다. 이때 단순히 외적인 표현을 위해서 마크업 요소를 선택하는 것이 아닌,   
> 문서 안의 요소의 의미, 정보를 명확하게 전달하는 마크업 요소를 사용해야 합니다.

<br>

### 왜 Semantic Markup을 사용해야 할까?

웹 페이지를 방문하는 일반적인 사람들은 웹 페이지가 얼마나 잘 꾸며져 있는지에 관심이 있지 마크업 상태는 별로 신경쓰지 않습니다.   
하지만 검색 엔진 웹 크롤러, 브라우저 번역 도구 또는 화면 판독기와 같은 computerized visitor가 웹 페이지에서 정확하게 정보를 얻기 위해서는 스타일링보다는 마크업이 훨씬 중요할 것입니다.   

Bruce Lawson은 HTML 요소를 semantic하게 사용할 수 있다면 '접근성, 검색성, 국제화 그리고 상호운용성을 강화할 것이다'라고 말했습니다.   
즉 semantic하게 만은 웹 사이트는 방문자가 더욱 쉽게 접근할 수 있으며, 검색 엔진 상위에 랭크될 것이고, 전 세계의 사람들이 사용할 수 있게 만들어주며 다른 웹 서비스와 효과적으로 연결되어 상호작용할 수 있다는 것입니다.   

sematic markup을 사용함으로서 인간과 기계 모두가 웹 콘텐츠를 읽고 이해할 수 있도록 해주어야 합니다.

<br>

### Semantic markup을 사용하는 방법

앞서 올바르게 의미와 정보를 전달하기 위해서 그에 적합한 tags를 사용한다고 이야기했습니다.   
HTML에는 semantic한 요소와 non-semantic한 요소들이 포함되어 있습니다.   
non-semantic한 요소의 대표적인 예는 `div`와 `span`이 있습니다. 해당 태그는 안에 포함되어 있는 콘텐츠의 의미를 컴퓨터에 전혀 알려주지 않습니다.   
이 태그들은 굉장히 유용한 태그이지만, 특정한 의미를 전달해야하고 그에 해당하는 semantic tag가 존재한다면 div와 span에 의존하기 이전에 해당 semantic tag를 사용해야합니다.   

구글과 오페라같은 회사들이 웹 페이지의 마크업을 분석했는데, 많은 웹사이트들이 non-semantic한 요소의 콘텐츠가 가진 의미를 암시하기 위해서 id와 class attributes를 사용한다는 것을 알아냈습니다.    
예를 들어 `<div id="nav">`, `<div id="header">`, `<div id="footer">` 와 같은 방식으로 div가 쓰인다는 것입니다.   
이러한 발견은 이후에 W3C가 nav, header, footer, article, aside와 같은 새로운 semantic tag를 HTML5에 포함시키는데 큰 도움을 주었습니다.   

> 이렇게 생겨난 semantic 요소들을 보통 4가지 카테고리로 분류합니다.   
> Document structure tags  
> Textual meaning tags  
> Media type tags  
> Correlation tag  

### Document Structure

과거에는 웹 사이트의 섹션을 식별하고 grouping하기 위해서 div를 주로 사용했습니다.   
하지만 HTML5가 등장함에 따라서 div tag로 단순히 grouping을 하는 것에서 더 나아가 semantic meaning을 부여할 수 있는 새로운 태그들을 사용할 수 있게 되었습니다.   

- header: 웹 페이지의 헤더 정보를 담은 컨테이너 역할을 하며 주로 site logo, heading elements, site navigation을 포함하고 있다.   
- footer: 웹 페이지의 바닥글에 사용되는 컨테이너 역할을 하며 주로 authorship, contact, copyright information, link back to the top of the web page 정보가 포함된다.   
- main: 여러 웹 페이지에서 반복되지 않고 단일 웹 페이지의 고유한 모든 정보를 포함하는데 사용되는 high-level 요소.   
- nav: 주로 사이트의 navigation links block을 포함합니다. 일반적으로 페이지의 header 또는 footer 안에 배치되며, aside(sidebar) 안에서도 사용할 수 있다.   
- section: 챕터와 같이 긴 형태의 포스트의 주요 섹션을 표시하는 데 사용.   
- aside: 문서의 주요 내용이 아닌 페이지의 주요 내용과 관련된 내용을 식별하는데 사용된다. 예를 들어 블로그 게시물에 나타내는 용어의 용어 정의를 포함하거나 페이지 내용과 관련된 광고를 포함할 수 있다.   
- article:  문서, 페이지, 애플리케이션, 또는 사이트 안에서 독립적으로 구분해 배포하거나 재사용할 수 있는 구획을 나타낸다. 예로 게시판과 블로그 글, 매거진이나 뉴스 기사 등이 있다.   

<br>

### Textual Meaning

과거 웹의 초창기에는 이런 식의 마크업이 자주 사용되었다고 합니다.   

```javascript
<style> .italics { font-style: italic; } </style> <p>Some paragraph content including one <span class="italics">italicized</span> word.</p>
```

visitors using screen readers or other computers accessing the content would understand that the tags were applied to add emphasis to the tagged content. The em element is just one example of how HTML tags add semantic meaning to textual content. Other examples include:

의미 없는 스팬 태그를 사용하는 대신 기울임꼴로 표시되는 단어 주위에 em 태그를 추가합니다. em 태그를 사용하면 화면 판독기 또는 콘텐츠에 액세스하는 다른 컴퓨터를 사용하는 방문자가 태그가 적용된 내용을 강조하기 위해 태그가 적용되었음을 이해할 수 있습니다. em 요소는 HTML 태그가 텍스트 내용에 의미론적 의미를 추가하는 방법의 한 예에 불과하다. 그 밖의 예는 다음과 같다.

opening tag와 closing tag사이에 있는 nested next가 사용된 목적이나 의미를 전혀 전달하지 않고 있습니다. 설마 현재에 이런 식으로 사용하는 사람이 있지는 않겠죠?   
저 단어를 기울여서 강조를 하고 싶은 상황인 것 같은데요, 이렇게 의미 없이 span tag를 사용하는 대신 해당 단어 주위에 em tags를 사용하는 것이 바람직합니다.   
em 태그를 사용함으로서 해당 태그가 적용된 내용을 강조하기 위해 사용되었구나, 라고 이해할 수 있습니다.   
em 외에도 Textual meaning을 전달할 수 있는 다양한 태그들이 있습니다.   

- strong: Text that is marked with strong tags is given added importance and is usually displayed in a bold typeface.   
- mark: The mark tag is used to highlight text of specific importance in a specific context. For example, it can be used to highlight every occurrence of a search term in a search results page.   
- cite: The cite element is used to identify the original work from which a bit of content originates.   
blockquote and q: The blockquote and q (quote) elements are used to identify text that is a direct quotation from another source.   
- time: The time element can be used to tell browsers, web crawlers, and other smart devices that a specific bit of content represents time on a 24-hour clock or a specific calendar date.   

<br>

### Media Type

미디어 유형을 식별하는 대표적인 3개의 태그가 있습니다. `<video>`를 사용한다면 브라우저에 video playback engine과 같은 특정 기술 리소스를 사용할 것이라는 신호를 보내면서 semantic meaning 또한 잘 드러납니다.   

- audio: Used to add one or more sources of audio content to a document and to allow the browser to pick the best option based on the visitor’s device and browser.   
- video: Similar to the audio element but used to add video content to a markup document.   
- picture: The picture element is used to allow a web browser to pick the best image from the available options based on the results of a media query.   

<br>

### Correlation Tags

어떤 요소들은 요소들 간의 상관관계를 나타내기 위해 사용됩니다. 예를 들어 정렬된 목록(ordered list, ol)을 사용해서 브라우저에게 리스트의 항목들이 서로 관련되어 있으므로 특정 순서로 나타나야 한다고 전달할 수 있습니다. 다음과 같은 요소가 상관 관계를 나타내는데 사용됩니다.   

- ul: Unordered lists are used to signal a relationship between the items on the list and to indicate that they do not need to be understood in a specific order.
- figure: The figure element is used to group together a piece of content, such as an image, chart, graph, or text, and a caption marked off by figcaption tags. By nesting the caption and the content between figure tags a relationship between the nested elements is identified.
- address: This attribute is used to associate contact information with the parent element that contains the address element. For example, when added to an article, the address element provides contact information for the article author, and when added to a web page footer the address identifies contact information for the web page owner.

<br>

참고: https://developer.mozilla.org/ko/docs/Web/HTML/Element  
(출처: https://html.com/semantic-markup/, 
https://developer.mozilla.org/ko/docs/Web/HTML/Element)
