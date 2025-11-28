# React 핵심 정리

## 1. DOM(Document Object Model)
- 개념  
  - HTML 문서를 객체 기반 트리 구조로 표현한 모델  
  - JS 같은 프로그래밍 언어가 DOM에 접근해 문서 구조, 스타일, 내용 수정 가능  
  - “브라우저가 화면을 어떻게 그릴지” 구조화하여 제공하는 인터페이스

---

## 2. Virtual DOM
- 개념  
  - 실제 DOM과 유사한 객체를 메모리에 먼저 만들어 변경을 계산한 뒤, 변화된 부분만 실제 DOM에 반영하는 기술  
- 필요한 이유  
  - DOM은 조작될 때마다 렌더링 과정을 반복 → 성능 저하  
  - Virtual DOM 사용 시 DOM 업데이트 횟수 최소화 → 빠른 렌더링 & 효율적인 UI 업데이트

---

## 3. Virtual DOM 작동 원리
- 상태(state)가 업데이트되면 새로운 Virtual DOM 생성  
- 이전 Virtual DOM과 비교(diffing)  
- 달라진 부분만 실제 DOM에 patch

---

## 4. 왜 React를 사용하는가?
- Virtual DOM 기반 고성능 UI 렌더링  
- 컴포넌트 단위 개발 → 재사용성 & 유지보수성 증가  
- 방대한 커뮤니티와 생태계, 자료 접근성 뛰어남  
- 지속적인 업데이트(메타/FB 유지)

---

## 5. 클래스 컴포넌트 vs 함수 컴포넌트
- 클래스 컴포넌트  
  - state 사용 가능  
  - 라이프사이클 메서드 사용 가능  
  - 반드시 `render()` 메서드 필요
- 함수 컴포넌트  
  - 간단한 구조  
  - React Hooks로 state/라이프사이클 기능 사용 가능  
  - 더 적은 메모리 사용  
  - 빌드 파일 크기가 더 작음

---

## 6. JSX란?
- JavaScript XML  
- JS 내부에서 HTML 같은 UI 구조를 표현할 수 있게 하는 문법  
- React.createElement() 호출을 축약한 문법적 설탕(Syntax sugar)

### 브라우저는 JSX를 읽을 수 있는가?
- 직접 읽지 못함  
- Babel 같은 컴파일러가 JSX → JS 코드로 변환해야 함

### React 17 이후 JSX에서 React import를 안 해도 되는 이유
- React.createElement 방식이 아니라 컴파일러가 자동으로 JSX 변환 함수를 import해오기 때문

---

## 7. Reconciliation(재조정)
- 상태 변경 시 새로운 Virtual DOM을 만들고 이전 Virtual DOM과 비교하여 바뀐 부분만 실제 DOM에 적용하는 과정

---

## 8. state vs props
- state  
  - 컴포넌트 내부에서 관리하는 값  
  - `setState` / `useState`로 변경 → 리렌더링 발생
- props  
  - 부모 → 자식 전달 값 (읽기 전용)  
  - 자식이 직접 변경 불가 (부모에게 setState 함수를 전달 받아 변경 가능)

---

## 9. React Hooks
- 기본 Hooks  
  - `useState`: 상태 관리  
  - `useEffect`: 렌더링 후 부수효과 처리 / 라이프사이클 대체  
  - `useContext`: 전역 context 사용
- 추가 Hooks  
  - `useReducer`: 복잡한 상태 업데이트 로직 분리  
  - `useRef`: DOM 접근 / 값 유지  
  - `forwardRef`: 부모 → 자식 ref 전달  
  - `useImperativeHandle`: 부모에서 자식 함수 제어  
  - `useMemo`: 연산 결과 메모이제이션  
  - `useCallback`: 함수 메모이제이션  
  - `useLayoutEffect`: DOM이 그려지기 전 실행  
  - `useDebugValue`: 디버깅용 라벨 표시
- React 18 Hooks  
  - `useId`: 고유 id 생성  
  - `useTransition`: 낮은 우선순위 상태 처리  
  - `useDeferredValue`: 일부 UI 업데이트 지연

---

## 10. React Lifecycle
- 컴포넌트 생명주기 단계: `mount`, `update`, `unmount`  
- 클래스 컴포넌트 주요 메서드: `componentDidMount`, `componentDidUpdate`, `componentWillUnmount`, `render`

