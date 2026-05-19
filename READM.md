<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Correa Archives</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Barlow:wght@400;700;900&family=Barlow+Condensed:wght@700;900&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --black: #0a0a0a;
      --white: #f5f5f5;
      --gray-1: #1a1a1a;
      --gray-2: #2e2e2e;
      --gray-3: #888;
      --gray-4: #bbb;
      --font-display: 'Barlow Condensed', sans-serif;
      --font-body: 'Barlow', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--white);
      color: var(--black);
      font-family: var(--font-body);
      overflow-x: hidden;
      cursor: none;
    }

    /* CUSTOM CURSOR */
    .cursor {
      width: 10px; height: 10px;
      background: var(--black);
      border-radius: 50%;
      position: fixed;
      top: 0; left: 0;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%, -50%);
      transition: width 0.2s, height 0.2s, background 0.2s;
    }
    .cursor.hover {
      width: 40px; height: 40px;
      background: transparent;
      border: 1.5px solid var(--black);
    }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 28px 48px;
      mix-blend-mode: normal;
      background: rgba(245,245,245,0.88);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(0,0,0,0.07);
    }

    .nav-logo {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: 18px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      text-decoration: none;
      color: var(--black);
    }

    .nav-links {
      display: flex;
      gap: 40px;
      list-style: none;
    }

    .nav-links a {
      font-family: var(--font-body);
      font-size: 12px;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      text-decoration: none;
      color: var(--gray-3);
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--black); }

    /* HERO */
    .hero {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding: 0 48px 64px;
      position: relative;
      overflow: hidden;
    }

    .hero-bg {
      position: absolute;
      inset: 0;
      background: var(--white);
      z-index: 0;
    }

    /* Thin diagonal rule accent */
    .hero-bg::after {
      content: '';
      position: absolute;
      top: 0; bottom: 0;
      right: 38%;
      width: 1px;
      background: rgba(0,0,0,0.08);
    }

    .hero-content {
      position: relative;
      z-index: 1;
    }

    .hero-label {
      font-family: var(--font-body);
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--gray-3);
      margin-bottom: 16px;
    }

    .hero-title {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: clamp(72px, 10vw, 148px);
      line-height: 0.88;
      text-transform: uppercase;
      letter-spacing: -0.01em;
      color: var(--black);
      max-width: 800px;
    }

    .hero-title span {
      display: block;
      color: var(--gray-3);
    }

    .hero-scroll {
      position: absolute;
      right: 48px;
      bottom: 64px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 12px;
      z-index: 1;
    }

    .hero-scroll span {
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gray-3);
      writing-mode: vertical-rl;
    }

    .scroll-line {
      width: 1px;
      height: 60px;
      background: var(--gray-3);
      animation: scrollPulse 2s ease-in-out infinite;
    }

    @keyframes scrollPulse {
      0%, 100% { transform: scaleY(1); opacity: 1; }
      50% { transform: scaleY(0.4); opacity: 0.3; }
    }

    /* SECTION SHARED */
    section {
      padding: 120px 48px;
    }

    .section-label {
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gray-3);
      margin-bottom: 64px;
      display: flex;
      align-items: center;
      gap: 16px;
    }

    .section-label::after {
      content: '';
      display: block;
      width: 40px;
      height: 1px;
      background: var(--gray-3);
    }

    /* GALLERY */
    #gallery {
      background: var(--white);
    }

    .gallery-nav {
      display: flex;
      gap: 0;
      margin-bottom: 64px;
      border-bottom: 1px solid rgba(0,0,0,0.1);
      overflow-x: auto;
    }

    .gallery-tab {
      font-family: var(--font-display);
      font-size: 14px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 14px 28px;
      cursor: pointer;
      color: var(--gray-3);
      border-bottom: 2px solid transparent;
      margin-bottom: -1px;
      transition: color 0.2s, border-color 0.2s;
      white-space: nowrap;
      background: none;
      border-top: none;
      border-left: none;
      border-right: none;
    }

    .gallery-tab.active {
      color: var(--black);
      border-bottom-color: var(--black);
    }

    .gallery-tab:hover { color: var(--black); }

    .gallery-project {
      display: none;
      animation: fadeIn 0.4s ease;
    }

    .gallery-project.active { display: block; }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(12px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .project-header {
      margin-bottom: 40px;
    }

    .project-title {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: clamp(36px, 5vw, 64px);
      text-transform: uppercase;
      line-height: 1;
      letter-spacing: -0.01em;
    }

    .project-meta {
      margin-top: 12px;
      font-size: 12px;
      color: var(--gray-3);
      letter-spacing: 0.1em;
    }

    /* Photo grid */
    .photo-grid {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 8px;
    }

    /* Grid layout variations per row */
    .photo-grid .span-7 { grid-column: span 7; }
    .photo-grid .span-5 { grid-column: span 5; }
    .photo-grid .span-4 { grid-column: span 4; }
    .photo-grid .span-8 { grid-column: span 8; }
    .photo-grid .span-6 { grid-column: span 6; }
    .photo-grid .span-3 { grid-column: span 3; }

    .photo-item {
      position: relative;
      overflow: hidden;
      background: #e0e0e0;
      cursor: pointer;
    }

    .photo-item::before {
      content: '';
      display: block;
      padding-top: 66%;
    }

    .photo-item.tall::before { padding-top: 120%; }
    .photo-item.square::before { padding-top: 100%; }

    .photo-item img,
    .photo-placeholder {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.6s cubic-bezier(0.25,0.46,0.45,0.94);
    }

    .photo-placeholder {
      background: var(--gray-2);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .photo-placeholder span {
      font-size: 10px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--gray-3);
    }

    .photo-item:hover img,
    .photo-item:hover .photo-placeholder {
      transform: scale(1.04);
    }

    .photo-overlay {
      position: absolute;
      inset: 0;
      background: rgba(0,0,0,0);
      transition: background 0.3s;
      display: flex;
      align-items: flex-end;
      padding: 20px;
    }

    .photo-item:hover .photo-overlay {
      background: rgba(0,0,0,0.25);
    }

    .photo-caption {
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: white;
      opacity: 0;
      transform: translateY(6px);
      transition: opacity 0.3s, transform 0.3s;
    }

    .photo-item:hover .photo-caption { opacity: 1; transform: translateY(0); }

    /* LIGHTBOX */
    .lightbox {
      position: fixed;
      inset: 0;
      background: rgba(10,10,10,0.96);
      z-index: 1000;
      display: none;
      align-items: center;
      justify-content: center;
      flex-direction: column;
    }

    .lightbox.open { display: flex; }

    .lightbox-img {
      max-width: 90vw;
      max-height: 85vh;
      object-fit: contain;
      animation: fadeIn 0.3s ease;
    }

    .lightbox-placeholder {
      width: 800px;
      max-width: 90vw;
      height: 500px;
      background: var(--gray-2);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .lightbox-placeholder span {
      color: var(--gray-3);
      font-size: 12px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
    }

    .lightbox-close {
      position: absolute;
      top: 32px; right: 40px;
      font-family: var(--font-display);
      font-weight: 900;
      font-size: 13px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--gray-3);
      cursor: pointer;
      background: none;
      border: none;
      transition: color 0.2s;
    }

    .lightbox-close:hover { color: var(--white); }

    .lightbox-caption {
      margin-top: 20px;
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--gray-3);
    }

    /* ABOUT */
    #about {
      background: var(--black);
      color: var(--white);
    }

    #about .section-label { color: #555; }
    #about .section-label::after { background: #555; }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: start;
    }

    .about-image-block {
      position: relative;
    }

    .about-image {
      width: 100%;
      aspect-ratio: 3/4;
      object-fit: cover;
      filter: grayscale(100%);
    }

    .about-image-placeholder {
      width: 100%;
      aspect-ratio: 3/4;
      background: var(--gray-2);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .about-image-placeholder span {
      font-size: 11px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: #555;
    }

    .about-image-label {
      position: absolute;
      bottom: -20px;
      left: 0;
      font-family: var(--font-display);
      font-weight: 900;
      font-size: 100px;
      line-height: 1;
      color: transparent;
      -webkit-text-stroke: 1px #2e2e2e;
      text-transform: uppercase;
      letter-spacing: -0.02em;
      pointer-events: none;
      user-select: none;
    }

    .about-text h2 {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: clamp(36px, 4vw, 56px);
      text-transform: uppercase;
      line-height: 1;
      letter-spacing: -0.01em;
      margin-bottom: 32px;
    }

    .about-text p {
      font-size: 16px;
      line-height: 1.8;
      color: #999;
      margin-bottom: 20px;
      max-width: 480px;
    }

    .about-stats {
      display: flex;
      gap: 48px;
      margin-top: 48px;
      padding-top: 40px;
      border-top: 1px solid #2e2e2e;
    }

    .stat-num {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: 42px;
      line-height: 1;
      letter-spacing: -0.02em;
    }

    .stat-label {
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: #555;
      margin-top: 6px;
    }

    /* CONTACT */
    #contact {
      background: var(--white);
    }

    .contact-layout {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: start;
    }

    .contact-heading {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: clamp(48px, 6vw, 88px);
      text-transform: uppercase;
      line-height: 0.9;
      letter-spacing: -0.02em;
    }

    .contact-heading span {
      display: block;
      color: var(--gray-3);
    }

    .contact-info {
      margin-top: 48px;
      display: flex;
      flex-direction: column;
      gap: 28px;
    }

    .contact-item label {
      display: block;
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--gray-3);
      margin-bottom: 6px;
    }

    .contact-item a, .contact-item span {
      font-family: var(--font-display);
      font-size: 20px;
      font-weight: 700;
      text-decoration: none;
      color: var(--black);
      letter-spacing: 0.02em;
      transition: color 0.2s;
    }

    .contact-item a:hover { color: var(--gray-3); }

    .contact-form {
      display: flex;
      flex-direction: column;
      gap: 24px;
    }

    .form-field {
      position: relative;
    }

    .form-field label {
      display: block;
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--gray-3);
      margin-bottom: 10px;
    }

    .form-field input,
    .form-field textarea {
      width: 100%;
      background: none;
      border: none;
      border-bottom: 1.5px solid rgba(0,0,0,0.15);
      padding: 10px 0;
      font-family: var(--font-body);
      font-size: 16px;
      color: var(--black);
      outline: none;
      transition: border-color 0.2s;
      resize: none;
    }

    .form-field input:focus,
    .form-field textarea:focus {
      border-bottom-color: var(--black);
    }

    .form-field textarea { min-height: 100px; }

    .btn-submit {
      display: inline-flex;
      align-items: center;
      gap: 14px;
      background: var(--black);
      color: var(--white);
      border: none;
      padding: 16px 36px;
      font-family: var(--font-display);
      font-size: 13px;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.2s, gap 0.2s;
      align-self: flex-start;
    }

    .btn-submit:hover {
      background: var(--gray-2);
      gap: 22px;
    }

    .btn-arrow { font-size: 18px; }

    /* FOOTER */
    footer {
      padding: 32px 48px;
      border-top: 1px solid rgba(0,0,0,0.08);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    footer .footer-logo {
      font-family: var(--font-display);
      font-weight: 900;
      font-size: 14px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--black);
    }

    footer .footer-copy {
      font-size: 11px;
      color: var(--gray-3);
      letter-spacing: 0.08em;
    }

    /* FADE IN ON SCROLL */
    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 20px 24px; }
      .nav-links { gap: 24px; }
      section { padding: 80px 24px; }
      .hero { padding: 0 24px 48px; }
      .hero-scroll { right: 24px; bottom: 48px; }
      .about-grid, .contact-layout { grid-template-columns: 1fr; gap: 48px; }
      .about-image-label { font-size: 60px; }
      .photo-grid .span-7, .photo-grid .span-5,
      .photo-grid .span-4, .photo-grid .span-8 { grid-column: span 12; }
      .photo-grid .span-6, .photo-grid .span-3 { grid-column: span 6; }
      footer { flex-direction: column; gap: 12px; text-align: center; }
    }
  </style>
