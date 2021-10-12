# 설치

Rollup도 Webpack과 마찬가지로 크고 복잡한 코드의 모듈(파일)들을 라이브러리나 어플리케이션으로 작게 만들어 주는 번들러이다.

Webpack의 문제점이자 Rollup의 사용하게된 계기는 다음과 같다.

* Webpack은 ESM(ES Module)형태의 번들이 불가능하다.
* Webpack에서 빌드할 시 중복 코드 제거가 되지 않는다.
* Webpack에서 빌드할 시 기본 용량이 크다.
* Webpack3에서 Tree Shaking이 잘 이루어지지 않는다.

Rollup을 사용하면 뭐가 좋을까?

**ESM형태로 번들이 가능**\
Tree Shaking 조건은 코드가 ESM형태여야 하지만 Webpack은 ESM형태로 번들할 수 없기 때문에 각각의 파일로 변환해야 한다. Rollup 은 여러 모듈(파일)을 한 모듈로 합치면서 ESM 형태로 번들이 가능하다. 이를 통해 개별 파일로 배포하는 것보다 파일 하나로 통합되기 때문에 관리 및 사용 편의성도 높아진다.

**중복코드 제거**\
모듈간의 import/export과정이 사라지기 때문에 중복되는 코드가 제거

**Webpack3에서도 Tree Shaking이 잘 된다**\
Webpack3에서 Tree Shaking이 되지 않는 이유 중 하나는 import한 모듈을 사용한 함수를 사용하지 않는 경우다.

## 설치 및 프로젝트 생성

rollup-test 폴더를 만든다.

```
mkdir rollup-test
cd rollup-test
```

Node.js 프로젝트를 생성한다. 모두 엔터를 입력한다.

```
npm init
```

rollup을 설치한다.

```
npm install -D rollup
```

### rollup.config.js

rollup.config.js 파일을 생성하고 다음을 입력한다

```javascript
default export {
  input: './src/index.js',
  output: {
    file: './dist/bundle.js',
    format: 'umd'
  }
};
```

### index.js 파일 생성

index.js 파일을 src 디렉토리에 생성한다.

```javascript
document.body.textContent = 'hello rollup';
```

### 빌드 작업 생성

package.json 파일을 열고 다음을 입력한다.

```javascript
"scripts": {
    "build": "rollup -c"
}
```

### build하기

터미널에 다음을 입력하여 번들이 생성되는지 확인한다.

```
npm run build
```

## References

[Rollup 웹개발 시작하기](https://medium.com/@feedbotstar/rollup-js-%EC%9B%B9%EA%B0%9C%EB%B0%9C-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-82013b364b1e)
