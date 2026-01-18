# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**각성연구소 (Awakening Lab)** - 프리미엄 커피 브랜드 홈페이지

커피를 통한 감각의 각성과 영감을 연구하는 실험적 커피 브랜드의 웹사이트.

## Site Structure

```
├── index.html          # 메인 페이지 (Hero + 브랜드 소개)
├── menu.html           # 서브페이지 1: 메뉴 (시그니처 음료)
├── laboratory.html     # 서브페이지 2: 연구소 (브랜드 스토리, 원두 연구)
├── location.html       # 서브페이지 3: 위치 (매장 정보)
├── css/
│   └── style.css
├── js/
│   └── main.js
└── assets/
    ├── icons/          # SVG 아이콘
    └── images/         # 이미지 파일
```

## Navigation Menu

| 메뉴 | 파일 | 설명 |
|------|------|------|
| HOME | index.html | 메인 랜딩 페이지 |
| MENU | menu.html | 시그니처 음료 & 원두 |
| LABORATORY | laboratory.html | 브랜드 스토리 & 연구 철학 |
| LOCATION | location.html | 매장 위치 & 운영 정보 |

## Brand Identity

### Brand Concept
- **키워드**: 각성, 연구, 실험, 감각, 영감
- **톤앤매너**: 미니멀하면서 실험실 같은 정제된 느낌
- **무드**: 어두운 배경 + 따뜻한 악센트 컬러

### Color Palette

```css
:root {
  /* Primary - 깊은 커피/에스프레소 톤 */
  --color-dark: #0D0D0D;
  --color-charcoal: #1A1A1A;
  --color-espresso: #2C1810;

  /* Accent - 따뜻한 커피 톤 */
  --color-copper: #B87333;
  --color-amber: #D4A574;
  --color-cream: #F5E6D3;

  /* Neutral */
  --color-white: #FAFAFA;
  --color-gray: #6B6B6B;

  /* Semantic */
  --color-highlight: #C9A66B;
}
```

### Typography

```css
/* 헤딩 - 세리프 또는 고딕 조합 */
--font-display: 'Playfair Display', 'Noto Serif KR', serif;

/* 본문 */
--font-body: 'Pretendard', -apple-system, sans-serif;

/* 영문 악센트 */
--font-accent: 'Space Mono', monospace;
```

### Icon Style

SVG 아이콘 사용 (인라인 또는 파일):
- **스타일**: Outline (선 두께 1.5px)
- **크기**: 24px, 32px, 48px
- **색상**: currentColor 사용하여 텍스트 색상 상속

핵심 아이콘:
- 커피 컵 / 원두
- 비커 / 플라스크 (연구소 컨셉)
- 온도계 / 저울 (정밀함)
- 드리퍼 / 추출 도구
- 위치 핀 / 시계

## Page Specifications

### 1. 메인 페이지 (index.html)

```
┌─────────────────────────────────────┐
│           NAVIGATION                │
├─────────────────────────────────────┤
│                                     │
│           HERO SECTION              │
│    "감각을 깨우는 한 잔의 실험"        │
│         [각성연구소 로고]             │
│                                     │
├─────────────────────────────────────┤
│         BRAND STATEMENT             │
│     커피 연구 철학 소개 텍스트         │
├─────────────────────────────────────┤
│         FEATURED MENU               │
│    [카드1] [카드2] [카드3]            │
├─────────────────────────────────────┤
│           FOOTER                    │
└─────────────────────────────────────┘
```

### 2. 메뉴 페이지 (menu.html)

- 시그니처 음료 그리드 (이미지 + 설명)
- 원두 라인업
- 카테고리 필터 (에스프레소, 브루잉, 시즌 한정)

### 3. 연구소 페이지 (laboratory.html)

- 브랜드 스토리 (타임라인 또는 스크롤 기반)
- 로스팅 & 추출 연구 프로세스
- 팀 소개 (바리스타/로스터)

### 4. 위치 페이지 (location.html)

- 매장 지도 (정적 이미지 또는 임베드)
- 운영 시간
- 연락처 정보

## Design Guidelines

### Visual Style
- 다크 모드 기본
- 여백 충분히 사용 (breathable layout)
- 이미지는 무드있는 커피 사진 (어두운 톤, 따뜻한 조명)
- 미세한 그레인/노이즈 텍스처 오버레이 (선택)

### Animation
- 부드러운 페이드인 (스크롤 트리거)
- 호버 시 미묘한 스케일/색상 변화
- 페이지 전환 시 부드러운 트랜지션

### Responsive Breakpoints
```css
/* Mobile */   @media (max-width: 767px)
/* Tablet */   @media (min-width: 768px)
/* Desktop */  @media (min-width: 1024px)
/* Wide */     @media (min-width: 1440px)
```

## Tech Stack

- **HTML5**: 시맨틱 마크업
- **CSS3**: CSS 변수, Flexbox, Grid
- **JavaScript**: Vanilla JS (가벼운 인터랙션)
- **Fonts**: Google Fonts (Playfair Display, Pretendard CDN)
- **Icons**: 인라인 SVG

## Anti-Patterns (피해야 할 것)

- 과도한 그라디언트 / 네온 색상
- 스톡 이미지 느낌의 밝은 사진
- 너무 둥근 모서리 (rounded-full 남용)
- 과한 애니메이션
- 보라-파랑 AI 스타일 그라디언트

## File Naming Convention

```
css/style.css
js/main.js
assets/icons/icon-coffee.svg
assets/icons/icon-flask.svg
assets/images/hero-bg.jpg
assets/images/menu-signature-01.jpg
```

## Build Commands

정적 사이트이므로 빌드 불필요. 로컬 서버 실행:

```bash
# Python
python -m http.server 8000

# Node.js (npx 사용)
npx serve .
```
