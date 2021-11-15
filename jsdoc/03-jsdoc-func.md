# 함수 주석
## 함수 주석

- @param을 사용하여 파라미터 주석
- {*} 을 사용하여 타입  설정
- @returns을 사용하여 리턴 할 내용 설명
- @throws를 사용하여 예외 설명

```jsx
/**
 * 원본 문자열에 덧 붙일 문자열을 합하여 반환한다. 
 * @param {string} src  원본문자열
 * @param {string} strToAppend  덧 붙일 문자열
 * @returns {string}
 *  합쳐진 문자열
 * @throws {CustomError} 널인 경우 오류를 던진다.
 */
function append(src, strToAppend) {
  //...
}
```

```jsx
/**
 * 함수 주석 
 * @returns {object} JSON 객체
 */
var toJSon = () => {
  //...
}
```