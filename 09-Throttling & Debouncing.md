# Throttling & Debouncing

### 🥱 Throttle & Debounce 수심 50m 찍먹

바야흐로, 2009년 twitter에서 하단 페이지로 scroll을 할 시, 
버벅임과 response 하지 않는 결함을 발견합니다.  

[해당 이슈 tech press by John Hann](http://unscriptable.com/2009/03/20/debouncing-javascript-methods/)

JS를 사용하여 debounce가 구현된 형태는 이 시점 이후 성립되었습니다. 

연속적으로 벌어지는 Dom Event에 handler function을 호출이 계속 됨으로 야기된 이슈.

resource의 낭비와 서버과부화를 protection하기 위해

현대 모던브라우저에서 자주 사용되는 기법입니다.



※ syntax나 brwoser에서 native하게 제공되는 기법이 아니란점을 명시해주세요. 😎

p.s
throttle & debounce는 browser 뿐 아니라 다른 분야에서도 많이 사용됩니다.


> 요약:  
>함수 실행의 타이밍을 정하는 기법
>
> 특정 이벤트 발생 시, handler function call이 반복적으로 혹은 많이 처리되는 상황에서 
> 사용되는 최적화 용도로 사용됩니다.
> 
> ※ 주로, resize, scroll, mousemove, 연속적으로 일어나는 events
>   

---
## Throttling

Throttled 함수는 정해 둔 일정한 타이밍에 호출 하는 기법입니다. 
타이밍 이전 기간 동안 호출된 함수들은 무시됩니다.

### 개념 이해를 위한 예시

집에 맛있는 초콜릿 케이크가 있습니다. 

파티를 위해 만들어 놓았어요.

아이가 단맛을 한 번 맛 보더니, 눈이 돌아갔습니다.

엄마에게 계속 쫄라요, 먹고 싶다고.

엄마는 아이가 계속 케이크를 먹는 것을 자제하기 위해, 

30분에 한번 먹을 수 있다고 시간을 설정했어요.

아이와 엄마가 정해 놓은 시간이 있기 떄문에,

먹고 난 이후에, 아이가 더 먹고 싶다고 찡얼 거려도, 

엄마는 답을 하지 않고 아이의 찡어거림을 사뿐하게 넘겨듣습니다.

![image](https://user-images.githubusercontent.com/77006427/120895826-b53d1400-c659-11eb-9a26-ea90c6205270.png)

### 코드 예시

```bash
function throttle(func, duration) {
  let shouldWait = false
  
  return function (...args) {
    if (!shouldWait) {
      func.apply(this, args)
      
      //케이크 기다려
      shouldWait = true
      
      setTimeout(function () {
        //케이크 파티 시작
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

### Throttling이 주로 사용 되는 상황: 
- resize 발생 시, UI update
- 서버와 클라이언트 쪽에 대량의 트래픽을 발생시키는 기능 일 떄

---

## Debouncing

debounced 함수는 마지막 호출로 부터 정해둔 시간이 지나야 호출 되는 기법입니다.
중간의 상태는 제쳐두고, 마지막 호출 된 시점을 바라봅니다.

### 개념 이해를 위한 예시

아빠가 아이들을 데리고, 에버랜드로 향하고 있어요. 

아이들은 아빠에게 "우리 이제 도착했어요?"라고 물어 봅니다.

1분 5분 10분 아무리 물어봐도 아빠는 답을 하지 않아요.

도착을 하고나서야 아빠가 말합니다.

"짜잔, 에버렌드 도착!"

![image](https://user-images.githubusercontent.com/77006427/120913129-a4c78080-c6cf-11eb-88e3-90bcd22ce793.png)


### 코드 예시

```bash
function debounce(func, duration) {
  let timeout

  return function (...args) {
    const effect = () => {
      timeout = null
    
    //도착했다!!
      return func.apply(this, args)
    }

    //물어봐도 아빠는 대답을 안해요.
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

### Debounce가 주로 사용되는 상황:
- 자동 검색 추천(비동기)
- 서버에 일괄 처리 하는 작업 시

---

## Visual Demo

- http://demo.nimius.net/debounce_throttle/

## Real World Examples

검색창에 자동 검색 기능을 제공할 떄,


의도에 따라,
**Throttling**을 적용할지, 
**Debouncing**을 적용할지 
선택 할 수 있습니다.

#### 상황:
네이버 검색창에 키워드를 타이핑 할 떄,


#### 액션:
일정 기간마다 검색 키워드를 자동완성해서 보여주느냐? -> **Throttling**

사용자가 입력을 다하고 일정 시간 이후에 타이핑된 키워드의 자동완성을 보여주느냐? -> **Debouncing**

![autocomplete](https://user-images.githubusercontent.com/77006427/120898291-3948c900-c665-11eb-8425-22c801d2c663.gif)

더 많은 재미난 예시들이 궁금하시다면 이 [링크](https://tomekdev.com/posts/throttle-vs-debounce-on-real-examples)에 살표보시기를 추천합니다!

--- 

## Micellaneous
### rAF(Reqeust Animation Frame)를 활용한 Throttling

일정 duration 기간을 정하는 것에 정답은 없지만, 

사용자에게 매끄러운 UX 환경을 제공해주고 싶다면, 

duration 값을 16ms로 제공하면 됩니다.

왜 16ms 냐? 😮

rFA에는 animation을 60FPS(1초에 60frame === 1/60 = 16) 기준으로 repainting 되기전에 호출 해줍니다.

scroll 혹은 mousemove event에 붙여지는 기능일 떄는, 
throttle 함수를 사용하기보다, rAF로 대체 할 수 있습니다.

브라우저에 내장된 API이기 떄문에, 
해당 외부 3rd Party에 작성된 함수보다 
신뢰도가 높다는 장점도 하나의 포인트.

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

### 치트키
개인적으로 구현하기보다는, 이미 충분히 개선된 함수 및 옵션들이 정립된 pacakge를 사용하는 것을 추천합니다.

- [loadsh throttle](https://www.npmjs.com/package/lodash.throttle)
- [loadsh debounce](https://www.npmjs.com/package/lodash.debounce)
- [underscore throttle](https://underscorejs.org/#throttle)
- [underscore debounce](https://underscorejs.org/#debounce)


### 흔히 저지르는 죄악
1. throttle/debounce 함수 재선언

```bash
// BAD ❌
button.addEventListener('click', function handleButtonClick() {
  return debounce(getCake, 500)
})

// Good ✅
button.addEventListener(
  'click',
  debounce(function handleButtonClick() {
    return getCake()
  }, 500)
)
```

호출할려는 callback 함수를 debounce를 해야되는 반면, 애꿎은 함수를 debounce하기 떄문에, 
debounce로 원하는 effect가 발생하지 않습니다.

getCake()는 event가 감지할 떄 발생하는 callback안에 처리되는 함수 일 뿐 입니다. 

우리가 의도 하는것은 handler function을 최대한 자제 하는 것이 목표입니다.

**handler function**에 throttle/debounce를 시켜야되는 것을 주의해주세요. 😁

---

## 정리 및 끝맺음

### 왜 이런 timing function을 사용하느냐?
무분별한 resource 낭비 방지를 위해 최적화 및 보호의 용도로 사용합니다.

### 탁's 견해

정답은 없습니다. 선택에 따라 Trade-off 만 있을 뿐, 

무슨 의도를 가지고 **사용자에게 컨텐츠/기능을 어떻게 제공할 것인가** 기준을 기반하여 정하면 됩니다.

사용자의 경험만을 생각하는 열혈팬이 됩시다.


### References:
- [Debouncing - levelup](https://levelup.gitconnected.com/debounce-in-javascript-improve-your-applications-performance-5b01855e086)
- [Throttling - levelup](https://levelup.gitconnected.com/throttle-in-javascript-improve-your-applications-performance-984a4e020a3f)
- [Debounce and Throttle Examples - CSS TRICK](https://css-tricks.com/debouncing-throttling-explained-examples/)
- [Debounce vs Throttle - REDD](https://redd.one/blog/debounce-vs-throttle)
- [MDN ClearTimeOut](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearTimeout)
- [MDN requestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)