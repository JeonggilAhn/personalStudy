# 1. Sync vs Async

## Sync(동기)
- 요청을 보낸 뒤 응답을 받을 때까지 기다림
- 다음 작업은 그 이후에 실행
- 대표 예: alert() (Blocking)
- 특징:
  - 순차적 실행 보장
  - 코드 이해가 직관적
  - 비동기 처리 불가 → UI 블로킹 가능

## Async(비동기)
- 요청을 보낸 뒤 응답을 기다리지 않고 다음 코드 실행
- 대표 예: setTimeout, fetch (Non-blocking)
- 특징:
  - 동시성 처리 가능
  - UI 블로킹 최소화
  - 콜백, Promise, async/await 활용

### 정리
- Sync: 순차 실행
- Async: 응답 여부와 상관없이 다음 작업 진행

---

# 2. Blocking vs Non-Blocking

## Blocking
- 작업이 완료될 때까지 **제어권이 해당 작업에 묶임**
- 다른 작업은 대기 상태
- 대표 예: alert(), 동기적 I/O
- 특징:
  - 동기적 처리
  - CPU와 스레드가 결과 기다림
  - UI가 멈출 수 있음

## Non-Blocking
- 작업이 완료되지 않아도 **즉시 제어권 반환**
- 다른 작업을 계속 수행 가능
- 대표 예: fetch, setTimeout, 비동기 파일 I/O
- 특징:
  - 비동기적 처리
  - 이벤트/콜백 큐 통해 나중에 처리
  - CPU 활용 효율 증가

### 차이
| 구분 | Blocking | Non-Blocking |
|------|----------|--------------|
| 처리 방식 | 동기 | 비동기 |
| 제어권 | 작업 완료까지 묶임 | 즉시 반환 |
| CPU 활용 | 대기 중 비효율 | 효율적 |
| 예시 | alert(), sync I/O | fetch(), setTimeout |

---

# 3. Callback & Callback Hell

## Callback
- 다른 함수의 인자로 전달되어 실행되는 함수
- 비동기 작업 결과 처리에 사용
- 예: `fs.readFile(path, callback)`

## Callback Hell
- 콜백 중첩으로 가독성 저하, 유지보수 어려움
- 예: `a(b(c(d())))`

### 해결 방법
- 콜백 분리 (named function)
- Promise 체인
- async/await

---

# 4. Event Loop

자바스크립트 비동기 처리 핵심 메커니즘

## 구성 요소
- Call Stack: 현재 실행 중인 함수 스택
- Microtask Queue: Promise.then, async/await
- Macrotask Queue: setTimeout, setInterval, DOM 이벤트 등

## 동작 원리
1. Call Stack이 비면
2. Microtask Queue 우선 처리
3. Macrotask Queue 처리
- 특징:
  - 단일 스레드 기반
  - 비동기 작업 순서 보장

---

# 5. Promise vs Async/Await

## Promise
- 비동기 작업을 객체로 처리
- `.then()`, `.catch()` 체인 활용
- 예: `fetch(url).then(res => res.json())`

## Async/Await
- Promise 기반을 동기처럼 작성 가능
- try/catch로 예외 처리
- 예: `const data = await fetcher(url)`

---

# 6. map vs forEach

| 구분 | map | forEach |
|------|-----|---------|
| 반환 값 | 새로운 배열 반환 | 반환값 없음 |
| 원본 변경 | ❌ | 가능 |
| 체이닝 | 가능 | 불가능 |

---

# 7. var, let, const 차이

| 키워드 | 스코프 | 재할당 | 재선언 | 특징 |
|--------|--------|---------|---------|------|
| var | 함수 | 가능 | 가능 | 호이스팅 시 undefined |
| let | 블록 | 가능 | 불가능 | TDZ 존재 |
| const | 블록 | 불가능 | 불가능 | TDZ 존재 |

---

# 8. 메서드 체이닝
- 반환값으로 자기 자신(this) 또는 객체 반환
- 예: `array.map().filter().reduce()`
- 장점: 코드 간결, 연속 처리 용이

---

# 9. 일반 함수 vs 화살표 함수

## 일반 함수
- this: 동적 바인딩
- arguments 사용 가능
- new로 생성자 가능

## 화살표 함수
- this: 상위 스코프(this) 바인딩
- arguments 없음
- new 생성자 사용 불가

---

# 10. this

- 생성자 함수 → 새 인스턴스
- 객체 메서드 → 해당 객체
- call/apply/bind → 명시적 바인딩
- 일반 함수 호출 → 전역 객체
- 화살표 함수 → 선언 시점 상위 this

---

# 11. 함수 선언식 vs 함수 표현식

## 함수 선언식
- 호이스팅: 선언 전 호출 가능

## 함수 표현식
- 변수 호이스팅만 발생 → 초기화 전 호출 불가

---

# 12. 호이스팅
- JS 엔진이 변수/함수 선언을 스코프 최상단으로 끌어올린 것처럼 동작
- let/const: TDZ 존재
- 함수 선언식: 전체 호이스팅

