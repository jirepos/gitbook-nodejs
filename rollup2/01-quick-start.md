# Quick Start 

롤업은 작은 코드 조각을 라이브러리나 애플리케이션과 같이 더 크고 복잡한 것으로 컴파일하는 JavaScript용 모듈 번들러입니다. CommonJS 및 AMD와 같은 이전의 독특한 솔루션 대신 JavaScript의 ES6 개정판에 포함된 코드 모듈에 대해 새로운 표준화된 형식을 사용합니다. ES 모듈을 사용하면 즐겨찾는 라이브러리에서 가장 유용한 개별 기능을 자유롭고 원활하게 결합할 수 있습니다. 이것은 결국 모든 곳에서 기본적으로 가능하지만 오늘 롤업을 사용하면 가능합니다.


Webpack의 문제점이자 Rollup의 사용하게된 계기는 다음과 같다.
* Webpack은 ESM(ES Module)형태의 번들이 불가능하다.
* Webpack에서 빌드할 시 중복 코드 제거가 되지 않는다.
* Webpack에서 빌드할 시 기본 용량이 크다.
* Webpack3에서 Tree Shaking이 잘 이루어지지 않는다.


Rollup을 사용하면 뭐가 좋을까?

**ESM형태로 번들이 가능**
Tree Shaking 조건은 코드가 ESM형태여야 하지만 Webpack은 ESM형태로 번들할 수 없기 때문에 각각의 파일로 변환해야 한다. Rollup 은 여러 모듈(파일)을 한 모듈로 합치면서 ESM 형태로 번들이 가능하다. 이를 통해 개별 파일로 배포하는 것보다 파일 하나로 통합되기 때문에 관리 및 사용 편의성도 높아진다.

**중복코드 제거**
모듈간의 import/export과정이 사라지기 때문에 중복되는 코드가 
제거

**Webpack3에서도 Tree Shaking이 잘 된다**
Webpack3에서 Tree Shaking이 되지 않는 이유 중 하나는 import한 모듈을 사용한 함수를 사용하지 않는 경우다.






## Installation

```shell
npm install --global rollup
```



## For browsers
브라우저에서 사용하기 위해 즉시 실행 함수(iife)로 변환 

```shell
# compile to a <script> containing a self-executing function ('iife')
rollup main.js --file bundle.js --format iife
```
main.js
```javascript
console.log("hello")
```
bundle.js
```javascript
(function () {
	'use strict';

	console.log("hello");

})();
```


# For Node.js
```shell
# compile to a CommonJS module ('cjs')
rollup main.js --file bundle.js --format cjs
```

bundle.js
```
'use strict';

console.log("hello");
```

# For both browsers and Node.js
```shell
# UMD format requires a bundle name
rollup main.js --file bundle.js --format umd --name "myBundle"
```

bundle.js

```javascript
(function (factory) {
	typeof define === 'function' && define.amd ? define(factory) :
	factory();
})((function () { 'use strict';

	console.log("hello");

}));
```


## Why
롤업을 사용하면 새 모듈 시스템을 사용하여 코드를 작성한 다음 CommonJS 모듈, AMD 모듈 및 IIFE 스타일 스크립트와 같은 기존 지원 형식으로 다시 컴파일할 수 있습니다. 즉 , 미래 보장 코드 를 작성 하고 다음과 같은 엄청난 이점도 얻을 수 있습니다.



## Tree-shaking

ES 모듈의 사용을 활성화하는 것 외에도 Rollup은 가져오는 코드를 정적으로 분석하고 실제로 사용되지 않는 모든 것을 제외합니다. 이를 통해 추가 종속성을 추가하거나 프로젝트 크기를 부풀리지 않고 기존 도구 및 모듈을 기반으로 빌드할 수 있습니다.

예를 들어 CommonJS에서는 전체 도구 또는 라이브러리를 가져와야 합니다.
```javascript
// import the entire utils object with CommonJS
const utils = require('./utils');
const query = 'Rollup';
// use the ajax method of the utils object
utils.ajax(`https://api.example.com?search=${query}`).then(handleResponse);
```

ES 모듈을 사용하면 전체 utils객체 를 가져오는 대신 ajax필요한 기능 하나만 가져올 수 있습니다 .

```javascript
// import the ajax function with an ES6 import statement
import { ajax } from './utils';
const query = 'Rollup';
// call the ajax function
ajax(`https://api.example.com?search=${query}`).then(handleResponse);
```

Rollup에는 최소한의 기능만 포함되어 있기 때문에 더 가볍고 빠르며 덜 복잡한 라이브러리와 응용 프로그램이 만들어집니다. 이 접근 방식은 명시적 import및 export문을 사용할 수 있으므로 컴파일된 출력 코드에서 사용되지 않는 변수를 감지하기 위해 단순히 자동화된 축소기를 실행하는 것보다 더 효과적입니다.

## 호환성
### CommonJS 가져오기
롤업은 플러그인을 통해 기존 CommonJS 모듈 을 가져올 수 있습니다 .

###  ES 모듈 게시
Node.js 및 webpack과 같은 CommonJS와 함께 작동하는 도구에서 ES 모듈을 즉시 사용할 수 있도록 하려면 Rollup을 사용하여 UMD 또는 CommonJS 형식으로 컴파일한 다음 파일 의 main속성을 사용하여 컴파일된 버전을 가리킬 수 package.json있습니다. 귀하의 경우 package.json파일도이 module필드를 롤업과 같은 ES-모듈 인식 도구 웹팩 2+는 것이다 배아 줄기 모듈 버전을 가져 직접.