---

## 11. useState
- 함수형 컴포넌트 상태 관리  
- 상태 변경 시 해당 컴포넌트 리렌더링

---

## 12. useEffect
- 동작 구조: `useEffect(callback, dependencyArray)`  
  - `[]` → mount 시 한 번 실행  
  - `[state]` → 특정 state 변경 시 실행  
  - `return cleanup` → unmount 시 호출

---

## 13. useEffect vs useLayoutEffect
| 구분 | useEffect | useLayoutEffect |
|------|-----------|------------------|
| 실행 시점 | 렌더 + paint 이후 | 렌더 직후, paint 이전 |
| 동기/비동기 | 비동기 | 동기 |
| DOM 깜빡임 | 있을 수 있음 | 없음 |

---

## 14. setState를 사용하는 이유
- React는 불변성을 기반으로 변경 사항을 감지  
- state를 직접 수정하면 렌더링이 일어나지 않음  
- 항상 `setState` / `useState` 활용해야 함

---

## 15. React 렌더링 성능 최적화
- `React.memo`  
- `useMemo`  
- `useCallback`  
- 객체/배열 state 분리  
- Debounce/throttle 적용  
- Lazy loading & Code splitting  
- 이미지 최적화  
- 가상 리스트(windowing)  
- `react-query`로 캐싱  
- 불필요한 reflow/repaint 최소화

---

## 16. Props Drilling & 해결 방법
- Props Drilling: 여러 단계의 자식 컴포넌트까지 props를 계속 전달하는 현상  
- 해결 방법: Context API, Redux, Recoil, Zustand, MobX 등 전역 상태 관리

---

## 17. 전역 상태 관리 방법
- Context API  
- Redux  
- Recoil  
- MobX  
- Zustand 등

---

## 18. useMemo란?
- 연산량이 큰 계산 결과를 메모이제이션하여 재사용  
- 동일 입력이면 캐시된 값을 반환 → 성능 최적화

---

## 19. useCallback란?
- 함수 자체를 메모이제이션  
- 매 렌더마다 새로운 함수 생성 → 자식 컴포넌트 리렌더링 발생  
- `useCallback`으로 의존성이 변할 때만 새 함수 생성하여 불필요한 렌더링 방지

---

## 20. React 렌더링 최적화 (추가 상세)
- `useMemo`  
- `React.memo`  
- `useCallback`  
- 객체를 props로 전달 시 얕은 비교 문제 → 객체 생성 최소화  
- key에 index 사용 지양  
- `useState` 함수형 업데이트로 `useCallback`에서 의존성 제거  
- Input `onChange` Debounce/Throttle

---

## 21. React, Vue, Angular 비교
| 항목 | React | Vue | Angular |
|------|-------|-----|---------|
| 타입 | 라이브러리 | 프레임워크 성격 | 완전한 프레임워크 |
| 데이터 바인딩 | 단방향 | 양방향 | 양방향 |
| 러닝커브 | 중간~높음 | 낮은 편 | 매우 높음 |
| 장점 | 생태계, 유연성 | 쉬운 접근 | 강력한 규모 확장 |

---

## 22. MVC, MVVM
- MVC: Model / View / Controller (뷰와 모델 의존성 높음, 대형 앱에서 복잡)  
- MVVM: Model / View / ViewModel (데이터 바인딩 통해 뷰와 뷰모델 분리, 유지보수성 우수)

---

## 23. Webpack & Babel
- Webpack: 모듈 번들러, 여러 파일을 하나로 묶고 로더로 JSX/CSS 처리  
- Babel: 트랜스파일러, ES6+ → ES5 변환하여 브라우저 호환성 확보

---

## 24. use strict
- 장점: 오류를 초기에 발견, 암묵적 전역변수 생성 방지  
- 단점: 지원하지 않는 환경에서 다르게 동작할 수 있음

---

## 25. NPM
- Node Package Manager  
- JS 패키지 설치/관리 도구, 방대한 패키지 저장소 제공

---

## 26. TDD (Test Driven Development)
- 테스트 → 구현 → 리팩토링 반복  
- 코드 모듈화 용이  
- React 테스트 도구: Jest, React Testing Library

