# JavaScript & TypeScript 핵심 개념 정리

---

## 1. Sync vs Async

- **Sync(동기)**: 요청을 보내고 응답이 올 때까지 기다리는 방식. 순차적으로 처리됨.  
  - 예: `alert()`
- **Async(비동기)**: 요청을 보낸 뒤 응답을 기다리지 않고 다음 작업 실행. UI 블로킹 최소화.  
  - 예: `setTimeout()`, `fetch()`

---

## 2. Blocking vs Non-Blocking

- **Blocking**: 작업 완료 전까지 제어권이 해당 작업에 묶임. 다음 작업은 대기.  
- **Non-Blocking**: 작업 완료 여부와 상관없이 다음 작업 수행 가능. 이벤트 큐로 처리.

---

## 3. Callback & Callback Hell

- **Callback**: 함수의 인자로 전달되어 특정 이벤트나 작업 후 실행되는 함수.  
- **Callback Hell**: 콜백 중첩으로 코드 가독성이 떨어지는 현상.  
  - **해결**: 함수 분리, Promise, Async/Await

---

## 4. Event Loop

- JS의 비동기 처리 핵심 메커니즘. 단일 스레드 기반.  
- **구성요소**: Call Stack, Microtask Queue(Promise, async/await), Macrotask Queue(setTimeout 등)  
- **동작**: Call Stack → Microtask → Macrotask 순으로 처리

---

## 5. Promise vs Async/Await

- **Promise**: 비동기 작업 결과 처리 객체. `.then()`, `.catch()` 사용  
- **Async/Await**: Promise 기반 동기형 코드 작성 가능, `try/catch`로 에러 처리

---

## 6. map vs forEach

| 구분 | map | forEach |
|------|-----|---------|
| 반환 | 새로운 배열 | 없음 |
| 원본 변경 | ❌ | 가능 |
| 체이닝 | 가능 | 불가능 |

---

## 7. var, let, const

| 키워드 | 스코프 | 재선언 | 재할당 | 특징 |
|--------|--------|---------|---------|------|
| var    | 함수   | 가능    | 가능    | 호이스팅 시 초기값 `undefined` |
| let    | 블록   | 불가    | 가능    | TDZ 존재 |
| const  | 블록   | 불가    | 불가    | TDZ 존재 |

---

## 8. 메서드 체이닝

- 자기 자신(this) 또는 객체를 반환해 연속 호출 가능  
- 장점: 코드 간결, 단점: 에러 발생 위치 확인 어려움  
- 예: `array.map().filter().reduce()`

---

## 9. 일반 함수 vs 화살표 함수

- **일반 함수**
  - this: 호출 방식에 따라 동적 바인딩  
  - arguments 사용 가능  
  - new로 생성자 사용 가능
- **화살표 함수**
  - this: 상위 스코프(Lexical this)  
  - arguments 없음  
  - 생성자로 사용 불가

---

## 10. this

- 자신이 속한 객체 또는 생성된 인스턴스 참조  
- 호출 방식에 따라 바인딩:  
  1. 생성자 함수 → 인스턴스  
  2. call/apply/bind → 명시적 객체  
  3. 객체 메서드 → 해당 객체  
  4. 일반 함수 → 전역 객체  
  5. 화살표 함수 → 선언 시점 상위 this

---

## 11. 함수 선언식 vs 함수 표현식

- **선언식**: 호이스팅 가능, 선언 전 호출 가능  
- **표현식**: 선언 후 호출 가능, 변수 호이스팅만 발생

---

## 12. 호이스팅

- 변수/함수 선언이 스코프 최상단으로 끌어올려지는 것처럼 보이는 현상  
- let/const는 TDZ 때문에 선언 전 접근 불가, 함수 선언식은 전체 호이스팅

---

## 13. 이벤트 버블링 & 캡처링

- **버블링**: 이벤트 하위 → 상위 요소 순 전파  
- **캡처링**: 상위 → 하위 요소 순 전파

---

## 14. 이벤트 전파 & 이벤트 위임

- **전파**: Capturing → Target → Bubbling  
- **위임**: 하위 요소 이벤트 대신 상위 요소에서 처리

---

## 15. Closure(클로저)

- 함수가 선언 당시 스코프를 기억  
- 외부에서도 해당 스코프 접근 가능  
- 캡슐화/상태 은닉에 활용

