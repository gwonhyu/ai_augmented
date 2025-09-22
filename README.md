# ai_augmented

단일 페이지 포트폴리오 웹사이트 템플릿입니다. 순수 HTML/CSS/Vanilla JS만으로 제작되어 어디서든 쉽게 호스팅할 수 있습니다. 반응형 레이아웃, 스무스 스크롤, 스킬바 애니메이션, 타이핑 효과, 타임라인, 프로젝트 카드, 연락처 폼 UI 등을 포함합니다.

## 미리보기
- 메인 히어로 영역: 이름/직함, 다국어 멀티 타이핑 효과, CTA 버튼
- 소개(About): 경력 요약과 간단 지표
- 기술(Skills): 카테고리별 스킬바 애니메이션
- 경력(Experience): 타임라인 UI
- 프로젝트(Projects): 카드형 프로젝트 목록
- 연락처(Contact): 정보/소셜 링크/폼 UI

## 주요 기능
- 반응형 UI (모바일 햄버거 메뉴 포함)
- 고정 헤더 + 섹션별 스무스 스크롤 및 활성 네비게이션 표시
- IntersectionObserver 기반 스킬바 애니메이션 (`data-width`로 제어)
- 멀티 타이핑 효과 (`data-texts` JSON 배열로 제어) 및 단일 타이핑 효과
- 스크롤 등장 애니메이션(AOS 유사 효과)
- 접근성/키보드 네비게이션 보조(Escape로 모바일 메뉴 닫기)
- 경량, 의존성 없음(외부 폰트 제외)

## 기술 스택
- HTML5
- CSS3 (Flex/Grid, 반응형, 애니메이션)
- Vanilla JavaScript (ES6+)

## 시작하기
1) 프로젝트 클론 또는 다운로드
```bash
git clone <your-repo-url>
cd ai_augmented
```

2) 로컬에서 열기
- 단순히 `index.html`을 더블클릭하여 브라우저로 열어도 동작합니다.
- 정적 서버를 권장합니다(히스토리/캐시/보안 헤더 테스트 등 위해):
```bash
# Python 3
python3 -m http.server 8080
# 또는 Node http-server(사전 설치 필요)
# npx http-server -p 8080 --silent
```
브라우저에서 `http://localhost:8080` 접속.

## 파일 구조
```
/Users/jin/Desktop/codes/ai_augmented/
├─ index.html   # 페이지 마크업(섹션 구성, 텍스트/데이터 속성 포함)
├─ style.css    # 전역 스타일, 반응형, 애니메이션, 컴포넌트 스타일
├─ script.js    # 네비게이션, 스크롤/타이핑/스킬바 애니메이션, 폼 처리
└─ LICENSE
```

## 커스터마이징 포인트
- 헤더/네비게이션: `index.html`의 `.nav-menu` 항목과 섹션 `id`를 맞춰 수정
- 히어로 텍스트: `index.html`의 `.hero-title`, `.hero-name`
- 멀티 타이핑 문구: `index.html`의 `.typing-text` 요소의 `data-texts` 속성(JSON 배열)
- 소개/경력/프로젝트 내용: 해당 섹션 마크업을 직접 편집
- 스킬바 퍼센트: 각 `.skill-progress`의 `data-width` 값(예: `90%`)
- 색상/타이포: `style.css`의 색상 토큰(예: `#3498db`, `#2c3e50`)과 폰트 설정
- 반응형 임계점: `style.css`의 `@media (max-width: 768px)`, `(max-width: 480px)`
- 애니메이션 속도: `style.css`의 `transition`, `@keyframes`, `script.js`의 타이핑 속도 인자

## 스크립트 개요(`script.js`)
- 모바일 메뉴 토글: `.hamburger` 클릭 시 `.nav-menu.active` 토글
- 스무스 스크롤 오프셋: 고정 헤더 높이를 고려하여 스크롤 위치 계산
- 스크롤 시 헤더 스타일 변화
- 현재 섹션에 따라 네비게이션 활성화 상태 업데이트
- 스킬바 애니메이션: IntersectionObserver로 최초 노출 시 `width`와 `.animate` 적용
- 타이핑 효과: 단일(`typeWriter`)과 멀티(`multiTypeWriter`) 모두 제공
- AOS 유사 효과: 스크롤 진입 시 `.timeline-item`, `.project-card`, `.skill-category` 페이드/슬라이드 인
- 접근성: ESC 키로 모바일 메뉴 닫기, 외부 클릭/리사이즈 시 메뉴 닫기
- 성능: `utils.debounce/throttle`, 스크롤 핸들러 최적화

## 폼 처리
- 현재는 클라이언트 측 유효성 검사 및 성공 알림만 수행합니다.
- 실제 메일 전송이 필요하면 백엔드 엔드포인트 또는 서드파티(예: Formspree, EmailJS) 연동을 추가하세요.

## 개발 팁
- 고정 헤더 오프셋: 섹션에 `scroll-margin-top: 80px;` 적용(`style.css`), 스크롤 계산은 `script.js`에서 헤더 높이를 반영
- 시스템 폰트/언어: 현재 한국어 콘텐츠 기준, 다국어 지원 시 `data-texts`에 다국어 문구를 추가
- 이미지 교체: `.profile-image`와 프로젝트 썸네일 영역(`.project-image`)을 실제 이미지로 교체 가능

## 배포
정적 호스팅 지원 플랫폼에 업로드하면 끝입니다.
- GitHub Pages: `index.html`이 루트에 있으므로 리포지토리 Pages 활성화만으로 동작
- Netlify/Vercel: 신규 사이트 생성 → 이 리포지토리 연결 → 빌드 단계 없이 배포

## 라이선스
이 프로젝트는 리포지토리의 `LICENSE` 파일 내용을 따릅니다.

## 변경 로그
- 0.1.0: 초기 공개 버전(포트폴리오 템플릿, 반응형/애니메이션/타이핑 포함)