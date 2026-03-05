Index · HTML
Copy

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Churnless Studio — Growth Operating Agency</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --bg: #080808;
      --surface: #111111;
      --border: #1e1e1e;
      --acid: #c6f135;
      --acid-dim: rgba(198,241,53,0.12);
      --white: #f0ede6;
      --muted: #5a5a5a;
      --mid: #2a2a2a;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--white);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      overflow-x: hidden;
      cursor: none;
    }

    /* CUSTOM CURSOR */
    .cursor {
      position: fixed;
      width: 10px; height: 10px;
      background: var(--acid);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%, -50%);
      transition: transform 0.08s ease, width 0.2s ease, height 0.2s ease;
      mix-blend-mode: difference;
    }
    .cursor-ring {
      position: fixed;
      width: 36px; height: 36px;
      border: 1px solid rgba(198,241,53,0.5);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9998;
      transform: translate(-50%, -50%);
      transition: transform 0.18s ease, width 0.2s, height 0.2s;
    }
    body:has(a:hover) .cursor, body:has(button:hover) .cursor { width: 18px; height: 18px; }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 24px 48px;
      border-bottom: 1px solid transparent;
      transition: border-color 0.3s, background 0.3s;
    }
    nav.scrolled {
      background: rgba(8,8,8,0.92);
      backdrop-filter: blur(12px);
      border-color: var(--border);
    }
    .nav-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 22px;
      letter-spacing: 0.08em;
      color: var(--white);
      text-decoration: none;
      display: flex; align-items: center; gap: 8px;
    }
    .nav-logo span { color: var(--acid); }
    .nav-links { display: flex; gap: 36px; align-items: center; }
    .nav-links a {
      font-family: 'Space Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--white); }
    .nav-cta {
      font-family: 'Space Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 10px 22px;
      background: var(--acid);
      color: var(--bg);
      border: none;
      cursor: none;
      font-weight: 700;
      transition: background 0.2s, transform 0.15s;
    }
    .nav-cta:hover { background: #d8ff5a; transform: translateY(-1px); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; flex-direction: column; justify-content: flex-end;
      padding: 0 48px 80px;
      position: relative;
      overflow: hidden;
    }
    .hero-grid {
      position: absolute; inset: 0;
      background-image:
        linear-gradient(rgba(198,241,53,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(198,241,53,0.04) 1px, transparent 1px);
      background-size: 60px 60px;
      mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 30%, transparent 100%);
    }
    .hero-ticker {
      position: absolute; top: 50%; left: 0; right: 0;
      transform: translateY(-50%);
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(120px, 18vw, 240px);
      color: transparent;
      -webkit-text-stroke: 1px rgba(198,241,53,0.06);
      white-space: nowrap;
      animation: tickerSlide 20s linear infinite;
      user-select: none;
      pointer-events: none;
    }
    @keyframes tickerSlide {
      from { transform: translateY(-50%) translateX(0); }
      to   { transform: translateY(-50%) translateX(-50%); }
    }
    .hero-badge {
      display: inline-flex; align-items: center; gap: 8px;
      border: 1px solid var(--border);
      padding: 6px 14px;
      font-family: 'Space Mono', monospace;
      font-size: 10px;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 28px;
      width: fit-content;
    }
    .hero-badge::before {
      content: '';
      width: 6px; height: 6px;
      background: var(--acid);
      border-radius: 50%;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.5; transform: scale(0.7); }
    }
    .hero h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(72px, 10vw, 148px);
      line-height: 0.92;
      letter-spacing: 0.01em;
      position: relative;
      z-index: 1;
    }
    .hero h1 em {
      font-style: normal;
      color: var(--acid);
      display: block;
    }
    .hero-sub {
      margin-top: 32px;
      max-width: 520px;
      font-size: 16px;
      line-height: 1.65;
      color: #8a8a8a;
      position: relative; z-index: 1;
    }
    .hero-actions {
      margin-top: 48px;
      display: flex; gap: 16px; align-items: center;
      position: relative; z-index: 1;
    }
    .btn-primary {
      font-family: 'Space Mono', monospace;
      font-size: 12px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      font-weight: 700;
      padding: 16px 36px;
      background: var(--acid);
      color: var(--bg);
      border: none; cursor: none;
      transition: all 0.2s;
    }
    .btn-primary:hover { background: #d8ff5a; transform: translateY(-2px); }
    .btn-ghost {
      font-family: 'Space Mono', monospace;
      font-size: 12px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      padding: 16px 36px;
      background: transparent;
      color: var(--white);
      border: 1px solid var(--border); cursor: none;
      transition: all 0.2s;
    }
    .btn-ghost:hover { border-color: var(--muted); }
    .hero-stats {
      position: absolute; right: 48px; bottom: 80px;
      display: flex; flex-direction: column; gap: 24px;
      z-index: 1;
    }
    .stat { text-align: right; }
    .stat-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 42px;
      color: var(--acid);
      line-height: 1;
    }
    .stat-label {
      font-family: 'Space Mono', monospace;
      font-size: 10px;
      color: var(--muted);
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-top: 4px;
    }

    /* MARQUEE */
    .marquee-wrap {
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      overflow: hidden;
      padding: 16px 0;
      background: var(--surface);
    }
    .marquee-track {
      display: flex;
      animation: marquee 18s linear infinite;
      white-space: nowrap;
    }
    .marquee-track:hover { animation-play-state: paused; }
    @keyframes marquee {
      from { transform: translateX(0); }
      to   { transform: translateX(-50%); }
    }
    .marquee-item {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 14px;
      letter-spacing: 0.18em;
      color: var(--muted);
      padding: 0 32px;
      display: flex; align-items: center; gap: 32px;
      flex-shrink: 0;
    }
    .marquee-item .dot { color: var(--acid); font-size: 20px; }

    /* SECTIONS */
    section { padding: 120px 48px; }

    .section-label {
      font-family: 'Space Mono', monospace;
      font-size: 10px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--acid);
      margin-bottom: 20px;
    }
    .section-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(48px, 6vw, 88px);
      line-height: 0.95;
      letter-spacing: 0.01em;
    }

    /* SERVICES */
    .services { border-top: 1px solid var(--border); }
    .services-header {
      display: grid; grid-template-columns: 1fr 1fr; gap: 48px;
      margin-bottom: 80px; align-items: end;
    }
    .services-desc {
      font-size: 16px; line-height: 1.7; color: #8a8a8a;
      align-self: end;
    }
    .services-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1px; background: var(--border); }
    .service-card {
      background: var(--bg);
      padding: 48px 40px;
      position: relative;
      overflow: hidden;
      transition: background 0.3s;
    }
    .service-card:hover { background: #0e0e0e; }
    .service-card::after {
      content: '';
      position: absolute; bottom: 0; left: 0; right: 0;
      height: 2px;
      background: var(--acid);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.4s ease;
    }
    .service-card:hover::after { transform: scaleX(1); }
    .service-num {
      font-family: 'Space Mono', monospace;
      font-size: 11px;
      color: var(--muted);
      letter-spacing: 0.12em;
      margin-bottom: 32px;
    }
    .service-icon {
      width: 48px; height: 48px;
      margin-bottom: 28px;
      color: var(--acid);
    }
    .service-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 30px;
      letter-spacing: 0.04em;
      margin-bottom: 16px;
    }
    .service-desc { font-size: 14px; line-height: 1.7; color: #7a7a7a; }
    .service-tags { margin-top: 28px; display: flex; flex-wrap: wrap; gap: 8px; }
    .tag {
      font-family: 'Space Mono', monospace;
      font-size: 10px;
      padding: 4px 10px;
      border: 1px solid var(--mid);
      color: var(--muted);
      letter-spacing: 0.06em;
    }

    /* HOW IT WORKS */
    .process { border-top: 1px solid var(--border); background: var(--surface); }
    .process-steps {
      margin-top: 80px;
      display: grid; grid-template-columns: repeat(4, 1fr);
      position: relative;
    }
    .process-steps::before {
      content: '';
      position: absolute;
      top: 28px; left: 12.5%; right: 12.5%;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--acid), transparent);
      opacity: 0.3;
    }
    .step { padding: 0 24px; }
    .step-dot {
      width: 56px; height: 56px;
      border: 1px solid var(--border);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 22px;
      color: var(--acid);
      margin-bottom: 28px;
      background: var(--bg);
      transition: border-color 0.3s, background 0.3s;
    }
    .step:hover .step-dot { border-color: var(--acid); background: var(--acid-dim); }
    .step-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 24px; letter-spacing: 0.04em;
      margin-bottom: 12px;
    }
    .step-desc { font-size: 13px; line-height: 1.7; color: #6a6a6a; }

    /* RESULTS */
    .results { border-top: 1px solid var(--border); }
    .results-grid {
      margin-top: 80px;
      display: grid;
      grid-template-columns: 2fr 1fr 1fr;
      grid-template-rows: auto auto;
      gap: 1px;
      background: var(--border);
    }
    .result-card {
      background: var(--bg);
      padding: 56px 48px;
      position: relative;
      overflow: hidden;
    }
    .result-card.featured {
      grid-row: span 2;
      background: var(--acid);
    }
    .result-card.featured * { color: var(--bg) !important; }
    .result-big {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(64px, 8vw, 112px);
      line-height: 1;
      color: var(--acid);
    }
    .result-card.featured .result-big { color: var(--bg); }
    .result-label {
      font-family: 'Space Mono', monospace;
      font-size: 11px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: 8px;
    }
    .result-desc { font-size: 14px; line-height: 1.6; color: #6a6a6a; margin-top: 16px; }
    .result-quote {
      font-size: 18px; line-height: 1.6;
      font-style: italic; color: var(--bg);
      margin-top: 24px;
    }
    .result-author {
      font-family: 'Space Mono', monospace;
      font-size: 11px;
      margin-top: 20px;
      color: rgba(8,8,8,0.6);
      letter-spacing: 0.1em;
    }

    /* CTA */
    .cta-section {
      border-top: 1px solid var(--border);
      text-align: center;
      padding: 160px 48px;
      position: relative;
      overflow: hidden;
    }
    .cta-bg {
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 60% 60% at 50% 50%, rgba(198,241,53,0.05) 0%, transparent 70%);
    }
    .cta-section h2 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(60px, 8vw, 120px);
      line-height: 0.95;
      position: relative; z-index: 1;
    }
    .cta-section h2 em { font-style: normal; color: var(--acid); }
    .cta-section p {
      max-width: 480px; margin: 28px auto 48px;
      font-size: 16px; line-height: 1.6; color: #7a7a7a;
      position: relative; z-index: 1;
    }
    .cta-section .btn-primary { position: relative; z-index: 1; font-size: 13px; padding: 18px 48px; }

    /* FOOTER */
    footer {
      border-top: 1px solid var(--border);
      padding: 48px;
      display: flex; justify-content: space-between; align-items: center;
    }
    .footer-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 20px; letter-spacing: 0.08em;
    }
    .footer-logo span { color: var(--acid); }
    .footer-links { display: flex; gap: 28px; }
    .footer-links a {
      font-family: 'Space Mono', monospace;
      font-size: 10px; letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--muted); text-decoration: none;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: var(--white); }
    .footer-copy {
      font-family: 'Space Mono', monospace;
      font-size: 10px; color: var(--muted);
      letter-spacing: 0.08em;
    }

    /* ANIMATIONS */
    .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }

    @media (max-width: 900px) {
      nav { padding: 20px 24px; }
      .nav-links { display: none; }
      section { padding: 80px 24px; }
      .hero { padding: 0 24px 60px; }
      .hero-stats { display: none; }
      .services-header { grid-template-columns: 1fr; }
      .services-grid { grid-template-columns: 1fr; }
      .process-steps { grid-template-columns: 1fr 1fr; gap: 40px; }
      .process-steps::before { display: none; }
      .results-grid { grid-template-columns: 1fr; }
      .result-card.featured { grid-row: span 1; }
      footer { flex-direction: column; gap: 24px; text-align: center; }
      .footer-links { flex-wrap: wrap; justify-content: center; }
    }
  </style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav id="nav">
  <a href="#" class="nav-logo">CHURNLESS<span>.</span></a>
  <div class="nav-links">
    <a href="#services">Services</a>
    <a href="#process">Process</a>
    <a href="#results">Results</a>
    <a href="#contact">Contact</a>
  </div>
  <button class="nav-cta" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Get Started</button>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-grid"></div>
  <div class="hero-ticker">GROW RETAIN CONVERT SCALE GROW RETAIN CONVERT SCALE&nbsp;&nbsp;&nbsp;</div>

  <div class="hero-badge">Growth Operating Agency — Est. 2024</div>
  <h1 class="reveal">
    Stop Losing<br>
    <em>Revenue.</em><br>
    Start Scaling.
  </h1>
  <p class="hero-sub reveal reveal-delay-1">
    We build and optimize the systems that drive revenue — across marketing, sales, and customer retention. Data-driven. Automation-first. Built to compound.
  </p>
  <div class="hero-actions reveal reveal-delay-2">
    <button class="btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Build Your Growth Engine</button>
    <button class="btn-ghost" onclick="document.getElementById('services').scrollIntoView({behavior:'smooth'})">See What We Do</button>
  </div>

  <div class="hero-stats">
    <div class="stat reveal reveal-delay-1">
      <div class="stat-num">3.4×</div>
      <div class="stat-label">Avg. Revenue Lift</div>
    </div>
    <div class="stat reveal reveal-delay-2">
      <div class="stat-num">-62%</div>
      <div class="stat-label">Churn Reduction</div>
    </div>
    <div class="stat reveal reveal-delay-3">
      <div class="stat-num">90d</div>
      <div class="stat-label">To First Results</div>
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track">
    <div class="marquee-item">Growth Strategy <span class="dot">·</span></div>
    <div class="marquee-item">Marketing Automation <span class="dot">·</span></div>
    <div class="marquee-item">Revenue Operations <span class="dot">·</span></div>
    <div class="marquee-item">Churn Reduction <span class="dot">·</span></div>
    <div class="marquee-item">Sales Optimization <span class="dot">·</span></div>
    <div class="marquee-item">Data & Analytics <span class="dot">·</span></div>
    <div class="marquee-item">Funnel Engineering <span class="dot">·</span></div>
    <div class="marquee-item">Lifecycle Marketing <span class="dot">·</span></div>
    <div class="marquee-item">Experimentation <span class="dot">·</span></div>
    <!-- duplicate for seamless loop -->
    <div class="marquee-item">Growth Strategy <span class="dot">·</span></div>
    <div class="marquee-item">Marketing Automation <span class="dot">·</span></div>
    <div class="marquee-item">Revenue Operations <span class="dot">·</span></div>
    <div class="marquee-item">Churn Reduction <span class="dot">·</span></div>
    <div class="marquee-item">Sales Optimization <span class="dot">·</span></div>
    <div class="marquee-item">Data & Analytics <span class="dot">·</span></div>
    <div class="marquee-item">Funnel Engineering <span class="dot">·</span></div>
    <div class="marquee-item">Lifecycle Marketing <span class="dot">·</span></div>
    <div class="marquee-item">Experimentation <span class="dot">·</span></div>
  </div>
