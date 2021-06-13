# Code Spliting

### Intro

Bundling 과정을 통해, 중복되고 사용되지 않는 코드 리소스를 털어내는 과정을 겪었습니다만, 


> 불필요한 공백이나, 줄바꿈 혹은 주석 과 같은 렌더링 과정에 필요없는 코드를 제거 할 수 있는데 이를 Minify (압축)라 칭한다. 
> 
> 사용되지 않는 코드들(import 된 module 중 사용하지 않는)들을 DOM tree로 부터 제거하는 작업을 tree shaking
> 
> import code from the module really matter 😎

서비스가 커지면, 결국 털어내도 리소스 사이즈가 커지기 마련입니다. 

털어내도 털어내도 커지니 그럼 차라리 분할을 시켜버리자!

그래서 말 그대로 Code Spliting 이라고 합니다.

---

Client Side Rendering(CSR)은 SPA(Single Page Application) 입니다.

즉, 하나의 html 파일을 받고, 번들링이 된 하나의 JS파일을 통해 DOM을 조작해서 그려줍니다.

```bash
// Download a whole bundle looks like:

///////////////////////// whole bundle

```

웹페이지에서 번들링 된 파일을 로드하기까지는 결국 동기적 형태로 진행됩니다.

시작 엔트리 포인트가 login 페이지로 가정 해봅니다. 

접속할 시, Admin Page를 담당하는 로직이 들어있는 리소스도 같이 다운로드 됩니다.

당장 사용하지는 않을 것이지만,

그래서 사용자가 필요 할 떄! 사용할 떄! load를 하는게 좋지 않겠느냐!

**첫 페이지 로드 시 에 불필요한 것들을 지금 불러오는게 말인 것이냐!!!!**

```bash

// split the code then it would look like:

//// login
//////// admin
//about

```

이런 추후에 불러오는 과정을 보통 저희는 비동기(Asynchronous) 라고 봅니다.

※ 각 분할 된 것들을 chunk라고 부릅니다.

필요 할 떄 load를 하기에 첫 페이지 초기 로딩 시, 최적화가 됩니다.

