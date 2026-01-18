# 각성연구소 디자인 관리 가이드

이 문서는 각성연구소 (Awakening Lab) 커피 브랜드 홈페이지의 디자인을 관리하고 수정하는 방법을 안내합니다.

---

## 목차

1. [파일 구조](#파일-구조)
2. [색상 변경](#색상-변경)
3. [폰트 변경](#폰트-변경)
4. [간격/여백 조정](#간격여백-조정)
5. [컴포넌트별 수정 위치](#컴포넌트별-수정-위치)
6. [반응형 디자인](#반응형-디자인)
7. [애니메이션](#애니메이션)
8. [아이콘 수정](#아이콘-수정)
9. [다크 모드 관리](#다크-모드-관리)
10. [실전 예제](#실전-예제)

---

## 파일 구조

```
Awakening/
├── index.html          # 메인 페이지
├── menu.html           # 메뉴 (시그니처 음료)
├── laboratory.html     # 연구소 (브랜드 스토리)
├── location.html       # 위치 (매장 정보)
├── css/
│   └── style.css       # ⭐ 모든 스타일 관리
├── js/
│   └── main.js         # 인터랙션
└── CLAUDE.md           # 브랜드 가이드라인
```

**핵심 파일:** `css/style.css` - 모든 디자인은 이 파일에서 관리됩니다.

---

## 색상 변경

### CSS 변수 위치: `css/style.css` 6~23번 줄

```css
:root {
  /* ========== PRIMARY - 어두운 배경 ========== */
  --color-dark: #0D0D0D;        /* 메인 배경 (거의 검정) */
  --color-charcoal: #1A1A1A;    /* 카드/섹션 배경 */
  --color-espresso: #2C1810;    /* 에스프레소 브라운 */

  /* ========== ACCENT - 따뜻한 커피 톤 ========== */
  --color-copper: #B87333;      /* 메인 강조색 (버튼, 링크) */
  --color-amber: #D4A574;       /* 밝은 강조색 */
  --color-cream: #F5E6D3;       /* 크림 (텍스트 색상) */

  /* ========== NEUTRAL ========== */
  --color-white: #FAFAFA;       /* 밝은 흰색 */
  --color-gray: #6B6B6B;        /* 중간 회색 */
  --color-gray-light: #8A8A8A;  /* 밝은 회색 */

  /* ========== SEMANTIC ========== */
  --color-highlight: #C9A66B;   /* 하이라이트 (골드) */
}
```

### 색상 변경 예시

#### 코퍼 → 레드 와인으로 변경
```css
--color-copper: #722F37;
--color-amber: #A0522D;
--color-highlight: #8B4513;
```

#### 코퍼 → 모카 그린으로 변경
```css
--color-copper: #5D7052;
--color-amber: #8FBC8F;
--color-highlight: #6B8E23;
```

#### 배경을 더 밝게 (라이트 모드 느낌)
```css
--color-dark: #F5E6D3;
--color-charcoal: #FFFFFF;
--color-cream: #1A1A1A;  /* 텍스트 색상 반전 */
```

---

## 폰트 변경

### CSS 변수 위치: `css/style.css` 25~28번 줄

```css
/* 제목용 (세리프 - 고급스러운 느낌) */
--font-display: 'Playfair Display', 'Noto Serif KR', serif;

/* 본문용 (산세리프 - 가독성) */
--font-body: 'Pretendard', -apple-system, BlinkMacSystemFont, sans-serif;

/* 영문 강조용 (모노스페이스 - 연구소 컨셉) */
--font-accent: 'Space Mono', monospace;
```

### 폰트 변경 방법

1. **HTML 파일의 `<head>`에서 Google Fonts 링크 수정**

```html
<!-- 현재 -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600&family=Space+Mono&display=swap" rel="stylesheet">

<!-- 새 폰트로 변경 -->
<link href="https://fonts.googleapis.com/css2?family=새폰트명:wght@400;500;600&display=swap" rel="stylesheet">
```

2. **CSS 변수 수정**

```css
--font-display: '새폰트명', serif;
```

### 추천 폰트 조합

| 용도 | 현재 폰트 | 대안 1 | 대안 2 |
|------|----------|--------|--------|
| 제목 | Playfair Display | Cormorant Garamond | EB Garamond |
| 본문 | Pretendard | Noto Sans KR | IBM Plex Sans KR |
| 영문 강조 | Space Mono | JetBrains Mono | IBM Plex Mono |

---

## 간격/여백 조정

### CSS 변수 위치: `css/style.css` 30~37번 줄

```css
--space-xs: 0.5rem;    /* 8px - 아주 작은 간격 */
--space-sm: 1rem;      /* 16px - 작은 간격 */
--space-md: 1.5rem;    /* 24px - 중간 간격 */
--space-lg: 2rem;      /* 32px - 큰 간격 */
--space-xl: 3rem;      /* 48px - 아주 큰 간격 */
--space-2xl: 4rem;     /* 64px */
--space-3xl: 6rem;     /* 96px - 섹션 간격 */
```

### 전체적으로 여백 늘리기 (더 넓은 레이아웃)
```css
--space-md: 2rem;      /* 24px → 32px */
--space-lg: 3rem;      /* 32px → 48px */
--space-xl: 4rem;      /* 48px → 64px */
```

---

## 컴포넌트별 수정 위치

| 컴포넌트 | CSS 줄 번호 (대략) | 설명 |
|----------|-------------------|------|
| **네비게이션** | 100~180 | 상단 메뉴바, 로고, 모바일 메뉴 |
| **버튼** | 180~230 | .btn-primary, .btn-secondary |
| **Hero 섹션** | 230~320 | 메인 페이지 상단 영역 |
| **섹션 공통** | 320~380 | .section, .section-header |
| **메뉴 카드** | 380~480 | 음료 메뉴 카드 스타일 |
| **연구소 페이지** | 480~600 | 타임라인, 프로세스 |
| **위치 페이지** | 600~700 | 지도, 운영시간 |
| **Footer** | 700~800 | 하단 영역 |
| **유틸리티** | 800~896 | 애니메이션, 헬퍼 클래스 |

---

## 반응형 디자인

### 브레이크포인트

```css
/* 모바일 (기본) */
/* 모든 스타일이 모바일 우선으로 작성됨 */

/* 태블릿 */
@media (min-width: 768px) { ... }

/* 데스크톱 */
@media (min-width: 1024px) { ... }

/* 와이드 스크린 */
@media (min-width: 1440px) { ... }
```

### 반응형 수정 예시

모바일에서 카드 1열로 표시:
```css
@media (max-width: 767px) {
  .menu-grid {
    grid-template-columns: 1fr;  /* 1열 */
  }
}
```

---

## 애니메이션

### 트랜지션 속도: `css/style.css` 39~42번 줄

```css
--transition-fast: 150ms ease;    /* 빠른 (호버) */
--transition-normal: 300ms ease;  /* 일반 */
--transition-slow: 500ms ease;    /* 느린 (페이드인) */
```

### 페이드인 효과 수정

```css
.fade-in {
  opacity: 0;
  transform: translateY(30px);  /* 등장 거리 (30px → 50px로 늘리면 더 dramatic) */
  transition: opacity var(--transition-slow),
              transform var(--transition-slow);
}
```

### 애니메이션 끄기

```css
.fade-in {
  opacity: 1;
  transform: none;
  transition: none;
}
```

---

## 아이콘 수정

모든 아이콘은 **인라인 SVG**로 구현되어 있습니다.

### 아이콘 색상 변경

```css
/* 네비게이션 로고 아이콘 */
.nav-logo svg {
  color: var(--color-copper);  /* 코퍼 → 다른 색 */
}

/* 메뉴 카드 아이콘 */
.menu-icon {
  color: var(--color-amber);
}
```

### 아이콘 크기 변경

```css
.menu-icon {
  width: 48px;   /* 기본값 */
  height: 48px;
}
```

### 사용 중인 아이콘 목록

| 아이콘 | 용도 | 위치 |
|--------|------|------|
| 커피컵 | 메뉴 카테고리 | menu.html |
| 비커/플라스크 | 연구소 컨셉 | laboratory.html |
| 위치 핀 | 매장 위치 | location.html |
| 시계 | 운영 시간 | location.html |

---

## 다크 모드 관리

각성연구소는 **다크 모드가 기본**입니다.

### 현재 다크 모드 설정

```css
body {
  color: var(--color-cream);        /* 밝은 텍스트 */
  background-color: var(--color-dark);  /* 어두운 배경 */
}
```

### 라이트 모드로 전환하려면

```css
:root {
  /* 배경 색상 밝게 */
  --color-dark: #FAFAFA;
  --color-charcoal: #FFFFFF;

  /* 텍스트 색상 어둡게 */
  --color-cream: #1A1A1A;
  --color-white: #0D0D0D;
}
```

### 다크/라이트 모드 토글 (고급)

미디어 쿼리를 사용한 시스템 설정 연동:

```css
@media (prefers-color-scheme: light) {
  :root {
    --color-dark: #FAFAFA;
    --color-cream: #1A1A1A;
  }
}
```

---

## 실전 예제

### 예제 1: 강조 색상 전체 변경 (코퍼 → 로즈 골드)

`css/style.css` 수정:

```css
/* 변경 전 */
--color-copper: #B87333;
--color-amber: #D4A574;
--color-highlight: #C9A66B;

/* 변경 후 (로즈 골드) */
--color-copper: #B76E79;
--color-amber: #E8B4BC;
--color-highlight: #D4A5A5;
```

### 예제 2: 배경에 미세한 텍스처 추가

```css
body {
  background-color: var(--color-dark);
  background-image: url('../assets/images/noise-texture.png');
  background-blend-mode: overlay;
}
```

### 예제 3: 카드 호버 효과 강화

```css
.menu-card:hover {
  transform: translateY(-8px);  /* -4px → -8px */
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);  /* 그림자 강화 */
  border-color: var(--color-copper);
}
```

### 예제 4: 네비게이션 고정 (스크롤 시)

```css
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(13, 13, 13, 0.95);
  backdrop-filter: blur(10px);
}

body {
  padding-top: 80px;  /* 네비게이션 높이만큼 여백 */
}
```

### 예제 5: 글꼴 크기 전체 확대

```css
html {
  font-size: 18px;  /* 기본 16px → 18px */
}
```

모든 rem 단위가 자동으로 확대됩니다.

---

## 빠른 참조 표

| 변경 항목 | 수정 파일 | 줄 번호 |
|----------|----------|---------|
| 메인 강조색 (코퍼) | style.css | 13 |
| 보조 강조색 (앰버) | style.css | 14 |
| 배경색 (다크) | style.css | 8~10 |
| 텍스트색 (크림) | style.css | 15 |
| 제목 폰트 | style.css | 26 |
| 본문 폰트 | style.css | 27 |
| 모노 폰트 | style.css | 28 |
| 간격/여백 | style.css | 30~37 |
| 애니메이션 속도 | style.css | 39~42 |

---

## 디자인 원칙 (CLAUDE.md에서 발췌)

### 지향점
- 다크 모드 기본 (미니멀, 실험실 느낌)
- 충분한 여백 (breathable layout)
- 어두운 톤의 무드있는 커피 사진
- 부드럽고 절제된 애니메이션

### 피해야 할 것
- 과도한 그라디언트 / 네온 색상
- 스톡 이미지 느낌의 밝은 사진
- 너무 둥근 모서리 (rounded-full)
- 과한 애니메이션
- 보라-파랑 AI 스타일 그라디언트

---

## 로컬 테스트 방법

```bash
cd /Users/miaro/claude/coffee/Awakening
python -m http.server 8000
```

브라우저에서 http://localhost:8000 접속하여 변경사항을 확인하세요.

---

*이 문서는 각성연구소 커피 브랜드 홈페이지 디자인 관리를 위해 작성되었습니다.*
