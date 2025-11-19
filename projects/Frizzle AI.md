🔹 1. API 통신 구조 (FetchClient)

사용 기술

fetch, async/await, RequestInit, Headers

쿠키 기반 인증 처리 (getCookie)

토큰 만료 시 자동 재요청 (refresh_token 기반)

기술 포인트

재시도 로직 (retryCount) 구현

공통 API client 클래스화 (get/post/patch/delete)

인증 여부 및 content-type 유연 설정

🔹 2. 퀴즈 기능

사용 기술

React useState/useEffect

커스텀 훅 useQuiz, usePreventNavigation

조건부 렌더링 (QuizCard ↔ QuizAnswer)

API: GET /quiz, POST /quiz

기술 포인트

정답 제출 후 화면 전환 및 스크롤 리셋 처리

페이지 이탈 방지 (뒤로가기/링크 차단 → Dialog 처리)

selected, isCompleted, hasAnswered 상태를 별도로 관리하여 UX 최적화

🔹 3. 강의/전문가 추천 기능

사용 기술

RESTful API 호출 (쿼리 스트링 기반)

커스텀 훅 usePagination

반응형 카드 UI (LectureCard, ExpertCard)

기술 포인트

URLSearchParams로 필터링 파라미터 처리

params.get()을 통해 동적 endpoint 분기 처리

keyword 기반 강조 UI 및 비동기 에러 핸들링

🔹 4. 스냅리뷰 (프레임별 설명 기능)

사용 기술

useEffect, useState를 통한 로컬 상태 관리

PATCH /snap-review API로 부분 업데이트

코멘트 입력창 → 실시간 바인딩 및 Enter 저장

기술 포인트

리뷰 1건마다 개별 수정 가능 (editingId 기반 제어)

MAX_SNAP_REVIEW_LENGTH로 글자 수 제한 UX 제공

이미지 클릭 시 TimeStamp 처리로 영상 이동 가능

🔹 5. 스냅리뷰 목록 기능 (무한 스크롤)

사용 기술

@tanstack/react-query 기반 useInfiniteQuery

커스텀 훅 useInfiniteScroll

IntersectionObserver API

기술 포인트

observerTarget ref 관리 → 뷰포트 진입 시 다음 페이지 호출

날짜별 리뷰 그룹화 → SnapDateGroup에서 reduce + 정렬 처리

초기 로딩/빈 리스트/에러 상태까지 완전 대응

🔹 6. 스냅리뷰 공유 기능

사용 기술

공유 코드 API (GET/POST /share-code)

클립보드 복사 (navigator.clipboard)

공유 링크 기반 접근 페이지 (SharedSnapBookPage)

기술 포인트

링크 클릭 시 modal로 공유 다이얼로그 노출

공유 코드 존재 여부 확인 후 없으면 자동 생성

리뷰 렌더링 시 이미지 hover 시 comment 오버레이 UI 처리

🔹 7. 관리자 로그인 / 인증

사용 기술

FormData, fetch, 쿠키 기반 로그인 처리

서버 측 토큰 저장 (setCookie 사용)

AuthCallback → 로그인 후 리다이렉트

기술 포인트

GET /auth/me로 role 확인 후 접근 제어

로그인 실패 시 BasicToaster로 UX 피드백 처리

로그인 성공 시 /admin/strategyboard 자동 이동

🔹 8. 관리자 전략 대시보드 (차트)

사용 기술

react-chartjs-2, chart.js, date-fns, react-date-range

커스텀 훅: useStrategyData

컴포넌트 분리: DateRangeSelector, TopCharts, BottomChart

기술 포인트

날짜별/옵션별 API 통합 관리 및 병렬 처리

차트 색상은 순환 컬러 팔레트로 가독성 향상

Y축 0 고정 및 최소 마크 수 지정

10개 이상 데이터 → 가로 스크롤 자동 적용 (min-w-[1200px])
