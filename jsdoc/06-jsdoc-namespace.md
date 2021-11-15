# Namespace

ES6의 모듈 시스템과는 별개로 이름공간을 만들어 클래스나 함수 등을 그룹화 할 필요가 있다. 

- @namespace 태그 사용

## 기초

Tools라는 namespace가 생기고 hammer는 Tools namespace의 member가 된다. 

```jsx
/** @namespace */
var Tools = {};

/** @memberof Tools */
var hammer = function() {
};
```

Dot 클래스는 Tools라는 이름 이름 공간의 멤버가 된다.  getWidth()는 Dot 클래스의 멤버로 표시된다.

> class의 멤버는 @memberof를 쓰면 문서에서 제외된다. 사용하지 않는다.
> 

@memberof를 사용하여 Tools라는 이름 공간의 클래스임을 나타낸다. 

```jsx
/**
 * Class representing a dot.
 * @memberof Tools
 * @extends Point
 */
 class Dot extends Point {
}
```

다음과 같이 하면 Tools라는 namespace가 생긴다. 

```jsx
/** @namespace Tools */
```

그러면 Dot class는 Tools라는 namespace의 클래스가 된다. 

```jsx
/** @namespace Tools */

/**
 * Class representing a dot.
 * @memberof Tools
 * @extends Point
 */
 class Dot extends Point {
}
```

## 디렉터리 이름 공간 만들기

자바와 같은 패키지 구조로 디렉터리 들을 만든다. 

```jsx
📁project root
   📁com
      📁sogood
         📁common
         📁biz

```

각 디렉터리에 빈 파일을 각각 만든다.  이름은 관계 없지만 디렉터리 명과 같게 만든다. 

```jsx
📁project root
   📁com
      📄com.js
      📁sogood
         📄sogood.js
         📁common
            📄common.js
         📁biz
            📄biz.js

```

각각의 파일에  dot(.)을 사용하여 계층적인 이름 공간을 만든다. 

```jsx
// com.js
/** @namespace com */
```

```jsx
// sogood.js
/** @namespace com.sogood */
```

```jsx
// common.js
/** @namespace com.sogood.common */
```

```jsx
// biz.js
/** @namespace com.sogood.biz */ 
```

biz 디렉터리에 Dot.class를 만든다면 @memberof 태그를 사용하여 이름 공간을 설정한다. 

```jsx
/**
 * Class representing a dot.
 * @memberof com.sogood.biz
 */
 class Dot extends Point {

 }
```