</head>
<body>

  <!-- CURSOR -->
  <div class="cursor" id="cursor"></div>

  <!-- NAV -->
  <nav>
    <a href="#" class="nav-logo">Correa Archives</a>
    <ul class="nav-links">
      <li><a href="#gallery">Work</a></li>
      <li><a href="#about">About</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section class="hero" id="home">
    <div class="hero-bg"></div>
    <div class="hero-content reveal">
      <p class="hero-label">Photography &amp; Visual Storytelling</p>
      <h1 class="hero-title">
        Correa<br>
        <span>Archives</span>
      </h1>
    </div>
    <div class="hero-scroll">
      <div class="scroll-line"></div>
      <span>Scroll</span>
    </div>
  </section>

  <!-- GALLERY -->
  <section id="gallery">
    <p class="section-label reveal">Selected Work</p>

    <div class="gallery-nav reveal">
      <button class="gallery-tab active" onclick="switchProject(0)">Street</button>
      <button class="gallery-tab" onclick="switchProject(1)">Portrait</button>
      <button class="gallery-tab" onclick="switchProject(2)">Architecture</button>
      <button class="gallery-tab" onclick="switchProject(3)">Nature</button>
    </div>

    <!-- PROJECT 1: STREET -->
    <div class="gallery-project active" id="project-0">
      <div class="project-header reveal">
        <h2 class="project-title">Street</h2>
        <p class="project-meta">Washington, DC &mdash; 2024–2025</p>
      </div>
      <div class="photo-grid">
        <div class="photo-item span-7 tall" onclick="openLightbox(null, 'Street 01')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 01</span></div>
        </div>
        <div class="photo-item span-5" onclick="openLightbox(null, 'Street 02')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 02</span></div>
        </div>
        <div class="photo-item span-5" onclick="openLightbox(null, 'Street 03')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 03</span></div>
        </div>
        <div class="photo-item span-4" onclick="openLightbox(null, 'Street 04')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 04</span></div>
        </div>
        <div class="photo-item span-3" onclick="openLightbox(null, 'Street 05')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 05</span></div>
        </div>
        <div class="photo-item span-8" onclick="openLightbox(null, 'Street 06')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 06</span></div>
        </div>
        <div class="photo-item span-4" onclick="openLightbox(null, 'Street 07')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Street 07</span></div>
        </div>
      </div>
    </div>

    <!-- PROJECT 2: PORTRAIT -->
    <div class="gallery-project" id="project-1">
      <div class="project-header">
        <h2 class="project-title">Portrait</h2>
        <p class="project-meta">Washington, DC &mdash; 2024–2025</p>
      </div>
      <div class="photo-grid">
        <div class="photo-item span-4 tall" onclick="openLightbox(null, 'Portrait 01')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Portrait 01</span></div>
        </div>
        <div class="photo-item span-4 tall" onclick="openLightbox(null, 'Portrait 02')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Portrait 02</span></div>
        </div>
        <div class="photo-item span-4 tall" onclick="openLightbox(null, 'Portrait 03')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Portrait 03</span></div>
        </div>
        <div class="photo-item span-6" onclick="openLightbox(null, 'Portrait 04')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Portrait 04</span></div>
        </div>
        <div class="photo-item span-6" onclick="openLightbox(null, 'Portrait 05')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Portrait 05</span></div>
        </div>
      </div>
    </div>

    <!-- PROJECT 3: ARCHITECTURE -->
    <div class="gallery-project" id="project-2">
      <div class="project-header">
        <h2 class="project-title">Architecture</h2>
        <p class="project-meta">Various Locations &mdash; 2023–2025</p>
      </div>
      <div class="photo-grid">
        <div class="photo-item span-8" onclick="openLightbox(null, 'Architecture 01')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Architecture 01</span></div>
        </div>
        <div class="photo-item span-4 tall" onclick="openLightbox(null, 'Architecture 02')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Architecture 02</span></div>
        </div>
        <div class="photo-item span-4" onclick="openLightbox(null, 'Architecture 03')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Architecture 03</span></div>
        </div>
        <div class="photo-item span-6" onclick="openLightbox(null, 'Architecture 04')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Architecture 04</span></div>
        </div>
        <div class="photo-item span-6" onclick="openLightbox(null, 'Architecture 05')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Architecture 05</span></div>
        </div>
      </div>
    </div>

    <!-- PROJECT 4: NATURE -->
    <div class="gallery-project" id="project-3">
      <div class="project-header">
        <h2 class="project-title">Nature</h2>
        <p class="project-meta">Virginia &amp; Beyond &mdash; 2023–2025</p>
      </div>
      <div class="photo-grid">
        <div class="photo-item span-6" onclick="openLightbox(null, 'Nature 01')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Nature 01</span></div>
        </div>
        <div class="photo-item span-6" onclick="openLightbox(null, 'Nature 02')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Nature 02</span></div>
        </div>
        <div class="photo-item span-4" onclick="openLightbox(null, 'Nature 03')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Nature 03</span></div>
        </div>
        <div class="photo-item span-8" onclick="openLightbox(null, 'Nature 04')">
          <div class="photo-placeholder"><span>Your Photo Here</span></div>
          <div class="photo-overlay"><span class="photo-caption">Nature 04</span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- LIGHTBOX -->
  <div class="lightbox" id="lightbox">
    <button class="lightbox-close" onclick="closeLightbox()">✕ Close</button>
    <div id="lightbox-content" class="lightbox-placeholder">
      <span>Your Photo Here</span>
    </div>
    <p class="lightbox-caption" id="lightbox-caption"></p>
  </div>

  <!-- ABOUT -->
  <section id="about">
    <p class="section-label">About</p>
    <div class="about-grid">
      <div class="about-image-block reveal">
        <div class="about-image-placeholder">
          <span>Your Portrait Here</span>
        </div>
        <div class="about-image-label">N.C.</div>
      </div>
      <div class="about-text reveal">
        <h2>The Eye Behind<br>The Archive</h2>
        <p>
          I'm Nickolas Correa — a photographer based in Washington, DC with an eye for the
          moments that live just outside the frame. Correa Archives is my ongoing document
          of light, place, and people.
        </p>
        <p>
          My work spans street, portrait, and architectural photography, with a focus on
          honest storytelling. Every image is a study in patience and presence.
        </p>
        <p>
          Available for editorial, commercial, and portrait commissions.
        </p>
        <div class="about-stats">
          <div>
            <div class="stat-num">5+</div>
            <div class="stat-label">Years Shooting</div>
          </div>
          <div>
            <div class="stat-num">4</div>
            <div class="stat-label">Series Active</div>
          </div>
          <div>
            <div class="stat-num">DC</div>
            <div class="stat-label">Based</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <p class="section-label reveal">Get in Touch</p>
    <div class="contact-layout">
      <div class="reveal">
        <h2 class="contact-heading">
          Let's<br>Work<br><span>Together</span>
        </h2>
        <div class="contact-info">
          <div class="contact-item">
            <label>Email</label>
            <a href="mailto:hello@correaarchives.com">hello@correaarchives.com</a>
          </div>
          <div class="contact-item">
            <label>Website</label>
            <a href="https://correaarchives.com" target="_blank">correaarchives.com</a>
          </div>
          <div class="contact-item">
            <label>Location</label>
            <span>Washington, DC</span>
          </div>
        </div>
      </div>
      <div class="contact-form reveal">
        <div class="form-field">
          <label>Your Name</label>
          <input type="text" placeholder="First Last">
        </div>
        <div class="form-field">
          <label>Email</label>
          <input type="email" placeholder="you@email.com">
        </div>
        <div class="form-field">
          <label>Message</label>
          <textarea placeholder="Tell me about your project…"></textarea>
        </div>
        <button class="btn-submit" onclick="handleSubmit()">
          Send Message <span class="btn-arrow">→</span>
        </button>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">Correa Archives</div>
    <div class="footer-copy">© 2025 Nickolas Correa. All rights reserved.</div>
  </footer>

  <script>
    // CURSOR
    const cursor = document.getElementById('cursor');
    document.addEventListener('mousemove', e => {
      cursor.style.left = e.clientX + 'px';
      cursor.style.top = e.clientY + 'px';
    });
    document.querySelectorAll('a, button, .photo-item, .gallery-tab').forEach(el => {
      el.addEventListener('mouseenter', () => cursor.classList.add('hover'));
      el.addEventListener('mouseleave', () => cursor.classList.remove('hover'));
    });

    // GALLERY TABS
    function switchProject(index) {
      document.querySelectorAll('.gallery-tab').forEach((tab, i) => {
        tab.classList.toggle('active', i === index);
      });
      document.querySelectorAll('.gallery-project').forEach((proj, i) => {
        proj.classList.toggle('active', i === index);
      });
    }

    // LIGHTBOX
    function openLightbox(imgSrc, caption) {
      const lb = document.getElementById('lightbox');
      const content = document.getElementById('lightbox-content');
      const cap = document.getElementById('lightbox-caption');

      if (imgSrc) {
        content.innerHTML = `<img class="lightbox-img" src="${imgSrc}" alt="${caption}">`;
      } else {
        content.innerHTML = `<div class="lightbox-placeholder"><span>${caption}</span></div>`;
      }
      cap.textContent = caption;
      lb.classList.add('open');
      document.body.style.overflow = 'hidden';
    }

    function closeLightbox() {
      document.getElementById('lightbox').classList.remove('open');
      document.body.style.overflow = '';
    }

    document.getElementById('lightbox').addEventListener('click', function(e) {
      if (e.target === this) closeLightbox();
    });

    document.addEventListener('keydown', e => {
      if (e.key === 'Escape') closeLightbox();
    });

    // SCROLL REVEAL
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12 });

    reveals.forEach(el => observer.observe(el));

    // CONTACT FORM
    function handleSubmit() {
      alert('Message sent! (Connect a backend or Formspree to make this functional.)');
    }
  </script>

</body>
</html>