</div>

<!-- SERVICES -->
<section class="services" id="services">
  <div class="services-header">
    <div>
      <div class="section-label reveal">What We Build</div>
      <h2 class="section-title reveal reveal-delay-1">Three Pillars.<br>One Engine.</h2>
    </div>
    <p class="services-desc reveal reveal-delay-2">
      We don't offer isolated tactics. We design integrated growth systems that compound — where each pillar reinforces the others to create sustainable, predictable revenue.
    </p>
  </div>

  <div class="services-grid">
    <div class="service-card reveal">
      <div class="service-num">01 /</div>
      <svg class="service-icon" fill="none" viewBox="0 0 48 48" stroke="currentColor" stroke-width="1.5">
        <path d="M6 36 L18 22 L28 28 L42 12"/>
        <circle cx="42" cy="12" r="4" fill="currentColor" stroke="none"/>
        <path d="M6 42 L42 42" opacity="0.3"/>
      </svg>
      <div class="service-title">Growth Marketing</div>
      <div class="service-desc">Full-funnel demand generation that converts. We design and run campaigns that attract the right audience, nurture intent, and move prospects into paying customers efficiently.</div>
      <div class="service-tags">
        <span class="tag">Paid Acquisition</span>
        <span class="tag">SEO Systems</span>
        <span class="tag">Email Flows</span>
        <span class="tag">Content Engine</span>
      </div>
    </div>

    <div class="service-card reveal reveal-delay-1">
      <div class="service-num">02 /</div>
      <svg class="service-icon" fill="none" viewBox="0 0 48 48" stroke="currentColor" stroke-width="1.5">
        <rect x="6" y="28" width="8" height="14" rx="1"/>
        <rect x="20" y="18" width="8" height="24" rx="1"/>
        <rect x="34" y="8" width="8" height="34" rx="1"/>
        <path d="M10 24 L24 14 L38 4" stroke-dasharray="3 3" opacity="0.4"/>
      </svg>
      <div class="service-title">Revenue Operations</div>
      <div class="service-desc">Align your sales pipeline, CRM, and reporting so your team spends time closing — not managing chaos. We engineer the ops layer that turns leads into revenue systematically.</div>
      <div class="service-tags">
        <span class="tag">CRM Architecture</span>
        <span class="tag">Pipeline Design</span>
        <span class="tag">Sales Automation</span>
        <span class="tag">Reporting</span>
      </div>
    </div>

    <div class="service-card reveal reveal-delay-2">
      <div class="service-num">03 /</div>
      <svg class="service-icon" fill="none" viewBox="0 0 48 48" stroke="currentColor" stroke-width="1.5">
        <circle cx="24" cy="24" r="18"/>
        <path d="M24 6 A18 18 0 0 1 42 24"/>
        <path d="M16 24 C16 18, 32 18, 32 24 C32 30, 16 30, 16 24Z" fill="currentColor" opacity="0.2" stroke="none"/>
        <path d="M16 24 C16 18, 32 18, 32 24 C32 30, 16 30, 16 24Z"/>
      </svg>
      <div class="service-title">Retention & LTV</div>
      <div class="service-desc">The fastest path to revenue growth is stopping the leak. We build retention programs that extend customer lifetime, reduce churn, and create the compounding loops that define great businesses.</div>
      <div class="service-tags">
        <span class="tag">Churn Analysis</span>
        <span class="tag">Lifecycle Flows</span>
        <span class="tag">NPS Programs</span>
        <span class="tag">Win-Back</span>
      </div>
    </div>
  </div>