---

# 13. 이벤트 버블링 & 캡처링

## 버블링
- 이벤트 → 하위 → 상위 전파

## 캡처링
- 이벤트 → 상위 → 하위 전파

---

# 14. 이벤트 전파 & 이벤트 위임

## 이벤트 전파
- Capturing → Target → Bubbling

## 이벤트 위임
- 상위 요소에 이벤트 등록 → 하위 요소 일괄 처리

---

# 15. Closure(클로저)
- 함수가 선언된 당시의 렉시컬 스코프 기억
- 외부에서 내부 변수 접근 가능
- 예: private 변수 구현

---

# 16. Lexical Scope & Lexical Environment

## Lexical Scope
- 선언 위치 기준 상위 스코프 결정

## Lexical Environment
- 스코프 내부 변수/값/체인 정보 담음

---

# 17. 실행 컨텍스트
- 코드 실행 환경
- Variable Environment
- Lexical Environment
- thisBinding
→ 콜 스택 구조로 관리

---

# 18. 스코프 & 스코프 체인

## 스코프
- 변수 참조 유효 범위

## 스코프 체인
- 현재 → 상위 순서 탐색

---

# 19. 프로토타입 & 프로토타입 체인

## 프로토타입
- 모든 객체가 상속받는 기본 구조

## 프로토타입 체인
- 프로퍼티 없으면 prototype 따라 부모 탐색

---

# 20. 깊은 복사 vs 얕은 복사

- 얕은 복사: 참조값만 복사 → 주소 공유
- 깊은 복사: 새 메모리 생성 → 독립 객체

---

# 21. Destructuring
- 배열·객체 값을 해체하여 변수 할당
- 예: `const [a,b] = arr` / `const {x,y} = obj`

---

# 22. Spread vs Rest
- Spread: 펼침 → `...arr`
- Rest: 모음 → `function(...args)`

---

# 23. ES6 주요 기능 요약
- let/const
- Arrow Function
- for...of
- Class
- Promise
- Template Literal
- Default Parameter
- Rest/Spread
- Destructuring
- Generator
- import/export

---

# 24. Ajax
- XMLHttpRequest 기반 비동기 통신
- 페이지 새로고침 없이 데이터 송수신

---

# 25. import vs require

| 구분 | import | require |
|------|--------|--------|
| 문법 | ES Module | CommonJS |
| 로딩 시점 | 정적 | 런타임 |
| 사용 환경 | FE/BE 모두 | Node.js |
| Tree-Shaking | O | X |

---

# 26. npm
- Node.js 패키지 매니저
- 패키지 다운로드, 업데이트, 버전 관리

---

# 27. package.json / package-lock.json

## package.json
- 프로젝트 메타 정보
- 의존성 기록

## package-lock.json
- 의존성 정확한 버전 잠금

---

# 28. TypeScript를 쓰는 이유
- 컴파일 단계에서 에러 잡기
- 타입 기반 자동완성 / 개발 경험 향상
- 코드 안정성 & 유지보수성 증가

---

# 29. null / undefined / undeclared / NaN
- null: 개발자가 의도적으로 비어있음을 명시
- undefined: 선언됐지만 값 없음
- undeclared: 선언도 안 됨
- NaN: Number가 아님

---

# 30. 데이터 타입

## 원시 타입
- boolean, null, undefined, number, string, symbol, bigint

## 참조 타입
- object, array, function 등

---

# 31. Mutable vs Immutable

## Mutable
- 값 변경 가능 → 객체, 배열

## Immutable
- 값 변경 불가 → 새 값 생성
- 모든 원시 타입

---

# 32. Throttle & Debounce

- Throttle: 일정 주기마다 실행
- Debounce: 마지막 호출만 실행

---

# 33. Iterable / Iterator / Generator

## Iterable
- 순회 가능한 객체(Symbol.iterator 보유)

## Iterator
- next() → {value, done}

## Generator
- function* 문법
- 실행 중단/재개 가능

──────────────────────────────
TypeScript
──────────────────────────────

# TypeScript 사용 경험
- 정적 타입으로 **컴파일 단계에서 오류 포착**
- props, 상태, API 응답 타입 명확 선언 → 가독성/유지보수성 향상
- 대규모 리팩토링 안정적
- IDE 자동완성/타입체크 → 개발 생산성 향상

---

# TypeScript 특징
- 정적 타이핑
- 클래스/인터페이스/제네릭 등 객체지향 지원
- 기존 JS 프로젝트 점진적 도입 가능
- tsconfig.json으로 strict, target, moduleResolution 제어

---

# 실무 자주 쓰는 패턴

## Interface vs Type
- interface: 객체 형태 선언 + 확장 용이
- type: 유니언/인터섹션 등 고급 타입 조합

## Union / Intersection
- Union (A | B): 여러 타입 중 하나
- Intersection (A & B): 두 타입 모두 만족

## Generic
```ts
function identity<T>(arg: T): T { return arg }
