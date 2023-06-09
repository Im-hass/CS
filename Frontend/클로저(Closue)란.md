## 클로저(Closure)란?
> **상위 스코프의 식별자를 참조하고, 상위 스코프의 생명 주기보다 긴 생명 주기를 갖는 중첩 함수**

- 외부 함수보다 중첩 함수가 더 오래 유지되는 경우 중첩 함수는 이미 생명 주기가 종료한 외부 함수의 변수를 참조할 수 있다. 이러한 중첩 함수를 클로저라고 부른다.

  ⇒ 이미 생명 주기가 종료된 외부 함수의 변수를 참조하는 중첩 함수.

- 클로저는 함수와 그 함수가 선언된 렉시컬 환경과의 조합이다(MDN 정의).

  "그 함수가 선언된 렉시컬 환경"이란 함수가 정의된 위치의 스코프(상위 스코프)를 의미하는 실행 컨텍스트의 렉시컬 환경을 말한다.

- **예제**
  ```javascript
  const x = 1;

  // ①
  function outer() {
    const x = 10;
    const inner = function () {
      console.log(x); // ②
    };
    return inner;
  }

  // outer 함수를 호출하면 중첩 함수 inner를 반환한다.
  // 그리고 outer 함수의 실행 컨텍스트는 실행 컨텍스트 스택에서 팝되어 제거된다.
  const innerFunc = outer(); // ③
  innerFunc(); // ④

  // OUTPUT : 
  //10
  ```
  - outer 함수를 호출(③)하면 outer 함수는 중첩 함수 inner를 반환하고 생명 주기를 마감한다.
  
      즉, outer 함수의 실행이 종료되면 outer 함수의 실행 컨텍스트는 실행 컨텍스트 스택에서 제거된다.

  - 이때 outer 함수의 지역 변수 x와 변수 10을 저장하고 있던 outer 함수의 실행 컨텍스트가 제거되었으므로 outer 함수의 지역 변수 x 또한 생명 주기를 마감한다.
  
      따라서 outer 함수의 지역 변수 x에 접근할 수 있는 방법은 달리 없어 보인다.
  
  - 그러나 아래 코드의 실행 결과(④)는 outer 함수의 지역 변수 x의 값인 10이다.

    이처럼 외부 함수보다 중첩 함수가 더 오래 유지되는 경우, 중첩 함수는 이미 생명 주기가 종료한 외부 함수의 변수를 참조할 수 있다. 이러한 중첩 함수를 클로저라고 부른다.

<br />

### 📌 클로저가 되기 위한 조건

> 자바스크립트의 모든 함수는 상위 스코프를 기억하므로 **이론적으로 모든 함수는 클로저**다. 하지만 일반적으로 모든 함수를 클로저라고 하지는 않는다.

1. **중첩 함수가 상위 스코프의 식별자를 참조해야 한다.**
  
    상위 스코프의 식별자를 참조하지 않는다면 대부분의 모던 브라우저는 최적화를 통해 상위 스코프를 기억하지 않는다. 참조하지도 않는 식별자를 기억하는 것은 메모리 낭비이기 때문이다.

2. **외부 함수의 외부로 중첩 함수가 반환 되어야 한다.**

    즉, 외부 함수보다 중첩 함수의 생명 주기가 길어야 한다.

    외부 함수보다 일찍 소멸될 경우, 생명 주기가 종료된 외부 함수의 식별자를 참조할 수 있다는 클로저의 본질에 부합하지 않기 때문이다.

- **예제 : 클로저가 아닌 것**

  ```javascript
  function foo() {
    const x = 1;
    const y = 2;

    function bar() { // 상위 스코프의 식별자를 참조하지 않기 때문에 일반적으로 클로저라고 하지 않는다.
      const z = 3;

      console.log(z);
    }

    return bar;
  }

  const bar = foo();
  bar();
  ```

- **예제 : 클로저가 아닌 것**

  ```javascript
  function foo() {
    const x = 1;

    // 클로저였지만 곧바로 소멸한다.
    function bar() {
      console.log(x); // 상위 스코프의 식별자를 참조한다.
    }

    bar();
  }

  foo();
  ```

- **예제 : 클로저**

  ```javascript
  function foo() {
    const x = 1;
    const y = 2;

    function bar() { // 클로저
      console.log(x);
    }

    return bar;
  }

  const bar = foo();
  bar();
  ```

<br />

### 📌 클로저의 활용

<br />

### 📌 클로저 사용 시, 발생하는 실수

<br />
<br />

## 📌 참고
- **모던 자바스크립트 Deep Dive**


