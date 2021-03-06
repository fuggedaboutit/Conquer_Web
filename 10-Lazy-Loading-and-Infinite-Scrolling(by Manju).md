# Lazy Loading

<br>

## ๐ค What is Lazy Loading?

<br>

**`Lazy loading` (also called on-demand loading) is an `optimization technique` for the online content, be it a website or a web app.
Instead of loading the entire web page and rendering it to the user in one go as in bulk loading, the concept of lazy loading assists in `loading only the required section and delays the remaining, until it is needed by the user.`**

<br>

![LazyLoading](https://user-images.githubusercontent.com/75834421/121798147-a4932c00-cc5f-11eb-8a91-6fd6099ffbf2.png)

<br>

๐ก ๊ฐ๋จํ๊ฒ ๋งํด์, ์ฌ์ฉ์๊ฐ ์น์ฌ์ดํธ์ ์ ์ํ์ ๋, ํ์ํ ๊ฒ ๋ง ๋ก๋ฉ์์ผ์ ๋ณด์ฌ์ฃผ๊ณ , ๋๋จธ์ง๋ ์ฌ์ฉ์๊ฐ ๋ญ๊ฐ ํ์ํ๋ค๋ action์ ์ทจํ๊ฑฐ๋ ๊ทธ section์ ์ง์ํ์ ๋ ๋ก๋ฉ์ด ๋๋๋ก ์ปจํธ๋กค ํด์ฃผ๋ ๊ฒ์ Lazy Loading ์ด๋ผ๊ณ  ํฉ๋๋ค!

<br>

## ๐ฎ When and How to use Lazy Loading?

<br>

### image loading์์ lazy loading ์ ์ฉํ๊ธฐ

<br>

๋จผ์  ์กฐ๊ธ ๋ lazy loading ํจ๊ณผ๋ฅผ ์ ๋๋ก ๋ณด๊ธฐ ์ํด chrome network ์ค์ ์ `No cache`์ `Fast 3G`๋ก ํด๋ณด์์ต๋๋ค!

1) **firefox์์ Native Lazy Loading ์ด์ฉํ๊ธฐ (chrome ์ ์์ฃผ ์ต์ ์ Google Chrome ๋ธ๋ผ์ฐ์  ๋ฒ์ (Chroem 76)์์๋ง ์ง์)**

    **์ฌ์ฉํ๊ธฐ ์ **

    ![no_lazy_loading_example](https://user-images.githubusercontent.com/75834421/121799618-14a5b000-cc68-11eb-9021-84c3dd081551.png)

    <br>

    **์ฌ์ฉ ํ**

    ```html
        <img data-src="images/small0.jpg" alt="lift" loading="lazy">
        <img data-src="images/small1.jpg" alt="car" loading="lazy">
        <img data-src="images/small2.jpg" alt="record store" loading="lazy">
        <img data-src="images/small3.jpg" alt="lift" loading="lazy">
        <img data-src="images/small4.jpg" alt="car" loading="lazy">
        <img data-src="images/small5.jpg" alt="record store" loading="lazy">
    ```

    ![lazy_loading_example](https://user-images.githubusercontent.com/75834421/121799739-b6c59800-cc68-11eb-8f3a-3a14c4aac1b2.png)

    ์คํฌ๋กค์ ํด์ ์ฌ์ง ์์ญ์ผ๋ก ๊ฐ๋ฉด image๊ฐ loading ๋ฉ๋๋ค! => ์ง์  ๋ณด๊ธฐ!

<br>

2) **javascript๋ฅผ ์ฌ์ฉํ image Lazy Loading**

    ์ด ๊ธฐ์ ์ ๋ธ๋ผ์ฐ์  ๋ด scroll, resize ๊ทธ๋ฆฌ๊ณ  orientationChange ์ด๋ฒคํธ ๋ฆฌ์ค๋๋ฅผ ์ด์ฉํ  ์ ์์ต๋๋ค.

    chrome ์์๋ ์ ์ฉ์ด ๊ฐ๋ฅํฉ๋๋ค.

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
    ์ง์  ํ์ธํด๋ณด๊ธฐ!

<br>

3) ํฐ ์ด๋ฏธ์ง์ ๋ํด์ ๊ฐ์๊ธฐ loading ๋๋ ๊ฒ ๋ฐฉ์งํ๊ธฐ!

    ํฐ ์ด๋ฏธ์ง๋ ๋๊ฐ์ด lazy loading์ ์ ์ฉํด๋ณด๊ฒ ์ต๋๋ค!

    ```html
        <img class="lazy" data-src="images/big0.jpg" alt="record store" loading="lazy">
        <img class="lazy" data-src="images/big1.jpg" alt="record store" loading="lazy">
        <img class="lazy" data-src="images/big2.jpg" alt="record store" loading="lazy">
    ```

    ํฐ ์ด๋ฏธ์ง๋ฅผ ๋ก๋ฉํ ๋๋ ์๊ฐ์ด ๋ ๊ฑธ๋ฆฌ๋ ๋ฐ ๊ทธ ์๋์ text๊ฐ ์์ผ๋ฉด ์ฌ์ฉ์ ์์ฅ์์๋ ์๋ก์ด ์ด๋ฏธ์ง๊ฐ ๋ํ๋๋ ์ง ๋ชจ๋ฅด๊ณ  ์ฝ๋ค๊ฐ ๊ฐ์๊ธฐ ์ด๋ฏธ์ง๊ฐ loading๋๋ฉด์ text๋ฅผ ์ฝ๋๋ฐ ๋ฐฉํด๊ฐ ๋  ์ ์์ฃ ? ์ด๋ด ๋๋ ์ด๋ฏธ์ง์ ํฌ๊ธฐ๋ฅผ ์ ํด์ฃผ๋ฉด ๋ฉ๋๋ค!

    ```html
        <img width="972" height="1458" src="images/big0.jpg" alt="store" loading="lazy">
        <img width="1456" height="2184" src="images/big1.jpg" alt="record store" loading="lazy">
        <img width="2203" height="3000" src="images/big2.jpg" alt="phone" loading="lazy">
    ```

    ์ด๋ ๊ฒ ๋๋ฉด image๊ฐ loading๋๊ธฐ ์ ์๋ ๋น์ด์๋ ์ํ๋ก ์ด๋ฏธ์ง์ ์์น๋ฅผ ํ๋ณดํด์ค์ผ๋ก์ ์์ ๋ฌธ์ ์ ์ ํด๊ฒฐํด์ค๋๋ค!

<br>

## ๐ฎ Infinite Scrolling

<br>

infinite scrolling๋ lazy loading์ ์ ์ฉํ๋ ๋ํ์ ์ธ ์์๋ผ๊ณ  ํ  ์ ์์ต๋๋ค. ์ฌ์ฉ์์ ์คํฌ๋กค๋ง์ ์ถ์ ํ๋ฉด์ ํ์ํ  ๋ ์ถ๊ฐ์ ์ผ๋ก data๋ฅผ loading ํด์ค๋๋ค!

<br>

[infinite scrolling example] : https://codesandbox.io/s/day-seven-blueprint-forked-06yp4?file=/src/index.js
    
<br>

[์น์ฑ๋ฅ ์ต์ ํ๋ฅผ ์ํ image lazy loading ๊ธฐ๋ฒ] : https://helloinyong.tistory.com/297
