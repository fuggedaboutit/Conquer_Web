# Image Lazy Loading & Infinite Scrolling

클라이언트가 보고 있는 브라우저 화면의 크기는 제한되어 있기 때문에 보이지 않는 콘텐츠를 미리 렌더링할 필요가 없다.

## 1. Image Lazy Loading

페이지를 읽어들이는 시점에서 일부의 이미지만을 로딩하고 사용자 시야에 이미지가 들어오는 시점에 나머지를 로딩함으로써 메모리 낭비를 방지한다.

![lazy-loading](https://user-images.githubusercontent.com/65386533/121780635-38bbaf80-cbdc-11eb-98b8-51ebda6d559e.png)

이미지 출처: [https://addyosmani.com/blog/infinite-scroll-without-layout-shifts/](https://addyosmani.com/blog/infinite-scroll-without-layout-shifts/)

### 1.1 왜 사용해야 할까?

1. 성능 향상

   웹사이트의 로딩 시간은 성능 관리 면에서 가장 중요한 요소 중 하나이다. lazy loading을 사용하면 페이지 초기 로딩 시 필요로 하는 이미지의 수를 줄일 수 있으며, 리소스 요청을 줄이는 것은 다운로드 바이트를 줄이는 것이며, 이는 유저가 사용할 수 있는 제한된 네트워크 대역폭의 경쟁을 줄이는 것을 의미한다. 그렇기 때문에 쓰지 않는 것에 비해 페이지를 훨씬 빨리 유저가 이용하게 된다.

2. 비용 감소

   통신 비용이 감소된다. 이미지 전달 또는 다른 전달할 무언가는 주로 전송 바이트 수에 기반하여 청구되는데, 앞서 언급했듯이, 이미지가 보여지지 않으면 절대 로딩하지 않으므로, 페이지 내에서 전달할 총 바이트 용량을 줄일 수 있다. 특히 페이지를 이탈하거나 페이지의 상단에서만 서비스를 이용하는 유저에게 효과적이다.

### 1.2 어떻게 사용할 수 있을까?

1. `<img>` 태그를 이용한 방식
2. 자바스크립트 이벤트를 이용하여 image load를 일으키는 방식
3. Intersection Observer API를 이용하여 image load를 일으키는 방식
4. Native lazy loading 방식
5. CSS 속성 중 Background Image를 lazy loading하는 방식

## 2. Infinite Scrolling

콘텐츠 일부분을 로딩하고 나머지는 스크롤이 끝까지 내려왔을 때 로딩하는 방식을 말한다.

![infinite-scroll](https://user-images.githubusercontent.com/65386533/121780632-378a8280-cbdc-11eb-98cd-9b43e309c4a5.png)

이미지 출처: [https://www.knowband.com/blog/ecommerce-blog/pagination-vs-infinite-scrolling/](https://www.knowband.com/blog/ecommerce-blog/pagination-vs-infinite-scrolling/)

스크롤이 끝까지 내려왔는지 확인하기 위해서는 세가지 요소가 필요하다.

1. 사용자에게 보여지고 있는 브라우저의 높이
2. 현재 스크롤 위치
3. 전체 브라우저의 실질적인 높이

### 2.1 Infinite Scrolling VS Pagination

Infinite Scroll은 유저들이 직접 끊임없이 생성하는 콘텐츠가 많은 사이트와 앱에 적합하다.

페이스북, 트위터, 핀터레스트, 인스타그램 등 소셜미디어가 대표적인 예.

반면, Pagination은 사용자가 가야 할 방향이 뚜렷한, 목표 지향적인 사이트와 앱에 적합하다.

구글은 Infinite Scroll과 Pagination 방식을 모두 사용하는데, 구글 이미지는 텍스트보다 더 빨리 이미지를 보고 처리할 수 있기 때문에 Infinite Scroll 방식을 사용하고, 검색의 경우 검색 결과를 읽는 데 시간이 더 걸리기 때문에 Pagination 방식을 사용한다.

---

- 참조

  [https://velog.io/@boh001/Infinity-Scrolling](https://velog.io/@boh001/Infinity-Scrolling)

  [https://helloinyong.tistory.com/297](https://helloinyong.tistory.com/297)

  [https://slowalk.com/2596](https://slowalk.com/2596)