![image](https://user-images.githubusercontent.com/77006427/121800525-7288c680-cc6d-11eb-800c-4317ea5da768.png)



### 어떻게? 어디에?

번들 파일들을 엔트리 경로를 일일이 설정해서 청크로 분할하는 방식

[webpack entry point - code spliting](https://webpack.js.org/guides/code-splitting/#entry-dependencies)

혹은

Dynamic import를 통해 코드를 주입하여 청크로 분할 하는 방식

[webpack dynamic import](https://webpack.js.org/guides/code-splitting/#entry-dependencies)
[babel config dynamic import](https://babeljs.io/docs/en/babel-plugin-syntax-dynamic-import)



후자의 방식에 대해 집중해보겠습니다. 

둘다 복잡 해지는 작업이지만, 지혜롭게...차악을 선택하겠습니다.

React에서 자체적으로 dynamic import를 제공해주는 hook을 사용합니다.
1. lazy
   - 컴포넌트를 dynamic import를 통해, 비동기로 로드해줍니다.
2. Suspense
   - 컴포넌트가 비동기로 로드가 될 떄까지, Suspense 컴포넌트로 감싸줍니다. 로드 되는 동안 로딩이라던가 기타 다른 컨텐츠를 fallback prop을 활용 해 보여 줄 수 있습니다.


3. Route Base splitting

```jsx
/* route base splitting */
import React, { lazy, Susepnse } from 'react';


...
function ...(){

const DashboardPage = React.lazy(() => import('../pages/dashboard'));
const SettingsPage = React.lazy(() => import('../pages/settings'));

return (
    <Route>
        <Switch>
            <Suspense fallback={<div>Loading ...</div>}>
                <DashboardPage />
                <SettingsPage />
            </Suspense>
        </Switch>
    </Route>
    )
}
```

※ **Named Exports(default)** 만 지원 [참고링크](https://reactjs.org/docs/code-splitting.html#named-exports)

2. Component Base splitting

```jsx
// > CustomComponent.jsx
import React, { useEffect } from "react";

const CustomComponent = ({ label }) => {
  useEffect(() => {
    console.log(`${label} created`);
    return () => console.log(`${label} destroyed`);
  }, []);

  return <div>{label}</div>;
};

export default CustomComponent;
```

```jsx
// > App.jsx
import React, { Suspense } from "react";
import ReactDOM from "react-dom";
/* wait 100 ms to render component */
const CustomComponent = React.lazy(
  () =>
    new Promise((resolve, reject) =>
      setTimeout(() => resolve(import("./custom-component")), 100)
    )
);
/* wait 500 ms to render component */
const CustomComponent2 = React.lazy(
  () =>
    new Promise((resolve, reject) =>
      setTimeout(() => resolve(import("./custom-component")), 5000)
    )
);

function App() {
  return (
    <>
      <Suspense fallback={<div>Loading</div>}>
        <CustomComponent label="Component 1" />
        <CustomComponent2 label="Component 2" />
      </Suspense>
    </>
  );
}

```

[Demo link](https://codesandbox.io/s/reactlazy-one-suspense-example-giy9c?expanddevtools=1&fontsize=14&hidenavigation=1&view=preview&file=/src/index.js)

3. Library base splitting

```jsx
import React from "react";
import ReactDOM from "react-dom";
import loadable from "@loadable/component";

const CustomComponent1 = loadable(
  () =>
    new Promise((resolve, reject) =>
      setTimeout(() => resolve(import("./custom-component")), 100)
    ),
  {
    fallback: <div>Loading...</div>
  }
);

const CustomComponent2 = loadable(
  () =>
    new Promise((resolve, reject) =>
      setTimeout(() => resolve(import("./custom-component")), 5000)
    ),
  {
    fallback: <div>Loading...</div>
  }
);

function App() {
  return (
    <>
      <CustomComponent1 label="Compnent 1" />
      <CustomComponent2 label="Component 2" />
    </>
  );
}

```

[@loadble/Component](https://github.com/gregberge/loadable-components#readme)


### Tip
```jsx
const MyComponent = React.lazy(() => import(
/* webpackChunkName: "MyComponent" */
"./my-component"));
```

lazy안에 comment를 입력하면 해당 chunk의 이름이 됩니다.


Suspense를 활용 시 fallback은 정말 필요할 때 만 사용하는게 좋습니다. 
보편적으로 주입 시, 되려 bundling 되야 할 resource가 증가하는 것을 명심!

### Caution 
Code Spliting 혹은 Bundle spliting을 하기 전에, 내부 코드 자체에서, 쓸데 없이 사용되고 있는 resource가 있는지 점검하는게 중요합니다. 

이미 -1000이 있는 상태에서 spliting을 통해 최적화를 선택하기보다,

-1000을 최대한 0으로 줄인 상태에서 spliting을 도입하는 자세를 취해야됩니다.

### Milestone
- preload
- prefetch


**References:**
Documentation
- [Webpack Code Spliting](https://webpack.js.org/guides/code-splitting/)
- [Webpack lazy loading](https://webpack.js.org/guides/lazy-loading/)
- [react-router-dom](https://reactrouter.com/web/guides/code-splitting)
- [react documentation code-spliting](https://reactjs.org/docs/code-splitting.html#:~:text=Code%2DSplitting%20is%20a%20feature,be%20dynamically%20loaded%20at%20runtime.)
- [React Suspense in React](https://css-tricks.com/react-suspense-in-practice/)
- [Suspense for data fetching](https://reactjs.org/docs/concurrent-mode-suspense.html)

---
Blog

- [React’s Experimental Suspense API Will Rock for Fallback UI During Data Fetches](https://css-tricks.com/reacts-experimental-suspense-api-will-rock-for-fallback-ui-during-data-fetches/)
- [Lazy Loading Components in React Application](https://medium.com/@muratcatal/lazy-loading-in-react-2a43ea2b2dd1)
- [Speed up your React app with dynamic imports and route-centric code splitting](https://blog.logrocket.com/speed-up-react-app-dynamic-imports-route-centric-code-splitting/)
- [webpack + react opimised from scratch](https://medium.com/nerd-for-tech/webpack-react-optimised-from-scratch-da8f75024ba4)
- [dynamic import](https://pks2974.medium.com/dynamic-import-%EB%A1%9C%EC%9B%B9%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%84%B1%EB%8A%A5-%EC%98%AC%EB%A6%AC%EA%B8%B0-caf62cc8c375)
- [perforamnce optimization by code spliting](https://medium.com/wesionary-team/performance-optimization-by-code-splitting-react-lazy-and-suspense-79b199c86717)

---
Videos
- [프론트엔드 웹서비스에서 우아하게 비동기 처리하기](https://youtu.be/FvRtoViujGg)
- [Beginner guide to code spliting your react app - fb conf](https://www.youtube.com/watch?v=bb6RCrDaxhw)