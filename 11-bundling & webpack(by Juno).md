# bundling & webpack

<br/>

## **😥 급변하는 프론트엔드 환경**

<br/>

&nbsp; 웹 개발에 있어서 프론트엔드의 급변하는 환경을 대부분은 **모던 Javascript**(**ECMA2015**)이후 부터 시작되었다고 대부분은 알고있지만

정확히는 **ECMA2015**부터가 아닌 그 이전부터 있었습니다. 바로 **Node.js**, **npm**을 통해 이루어지는 환경에서 시작되었습니다.

웹앱의 규모가 굉장히 커져감에 따라 더욱더 급변하고 복잡해집니다.

소프트웨어 하나를 만든다는 가정을 하면 규모가 어느정도일까요? 규모가 큰 웹앱은 수백만 수천만 라인의 코드가 될 수도 있습니다.

이코드들이 또 하나의 파일로는 작업할 수 없기때문에 수십, 수백개 이상의 파일이 하나의 어플리케이션을 위한 규모입니다.

하지만 이것들이 왜 프로젝트 구성을 복잡하게하는 원인이 되었을까요?

<br/>

## **👍 스펙의 필요성**

<br/>

&nbsp; **Javascript**는 초기엔 **HTML**을 조작하기위해 간단히 만들어진 언어입니다.

언어의 초기 컨셉 자체가 그러다보니 수만개의 소스코드를 가지고 하나의 애플리케이션을 만들기위한 기능들이 준비가 되어있지 않았습니다.

대부분의 언어에서 지원하던 **module**스펙이 없었기 때문에 많은 파일로 하나의 애플리케이션을 만든다고 하였을때 문제가 되었습니다.

**Javascript**는 이러한 **module**을 **ECMA2015**부터 지원하였었습니다.

**module**스펙은 파일과 파일간에 특정기능을 사용하기 위함입니다. 자바스크립트는 `export`와 `import`의 형태로 지원을합니다.

그런데 왜 이 스펙이 개발 환경을 복잡하게 만드는 원인이 되었을까요?

<br/>

## **❗ 원인**

<br/>

&nbsp; **HTML**에서 JS파일을 사용하기 위해서는 `script`태그를 이용하여 파일을 로딩하였었습니다.

그럼 10개의 파일이있다면 `script`태그가 10개, 100개라면 `script`태그를 100개 작성해야 할까요?

실제로도 그럴 수 밖에 없었기때문에 병목현상은 물론이거니와 `export`, `import`가 생겼지만 문제가 있었습니다.

바로 **브라우저 호환성 이슈**입니다.

<br/>

## **😅 호환성과 생산성 사이**

<br/>

&nbsp; 웹 프론트엔드 개발자가 새로운 스펙을 사용할때 제일 먼저 떠오르는것은 **브라우저 호환성**입니다.

웹은 누구에게나 공평하고 서비스를 하는 입장에서는 사용자가 어떤 환경에서 사용할지 강제하는것은 굉장히 어렵습니다.

때문에 웹 개발자들은 **브라우저 호환성**을 최대한 넓게 가져가는것이 중요합니다.

하지만 **Javascript**는 매년 새로운 버전과 문법이 나오고있으며 이미 현업에서 없어서는 안되는 스펙들도 있습니다.

이러한 스펙은 **생산성**또한 높아지기 때문에 개발자들은 사용하고 싶으나 지원을 하지않는 브라우저들 때문에 사용할 수 없는 경우도 있습니다.

이때 여러 엔지니어링 시도가 이루어집니다.

<br/>

## **😍 번들러의 등장**

<br/>

&nbsp; **Node.js**는 브라우저 외의 환경에서 **Javascript**를 동작하게 해주며 **Javascript**개발자들은 여러 툴을 만들고

**npm**을 통해 배포를 하기가 쉬워집니다. 이러한 상황에서 **번들러**라는 소프트웨어가 나옵니다.

**번들러는** 브라우저가 `script`를 부르기전에 미리 하나의 파일로 만들어둡니다.

그럼 **HTML**은 하나의 JS파일만 부르면 됩니다. 물론 **번들링**이라는 행위에서 문제가 없지는 않습니다.

