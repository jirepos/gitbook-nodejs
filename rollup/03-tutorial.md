# Tutorial 


## Creating you first bundle 
#### 설치
```shell
npm install rollup --global
# or `npm i rollup -g` for short
```

You can now run the rollup command. Try it!

```shell
rollup
```


#### 간단한 프로젝트 생성
```shell
mkdir -p my-rollup-project/src
cd my-rollup-project
```

먼저 진입점이 필요합니다 . 이것을 src/main.js 파일에 붙여넣는다. 

```jsx
// src/main.js
import foo from './foo.js';
export default function () {
  console.log(foo);
}
```
foo.js 모듈을 만들자. 
```jsx
// src/foo.js
export default 'hello world!';
```

이제 번틀링할 준비가 되었다. 다음은 번들 파일은 생성하지 않고 출력만한다. 
```shell
rollup src/main.js -f cjs
```

* -f 은 --format의 약어 
어떤 종류의 번들을 생성할 것인지를 결정. 위 경우에는 CommonJS 모듈. 

번들을 저장할 수 있다. 
```shell
rollup src/main.js -o bundle.js -f cjs
```
다음 코드를 실행한다. 
```shell
node
> var myBundle = require('./bundle.js');
> myBundle();
'hello world!'
```


## Using Config files

프로젝트 루트에 rollup.config.js 파일을 만든다. 
```jsx
// rollup.config.js
export default {
  input: 'src/main.js',
  output: {
    file: 'bundle.js',
    format: 'cjs'
  }
};
```

CJS modules을 사용하고 module.exports = { /* config }는 것에 주의 해라. 




COnfig file을 사용하기 위해서 --config 또는 -c 옵션을 사용한다. 

```shell
rm bundle.js # so we can check the command works!
rollup -c
```

커맨드 라인 옵션으로 config file에 있는 어떤 옵션도 오버라이드 할 수 있다. 
```shell
rollup -c -o bundle-2.js # `-o` is equivalent to `--file` (formerly "output")
```

> 업 자체가 구성 파일을 처리하므로 export default구문 을 사용할 수 있습니다 . 코드는 Babel 또는 이와 유사한 것으로 변환되지 않으므로 Node.js 버전에서 지원되는 ES2015 기능만 사용할 수 있습니다. 

default  rollup.config.js 파일과는 다른 config file을 명시할 수 있다. 
```shell
rollup --config rollup.config.dev.js
rollup --config rollup.config.prod.js
```


## Installing Rollup locally 

With NPM 
```shell
npm install rollup --save-dev
```

Wtih Yarn
```shell
yarn -D add rollup
```

설치한 이후에 프로젝트 루트에서 Rollup은 실행될 수 있다. 
```shell
npx rollup --config
```

With Yarn
```shell
yarn rollup --config
```
일단 설치된 이후에 package.json에 build script를 추가하는 것이 일반적인 관례이다. 
```json
{
  "scripts": {
    "build": "rollup --config"
  }
}
```



## Using plugins
지금까지 진입점과 상대 경로를 통해 가져온 모듈에서 간단한 번들을 만들었다. 더 복잡한 번들을 빌드함에 따라 NPM과 함께 설치된 모듈 가져오기, Babel로 코드 컴파일, JSON 파일 작업 등 더 많은 유연성이 필요한 경우가 많다.

이를 위해 번들링 프로세스의 주요 지점에서 롤업의 동작을 변경하는 플러그인 을 사용 한다. 멋진 플러그인 목록은 Rollup Awesome List 에서 관리된다.


이 자습서에서는 @rollup/plugin-json 을 사용하여 Rollup이 JSON 파일에서 데이터를 가져올 수 있도록 한다. 

프로젝트 루트에 파일을 package.json만들고 다음 콘텐츠를 추가한다. 

```json
{
  "name": "rollup-tutorial",
  "version": "1.0.0",
  "scripts": {
    "build": "rollup -c"
  }
}
```

@rollup/plugihn-json을 개발 의존성에 설치한다. 
```shell
npm install --save-dev @rollup/plugin-json
```

우리는 코드가 실행될 때 실제로 플러그인에 의존하지 않기 때문에 --save가 아니라 --save-dev를 사용한다.  번들을 빌드할 때만 사용한다. 

src/foo.js 대신에 package.json을 import하기 위해서 src/main.js를 업데이트 한다. 
```jsx
// src/main.js
import { version } from '../package.json';

export default function () {
  console.log('version ' + version);
}
```

JSON 플러그인을 추가하기 위해서 rollup.config.js를 수정한다. 
```jsx
// rollup.config.js
import json from '@rollup/plugin-json';

export default {
  input: 'src/main.js',
  output: {
    file: 'bundle.js',
    format: 'cjs'
  },
  plugins: [json()]
};
```


npm run build로 Rollup을 실행한다. 결과는 다음과 같이 보일 것이다. 

```shell
'use strict';

var version = '1.0.0';

function main() {
  console.log('version ' + version);
}

module.exports = main;
```















