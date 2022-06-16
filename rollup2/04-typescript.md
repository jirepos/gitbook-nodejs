# Rollup에서 Typescript 번들링 

프로젝트 초기화

```shell
npm init -y
```

Rollup 설치 
```shell
npm -i -D rollup 
```
TypeScript 플러그인 설치 
```shell
 npm i -D typescript  rollup-plugin-typescript2
```

생성된 package.json
```json
{
  "name": "rollup",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "rollup": "^2.59.0",
    "rollup-plugin-typescript2": "^0.30.0",
    "typescript": "^4.4.4"
  }
}
```


rollup.config.js 파일 생성
```jsx
// rollup.config.js

import typescript from 'rollup-plugin-typescript2';

export default {
  input: './src/app.ts',
  output: {
    file: './dist/bundle.js',
    format: 'iife'
  },
  plugins: [
    typescript({
      tsconfig: 'tsconfig.json'
    })
  ]
}
```
package.json에 bundle 명령을 추가 
```json
// package.json

"scripts": {
  "bundle": "rollup -c"
}
```

tsconfig.json을 작성
```json
{
  "compilerOptions": {
    "target": "ES5", // "ESNext",
    "useDefineForClassFields": true,
    "module":  "ES2015",   // "ESNext",
    "lib": ["ESNext", "DOM"],
    "moduleResolution": "Node",
    "strict": true,
    "sourceMap": true,
    "resolveJsonModule": true,
    "esModuleInterop": true,
    "noEmit": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true
  },
  "include": ["./src"]
}

```
bundle 생성
```shell
npm run build 
```



## 설정2

한 번에 몇 개의 다른 관련없는 input들로부터 bundle들을 생성하기 위해서 config file로부터 array을 export할 수 있다. watch 모드에서 조차도 가능하다. 같은 input으로 다른 번들들을 생성하기 위해서, 각 input에 대한 output options의 배열을 제공한다.

```javascript
// rollup.config.js (building more than one bundle)

export default [{
  input: 'main-a.js',
  output: {
    file: 'dist/bundle-a.js',
    format: 'cjs'
  }
}, {
  input: 'main-b.js',
  output: [
    {
      file: 'dist/bundle-b1.js',
      format: 'cjs'
    },
    {
      file: 'dist/bundle-b2.js',
      format: 'es'
    }
  ]
}];
```


## References

[Rollup 공식사이트](https://rollupjs.org/guide/en/#creating-your-first-bundle)