</section>

<!-- PROCESS -->
<section class="process" id="process">
  <div class="section-label reveal">How We Operate</div>
  <h2 class="section-title reveal reveal-delay-1">From Audit to<br>Revenue. Fast.</h2>

  <div class="process-steps">
    <div class="step reveal">
      <div class="step-dot">01</div>
      <div class="step-title">Diagnose</div>
      <div class="step-desc">Deep-dive into your current funnel, retention data, and revenue leaks. We map exactly where growth is stalling and why — no guesswork.</div>
    </div>
    <div class="step reveal reveal-delay-1">
      <div class="step-dot">02</div>
      <div class="step-title">Design</div>
      <div class="step-desc">We architect a custom growth system — the specific levers, sequences, and automations that will drive the most impact for your business.</div>
    </div>
    <div class="step reveal reveal-delay-2">
      <div class="step-dot">03</div>
      <div class="step-title">Build & Launch</div>
      <div class="step-desc">We implement everything. Campaigns, CRM configurations, retention flows, dashboards. You stay focused on the business while we ship.</div>
    </div>
    <div class="step reveal reveal-delay-3">
      <div class="step-dot">04</div>
      <div class="step-title">Compound</div>
      <div class="step-desc">Continuous experimentation and iteration. We run the growth loop — test, learn, optimize — turning early wins into sustained revenue momentum.</div>
    </div>
  </div>
