# Throttling & Debouncing

### ๐ฅฑ Throttle & Debounce ์์ฌ 50m ์ฐ๋จน

๋ฐ์ผํ๋ก, 2009๋ twitter์์ ํ๋จ ํ์ด์ง๋ก scroll์ ํ  ์, 
๋ฒ๋ฒ์๊ณผ response ํ์ง ์๋ ๊ฒฐํจ์ ๋ฐ๊ฒฌํฉ๋๋ค.  

[ํด๋น ์ด์ tech press by John Hann](http://unscriptable.com/2009/03/20/debouncing-javascript-methods/)

JS๋ฅผ ์ฌ์ฉํ์ฌ debounce๊ฐ ๊ตฌํ๋ ํํ๋ ์ด ์์  ์ดํ ์ฑ๋ฆฝ๋์์ต๋๋ค. 

์ฐ์์ ์ผ๋ก ๋ฒ์ด์ง๋ Dom Event์ handler function์ ํธ์ถ์ด ๊ณ์ ๋จ์ผ๋ก ์ผ๊ธฐ๋ ์ด์.

resource์ ๋ญ๋น์ ์๋ฒ๊ณผ๋ถํ๋ฅผ protectionํ๊ธฐ ์ํด

ํ๋ ๋ชจ๋๋ธ๋ผ์ฐ์ ์์ ์์ฃผ ์ฌ์ฉ๋๋ ๊ธฐ๋ฒ์๋๋ค.



โป syntax๋ brwoser์์ nativeํ๊ฒ ์ ๊ณต๋๋ ๊ธฐ๋ฒ์ด ์๋๋์ ์ ๋ช์ํด์ฃผ์ธ์. ๐

p.s
throttle & debounce๋ browser ๋ฟ ์๋๋ผ ๋ค๋ฅธ ๋ถ์ผ์์๋ ๋ง์ด ์ฌ์ฉ๋ฉ๋๋ค.


> ์์ฝ:  
>ํจ์ ์คํ์ ํ์ด๋ฐ์ ์ ํ๋ ๊ธฐ๋ฒ
>
> ํน์  ์ด๋ฒคํธ ๋ฐ์ ์, handler function call์ด ๋ฐ๋ณต์ ์ผ๋ก ํน์ ๋ง์ด ์ฒ๋ฆฌ๋๋ ์ํฉ์์ 
> ์ฌ์ฉ๋๋ ์ต์ ํ ์ฉ๋๋ก ์ฌ์ฉ๋ฉ๋๋ค.
> 
> โป ์ฃผ๋ก, resize, scroll, mousemove, ์ฐ์์ ์ผ๋ก ์ผ์ด๋๋ events
>   

---
## Throttling

Throttled ํจ์๋ ์ ํด ๋ ์ผ์ ํ ํ์ด๋ฐ์ ํธ์ถ ํ๋ ๊ธฐ๋ฒ์๋๋ค. 
ํ์ด๋ฐ ์ด์  ๊ธฐ๊ฐ ๋์ ํธ์ถ๋ ํจ์๋ค์ ๋ฌด์๋ฉ๋๋ค.

### ๊ฐ๋ ์ดํด๋ฅผ ์ํ ์์

์ง์ ๋ง์๋ ์ด์ฝ๋ฆฟ ์ผ์ดํฌ๊ฐ ์์ต๋๋ค. 

ํํฐ๋ฅผ ์ํด ๋ง๋ค์ด ๋์์ด์.

์์ด๊ฐ ๋จ๋ง์ ํ ๋ฒ ๋ง ๋ณด๋๋, ๋์ด ๋์๊ฐ์ต๋๋ค.

์๋ง์๊ฒ ๊ณ์ ์ซ๋ผ์, ๋จน๊ณ  ์ถ๋ค๊ณ .

์๋ง๋ ์์ด๊ฐ ๊ณ์ ์ผ์ดํฌ๋ฅผ ๋จน๋ ๊ฒ์ ์์ ํ๊ธฐ ์ํด, 

30๋ถ์ ํ๋ฒ ๋จน์ ์ ์๋ค๊ณ  ์๊ฐ์ ์ค์ ํ์ด์.

์์ด์ ์๋ง๊ฐ ์ ํด ๋์ ์๊ฐ์ด ์๊ธฐ ๋๋ฌธ์,

๋จน๊ณ  ๋ ์ดํ์, ์์ด๊ฐ ๋ ๋จน๊ณ  ์ถ๋ค๊ณ  ์ฐก์ผ ๊ฑฐ๋ ค๋, 

์๋ง๋ ๋ต์ ํ์ง ์๊ณ  ์์ด์ ์ฐก์ด๊ฑฐ๋ฆผ์ ์ฌ๋ฟํ๊ฒ ๋๊ฒจ๋ฃ์ต๋๋ค.

![image](https://user-images.githubusercontent.com/77006427/120895826-b53d1400-c659-11eb-9a26-ea90c6205270.png)

### ์ฝ๋ ์์

```bash
function throttle(func, duration) {
  let shouldWait = false
  
  return function (...args) {
    if (!shouldWait) {
      func.apply(this, args)
      
      //์ผ์ดํฌ ๊ธฐ๋ค๋ ค
      shouldWait = true
      
      setTimeout(function () {
        //์ผ์ดํฌ ํํฐ ์์
        shouldWait = false
      }, duration)
    }
  }
}

button.addEventListener(
  'click',
  throttle(function () {
    getCake()
  }, 1800000)
)
```

### Throttling์ด ์ฃผ๋ก ์ฌ์ฉ ๋๋ ์ํฉ: 
- resize ๋ฐ์ ์, UI update
- ์๋ฒ์ ํด๋ผ์ด์ธํธ ์ชฝ์ ๋๋์ ํธ๋ํฝ์ ๋ฐ์์ํค๋ ๊ธฐ๋ฅ ์ผ ๋

---

## Debouncing

debounced ํจ์๋ ๋ง์ง๋ง ํธ์ถ๋ก ๋ถํฐ ์ ํด๋ ์๊ฐ์ด ์ง๋์ผ ํธ์ถ ๋๋ ๊ธฐ๋ฒ์๋๋ค.
์ค๊ฐ์ ์ํ๋ ์ ์ณ๋๊ณ , ๋ง์ง๋ง ํธ์ถ ๋ ์์ ์ ๋ฐ๋ผ๋ด๋๋ค.

### ๊ฐ๋ ์ดํด๋ฅผ ์ํ ์์

์๋น ๊ฐ ์์ด๋ค์ ๋ฐ๋ฆฌ๊ณ , ์๋ฒ๋๋๋ก ํฅํ๊ณ  ์์ด์. 

์์ด๋ค์ ์๋น ์๊ฒ "์ฐ๋ฆฌ ์ด์  ๋์ฐฉํ์ด์?"๋ผ๊ณ  ๋ฌผ์ด ๋ด๋๋ค.

1๋ถ 5๋ถ 10๋ถ ์๋ฌด๋ฆฌ ๋ฌผ์ด๋ด๋ ์๋น ๋ ๋ต์ ํ์ง ์์์.

๋์ฐฉ์ ํ๊ณ ๋์์ผ ์๋น ๊ฐ ๋งํฉ๋๋ค.

"์ง์, ์๋ฒ๋ ๋ ๋์ฐฉ!"

![image](https://user-images.githubusercontent.com/77006427/120913129-a4c78080-c6cf-11eb-88e3-90bcd22ce793.png)


### ์ฝ๋ ์์

```bash
function debounce(func, duration) {
  let timeout

  return function (...args) {
    const effect = () => {
      timeout = null
    
    //๋์ฐฉํ๋ค!!
      return func.apply(this, args)
    }

    //๋ฌผ์ด๋ด๋ ์๋น ๋ ๋๋ต์ ์ํด์.
    clearTimeout(timeout)

    timeout = setTimeout(effect, duration)
  }
}

button.addEventListener(
  'click',
  debounce(function () {
    announceArrival()
  }, 3600000)
)
```

### Debounce๊ฐ ์ฃผ๋ก ์ฌ์ฉ๋๋ ์ํฉ:
- ์๋ ๊ฒ์ ์ถ์ฒ(๋น๋๊ธฐ)
- ์๋ฒ์ ์ผ๊ด ์ฒ๋ฆฌ ํ๋ ์์ ์

---

## Visual Demo

- http://demo.nimius.net/debounce_throttle/

## Real World Examples

๊ฒ์์ฐฝ์ ์๋ ๊ฒ์ ๊ธฐ๋ฅ์ ์ ๊ณตํ  ๋,


์๋์ ๋ฐ๋ผ,
**Throttling**์ ์ ์ฉํ ์ง, 
**Debouncing**์ ์ ์ฉํ ์ง 
์ ํ ํ  ์ ์์ต๋๋ค.

#### ์ํฉ:
๋ค์ด๋ฒ ๊ฒ์์ฐฝ์ ํค์๋๋ฅผ ํ์ดํ ํ  ๋,


#### ์ก์:
์ผ์  ๊ธฐ๊ฐ๋ง๋ค ๊ฒ์ ํค์๋๋ฅผ ์๋์์ฑํด์ ๋ณด์ฌ์ฃผ๋๋? -> **Throttling**

์ฌ์ฉ์๊ฐ ์๋ ฅ์ ๋คํ๊ณ  ์ผ์  ์๊ฐ ์ดํ์ ํ์ดํ๋ ํค์๋์ ์๋์์ฑ์ ๋ณด์ฌ์ฃผ๋๋? -> **Debouncing**

![autocomplete](https://user-images.githubusercontent.com/77006427/120898291-3948c900-c665-11eb-8425-22c801d2c663.gif)

๋ ๋ง์ ์ฌ๋ฏธ๋ ์์๋ค์ด ๊ถ๊ธํ์๋ค๋ฉด ์ด [๋งํฌ](https://tomekdev.com/posts/throttle-vs-debounce-on-real-examples)์ ์ดํ๋ณด์๊ธฐ๋ฅผ ์ถ์ฒํฉ๋๋ค!

--- 

## Micellaneous
### rAF(Reqeust Animation Frame)๋ฅผ ํ์ฉํ Throttling

์ผ์  duration ๊ธฐ๊ฐ์ ์ ํ๋ ๊ฒ์ ์ ๋ต์ ์์ง๋ง, 

์ฌ์ฉ์์๊ฒ ๋งค๋๋ฌ์ด UX ํ๊ฒฝ์ ์ ๊ณตํด์ฃผ๊ณ  ์ถ๋ค๋ฉด, 

duration ๊ฐ์ 16ms๋ก ์ ๊ณตํ๋ฉด ๋ฉ๋๋ค.

์ 16ms ๋? ๐ฎ

rFA์๋ animation์ 60FPS(1์ด์ 60frame === 1/60 = 16) ๊ธฐ์ค์ผ๋ก repainting ๋๊ธฐ์ ์ ํธ์ถ ํด์ค๋๋ค.

scroll ํน์ mousemove event์ ๋ถ์ฌ์ง๋ ๊ธฐ๋ฅ์ผ ๋๋, 
throttle ํจ์๋ฅผ ์ฌ์ฉํ๊ธฐ๋ณด๋ค, rAF๋ก ๋์ฒด ํ  ์ ์์ต๋๋ค.

๋ธ๋ผ์ฐ์ ์ ๋ด์ฅ๋ API์ด๊ธฐ ๋๋ฌธ์, 
ํด๋น ์ธ๋ถ 3rd Party์ ์์ฑ๋ ํจ์๋ณด๋ค 
์ ๋ขฐ๋๊ฐ ๋๋ค๋ ์ฅ์ ๋ ํ๋์ ํฌ์ธํธ.

```bash
window.requestAnimationFrame(callback);

button.addEventListener(
  'click',
  throttle(function () {
    getCake()
  }, 16)
)

//they both manage the handler function every 16ms.
//seems they work equivalent, but remeber, depending on the device you are using,
//it may result into slightly difference. 
//Never mind it unless it arises the critical performance issue.
```

[Animation & Throttle Comparison Demo Site](https://codepen.io/dcorb/pen/pgOKKw)

### ์นํธํค
๊ฐ์ธ์ ์ผ๋ก ๊ตฌํํ๊ธฐ๋ณด๋ค๋, ์ด๋ฏธ ์ถฉ๋ถํ ๊ฐ์ ๋ ํจ์ ๋ฐ ์ต์๋ค์ด ์ ๋ฆฝ๋ pacakge๋ฅผ ์ฌ์ฉํ๋ ๊ฒ์ ์ถ์ฒํฉ๋๋ค.

- [loadsh throttle](https://www.npmjs.com/package/lodash.throttle)
- [loadsh debounce](https://www.npmjs.com/package/lodash.debounce)
- [underscore throttle](https://underscorejs.org/#throttle)
- [underscore debounce](https://underscorejs.org/#debounce)


### ํํ ์ ์ง๋ฅด๋ ์ฃ์
1. throttle/debounce ํจ์ ์ฌ์ ์ธ

```bash
// BAD โ
button.addEventListener('click', function handleButtonClick() {
  return debounce(getCake, 500)
})

// Good โ
button.addEventListener(
  'click',
  debounce(function handleButtonClick() {
    return getCake()
  }, 500)
)
```

ํธ์ถํ ๋ ค๋ callback ํจ์๋ฅผ debounce๋ฅผ ํด์ผ๋๋ ๋ฐ๋ฉด, ์ ๊ฟ์ ํจ์๋ฅผ debounceํ๊ธฐ ๋๋ฌธ์, 
debounce๋ก ์ํ๋ effect๊ฐ ๋ฐ์ํ์ง ์์ต๋๋ค.

getCake()๋ event๊ฐ ๊ฐ์งํ  ๋ ๋ฐ์ํ๋ callback์์ ์ฒ๋ฆฌ๋๋ ํจ์ ์ผ ๋ฟ ์๋๋ค. 

์ฐ๋ฆฌ๊ฐ ์๋ ํ๋๊ฒ์ handler function์ ์ต๋ํ ์์  ํ๋ ๊ฒ์ด ๋ชฉํ์๋๋ค.

**handler function**์ throttle/debounce๋ฅผ ์์ผ์ผ๋๋ ๊ฒ์ ์ฃผ์ํด์ฃผ์ธ์. ๐

---

## ์ ๋ฆฌ ๋ฐ ๋๋งบ์

### ์ ์ด๋ฐ timing function์ ์ฌ์ฉํ๋๋?
๋ฌด๋ถ๋ณํ resource ๋ญ๋น ๋ฐฉ์ง๋ฅผ ์ํด ์ต์ ํ ๋ฐ ๋ณดํธ์ ์ฉ๋๋ก ์ฌ์ฉํฉ๋๋ค.

### ํ's ๊ฒฌํด

์ ๋ต์ ์์ต๋๋ค. ์ ํ์ ๋ฐ๋ผ Trade-off ๋ง ์์ ๋ฟ, 

๋ฌด์จ ์๋๋ฅผ ๊ฐ์ง๊ณ  **์ฌ์ฉ์์๊ฒ ์ปจํ์ธ /๊ธฐ๋ฅ์ ์ด๋ป๊ฒ ์ ๊ณตํ  ๊ฒ์ธ๊ฐ** ๊ธฐ์ค์ ๊ธฐ๋ฐํ์ฌ ์ ํ๋ฉด ๋ฉ๋๋ค.

์ฌ์ฉ์์ ๊ฒฝํ๋ง์ ์๊ฐํ๋ ์ดํํฌ์ด ๋ฉ์๋ค.


### References:
- [Debouncing - levelup](https://levelup.gitconnected.com/debounce-in-javascript-improve-your-applications-performance-5b01855e086)
- [Throttling - levelup](https://levelup.gitconnected.com/throttle-in-javascript-improve-your-applications-performance-984a4e020a3f)
- [Debounce and Throttle Examples - CSS TRICK](https://css-tricks.com/debouncing-throttling-explained-examples/)
- [Debounce vs Throttle - REDD](https://redd.one/blog/debounce-vs-throttle)
- [MDN ClearTimeOut](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearTimeout)
- [MDN requestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)