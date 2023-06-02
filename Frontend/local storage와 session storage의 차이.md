## local storage와 session storage의 차이

> **브라우저 저장소**로, LocalStorage와 SessionStorage가 있습니다.
>
> **LocalStorage :** 영구적 보관
>
> **SessionStorage :** 브라우저가 종료되면 데이터도 삭제됨 ⇒ 같은 세션만 사용 가능.

- 키(key)와 값(value)을 하나의 세트로 저장한다.

- 값은 문자열로 저장된다.

- 도메인과 브라우저 별로 저장된다.

|  | LocalStorage | SessionStorage |
| --- | --- | --- |
| Origin(프로토콜, 도메인, 포트) | Origin이 같은 탭, | Origin이 같은 탭,
| |브라우저 전체에 공유 | 브라우저,
||| iframe에서 공유 |
| 새로고침 | 데이터 유지 | 데이터 유지 |
| 데이터 제거 | 직접 제거 | 탭, 브라우저 종료 시 제거됨 |


