# 설정2

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
