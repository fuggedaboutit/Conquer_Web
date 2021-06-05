# Throttling and Debouncing

<br>

scroll, resize, input, mousemove 같은 이벤트는 짧은 시간 간격으로 연속해서 발생하므로 이러한 이벤트에 바인딩한 핸들러는 과도하게 호출되어 ❗❗성능에 문제를 일으킬 수 있습니다❗❗

<br>

**`스로틀`과 `디바운스`는 짧은 시간 간격으로 `연속해서 발생하는 이벤트를 그룹화`해서 과도한 이벤트 핸들러의 호출을 방지하는 프로그래밍 기법입니다**

<br>

## 🤔 What is Debouncing?

<br>

디바운스는 짧은 시간 간격으로 이벤트가 연속해서 발생하면 이벤트 핸들러를 호출하지 않다가 일정 시간이 경과한 이후에 이벤트 핸들러가 한번에 호출되도록 합니다. 즉, **디바운스는 짧은 시간 간격으로 발생하는 이벤트를 그룹화해서 `마지막에 한번만 이벤트 핸들러가 호출되도록` 한다**

<br>

![debounce](https://user-images.githubusercontent.com/75834421/120897999-0225e800-c664-11eb-8ee9-2d1348c15858.png)

> <--> : delaytime

<br>

### 😮 When we use Debouncing?

<br>

- 검색 할 때

    : input 이벤트는 사용자가 텍스트 입력 필드에 값을 입력할 때 마다 연속해서 발생합니다. 사용자가 검색창에 한글자 한글자 칠때마다 Ajax 요청과 같은 무거운 처리를 수행하면 사용자가 입력을 완료하지 않았어도 Ajax요청이 전송될 수 있고 이는 서버에도 부담을 줄수 있습니다❗❗ 
    
    따라서 사용자가 입력을 완료했을 때 한번만 Ajax 요청을 전송하는 것이 좋습니다.  => **일정 시간동안 텍스트 입력필드에 값을 입력 하지 않으면 입력이 완료된 것으로 간주합니다!**

<br>

- 화면 resizing 할 때

    : debounce를 사용하지 않는 resize 이벤트는 화면의 사이즈를 변결할 때마다 기록하지만, **debounce를 사용하면 resize이벤트의 마지막을 추적해서 사이즈를 기록하고 있습니다!**

    ```js
    $(document).ready(function(){
  
    var $win = $(window);
    var $left_panel = $('.left-panel');
    var $right_panel = $('.right-panel');
    
    function display_info($div) {
      $div.append($win.width() + ' x ' + $win.height() +  '<br>');
    }
                  
    $(window).on('resize', function(){
      display_info($left_panel);
    });
    
    $(window).on('resize', _.debounce(function() {
      display_info($right_panel);
    }, 400));
    });
    ```

<br>

#### 📝 이처럼 **`짧은 시간 간격으로 이벤트가 연속해서 발생하면 이벤트 핸들러를 호출하지 않다가 일정 시간 동안 이벤트가 더 이상 발생하지 않으면 이벤트 핸들러가 한 번만!! 호출되도록 하는 것이 debounce 입니다!`** 

<br>


# 🤔 What is Throttling?

<br>

스로틀은 짧은 시간 간격으로 이벤트가 연속해서 발생하더라도 **일정 시간 간격으로 이벤트 핸들러가 최대 한 번만!!** 호출 되도록 합니다. 즉, 짧은 시간 간격으로 연속해서 발생하는 이벤트를 **`그룹화`** 해서 **`일정 시간 단위로 이벤트 핸들러가 호출되도록 호출 주기를 만듭니다`**.

<br>

![throttling](https://user-images.githubusercontent.com/75834421/120898042-339eb380-c664-11eb-83cb-d10f80163308.png)

<br>

### 😮 When we use Throttling?

<br>

- 무한 스크롤(Infinite Scrolling) 

    : 사용자가 footer 에서 얼마나 떨어져 있는지 확인해야하고 사용자가 맨 아래로 스크롤 했다면 Ajax 를 통해 더 많은 콘텐츠를 요청하여 페이지에 추가해야 합니다. 여기서 debouncing 은 사용자가 스크롤을 멈출때만 이벤트를 발생시키므로, **`주기적으로 사용자의 위치를 파악하는 함수를 실행하기 위해 throttling을 사용합니다!`**

    ```js
    $(document).ready(function(){
    $(document).on('scroll', _.throttle(function(){
      check_if_needs_more_content();
    }, 300));
  
    function check_if_needs_more_content() {     
      pixelsFromWindowBottomToBottom = 0 + $(document).height() - $(window).scrollTop() -$(window).height();
      
      if (pixelsFromWindowBottomToBottom < 200){
        // Here it would go an ajax request
        $('body').append($('.item').clone()); 
      }
    }
    });
    ```

<br>

#### 📝 위의 예제에서 Thtottling 없이 scroll 이벤트를 발생시키면 사용자가 스크롤할때마다 발생합니다. 이를 방지하기 위해 **`짧은 시간 간격으로 연속해서 발생하는 이벤트를 그룹화해서 일정 시간 간격으로 이벤트 핸들러를 호출하는 것이 Throttling 입니다!`**

<br>

## 🤔 What is differences between Debounce and Throttle?

<br>

제일 큰 차이점은 **`스로틀은 적어도 X밀리 초마다 정기적으로 기능 실행을 보장한다는 것`** 입니다! Debounce는 아무리 많은 이벤트가 발생해도 모두 무시하고 **`특정 시간 사이에 어떤 이벤트도 발생하지 않았을 때 딱 한번만 마지막 이벤트를 발생시키는 기법`**입니다. 따라서 일정 시간이 지나기 전에 계속 이벤트가 발생하면 콜백에 반응하는 이벤트는 **`발생하지 않고 ❗❗계속 무시됩니다❗❗`**

```js
var inside1 = $(".inside-1");
var thing1 = $(".thing-1");
var count1 = $(".count-1");
inside1.on('scroll', function() {
  thing1.css("top", inside1[0].scrollTop);
  count1.html(parseInt(count1.html())+1);
});

// 2 
var inside2 = $(".inside-2");
var thing2 = $(".thing-2");
var count2 = $(".count-2");
inside2.on('scroll', _.throttle(function() {
  thing2.css("top", inside2[0].scrollTop); 
  count2.html(parseInt(count2.html())+1);
}, 150));

// 3
var inside3 = $(".inside-3");
var thing3 = $(".thing-3");
var count3 = $(".count-3");
inside3.on('scroll', _.debounce(function() {
  thing3.css("top", inside3[0].scrollTop);
  count3.html(parseInt(count3.html())+1);
}, 100));
```

https://lodash.com/docs/4.17.15#throttle

https://underscorejs.org/#throttle

https://webclub.tistory.com/607