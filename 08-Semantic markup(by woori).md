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

(보충 예정)

(출처: https://html.com/semantic-markup/)