</section>

<!-- RESULTS -->
<section class="results" id="results">
  <div class="section-label reveal">Proof It Works</div>
  <h2 class="section-title reveal reveal-delay-1">Numbers That<br>Matter.</h2>

  <div class="results-grid" style="margin-top: 80px;">
    <div class="result-card featured reveal">
      <div class="section-label" style="color: rgba(8,8,8,0.5); margin-bottom: 40px;">Featured Result</div>
      <div class="result-big">3.4×</div>
      <div class="result-label" style="color: rgba(8,8,8,0.5);">Revenue in 6 Months</div>
      <p class="result-quote">"Churnless didn't just run campaigns — they rebuilt how we think about revenue. Our MRR tripled and churn dropped below 4% for the first time."</p>
      <div class="result-author">— Founder, B2B SaaS · Series A</div>
    </div>
    <div class="result-card reveal reveal-delay-1">
      <div class="result-big">-62%</div>
      <div class="result-label">Churn Reduction</div>
      <p class="result-desc">E-commerce brand rebuilt their retention stack — repurchase rate soared in 90 days.</p>
    </div>
    <div class="result-card reveal reveal-delay-2">
      <div class="result-big">8.1×</div>
      <div class="result-label">Return on Ad Spend</div>
      <p class="result-desc">Full-funnel rebuild for a DTC brand. Same budget, dramatically better returns.</p>
    </div>
    <div class="result-card reveal reveal-delay-1">
      <div class="result-big">+$2.4M</div>
      <div class="result-label">Recovered Revenue</div>
      <p class="result-desc">Win-back and lifecycle program turned dormant customers into a new revenue channel.</p>
    </div>
    <div class="result-card reveal reveal-delay-2">
      <div class="result-big">41%</div>
      <div class="result-label">CAC Reduction</div>
      <p class="result-desc">Rebuilt acquisition funnel for a marketplace. Leads got cheaper and closed faster.</p>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section" id="contact">
  <div class="cta-bg"></div>
  <h2 class="reveal">Ready to Stop <em>Leaking</em><br>Revenue?</h2>
  <p class="reveal reveal-delay-1">Let's audit your growth system and build the engine that turns traffic into customers — and customers into long-term revenue.</p>
  <button class="btn-primary reveal reveal-delay-2" onclick="window.location.href='mailto:hello@churnlessstudio.com'">Book a Free Growth Audit</button>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">CHURNLESS<span>.</span>STUDIO</div>
  <div class="footer-links">
    <a href="#services">Services</a>
    <a href="#process">Process</a>
    <a href="#results">Results</a>
    <a href="mailto:hello@churnlessstudio.com">hello@churnlessstudio.com</a>
  </div>
  <div class="footer-copy">© 2024 Churnless Studio</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animateCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animateCursor);
  }
  animateCursor();

  // Nav scroll
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 40);
  });

  // Reveal on scroll
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));

  // Trigger hero reveals immediately
  document.querySelectorAll('.hero .reveal').forEach((el, i) => {
    setTimeout(() => el.classList.add('visible'), 200 + i * 120);
  });
</script>
</body>
</html>
