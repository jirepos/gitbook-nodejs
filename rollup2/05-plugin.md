# 플러그인 설정

## 플러그인 설정

rollup 에 확장할 기능은 플러그인으로 추가할 수 있다. 그 중에 웹 개발에 필요한 몇 가지 도구를 설치하고 설정하는 작업을 진행한다.

* rollup-plugin-node-resolve : 외부 노드 모듈을 사용시 (node_modules 디렉토리)
* rollup-plugin-commonjs : 외부 노드 모듈이 es6 으로 변환되지 않았을 경우 es6 으로 변환
* rollup-plugin-browsersync : 번들 디렉토리의 변경사항을 웹브라우저에 반영
* rollup-plugin-generate-html-template : index.html에 번들 스크립트 추가하여 생성
* rollup-plugin-babel : babel 변환 지원
* rollup-plugin-postcss : postcss 도구 지원
* rollup-plugin-eslint : 코드 스타일 검사
* rollup-plugin-uglify : 번들 파일 난독화

### 빌드 플러그인

플러그인을 설치한다.

```
npm i rollup-plugin-browsersync rollup-plugin-generate-html-template
```

rollup.config.js에 플러그인 설정을 추가한다.

```javascript
import browsersync from 'rollup-plugin-browsersync'
import html from 'rollup-plugin-generate-html-template'

export default {
   input : 'src/index.js',
   output : {
     file : 'dist/bundle.js',
     format : 'umd'
   },
   plugins : [
     browsersync({
        server : 'dist'
     }),
     html({
       template : 'src/index.html',
       target : 'dist/index.html'
     })
   ]
}
```

index.html을 생성한다.

```markup
<!doctype html>
<html lang="ko">
<head><meta charset="utf-8"><title>hello rollup</title></head>
<body>
</body>
</html>
```

빌드 후 'hello rollup'이 브라우저에 출력되는지 확인한다.

```
npm run build
```

index.js 수정한 후 저장할 때마다 브라우저에 수정 사항이 반영되는지 확인한다.

### 외부 모듈 변환 플러그인

플러그인을 설치한다.

```
npm i rollup-plugin-node-resolve rollup-plugin-commonjs
```

플러그인 설정을 추가한다.

```javascript
import resolve from 'rollup-plugin-node-resolve';
import commonjs from 'rollup-plugin-commonjs';
default export {
 ...
    plugins : [
     ...
        resolve(),
        commonjs({
            include : 'node_modules/**'
        }),
}
```

### Babel 변환 플러그인

플러그인과 babel7을 설치한다.

```
$ npm i @babel/core @babel/cli @babel/preset-env
$ npm i @babel/plugin-transform-runtime regenerator-runtime
$ npm i rollup-plugin-babel
```

babel 설정을 추가한다. .babelrc 파일을 생성한 다음에 다음을 추가한다.

```javascript
{
    "presets" : [
        [ "@babel/env", {
            modules : false,
            useBuiltIns : "usage",
            corejs : 3
        }]
    ]
}
```

rollup 플러그인 설정을 추가한다.

```javascript
import babel from 'rollup-plugin-babel';
default export {
 ...
    plugins : [
     ...
     babel({
            exclude : 'node_modules/**'
        }),
}
```

테스트용 index.js을 다시 작성한다.

```javascript
const text  = 'rollup';
async function say() {
    return `Hello ${text} async`;
}
const main = async () => {
    const message = await say();
    document.body.textContent = message;
    console.log(message);
}
main().catch(console.error)
```

빌드 후 ‘Hello rollup async’이 브라우저에 출력되는지 확인한다..

### CSS 플러그인

플러그인과 기본 css를 설치한다.

```
$ npm i rollup-plugin-postcss postcss-import autoprefixer
$ npm i reset-css normalize.css
```

플러그인 설정을 추가한다.

```javascript
import cssimport from 'postcss-import';
import autoprefixer from 'autoprefixer';
import postcss from 'rollup-plugin-postcss'

default export {
    plugins : [
     ...
     postcss({
            plugins : [ cssimport(), autoprefixer() ]
     })        
}
```

변환시 지원할 브라우저를 지정한다. package.json에 다음을 추가한다.

```javascript
{ ...
  },
  "browserslist": [
    "defaults"
  ]
}
```

테스트 css를 작성한다.

```css
// src/index.css

@charset "utf-8";
@import "reset-css";
@import "normalize.css";
* {
    box-sizing: border-box;
}
body {
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    color: #333;
    background-color: #f0f3f4;
}
li { list-style: none; }
a { text-decoration: none; }
.hello {
    font-size: 17px;
}
.test-autoprefixer {
    display: grid;
    transition: all .5s;
    user-select: none;
    background: linear-gradient(to bottom, white, black);
}
```

테스트 파일을 다시 작성한다.

```javascript
// src/index.js
import style from './index.css';
   const text  = 'rollup';
   async function say() {
   return `Hello ${text} async`;
}
   const main = async () => {
   const message = await say();
   console.log(message);
   const body = document.querySelector("body");
   const greeting = document.createElement("div");
   greeting.innerText = message;
   greeting.classList.add("hello");
   body.appendChild(greeting);
   console.log(greeting.outerHTML);
   const test = document.createElement("div");
   test.innerText = "Test prefixer";
   test.classList.add("test-autoprefixer");
   body.appendChild(test);
   console.log(test.outerHTML);
}
   main().catch(console.error)
```

빌드 후 ‘Test prefixer’가 브라우저에 출력되는지 확인한다.

```
npm run build
```
