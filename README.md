# 🖥 Portfolio Website

    반응형 웹사이트 제작
    
    기술 : HTML, CSS, JAVASCRIPT, JQUERY, swiper slide, AOS
    프로그램 : 피그마, 비주얼 스튜디오 코드
    링크 : https://luv-hanna.github.io/Salady/


---

## 🔍 Self Review

### 📁 1. 파일 구조 및 구성
- [x] 역할별로 디렉토리 분리 (`/css`, `/js`, `/images`)
- [x] 인라인 스타일, 스크립트 제거 → 외부 파일로 분리 완료
- [x] 파일/폴더 네이밍 일관성 유지
- [x] index.html을 루트 디렉토리에 배치하여 진입점 명확화

---

### 🧱 2. HTML 리뷰
```html
<header class="header">
    <nav class="nav">
        <ul class="gnb">
            <li><a href="#">브랜드</a></li>
        </ul>
    </nav>
</header>

<div class="main">
    <div class="main_visual"> ... </div>
</div>
```
- [ ] 의미론적 태그 사용이 부족함 (`<article>`, `<section>`, `<header>`, `<main>`, `<nav>` 등)
- [ ] `div id="main"` 의 `div`대신 `<main>` 태그 사용이 필요함
- [ ] heading 태그는 순차적으로 구조화 필요함 (`<h1>` → `<h2>` → `<h3>` 등 계층 구조 미흡)
- [x] 모든 이미지에 `alt` 속성 적용
- [x] 폼 요소는 없으나 버튼 등 UI 요소에 시각적 연결 적절함
- [ ] `<h1>` 태그가 여러 번 사용됨 → 한 페이지에 하나만 사용하도록 구조 변경 예정
- [ ] `<a>` 태그 안에 `<button>` 태그가 포함되어 있음 → `<a>`만 사용하거나 `<button>`만 사용하도록 일관성 필요
- [ ] 중복되는 메뉴 구조 (`<nav class="hav">` 등)는 유지보수와 접근성 측면에서 개선 필요
- [x] `<header>`와 `<nav>` 시맨틱 태그는 적절히 사용됨

---

### 🎨 3. CSS 리뷰
- [x]  @font-face를 활용한 웹폰트 정의 및 다양한 굵기 분리 (Pretendard, Red Hat Display, Mont 등)
- [x] 초기화 스타일 적용 (*, li, a, body, button 등 기본 리셋 완료)
- [x] 레이아웃 요소에 flex, gap, margin, padding 등을 활용해 유연한 배치 구성
- [x] 컴포넌트 단위로 hover 효과, 트랜지션 등 시각적 인터랙션 부여
- [x] 중복되는 디자인 요소는 일관성 있게 사용 (버튼, 텍스트, 타이포 등)
- [ ] common.css, reset.css 파일로 스타일 분리 필요 → 유지보수성과 가독성 향상 가능
- [ ] 반응형 웹 대응 없음 → @media 쿼리 적용하여 다양한 해상도 대응 필요
- [ ] .section-01, .main_visual 등 고정된 width, height, px 단위 다수 사용 → 상대 단위(%, vw, vh)로의 전환 고려 가능

---

### ⚙️ 4. JavaScript 리뷰
```javascript
window.onload = () => {

    menuBtn.addEventListener('click', () => {
        allMenu.classList.toggle('active');
    });

    var meSwiper = new Swiper(".meSwiper", { ... });

    fixedBtn.addEventListener('click', () => {
        Menu.classList.toggle('active');
    });

    AOS.init();

    scrollToTopButton.addEventListener('click', () => {
        window.scrollTo({ top: 0, behavior: 'smooth' });
    });
};
```

- [x] Swiper, AOS 등 외부 라이브러리 정상 적용 및 초기화
- [x] 메뉴 토글, 슬라이드, 스크롤 이동 등 사용자 인터랙션 기능 구현 완료
- [x] window.onload 내부에 모든 기능을 그룹화하여 초기 실행 흐름을 명확히 구성함
- [ ] 이벤트 핸들러와 관련 DOM 요소가 기능별로 섞여 있음 → 함수로 분리하여 코드 모듈화 필요
- [ ] 변수명 일부가 추상적 (Menu, allMenu) → 기능을 설명하는 의미 있는 이름 사용 권장 (fixedMenu, mobileMenu 등)
- [ ] scrollToTopButton.style.display = 'block'이 스크롤 여부와 관계없이 항상 실행됨 → 조건문 로직 수정 필요

```javascript
 if (window.scrollY > 300) {
    scrollToTopButton.style.display = 'block';
} else {
    scrollToTopButton.style.display = 'none';
}
```
- [ ] 중복되는 Swiper 초기화 코드를 공통 함수로 추출 가능
- [x] 모든 Swiper에 loop, spaceBetween, slidesPerView 등 옵션 명확히 지정함

---

### 🎯 5. UX/UI 측면
- [x] 인터랙션 요소(버튼, 메뉴 등)에 hover 및 focus 스타일 적용 완료
- [x] 디자인의 시각적 계층 구조가 명확함 → 타이포그래피, 여백, 색 대비 등
- [ ] 특정 콘텐츠(PPL, 영상 등)로 직접 이동할 수 있는 링크 기능 미구현 → CTA(Button) 추가 예정

<img src="https://github.com/user-attachments/assets/3d912a77-3388-4aeb-91e4-671d61d0177a" style="width: 500px;"/>

---

## 🛠️ 6. 개선 계획 (To-Do)
- [ ] `<h1>` 태그 구조 개선 → 한 페이지에 하나만 사용되도록 시맨틱 구조 조정
- [ ] JavaScript 함수명 정비 → 추상적인 이름(Menu, allMenu) → 구체적 기능 기반 네이밍으로 변경
- [ ] 로딩 애니메이션 추가
- [ ] 불필요한 font 파일 제거 → 실제 사용하지 않는 굵기 또는 폰트는 제거하여 용량 최적화

---

## ✅ 참고 도구
- [W3C HTML Validator](https://validator.w3.org/)
- [Lighthouse Performance Check (Chrome DevTools)](https://developer.chrome.com/docs/lighthouse/overview/)
- [Wave Accessibility Checker](https://wave.webaim.org/)
