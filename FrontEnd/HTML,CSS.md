# 1. Attribute vs Property

## Attribute
- HTML 문서(정적)에 작성된 속성
- 변하지 않음
- 예: `<div class="myClass"></div>` → `class="myClass"`

## Property
- 브라우저가 HTML을 파싱한 뒤 생성되는 DOM 객체의 동적 속성
- JavaScript 조작에 따라 값이 변경될 수 있음
- 예: `element.className`

### 정리
- Attribute: HTML 문서에 존재 (정적)
- Property: DOM 객체에 존재 (동적)

---

# 2. Cascading(카스케이딩)

브라우저가 여러 CSS 규칙 중 어떤 스타일을 적용할지 결정하는 우선순위 규칙.

## 우선순위 요소 3가지
1. **출처(Origin)**  
   브라우저 기본 < 외부 CSS < 내부 CSS < 인라인 스타일

2. **명시도(Specificity)**  
   태그 < 클래스 < ID < 인라인 스타일

3. **선언 순서(Order)**  
   나중에 선언된 스타일 우선

---

# 3. Flexbox

반응형 레이아웃을 위해 도입된 1차원(가로/세로) 레이아웃 시스템.

## Flex Container 속성
- `display: flex`
- `flex-direction`  
- `justify-content`
- `align-items`
- `flex-wrap`

## Flex Item 속성
- `flex-grow` : 남는 공간 확장 비율
- `flex-shrink` : 줄어드는 비율
- `flex-basis` : 기본 크기

---

# 4. Box Model

모든 HTML 요소가 가지는 박스 구조.

## 구성 요소
- **Content** : 내용
- **Padding** : 내용과 테두리 사이 간격
- **Border** : 테두리
- **Margin** : 요소와 요소 간 간격

---

# 5. Display 속성

요소의 배치 방식 지정.

- `none` : 화면에서 제거
- `block` : 한 줄 전체 차지
- `inline` : 내용 크기만큼, width/height 적용 불가
- `inline-block` : inline + block 특성 혼합
- `flex` : 1차원 레이아웃
- `grid` : 2차원 레이아웃

---

# 6. Position

요소를 문서에서 배치하는 방식.

- `static` : 기본 배치
- `relative` : 원래 위치 기준 이동
- `absolute` : 가장 가까운 positioned ancestor 기준 (없으면 body)
- `fixed` : viewport 기준 고정
- `sticky` : 스크롤 시 특정 지점까지 relative처럼, 이후 fixed처럼 동작

---

# 7. Float

요소를 좌/우로 띄워 다른 요소가 흐르도록 하는 방식(과거 레이아웃 방식).

- `float: left/right`
- 뒤 요소가 따라붙는 문제 → `clear: both` 등으로 해결
- 현재는 flex, grid가 대체

---

# 8. CSS Animation vs JavaScript Animation

## CSS Animation
- `transition`, `@keyframes` 기반
- `transform`, `opacity` 중심 → 레이아웃 영향 없음
- 단순하고 성능 좋음
- 브라우저 최적화 엔진 활용 가능

## JavaScript Animation
- 복잡한 애니메이션 및 상호작용에 유리
- `requestAnimationFrame` 사용 시 60fps 가능
- `top`, `left` 변경 시 layout 발생 → 성능 저하 가능
- GSAP 등 라이브러리 사용 가능

### 결론
- 단순 애니메이션 → CSS  
- 복잡/정교/상호작용 중심 → JS

---

# 9. Reflow & Repaint

브라우저 렌더링 성능에 영향을 주는 과정.

## Reflow (Layout)
- 요소의 크기/위치가 변경될 때 발생
- 비용 가장 큼

## Repaint (Paint)
- 색상 변경 등 레이아웃 영향이 없을 때 발생

### 성능 최적화 팁
- `transform`, `opacity` 중심으로 애니메이션 처리
- `top/left` 대신 `translate` 사용
- 필요할 경우 `will-change`로 레이어 생성

---

# 10. z-index & Stacking Context

요소의 쌓임 맥락을 결정하는 구조.

## Stacking Context 생성 조건
- position: absolute/fixed + z-index
- opacity < 1
- transform 존재
- filter 적용
- flex/grid 아이템에서 z-index 지정

### 자주 묻는 질문
**Q. z-index 높여도 위로 안 올라가는 이유?**  
→ 다른 stacking context 내부에 있기 때문

---

# 11. Media Query (반응형 디자인)

다양한 화면 크기에 대응하는 CSS 기법.

```css
@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }
}
```
## 기본 사용 패턴

- max-width : 모바일 우선(Mobile First)

- min-width : 데스크탑 우선
