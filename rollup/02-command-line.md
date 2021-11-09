# Command Line Interface


## Configuration Files 
롤업 구성 파일은 선택 사항이지만 강력하고 편리하므로 권장 됩니다. 구성 파일은 원하는 옵션과 함께 기본 개체를 내보내는 ES 모듈입니다.

```javascript
export default {
  input: 'src/main.js',
  output: {
    file: 'bundle.js',
    format: 'cjs'
  }
};
```

일반적으로 호출 rollup.config.js되어 프로젝트의 루트 디렉터리에 위치합니다. 롤업은 일반적으로 요구하기 전에 이 파일과 관련 종속성을 CommonJS로 트랜스파일 및 번들링합니다. 이는 노드 생태계와 완전한 상호 운용성을 유지하면서 ES 모듈 코드 기반과 코드를 공유할 수 있다는 장점이 있습니다.


* rollup.config.js는 프로젝트의 루트 디렉터리에 위치
* 파일과 관련 종속성을 CommonJS로 트랜스파일 및 번들링


TypeScript와 같은 구성 파일에 다른 언어를 사용할 수도 있습니다. 그렇게 하려면 다음과 같은 해당 롤업 플러그인 @rollup/plugin-typescript을 설치하고  --configPlugin옵션을 사용하세요 .

설치 먼저 
```shell
 npm i -D typescript  rollup-plugin-typescript2
```

다음과 같이 사용하여 번들을 만든다. 

```shell
rollup --config rollup.config.ts --configPlugin typescript
```



구성 파일과 함께 롤업을 사용하려면 --config또는 -c플래그를 전달합니다 .


```shell
# pass a custom config file location to Rollup
rollup --config my.config.js
```

기본적으로 명령줄 인수는 항상 구성 파일에서 내보낸 각 값을 재정의합니다. 이 동작을 변경하려면 commandLineArgs개체 에서 명령줄 인수를 삭제하여 Rollup이 명령줄 인수를 무시하도록 할 수 있습니다 .


--configPlugin옵션을 통해 TypeScript에서 구성을 직접 작성할 수도 있습니다 .



--configPlugin <plugin>
롤업 플러그인을 지정하여 구성 파일의 구문 분석을 변환하거나 제어할 수 있습니다. 주요 이점은 JavaScript가 아닌 구성 파일을 사용할 수 있다는 것입니다. 예를 들어 다음을 사용하면 @rollup/plugin-typescript설치한 경우 TypeScript에서 구성을 작성할 수 있습니다 .


```shell
rollup --config rollup.config.ts --configPlugin @rollup/plugin-typescript
```




## References
[https://rollupjs.org/guide/en/](https://rollupjs.org/guide/en/)
