# 클래스 주석
### 클래스 주석

- 상속은 @extends 사용
- @class 태그는 사용하지 않아도 된다.
- @memberof는 사용하지 않는다.
- @constructor 사용하지 않는다.

[https://jsdoc.app/howto-es2015-classes.html](https://jsdoc.app/howto-es2015-classes.html)

> JSDoc 3을 사용하면 [ECMAScript 2015 사양](http://www.ecma-international.org/ecma-262/6.0/#sec-class-definitions) 을 따르는 클래스를 쉽게 문서화할 수 있습니다. 당신은 다음과 같은 태그를 사용할 필요가 없습니다 `@class`와 `@constructor`간단하게 코드를 분석하여 자동으로 식별 클래스와 자신의 생성자 ES 2015 클래스 - JSDoc과 함께합니다. ES 2015 클래스는 JSDoc 3.4.0 이상에서 지원됩니다.
> 

```jsx
/**
 * Class representing a dot.
 * @extends Point
 */
 class Dot extends Point {
  /**
   * Create a dot.
   * @param {number} x - The x value.
   * @param {number} y - The y value.
   * @param {number} width - The width of the dot, in pixels.
   */
  constructor(x, y, width) {
      // ...
  }

  /**
   * Get the dot's width.
   * @return {number} The dot's width, in pixels.
   */
  getWidth() {
      // ...
  }
}
```