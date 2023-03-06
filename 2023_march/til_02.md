
---

🍎 새로 알게된 사실 혹은 알고 있던 사실에대한 질문, 답변

생각해보기

🍎 auto increment가 pK 로 존해할 필요가 있을까?

🍎 Test slicing 이란 무엇인가?

🍎 REACT는 부모에서 자식으로 단방향뿐 존재하지 않는다.

🍊 What is components, props, state?

❓ JS 화살표 함수는 무엇인가요?

→ JS의 화살표 함수는 전통적인 함수표현의 간편한 대안입니다. 하지만, 화살표 함수는 몇 가지 제한점이 있고 모든 상황에 사용할 수는 없습니다. 자바에서 사용하는 FP와 느낌이 비슷합니다.

❓ JS Class는 무엇인가요?

→ Class는 객체를 생성하기 위한 템플릿입니다. 클래스는 데이터와 이를 조작하는 코드를 하나로 추상화합니다. JS에서 클래스는 prototype을 이용해서 만들어졌지만 ES5의 클래스 의미와는 다른 문법과 의미를 가집니다.

→ class 표현식 and class 선언 두 가지 방법을 제공합니다.

#### Class 선언
```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

#### Class 표현식
```js
// unnamed
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// 출력: "Rectangle"

// named
let Rectangle = class Rectangle2 {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// 출력: "Rectangle2"

```

🍎 let 명령문은 블록 스코프의 범위를 가지는 지역 변수를 선언합니다. 프로그램 최상위에서 사용할 경우 var는 전역 객체에 속성을 추가하지만 let은 추가하지 않습니다.

🍎 const 선언은 블록 범위의 상수를 선언합니다. 상수의 값은 재할당할 수 없으며 다시 선언할 수도 없습니다. 초기값을 생략하면 안됩니다.

❓ React란 무엇인가요?

→ React는 사용자 인터페이스를 구축하기 위한 선언적이고 효율적이며 유연한 JS Library입니다. **컴포넌트**라고 불리는 작고 고립된 코드의 파편을 이용하여 복잡한 UI를 구성하도록 돕습니다.

→ 컴포넌트를 사용하여 React에게 화면에 표현하고 싶은 것이 무엇인지 알려줍니다. 데이터가 변경될 때 React는 컴포넌트를 효율적으로 업데이트하고 다시 렌더링합니다.

→ React JSX 문법에서 \<div \/> 구문은 빌드하는 시점에서 React.createElement('div')로 변환됩니다.

~~~react
<div className="shopping-list">

to

return React.createElement('div', {className: 'shopping-list'}
~~~