하지만 **번들링**을 사용하며 **module**이라는 스펙을 사용할 수 없는 환경에서도 사용할 수 있게 되었습니다.

<br/>

> **💡 번들러 종류**
>
> 현재 사용되는 번들러들은 webpack, parcel, rollup 등이 있습니다.  
> 이중 가장 많이 사용되는 번들러는 webpack 입니다.
>
> [webpack vs parcel vs rollup 번들러 비교하기](https://sambalim.tistory.com/137)

<br/>

## **🙏 번들러의 역할**

<br/>

<p align="center"><img src="https://miro.medium.com/max/1634/0*MztcXroPHZ5nkHOS.png"/></p>

<br/>

&nbsp; 실제 **번들러**는 여러 JS파일을 하나로 합치는것 뿐만아니라 .jpg, .png, .sass 등등 여러 유형의 파일들을 하나로 합쳐줍니다.

**번들러**의 기본 개념은 위에서 말한것과 같지만 **번들링**이라는 처음의 작업을 해보니 이상의 무언가를 해보자 했을때 여러 유형의 작업을 하게되었습니다.

이러한 측면으로 보자면

<br/>

> "합치는 중에 필요없는 소스코드를 제거하면 어떨까?"
>
> "이미지도 최적화 시켜보고 소스코드를 난독화 하기위한 작업들도 해보면 어떨까?"

<br/>

여러 아이디어들로 현재의 **번들러**가 나오게 된것입니다.

또한 가장중요한 작업은 **트랜스파일러** 작업입니다.

<br/>

> "**번들링**중에 **모던 Javascript**를 `ES5`로 변환하는 **트랜스파일러**작업을 하면 어떨까?"
>
> "그러면 구형 브라우저에서도 최신의 스펙들을 사용할 수 있을텐데.."

<br/>

위와 같은 아이디어를 통해 **번들러**들은 **트랜스파일러** 작업 또한 **babel**과 연동하여 **ECMA2015**, **TS**, **React** 등을 지원하게됩니다.

## **🙏 웹팩과 바벨**

<br/>

&nbsp; 이제부터 간단하게 바벨과 웹팩을 셋팅하는 법을 알아보겠습니다.

<br/>

### **🔧 babel 설치하기**

---

<br/>

&nbsp; 먼저 바벨의 기본 모듈들을 설치합니다.

<br/>

```bash
yarn add @babel/core @babel/cli @babel/preset-env --dev
```

<br/>

모듈들의 역할은 아래와 같습니다.

- @babel/core : 바벨의 핵심 기능들을 포함
- @babel/cli : 터미널에서 바벨 명령어를 사용할 수 있게 도와줌
- @babel/preset-env : 코드 구문 변환 설정을 도와줌 (지원 브라우저 점유율, 호환성 설정 등)

<br/>

> **@babel/preset-env**은 함께 사용되어야하는 플러그인을 모아둔것이며.  
> 공식 Babel 프리셋은 아래와 같습니다.
>
> @babel/preset-env  
> @babel/preset-flow  
> @babel/preset-react  
> @babel/preset-typescript
>
> 원하는 다른 플러그인이 있다면 babel 공식 홈페이지에서 확인이 가능합니다.
>
> https://babeljs.io/docs/en/

<br/>

&nbsp; 모듈을 설치하였다면 .babelrc파일을 생성 후 `presets`를 작성합니다.

<br/>

```json
{
  "presets": ["@babel/preset-env"]
}
```

<br/>

### **📂 웹팩 설치하기**

---

<br/>

&nbsp; 웹팩 또한 모듈들을 설치합니다.

<br/>

```bash
yarn add webpack webpack-cli webpack-dev-server --dev
yarn add babel-loader style-loader css-loader --dev
yarn add html-webpack-plugin --dev
yarn add sass sass-loader --dev
```

<br/>

모듈들의 역할은 아래와 같습니다.

- webpack: 웹팩 모듈

- webpack-cli: 터미널에서 웹팩 명령어를 사용할 수 있게 도와줌

- webpack-dev-server: nodemon과 같이 웹팩 환경에서 개발서버를 생성

- babel-loader: 웹팩과 바벨을 연동

- css-loader: 웹팩이 css파일을 읽을 수 있도록 도와줌

- html-webpack-plugin: 번들링된 html파일에 css와 js파일들을 추가해줌

- sass-loader: 웹팩이 sass파일을 읽을 수 있도록 도와줌

<br/>

&nbsp; 모듈을 설치하였다면 webpack.config.js파일을 생성합니다.

<br/>

```js
//webpack.config.js
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "bundle.js",
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader",
        },
      },
      {
        test: /\.s?css$/,
        use: ["style-loader", "css-loader", "sass-loader"],
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: {
              minimize: true,
            },
          },
        ],
      },
    ],
  },

  devServer: {
    host: "localhost",
    port: 3000,
    open: true,
  },

  plugins: [
    new HtmlWebpackPlugin({
      template: "./index.html",
    }),
  ],
};
```

<br/>

&nbsp; 각각의 옵션에대한 설명은 아래와 같습니다.

<br/>

- mode: `production`, `development`, `none` 세가지 옵션을 사용할 수 있는데 사용한 옵션에 따라 웹팩에서 내부적으로 최적화를 해준다.

- entry: 번들링을 시작할 파일을 결정할 수 있다. 멀티 페이지 번들링시 여러 파일을 설정할 수 있다.

- module: 다양한 모듈들을 처리하는 방법들을 결정한다. js파일, ts파일을 포함한 이미지파일, 스타일 파일 등 웹팩을 통해 번들링 되는 모든 파일들의 처리 방법을 설정하며 좀전에 설정한 바벨 또한 이 곳에서 설정한다. module을 설정할 때 중요한 부분은 loader를 읽을때 오른쪽에서 왼쪽으로 loader가 실행되기 때문에 sass-loader의 경우 css-loader보다 오른쪽에 위치시켜야 한다. (typescript의 경우에는 babel-loader 오른쪽에 ts-loader를 위치시켜야 한다.)

- devServer: 개발 서버에 대한 설정을 할 수 있다. 에러처리, 포트 설정, 기본 path 등 여러 옵션을 설정할 수 있다.

- output: 웹팩을 통해 최종적으로 번들링 된 파일을 저장할 위치를 설정한다.

- plugins: 웹팩에 적용할 플러그인들을 설정한다.

<br/>

&nbsp; 추가적으로 `package.json`에 `scripts`를 작성합니다.

<br/>

```json
// package.json
{
  "name": "webpack",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "scripts": {
    "build": "webpack",
    "start": "webpack serve --mode development"
  },
  "devDependencies": {
    "@babel/cli": "^7.14.5",
    "@babel/core": "^7.14.5",
    "@babel/preset-env": "^7.14.5",
    "babel-loader": "^8.2.2",
    "css-loader": "^5.2.6",
    "html-loader": "^2.1.2",
    "html-webpack-plugin": "^5.3.1",
    "sass": "^1.34.1",
    "sass-loader": "^12.1.0",
    "style-loader": "^2.0.0",
    "webpack": "^5.38.1",
    "webpack-cli": "^4.7.2",
    "webpack-dev-server": "^3.11.2"
  }
}
```

<br/>

&nbsp; 다음 테스트를 위한 코드를 작성합니다.

<br/>

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>bundling</title>
  </head>
  <body>
    <h1 class="card-title">Card Title</h1>
    <button class="btn-change">버튼 변경</button>
  </body>
</html>
```

<br/>

```js
//src/btn.js
const btnChange = document.querySelector(".btn-change");
export { btnChange };
```

<br/>

```js
//src/color.js
const cardTitle = document.querySelector(".card-title");
const changeColor = function (color) {
  cardTitle.style.backgroundColor = color;
};
export { changeColor };
```

<br/>

```js
//src/index.js
import "../style.scss";
import { btnChange } from "./btn";
import { changeColor } from "./color";
btnChange.addEventListener("click", function () {
  changeColor("pink");
});
console.log("Hello World");
```

<br/>

```scss
//style.scss
body {
  background-color: #369fff;
}
```

<br/>

&nbsp; 이후 `build`와 `start`를 실행해보면 정상적으로 작동됨을 확인할 수 있습니다.
