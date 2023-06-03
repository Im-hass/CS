## null과 undefiend의 차이

> **null :** 개발자가 의도적으로 값이 비어있음을 명시해 주는 값. 즉 빈 값을 할당하는 것.
> 
> **undefiend :** 자바스크립트 엔진에 의해 자동으로 할당되는 값. 즉 변수를 선언만 하고 값을 할당하지 않은 것.

- `typeof`를 통해 확인해 보면, `null`은 `object`가 출력되고 `undefiend`는 `undefiend`가 출력된다.
- `undefined == null`은 `true`이다.