---

## 16. Lexical Scope & Lexical Environment

- **Lexical Scope**: 선언 위치 기준 상위 스코프 결정  
- **Lexical Environment**: 변수, 값, 스코프 체인 정보를 담는 구조

---

## 17. 실행 컨텍스트

- 코드 실행 환경  
- 구성: Variable Environment, Lexical Environment, ThisBinding  
- Call Stack으로 관리

---

## 18. 스코프 & 스코프 체인

- **스코프**: 변수 접근 범위  
- **스코프 체인**: 현재 → 상위 스코프 순 탐색

---

## 19. 프로토타입 & 프로토타입 체인

- **프로토타입**: 객체가 상속받는 기본 구조  
- **체인**: 객체에 프로퍼티 없으면 부모 탐색

---

## 20. 깊은 복사 vs 얕은 복사

- **얕은 복사**: 참조 값만 복사, 원본 영향 가능  
- **깊은 복사**: 새로운 메모리 생성, 독립적

---

## 21. Destructuring

- 배열/객체 값을 해체하여 변수에 바로 할당

---

## 22. Spread vs Rest

- **Spread**: 값 펼치기 → `...arr`  
- **Rest**: 값 모음 → `function(...args)`

---

## 23. ES6 주요 기능

- let/const, Arrow Function, for...of, Class, Promise, Template Literal  
- Default Parameter, Rest/Spread, Destructuring, Generator, import/export

---

## 24. Ajax

- XMLHttpRequest 기반 비동기 통신  
- 페이지 전체 새로고침 없이 데이터 송수신

---

## 25. import vs require

| 구분 | import | require |
|------|--------|---------|
| 문법 | ES Module | CommonJS |
| 로딩 시점 | 정적 | 런타임 |
| 환경 | FE/BE | Node.js |
| Tree-Shaking | O | X |

---

## 26. npm

- Node.js 패키지 관리 툴  
- 패키지 설치, 업데이트, 버전 관리

---

## 27. package.json / package-lock.json

- **package.json**: 프로젝트 정보 + 의존성 기록  
- **package-lock.json**: 의존성 정확한 버전 잠금

---

## 28. TypeScript

- 정적 타입으로 컴파일 단계 오류 잡기  
- props, 상태, API 응답 타입 명확히 선언 가능  
- IDE 자동완성/타입체크 → 생산성 증가

### 실무 패턴
- Interface vs Type, Union/Intersection, Generic, API 타입 설계

---

## 29. null / undefined / undeclared / NaN

- null: 의도적 빈 값  
- undefined: 선언 후 값 없음  
- undeclared: 선언 없음  
- NaN: Not a Number

---

## 30. 데이터 타입

- **원시 타입**: boolean, null, undefined, number, string, symbol, bigint  
- **참조 타입**: object, array, function

---

## 31. Mutable vs Immutable

- **Mutable**: 값 변경 가능, 객체/배열  
- **Immutable**: 값 변경 불가, 새로운 값 생성, 원시 타입

---

## 32. Throttle & Debounce

- Throttle: 일정 주기마다 실행  
- Debounce: 마지막 호출만 실행

---

## 33. Iterable / Iterator / Generator

- **Iterable**: 순회 가능 객체 (`Symbol.iterator`)  
- **Iterator**: 반복 인터페이스, `next()` 사용  
- **Generator**: iterator 생성 함수, 실행 중단/재개 가능

---

## 34. 자바스크립트 동작 원리

- 싱글 스레드, V8 엔진 기반  
- **Memory Heap**: 메모리 할당  
- **Call Stack**: 코드 실행 스택  
- **Web APIs + Callback Queue + Event Loop** → 비동기 처리 가능

---

## 35. OOP 특징

- 객체 추상화, 상태+행위, 재사용성 높음  
- 클래스, 객체, 상속, 캡슐화 활용  
- 단점: 처리속도 느림, 객체 많으면 용량 증가

---

## 36. '==' vs '==='

- `==`: 타입 변환 후 값 비교  
- `===`: 타입 + 값 모두 동일해야 true

---

## 37. Map vs Set

- **Map**: key-value 쌍, 순서 유지, key 제한 없음  
- **Set**: 중복 불가, key 없음, 값 판단 효율적

---
