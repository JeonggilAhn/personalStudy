🔹 1. API 통신 구조 (FetchClient)

목적: 인증 포함 fetch 요청을 공통화하여 일관된 API 통신 유지

구성

FetchClient 클래스: get, post, patch, delete 메서드 제공

자동 토큰 갱신 (401 Unauthorized 발생 시 refresh_token 요청 후 재시도)

쿼리 파라미터 직렬화 처리

기술: fetch, getCookie, Headers, 재귀적 재시도 처리

🔹 2. 퀴즈 기능

목적: 콘텐츠별 OX 퀴즈 풀이 및 정답 피드백 제공

구성

API: 퀴즈 조회(GET), 정답 제출(POST)

컴포넌트: QuizContainer, QuizCard, QuizAnswer, QuizLoading

커스텀 훅: useQuiz, usePreventNavigation (페이지 이탈 방지)

기술: useState, useEffect, map, axios, 조건부 렌더링, 사용자 피드백

🔹 3. 추천 기능 (강의 & 전문가)

목적: 콘텐츠 기반 유사 강의/전문가 추천 제공

구성

API: /recommendations, /expert-recommendations

컴포넌트: Lecture, Expert, LectureCard, ExpertCard

커스텀 훅: usePagination을 통한 페이지네이션

기술: fetch, query string 구성, 반응형 카드 UI, 리스트 렌더링

🔹 4. 스냅리뷰 기능 (MVP)

목적: 콘텐츠별 주요 영상 장면을 이미지와 코멘트로 기록 및 편집

구성

API: 스냅리뷰 조회(GET), 코멘트 수정(PATCH)

컴포넌트: ReviewCard, ReviewTextField, ReviewWriteButton

유틸: 최대 글자 수 제한, TimeStamp 클릭으로 영상 이동 유도

기술: useState, 리스트 매핑, textarea 이벤트 처리, 입력 유효성

🔹 5. 스냅리뷰 목록 (무한 스크롤)

목적: 날짜별 그룹화된 스냅리뷰 리스트 조회

구성

API: getSnapReviews (페이지네이션 기반)

컴포넌트: SnapList, SnapDateGroup, SnapCard

커스텀 훅: useInfiniteScroll (IntersectionObserver 기반)

기술: react-query, IntersectionObserver, flatMap, 날짜 포맷 정렬

🔹 6. 스냅리뷰 공유 기능

목적: 스냅리뷰를 링크 형태로 외부 사용자에게 공유

구성

API: 공유 코드 생성(GET/POST), 코드 기반 조회(GET), 삭제(DELETE)

컴포넌트:

SnapBookContent: 공유버튼 포함 상세 뷰

SharedSnapBookPage: 외부 공유 접근 시 리뷰 렌더링

Share, ShareButton, Review

기술: 클립보드 복사, 다이얼로그 처리, 조건부 렌더링, fetch

🔹 7. 관리자 기능 - 로그인 및 인증

목적: 관리자만 접근 가능한 전략 대시보드 인증 처리

구성

API Route: /api/auth/admin, /auth/me

컴포넌트: LoginForm, InputField, AuthCallback

로그인 성공 시 대시보드로 리다이렉션 처리

기술: FormData, fetch, useRouter, accessToken 저장 (setCookie)

🔹 8. 관리자 대시보드 (전략 차트)

목적: 플랫폼 주요 지표 시각화(전환율, 학습률 등)

구성

API: 지표별 /admin/strategy/... 엔드포인트

컴포넌트:

StrategyBoardPage: 전체 구조

TopCharts, BottomChart: 주요 지표별 그래프

CurveGraphCard: 커스텀 라인 차트

DateRangeSelector: 날짜 범위 설정

커스텀 훅: useStrategyData

기술: chart.js, react-chartjs-2, date-fns, 반응형 차트, 그래프 설명 툴팁
