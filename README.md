<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>임현빈 포트폴리오</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@400;700&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">

  <style>
    /* ============================================================
       CSS 변수 — 무지개 섹션 팔레트
       섹션별: red → orange → yellow → green → blue → indigo → violet
    ============================================================ */
    :root {
      --nav-bg:       #0f0f1a;
      --nav-accent:   #fff;

      /* 섹션별 배경 & 포인트 컬러 */
      --hero-bg:      #0f0f1a;
      --hero-line:    linear-gradient(90deg,#ff6b6b,#ffa94d,#ffe066,#69db7c,#74c0fc,#9775fa,#f783ac);

      --about-bg:     #fff5f5;   /* 빨강 계열 */
      --about-acc:    #e03131;
      --about-badge:  #ffc9c9;
      --about-bdg-t:  #c92a2a;

      --act-bg:       #fff4e6;   /* 주황 계열 */
      --act-acc:      #e8590c;
      --act-badge:    #ffd8a8;
      --act-bdg-t:    #d9480f;

      --proj-bg:      #fff9db;   /* 노랑 계열 */
      --proj-acc:     #f08c00;
      --proj-badge:   #ffec99;
      --proj-bdg-t:   #e67700;

      --gal-bg:       #ebfbee;   /* 초록 계열 */
      --gal-acc:      #2f9e44;
      --gal-badge:    #b2f2bb;
      --gal-bdg-t:    #2b8a3e;

      --vid-bg:       #e7f5ff;   /* 파랑 계열 */
      --vid-acc:      #1971c2;
      --vid-badge:    #a5d8ff;
      --vid-bdg-t:    #1864ab;

      --con-bg:       #f3f0ff;   /* 보라 계열 */
      --con-acc:      #7048e8;
      --con-badge:    #d0bfff;
      --con-bdg-t:    #5f3dc4;

      --footer-bg:    #0f0f1a;

      --card-bg:      #ffffff;
      --card-radius:  12px;
      --card-shadow:  0 2px 16px rgba(0,0,0,0.07);
      --text-main:    #1a1a2e;
      --text-sub:     #555;
      --text-muted:   #999;
      --transition:   0.22s ease;
    }

    /* ============================================================
       리셋 & 기본
    ============================================================ */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; font-size: 16px; }
    body {
      font-family: 'Noto Sans KR', sans-serif;
      color: var(--text-main);
      line-height: 1.75;
      background: #fafafa;
    }
    a { text-decoration: none; color: inherit; }
    img { display: block; max-width: 100%; }

    /* ============================================================
       관리자 상태 바
    ============================================================ */
    #admin-bar {
      display: none;
      background: linear-gradient(90deg,#ff6b6b,#ffa94d,#ffe066,#69db7c,#74c0fc,#9775fa);
      color: #fff;
      font-size: 0.8rem;
      font-weight: 500;
      padding: 7px 24px;
      text-align: center;
      letter-spacing: 0.04em;
    }
    #admin-bar.active { display: flex; align-items: center; justify-content: center; gap: 16px; }
    #admin-bar button {
      background: rgba(255,255,255,0.25);
      border: 1px solid rgba(255,255,255,0.6);
      color: #fff;
      padding: 2px 12px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 0.76rem;
      font-family: inherit;
      transition: background var(--transition);
    }
    #admin-bar button:hover { background: rgba(255,255,255,0.45); }

    /* ============================================================
       내비게이션
    ============================================================ */
    #nav {
      position: sticky;
      top: 0;
      z-index: 100;
      background: var(--nav-bg);
      height: 60px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 32px;
      box-shadow: 0 2px 12px rgba(0,0,0,0.4);
    }
    #nav .nav-logo {
      font-family: 'Noto Serif KR', serif;
      color: #fff;
      font-size: 1.05rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      /* 로고에 무지개 그라디언트 */
      background: var(--hero-line);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    #nav ul {
      display: flex;
      gap: 28px;
      list-style: none;
    }
    #nav ul a {
      color: #aaa;
      font-size: 0.82rem;
      letter-spacing: 0.04em;
      transition: color var(--transition);
      position: relative;
      padding-bottom: 2px;
    }
    #nav ul a::after {
      content: '';
      position: absolute;
      bottom: -2px; left: 0;
      width: 0; height: 2px;
      background: var(--hero-line);
      border-radius: 2px;
      transition: width var(--transition);
    }
    #nav ul a:hover { color: #fff; }
    #nav ul a:hover::after { width: 100%; }

    #admin-btn {
      background: transparent;
      border: 1px solid rgba(255,255,255,0.25);
      color: #aaa;
      padding: 5px 14px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 0.76rem;
      font-family: inherit;
      letter-spacing: 0.04em;
      transition: all var(--transition);
    }
    #admin-btn:hover { border-color: rgba(255,255,255,0.6); color: #fff; }

    /* ============================================================
       히어로 섹션
    ============================================================ */
    #hero {
      background: var(--hero-bg);
      padding: 100px 24px 80px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    /* 배경 무지개 광선 효과 */
    #hero::before {
      content: '';
      position: absolute;
      top: -120px; left: 50%;
      transform: translateX(-50%);
      width: 700px; height: 700px;
      border-radius: 50%;
      background: conic-gradient(
        from 200deg,
        rgba(255,107,107,0.12),
        rgba(255,169,77,0.10),
        rgba(255,224,102,0.10),
        rgba(105,219,124,0.10),
        rgba(116,192,252,0.10),
        rgba(151,117,250,0.12),
        rgba(247,131,172,0.10),
        rgba(255,107,107,0.08)
      );
      pointer-events: none;
    }
    #hero .hero-avatar {
      width: 100px; height: 100px;
      border-radius: 50%;
      background: linear-gradient(135deg,#ff6b6b,#ffa94d,#ffe066,#69db7c,#74c0fc,#9775fa);
      display: flex; align-items: center; justify-content: center;
      font-family: 'Noto Serif KR', serif;
      font-size: 2rem; color: #fff;
      margin: 0 auto 28px;
      box-shadow: 0 0 0 4px rgba(255,255,255,0.08), 0 8px 32px rgba(0,0,0,0.3);
      position: relative; z-index: 1;
    }
    #hero .hero-name {
      font-family: 'Noto Serif KR', serif;
      font-size: 2.8rem;
      font-weight: 700;
      color: #fff;
      letter-spacing: 0.06em;
      margin-bottom: 10px;
      position: relative; z-index: 1;
    }
    /* 이름 아래 무지개 밑줄 */
    #hero .hero-rainbow-bar {
      width: 120px;
      height: 3px;
      background: var(--hero-line);
      border-radius: 2px;
      margin: 0 auto 20px;
    }
    #hero .hero-tagline {
      font-size: 1rem;
      color: #bbb;
      margin-bottom: 20px;
      letter-spacing: 0.04em;
      position: relative; z-index: 1;
    }
    #hero .hero-bio {
      font-size: 0.92rem;
      color: #888;
      max-width: 480px;
      margin: 0 auto;
      line-height: 1.9;
      position: relative; z-index: 1;
    }
    /* 스크롤 유도 화살표 */
    #hero .scroll-hint {
      margin-top: 48px;
      position: relative; z-index: 1;
    }
    #hero .scroll-hint span {
      display: inline-block;
      width: 24px; height: 24px;
      border-right: 2px solid #555;
      border-bottom: 2px solid #555;
      transform: rotate(45deg);
      animation: bounce 1.4s infinite;
    }
    @keyframes bounce {
      0%,100% { transform: rotate(45deg) translateY(0); opacity:.4; }
      50%      { transform: rotate(45deg) translateY(6px); opacity:1; }
    }

    /* ============================================================
       공통 섹션 래퍼
    ============================================================ */
    .section-wrap {
      padding: 72px 0;
    }
    .section-inner {
      max-width: 900px;
      margin: 0 auto;
      padding: 0 32px;
    }
    .section-header {
      display: flex;
      align-items: baseline;
      gap: 14px;
      margin-bottom: 36px;
    }
    .section-label {
      font-size: 0.68rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      font-weight: 600;
      opacity: 0.55;
    }
    .section-title {
      font-family: 'Noto Serif KR', serif;
      font-size: 1.7rem;
      font-weight: 700;
    }
    /* 섹션 제목 왼쪽 컬러 바 */
    .section-title-bar {
      display: inline-block;
      width: 5px;
      height: 1.6rem;
      border-radius: 3px;
      margin-right: 10px;
      vertical-align: middle;
    }

    /* ============================================================
       카드 공통
    ============================================================ */
    .card {
      background: var(--card-bg);
      border-radius: var(--card-radius);
      box-shadow: var(--card-shadow);
      padding: 22px 26px;
      transition: transform var(--transition), box-shadow var(--transition);
      position: relative;
      overflow: hidden;
    }
    .card:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 28px rgba(0,0,0,0.11);
    }
    /* 카드 좌측 컬러 accent 선 */
    .card::before {
      content: '';
      position: absolute;
      left: 0; top: 0; bottom: 0;
      width: 4px;
      border-radius: 12px 0 0 12px;
      background: var(--card-accent, #ddd);
    }
    .card-badge {
      display: inline-block;
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      padding: 3px 10px;
      border-radius: 20px;
      margin-bottom: 10px;
      background: var(--badge-bg, #eee);
      color: var(--badge-color, #555);
    }
    .card-title {
      font-size: 1rem;
      font-weight: 700;
      color: var(--text-main);
      margin-bottom: 6px;
    }
    .card-desc {
      font-size: 0.87rem;
      color: var(--text-sub);
      line-height: 1.75;
    }
    .card-date {
      font-size: 0.74rem;
      color: var(--text-muted);
      margin-top: 10px;
      display: flex;
      align-items: center;
      gap: 5px;
    }
    .card-date::before {
      content: '';
      display: inline-block;
      width: 14px; height: 1px;
      background: var(--text-muted);
    }

    /* ============================================================
       그리드
    ============================================================ */
    .grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 18px;
    }

    /* ============================================================
       [1] 자기소개 — 빨강 계열
    ============================================================ */
    #section-about {
      background: var(--about-bg);
    }
    #section-about .section-label { color: var(--about-acc); }
    #section-about .section-title { color: var(--about-acc); }
    #section-about .section-title-bar { background: var(--about-acc); }
    #section-about .card { --card-accent: var(--about-acc); --badge-bg: var(--about-badge); --badge-color: var(--about-bdg-t); }
    #about-text-card {
      font-size: 0.95rem;
      color: var(--text-sub);
      line-height: 2;
      margin-bottom: 20px;
    }

    /* ============================================================
       [2] 교내외 활동 — 주황 계열
    ============================================================ */
    #section-activities {
      background: var(--act-bg);
    }
    #section-activities .section-label { color: var(--act-acc); }
    #section-activities .section-title { color: var(--act-acc); }
    #section-activities .section-title-bar { background: var(--act-acc); }
    #section-activities .card { --card-accent: var(--act-acc); --badge-bg: var(--act-badge); --badge-color: var(--act-bdg-t); }

    /* ============================================================
       [3] 프로젝트 — 노랑 계열
    ============================================================ */
    #section-projects {
      background: var(--proj-bg);
    }
    #section-projects .section-label { color: var(--proj-acc); }
    #section-projects .section-title { color: var(--proj-acc); }
    #section-projects .section-title-bar { background: var(--proj-acc); }
    #section-projects .card { --card-accent: var(--proj-acc); --badge-bg: var(--proj-badge); --badge-color: var(--proj-bdg-t); }
    #projects-list { display: flex; flex-direction: column; gap: 18px; }

    /* ============================================================
       [4] 작품 갤러리 — 초록 계열
    ============================================================ */
    #section-gallery {
      background: var(--gal-bg);
    }
    #section-gallery .section-label { color: var(--gal-acc); }
    #section-gallery .section-title { color: var(--gal-acc); }
    #section-gallery .section-title-bar { background: var(--gal-acc); }

    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
      gap: 14px;
    }
    .gallery-item {
      aspect-ratio: 1 / 1;
      background: #fff;
      border: 2px dashed var(--gal-badge);
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.78rem;
      color: var(--gal-acc);
      text-align: center;
      cursor: pointer;
      transition: transform var(--transition), box-shadow var(--transition);
      overflow: hidden;
    }
    .gallery-item:hover {
      transform: scale(1.03);
      box-shadow: 0 6px 20px rgba(47,158,68,0.15);
    }
    .gallery-item img {
      width: 100%; height: 100%;
      object-fit: cover;
      border-radius: 8px;
    }

    /* ============================================================
       [5] 영상 갤러리 — 파랑 계열
    ============================================================ */
    #section-video {
      background: var(--vid-bg);
    }
    #section-video .section-label { color: var(--vid-acc); }
    #section-video .section-title { color: var(--vid-acc); }
    #section-video .section-title-bar { background: var(--vid-acc); }

    .video-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 18px;
    }
    .video-item {
      background: #fff;
      border-radius: var(--card-radius);
      box-shadow: var(--card-shadow);
      overflow: hidden;
      border-top: 4px solid var(--vid-acc);
      transition: transform var(--transition), box-shadow var(--transition);
    }
    .video-item:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 28px rgba(25,113,194,0.13);
    }
    .video-placeholder {
      aspect-ratio: 16 / 9;
      background: var(--vid-bg);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 10px;
      font-size: 0.82rem;
      color: var(--vid-acc);
    }
    .video-placeholder .play-icon {
      width: 44px; height: 44px;
      border-radius: 50%;
      border: 2px solid var(--vid-badge);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem;
    }
    .video-item iframe, .video-item video {
      width: 100%; aspect-ratio: 16/9;
      display: block; border: none;
    }
    .video-caption {
      padding: 12px 16px;
      font-size: 0.88rem;
      font-weight: 600;
      color: var(--text-main);
      border-top: 1px solid #e7f5ff;
    }

    /* ============================================================
       [6] 연락처 — 보라 계열
    ============================================================ */
    #section-contact {
      background: var(--con-bg);
    }
    #section-contact .section-label { color: var(--con-acc); }
    #section-contact .section-title { color: var(--con-acc); }
    #section-contact .section-title-bar { background: var(--con-acc); }

    .contact-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 14px;
    }
    .contact-item {
      background: #fff;
      border-radius: var(--card-radius);
      box-shadow: var(--card-shadow);
      padding: 20px 22px;
      border-bottom: 3px solid var(--con-acc);
      transition: transform var(--transition);
    }
    .contact-item:hover { transform: translateY(-2px); }
    .contact-label {
      font-size: 0.68rem;
      text-transform: uppercase;
      letter-spacing: 0.14em;
      color: var(--con-acc);
      font-weight: 700;
      margin-bottom: 6px;
    }
    .contact-value {
      font-size: 0.92rem;
      font-weight: 500;
      color: var(--text-main);
      word-break: break-all;
    }
    .contact-value a { color: var(--con-acc); }
    .contact-value a:hover { text-decoration: underline; }

    /* ============================================================
       섹션 구분 디바이더 (무지개 줄)
    ============================================================ */
    .rainbow-divider {
      height: 4px;
      background: var(--hero-line);
    }

    /* ============================================================
       푸터
    ============================================================ */
    #footer {
      background: var(--footer-bg);
      color: #555;
      text-align: center;
      padding: 28px 24px;
      font-size: 0.8rem;
      letter-spacing: 0.04em;
    }
    #footer .rainbow-text {
      background: var(--hero-line);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      font-weight: 700;
    }

    /* ============================================================
       로그인 모달
    ============================================================ */
    #login-modal {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.6);
      z-index: 200;
      align-items: center;
      justify-content: center;
      backdrop-filter: blur(4px);
    }
    #login-modal.open { display: flex; }
    .modal-box {
      background: #fff;
      border-radius: 16px;
      padding: 36px;
      width: min(380px, 92vw);
      box-shadow: 0 24px 60px rgba(0,0,0,0.25);
    }
    .modal-rainbow-top {
      height: 4px;
      background: var(--hero-line);
      border-radius: 16px 16px 0 0;
      margin: -36px -36px 28px;
    }
    .modal-box h3 {
      font-family: 'Noto Serif KR', serif;
      font-size: 1.2rem;
      color: var(--text-main);
      margin-bottom: 22px;
    }
    .modal-box label {
      display: block;
      font-size: 0.76rem;
      font-weight: 600;
      letter-spacing: 0.06em;
      color: #888;
      margin-bottom: 5px;
      margin-top: 14px;
    }
    .modal-box input {
      width: 100%;
      padding: 10px 14px;
      border: 1.5px solid #e0e0e0;
      border-radius: 8px;
      font-size: 0.9rem;
      font-family: inherit;
      outline: none;
      transition: border-color var(--transition);
    }
    .modal-box input:focus { border-color: #9775fa; }
    .modal-error {
      color: #e03131;
      font-size: 0.78rem;
      margin-top: 8px;
      display: none;
    }
    .modal-footer {
      display: flex;
      justify-content: flex-end;
      gap: 10px;
      margin-top: 24px;
    }
    .btn {
      padding: 9px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 0.85rem;
      font-family: inherit;
      font-weight: 500;
      transition: opacity var(--transition), transform var(--transition);
    }
    .btn:hover { opacity: 0.88; transform: translateY(-1px); }
    .btn-primary {
      background: linear-gradient(135deg,#7048e8,#9775fa);
      color: #fff;
    }
    .btn-ghost {
      background: #f3f0ff;
      color: #7048e8;
    }

    /* ============================================================
       스크롤 페이드인 애니메이션
    ============================================================ */
    .fade-in {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.55s ease, transform 0.55s ease;
    }
    .fade-in.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ============================================================
       반응형
    ============================================================ */
    @media (max-width: 680px) {
      #nav ul { display: none; }
      #hero .hero-name { font-size: 2rem; }
      .section-inner { padding: 0 18px; }
    }
  </style>
</head>
<body>

  <!-- 관리자 상태 바 -->
  <div id="admin-bar">
    <span>🌈 관리자 모드 활성화</span>
    <button onclick="logout()">로그아웃</button>
  </div>

  <!-- ============================================================
       내비게이션  id="nav"
  ============================================================ -->
  <nav id="nav">
    <a href="#hero" class="nav-logo">임현빈 Portfolio</a>
    <ul>
      <li><a href="#section-about">자기소개</a></li>
      <li><a href="#section-activities">활동</a></li>
      <li><a href="#section-projects">프로젝트</a></li>
      <li><a href="#section-gallery">작품</a></li>
      <li><a href="#section-video">영상</a></li>
      <li><a href="#section-contact">연락처</a></li>
    </ul>
    <button id="admin-btn" onclick="openLoginModal()">관리자 ↗</button>
  </nav>

  <!-- ============================================================
       히어로  id="hero"
  ============================================================ -->
  <header id="hero">
    <div class="hero-avatar" id="hero-avatar">현</div>
    <h1 class="hero-name" id="hero-name">임현빈</h1>
    <div class="hero-rainbow-bar"></div>
    <p class="hero-tagline" id="hero-tagline">성장하는 인재, 도전하는 고등학생</p>
    <p class="hero-bio" id="hero-bio">
      안녕하세요! 저는 새로운 것을 배우는 것을 즐기고,<br>
      팀워크와 창의적인 문제 해결을 중요하게 생각하는<br>
      고등학생 임현빈입니다.
    </p>
    <div class="scroll-hint"><span></span></div>
  </header>

  <div class="rainbow-divider"></div>

  <!-- ============================================================
       [1] 자기소개  id="section-about"  — 빨강 계열
  ============================================================ -->
  <div class="section-wrap" id="section-about">
    <div class="section-inner">
      <div class="section-header fade-in">
        <span class="section-title-bar"></span>
        <div>
          <p class="section-label">About Me</p>
          <h2 class="section-title">자기소개</h2>
        </div>
      </div>

      <div class="card fade-in" id="about-text-card">
        <p id="about-text">
          저는 □□고등학교에 재학 중인 임현빈입니다.
          학교에서 다양한 교내외 활동에 참여하며 협업 능력과 창의적 사고력을 키워왔습니다.
          특히 프로젝트 기반 학습과 실습 경험을 통해 이론을 실제로 적용하는 능력을 길렀습니다.
          앞으로도 끊임없이 배우고 성장하는 인재가 되겠습니다.
        </p>
      </div>

      <div class="grid-2">
        <div class="card fade-in" id="about-school-card">
          <span class="card-badge">학교</span>
          <p class="card-title" id="about-school">□□고등학교</p>
          <p class="card-desc" id="about-grade">○학년 재학 중</p>
        </div>
        <div class="card fade-in" id="about-interest-card">
          <span class="card-badge">관심 분야</span>
          <p class="card-title" id="about-interest">관심 분야를 입력하세요</p>
          <p class="card-desc" id="about-interest-desc">관심 분야에 대한 짧은 설명을 적어보세요.</p>
        </div>
      </div>
    </div>
  </div>

  <div class="rainbow-divider"></div>

  <!-- ============================================================
       [2] 주요 교내외 활동  id="section-activities"  — 주황 계열
  ============================================================ -->
  <div class="section-wrap" id="section-activities">
    <div class="section-inner">
      <div class="section-header fade-in">
        <span class="section-title-bar"></span>
        <div>
          <p class="section-label">Activities</p>
          <h2 class="section-title">주요 교내외 활동</h2>
        </div>
      </div>

      <div class="grid-2" id="activities-list">

        <div class="card activity-card fade-in" id="activity-1">
          <span class="card-badge">교내 활동</span>
          <p class="card-title">활동명을 입력하세요</p>
          <p class="card-desc">활동에 대한 설명을 입력하세요.</p>
          <p class="card-date">0000.00 ~ 0000.00</p>
        </div>

        <div class="card activity-card fade-in" id="activity-2">
          <span class="card-badge">교외 활동</span>
          <p class="card-title">활동명을 입력하세요</p>
          <p class="card-desc">활동에 대한 설명을 입력하세요.</p>
          <p class="card-date">0000.00 ~ 0000.00</p>
        </div>

        <div class="card activity-card fade-in" id="activity-3">
          <span class="card-badge">수상</span>
          <p class="card-title">수상명을 입력하세요</p>
          <p class="card-desc">수상 내용 및 주관 기관을 입력하세요.</p>
          <p class="card-date">0000.00</p>
        </div>

        <div class="card activity-card fade-in" id="activity-4">
          <span class="card-badge">봉사</span>
          <p class="card-title">봉사 활동명을 입력하세요</p>
          <p class="card-desc">봉사 내용 및 기관을 입력하세요.</p>
          <p class="card-date">0000.00 ~ 현재</p>
        </div>

      </div>
    </div>
  </div>

  <div class="rainbow-divider"></div>

  <!-- ============================================================
       [3] 프로젝트 경험  id="section-projects"  — 노랑 계열
  ============================================================ -->
  <div class="section-wrap" id="section-projects">
    <div class="section-inner">
      <div class="section-header fade-in">
        <span class="section-title-bar"></span>
        <div>
          <p class="section-label">Projects</p>
          <h2 class="section-title">프로젝트 경험</h2>
        </div>
      </div>

      <div id="projects-list">

        <div class="card project-card fade-in" id="project-1">
          <span class="card-badge">역할: 기획 / 디자인</span>
          <p class="card-title">프로젝트명을 입력하세요</p>
          <p class="card-desc">
            프로젝트에 대한 설명을 입력하세요.
            어떤 문제를 해결했는지, 본인의 역할은 무엇이었는지 작성해 보세요.
          </p>
          <p class="card-date">0000.00 ~ 0000.00</p>
        </div>

        <div class="card project-card fade-in" id="project-2">
          <span class="card-badge">역할: 개발</span>
          <p class="card-title">프로젝트명을 입력하세요</p>
          <p class="card-desc">
            프로젝트에 대한 설명을 입력하세요.
            어떤 기술을 사용했는지, 결과물은 무엇인지 작성해 보세요.
          </p>
          <p class="card-date">0000.00 ~ 0000.00</p>
        </div>

      </div>
    </div>
  </div>

  <div class="rainbow-divider"></div>

  <!-- ============================================================
       [4] 작품 갤러리  id="section-gallery"  — 초록 계열
  ============================================================ -->
  <div class="section-wrap" id="section-gallery">
    <div class="section-inner">
      <div class="section-header fade-in">
        <span class="section-title-bar"></span>
        <div>
          <p class="section-label">Gallery</p>
          <h2 class="section-title">작품 갤러리</h2>
        </div>
      </div>

      <div class="gallery-grid fade-in" id="gallery-grid">
        <div class="gallery-item" id="gallery-1"><span>작품 사진 1</span></div>
        <div class="gallery-item" id="gallery-2"><span>작품 사진 2</span></div>
        <div class="gallery-item" id="gallery-3"><span>작품 사진 3</span></div>
        <div class="gallery-item" id="gallery-4"><span>작품 사진 4</span></div>
        <div class="gallery-item" id="gallery-5"><span>작품 사진 5</span></div>
        <div class="gallery-item" id="gallery-6"><span>작품 사진 6</span></div>
      </div>
    </div>
  </div>

  <div class="rainbow-divider"></div>

  <!-- ============================================================
       [5] 영상 갤러리  id="section-video"  — 파랑 계열
  ============================================================ -->
  <div class="section-wrap" id="section-video">
    <div class="section-inner">
      <div class="section-header fade-in">
        <span class="section-title-bar"></span>
        <div>
          <p class="section-label">Videos</p>
          <h2 class="section-title">영상 갤러리</h2>
        </div>
      </div>

      <div class="video-grid fade-in" id="video-grid">

        <div class="video-item" id="video-1">
          <!--
            YouTube 삽입 시 아래 주석 해제:
            <iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe>
          -->
          <div class="video-placeholder">
            <div class="play-icon">▶</div>
            <span>영상 1 — URL 또는 파일 삽입</span>
          </div>
          <p class="video-caption">영상 제목을 입력하세요</p>
        </div>

        <div class="video-item" id="video-2">
          <div class="video-placeholder">
            <div class="play-icon">▶</div>
            <span>영상 2 — URL 또는 파일 삽입</span>
          </div>
          <p class="video-caption">영상 제목을 입력하세요</p>
        </div>

      </div>
    </div>
  </div>

  <div class="rainbow-divider"></div>

  <!-- ============================================================
       [6] 연락처  id="section-contact"  — 보라 계열
  ============================================================ -->
  <div class="section-wrap" id="section-contact">
    <div class="section-inner">
      <div class="section-header fade-in">
        <span class="section-title-bar"></span>
        <div>
          <p class="section-label">Contact</p>
          <h2 class="section-title">연락처</h2>
        </div>
      </div>

      <div class="contact-grid fade-in" id="contact-grid">

        <div class="contact-item" id="contact-email">
          <p class="contact-label">이메일</p>
          <p class="contact-value">
            <a href="mailto:example@email.com" id="contact-email-val">example@email.com</a>
          </p>
        </div>

        <div class="contact-item" id="contact-phone">
          <p class="contact-label">전화번호</p>
          <p class="contact-value" id="contact-phone-val">010-0000-0000</p>
        </div>

        <div class="contact-item" id="contact-school">
          <p class="contact-label">학교</p>
          <p class="contact-value" id="contact-school-val">□□고등학교</p>
        </div>

        <div class="contact-item" id="contact-sns">
          <p class="contact-label">SNS / 링크</p>
          <p class="contact-value">
            <a href="https://" id="contact-sns-val" target="_blank" rel="noopener">링크를 입력하세요</a>
          </p>
        </div>

      </div>
    </div>
  </div>

  <!-- ============================================================
       푸터  id="footer"
  ============================================================ -->
  <div class="rainbow-divider"></div>
  <footer id="footer">
    <p>© 2026 <span class="rainbow-text">임현빈</span> — 개인 포트폴리오</p>
  </footer>

  <!-- ============================================================
       관리자 로그인 모달  id="login-modal"
  ============================================================ -->
  <div id="login-modal">
    <div class="modal-box">
      <div class="modal-rainbow-top"></div>
      <h3>관리자 로그인</h3>

      <label for="login-id">아이디</label>
      <input type="text" id="login-id" placeholder="아이디 입력" autocomplete="username" />

      <label for="login-pw">비밀번호</label>
      <input type="password" id="login-pw" placeholder="비밀번호 입력" autocomplete="current-password"
             onkeydown="if(event.key==='Enter') doLogin()" />

      <p class="modal-error" id="login-error">아이디 또는 비밀번호가 틀렸습니다.</p>

      <div class="modal-footer">
        <button class="btn btn-ghost" onclick="closeLoginModal()">취소</button>
        <button class="btn btn-primary" onclick="doLogin()">로그인</button>
      </div>
    </div>
  </div>

  <!-- ============================================================
       JS — 로그인 + 스크롤 페이드인
  ============================================================ -->
  <script>
    const ADMIN_ID = 'Imhyeonbin';
    const ADMIN_PW = 'your3447*';

    /* 로그인 모달 */
    function openLoginModal() {
      document.getElementById('login-modal').classList.add('open');
      setTimeout(() => document.getElementById('login-id').focus(), 100);
    }
    function closeLoginModal() {
      document.getElementById('login-modal').classList.remove('open');
      document.getElementById('login-error').style.display = 'none';
    }
    document.getElementById('login-modal').addEventListener('click', function(e) {
      if (e.target === this) closeLoginModal();
    });

    function doLogin() {
      const id = document.getElementById('login-id').value.trim();
      const pw = document.getElementById('login-pw').value;
      const err = document.getElementById('login-error');
      if (id === ADMIN_ID && pw === ADMIN_PW) {
        closeLoginModal();
        setAdminMode(true);
        document.getElementById('login-id').value = '';
        document.getElementById('login-pw').value = '';
      } else {
        err.style.display = 'block';
      }
    }

    function logout() { setAdminMode(false); }

    function setAdminMode(on) {
      document.getElementById('admin-bar').classList.toggle('active', on);
    }

    /* 스크롤 페이드인 */
    const fadeEls = document.querySelectorAll('.fade-in');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry, i) => {
        if (entry.isIntersecting) {
          setTimeout(() => entry.target.classList.add('visible'), i * 60);
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12 });
    fadeEls.forEach(el => observer.observe(el));
  </script>

</body>
</html>
