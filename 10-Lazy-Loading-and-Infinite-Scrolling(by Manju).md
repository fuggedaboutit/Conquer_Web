# Lazy Loading

<br>

## 🤔 What is Lazy Loading?

<br>

**`Lazy loading` (also called on-demand loading) is an `optimization technique` for the online content, be it a website or a web app.
Instead of loading the entire web page and rendering it to the user in one go as in bulk loading, the concept of lazy loading assists in `loading only the required section and delays the remaining, until it is needed by the user.`**

<br>

![LazyLoading](https://user-images.githubusercontent.com/75834421/121798147-a4932c00-cc5f-11eb-8a91-6fd6099ffbf2.png)

<br>

💡 간단하게 말해서, 사용자가 웹사이트에 접속했을 때, 필요한 것 만 로딩시켜서 보여주고, 나머지는 사용자가 뭔가 필요하다는 action을 취하거나 그 section에 진입했을 때 로딩이 되도록 컨트롤 해주는 것을 Lazy Loading 이라고 합니다!

<br>

## 😮 When and How to use Lazy Loading?

<br>

### image loading에서 lazy loading 적용하기

<br>

먼저 조금 더 lazy loading 효과를 제대로 보기 위해 chrome network 설정을 `No cache`와 `Fast 3G`로 해보았습니다!

1) **firefox에서 Native Lazy Loading 이용하기 (chrome 은 아주 최신의 Google Chrome 브라우저 버전(Chroem 76)에서만 지원)**

    **사용하기 전**

    ![no_lazy_loading_example](https://user-images.githubusercontent.com/75834421/121799618-14a5b000-cc68-11eb-9021-84c3dd081551.png)

    <br>

    **사용 후**

    ```html
        <img data-src="images/small0.jpg" alt="lift" loading="lazy">
        <img data-src="images/small1.jpg" alt="car" loading="lazy">
        <img data-src="images/small2.jpg" alt="record store" loading="lazy">
        <img data-src="images/small3.jpg" alt="lift" loading="lazy">
        <img data-src="images/small4.jpg" alt="car" loading="lazy">
        <img data-src="images/small5.jpg" alt="record store" loading="lazy">
    ```

    ![lazy_loading_example](https://user-images.githubusercontent.com/75834421/121799739-b6c59800-cc68-11eb-8f3a-3a14c4aac1b2.png)

    스크롤을 해서 사진 영역으로 가면 image가 loading 됩니다! => 직접 보기!

<br>

2) **javascript를 사용한 image Lazy Loading**

    이 기술은 브라우저 내 scroll, resize 그리고 orientationChange 이벤트 리스너를 이용할 수 있습니다.

    chrome 에서도 적용이 가능합니다.

    ```js
          document.addEventListener("DOMContentLoaded", function() {
          let lazyloadImages = document.querySelectorAll("img.lazy");    
          let lazyloadThrottleTimeout;

          function lazyload () {
            if(lazyloadThrottleTimeout) {
              clearTimeout(lazyloadThrottleTimeout);
            }    

            lazyloadThrottleTimeout = setTimeout(function() {
                let scrollTop = window.pageYOffset;
                lazyloadImages.forEach(function(img) {
                    if(img.offsetTop < (window.innerHeight + scrollTop)) {
                      img.src = img.dataset.src;
                      img.classList.remove('lazy');
                    }
                });
                if(lazyloadImages.length == 0) { 
                  document.removeEventListener("scroll", lazyload);
                  window.removeEventListener("resize", lazyload);
                  window.removeEventListener("orientationChange", lazyload);
                }
            }, 20);
          }

          document.addEventListener("scroll", lazyload);
          window.addEventListener("resize", lazyload);
          window.addEventListener("orientationChange", lazyload);
        });
    ```
    직접 확인해보기!

<br>

3) 큰 이미지에 대해서 갑자기 loading 되는 것 방지하기!

    큰 이미지도 똑같이 lazy loading을 적용해보겠습니다!

    ```html
        <img class="lazy" data-src="images/big0.jpg" alt="record store" loading="lazy">
        <img class="lazy" data-src="images/big1.jpg" alt="record store" loading="lazy">
        <img class="lazy" data-src="images/big2.jpg" alt="record store" loading="lazy">
    ```

    큰 이미지를 로딩할때는 시간이 더 걸리는 데 그 아래에 text가 있으면 사용자 입장에서는 새로운 이미지가 나타나는 지 모르고 읽다가 갑자기 이미지가 loading되면서 text를 읽는데 방해가 될 수 있죠? 이럴 때는 이미지의 크기를 정해주면 됩니다!

    ```html
        <img width="972" height="1458" src="images/big0.jpg" alt="store" loading="lazy">
        <img width="1456" height="2184" src="images/big1.jpg" alt="record store" loading="lazy">
        <img width="2203" height="3000" src="images/big2.jpg" alt="phone" loading="lazy">
    ```

    이렇게 되면 image가 loading되기 전에도 비어있는 상태로 이미지의 위치를 확보해줌으로서 위의 문제점을 해결해줍니다!

<br>

## 😮 Infinite Scrolling

<br>

infinite scrolling도 lazy loading을 적용하는 대표적인 예시라고 할 수 있습니다. 사용자의 스크롤링을 추적하면서 필요할 때 추가적으로 data를 loading 해줍니다!

<br>

[infinite scrolling example] : https://codesandbox.io/s/day-seven-blueprint-forked-06yp4?file=/src/index.js
    
<br>

[웹성능 최적화를 위한 image lazy loading 기법] : https://helloinyong.tistory.com/297
