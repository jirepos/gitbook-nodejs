# build하기
JavaScript 파일 하나만 빌드하려면 다음과 같이 간단히 할 수 있다 

```jsx
yarn jsdoc test.js
```

## 실행 옵션

| 옵션| 설명 |
|--|--|
|-t, --template <value>	|문서 생성 시 사용할 템플릿 명을 설정 한다. 기본 값은 default 이다.|
|-c, --configure <value>|	설정 파일 정보를 이용하여 문서를 생성한다. 설정 파일 샘플은 같은 폴더 안에 있는 conf.json.EXAMPLE 파일이다.|
|-e, --encoding <value>	|스크립트 소스파일을 읽을 때 인코딩을 설정 한다. 기본 값은 utf8 이다.|
|-d, --destination <value>|	문서 생성 경로이다. 기본 값은 JSDOC 폴더 안에 out 폴더이다.|
|-r, --recurse	소스 파일 폴더 안에 여러 폴더가 있을 경우 이 옵션을 사용할 경우 사용자가 입력한 소스 파일 폴더 안에 있는 모든 스크립트 파일을 문서화 한다. 옵션을 주지 않을 경우 하위 폴더 안에 있는 스크립트는 문서화 하지 않는다.|
|-u, --tutorials <value>|	듀토리얼 파일이 있는 폴더를 설정한다. 옵션을 주지 않으면 듀토리얼 문서는 생성되지 않는다.|
|-p, --private	|기본 옵션으로 @private 태그로 되어 있는 것은 문서에 포함 시키지 않는다. 이 옵션을 사용하면 @private 태그가 있는 것들도 문서에 포함 시킨다.|
|-l, --lenient|	기본 적으로 소스파일 파싱 시 오류가 발생할 경우 문서 생성을 중단하고 오류를 사용자에게 보여 준다. 이 옵션을 사용할 경우 오류가 발생해도 문서 생성을 멈추지 않는다.|
|-X, --explain <value>|	모든 문서에 대해 덤프 정보를 콘솔에 표시하고 종료 합니다.|
|-h, --help|	도움말을 표시 한다.|
|--version|	버전 정보를 표시 한다.|
|-T, --test	|JSDOC 테스트를 실행 하고 결과를 콘솔에 표시 한다.|



## 설정 파일 사용

conf.json이라는 설정 파일을 만든다.  설정 파일 샘플은 jsdoc 폴더 안에 있다. 

```jsx
📁project root
   📁node_modules
      📁jsdoc
         conf.json.EXAMPLE
```

샘플 파일의 내용은 다음과 같다. 

```jsx
{
    "tags": {
        "allowUnknownTags": true
    },
    "source": {
        "includePattern": ".+\\.js(doc|x)?$",
        "excludePattern": "(^|\\/|\\\\)_"
    },
    "plugins": [],
    "templates": {
        "cleverLinks": false,
        "monospaceLinks": false,
        "default": {
            "outputSourceFiles": true
        }
    }
}
```

## 설정하기

conf.json 파일을 프로젝트 루트에 생성한다.

```jsx
📁project root
   conf.json
```

 다음과 같이 입력한다.

```jsx
{
  "tags": {
      "allowUnknownTags": true
  },
  "source": {
      "include": [ "src"],
      "includePattern": ".+\\.js(doc|x)?$",
      "excludePattern": "(^|\\/|\\\\)_"
  },
  "plugins": [],
  "templates": {
      "cleverLinks": false,
      "monospaceLinks": false,
      "default": {
          "outputSourceFiles": true
      }
  },
  "opts": {
    "encoding": "utf8",               
    "destination": "./out/",          
    "recurse": true,                  
  }  
}
```

다음을 입력하여 실행한다. 

```jsx
yarn jsdoc -c conf.json
```

매번 입력하기 귀찮으니 package.json 파일을 열고 build 스크립트를 추가한다. 

```jsx
{
  "name": "html5",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "scripts": {
    "build": "jsdoc -c conf.json"
  },  
  "devDependencies": {
    "docdash": "^1.2.0",
    "jsdoc": "^3.6.7"
  }
}
```

이제 커맨드 창에서 다음과 같이 입력하여 빌드할 수 있다. 

```jsx
yarn build
or
npm run build
```

## 참고

[https://jsdoc.app/about-configuring-jsdoc.html](https://jsdoc.app/about-configuring-jsdoc.html)