Index · HTML
Copy

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Churnless Studio — Growth Operating Agency</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root { --cream: #F7F4EF; --ink: #131210; --accent: #C8A96E; --mid: #7A7468; --border: #E2DDD6; }
  html { scroll-behavior: smooth; }
  body { font-family: 'DM Sans', sans-serif; background: var(--cream); color: var(--ink); font-weight: 300; overflow-x: hidden; }

  nav { position: fixed; top: 0; left: 0; right: 0; z-index: 100; display: flex; justify-content: space-between; align-items: center; padding: 28px 60px; background: rgba(247,244,239,0.92); backdrop-filter: blur(12px); border-bottom: 1px solid transparent; transition: border-color 0.3s; }
  nav.scrolled { border-color: var(--border); }
  .logo { font-family: 'Playfair Display', serif; font-size: 1.25rem; letter-spacing: -0.01em; color: var(--ink); text-decoration: none; }
  .logo span { color: var(--accent); }
  .nav-links { display: flex; gap: 40px; list-style: none; }
  .nav-links a { text-decoration: none; color: var(--mid); font-size: 0.875rem; letter-spacing: 0.04em; font-weight: 400; transition: color 0.2s; }
  .nav-links a:hover { color: var(--ink); }
  .nav-cta { background: var(--ink); color: var(--cream) !important; padding: 10px 22px; border-radius: 2px; font-size: 0.8rem !important; letter-spacing: 0.08em !important; text-transform: uppercase; font-weight: 500 !important; transition: background 0.2s !important; }
  .nav-cta:hover { background: var(--accent) !important; color: var(--ink) !important; }

  .hero { min-height: 100vh; display: grid; grid-template-columns: 1fr 1fr; padding-top: 100px; }
  .hero-left { display: flex; flex-direction: column; justify-content: center; padding: 80px 60px; }
  .hero-tag { font-size: 0.75rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--accent); font-weight: 500; margin-bottom: 28px; display: flex; align-items: center; gap: 10px; }
  .hero-tag::before { content: ''; display: inline-block; width: 30px; height: 1px; background: var(--accent); }
  h1 { font-family: 'Playfair Display', serif; font-size: clamp(3rem, 5vw, 5.5rem); line-height: 1.08; letter-spacing: -0.02em; margin-bottom: 32px; }
  h1 em { font-style: italic; color: var(--accent); }
  .hero-sub { font-size: 1.05rem; line-height: 1.7; color: var(--mid); max-width: 420px; margin-bottom: 48px; }
  .hero-actions { display: flex; gap: 16px; align-items: center; }
  .btn-primary { background: var(--ink); color: var(--cream); padding: 16px 32px; text-decoration: none; font-size: 0.85rem; letter-spacing: 0.06em; text-transform: uppercase; font-weight: 500; border-radius: 2px; transition: background 0.2s, transform 0.2s; display: inline-block; }
  .btn-primary:hover { background: var(--accent); color: var(--ink); transform: translateY(-1px); }
  .btn-ghost { color: var(--mid); text-decoration: none; font-size: 0.85rem; letter-spacing: 0.04em; font-weight: 400; display: flex; align-items: center; gap: 8px; transition: color 0.2s, gap 0.2s; }
  .btn-ghost:hover { color: var(--ink); gap: 14px; }
  .btn-ghost::after { content: '→'; font-size: 1rem; }

  .hero-right { position: relative; overflow: hidden; background: var(--ink); }
  .hero-right::before { content: ''; position: absolute; inset: 0; background: radial-gradient(ellipse at 30% 60%, rgba(200,169,110,0.18) 0%, transparent 60%), radial-gradient(ellipse at 80% 20%, rgba(200,169,110,0.08) 0%, transparent 50%); }
  .hero-stats { position: absolute; bottom: 60px; left: 50px; right: 50px; display: grid; grid-template-columns: 1fr 1fr; gap: 1px; background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.06); }
  .stat-box { padding: 28px; background: rgba(247,244,239,0.03); transition: background 0.2s; }
  .stat-box:hover { background: rgba(200,169,110,0.08); }
  .stat-num { font-family: 'Playfair Display', serif; font-size: 2.4rem; color: #F7F4EF; line-height: 1; margin-bottom: 6px; }
  .stat-label { font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: rgba(247,244,239,0.4); font-weight: 400; }
  .hero-big-text { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-family: 'Playfair Display', serif; font-size: clamp(4rem, 9vw, 10rem); color: rgba(255,255,255,0.04); white-space: nowrap; letter-spacing: -0.02em; pointer-events: none; }
  .hero-right-inner { position: absolute; top: 50px; left: 50px; right: 50px; }
  .hr-tag { font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--accent); font-weight: 500; margin-bottom: 16px; }
  .hr-title { font-family: 'Playfair Display', serif; font-size: 1.5rem; color: rgba(247,244,239,0.9); line-height: 1.3; margin-bottom: 8px; }
  .hr-sub { font-size: 0.85rem; color: rgba(247,244,239,0.35); line-height: 1.6; }

  section { padding: 120px 60px; }
  .section-tag { font-size: 0.72rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--accent); font-weight: 500; margin-bottom: 20px; display: flex; align-items: center; gap: 10px; }
  .section-tag::before { content: ''; display: inline-block; width: 24px; height: 1px; background: var(--accent); }
  h2 { font-family: 'Playfair Display', serif; font-size: clamp(2rem, 3.5vw, 3.5rem); line-height: 1.1; letter-spacing: -0.02em; }
  h2 em { font-style: italic; color: var(--accent); }

  .services { background: var(--cream); }
  .services-header { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: end; margin-bottom: 80px; }
  .services-header p { color: var(--mid); font-size: 1rem; line-height: 1.8; align-self: end; padding-bottom: 4px; }
  .services-grid { display: grid; grid-template-columns: repeat(3, 1fr); border-top: 1px solid var(--border); }
  .service-card { padding: 48px 40px; border-right: 1px solid var(--border); border-bottom: 1px solid var(--border); transition: background 0.3s; position: relative; overflow: hidden; }
  .service-card:nth-child(3n) { border-right: none; }
  .service-card::after { content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 3px; background: var(--accent); transform: scaleX(0); transform-origin: left; transition: transform 0.3s; }
  .service-card:hover { background: white; }
  .service-card:hover::after { transform: scaleX(1); }
  .service-num { font-size: 0.7rem; letter-spacing: 0.15em; color: var(--accent); font-weight: 500; margin-bottom: 24px; }
  .service-card h3 { font-family: 'Playfair Display', serif; font-size: 1.35rem; margin-bottom: 14px; letter-spacing: -0.01em; }
  .service-card p { color: var(--mid); font-size: 0.9rem; line-height: 1.75; }

  .work { background: var(--ink); color: var(--cream); }
  .work .section-tag { color: var(--accent); }
  .work h2 { color: var(--cream); }
  .work-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 60px; }
  .work-header a { color: var(--accent); text-decoration: none; font-size: 0.85rem; letter-spacing: 0.06em; text-transform: uppercase; display: flex; align-items: center; gap: 8px; transition: gap 0.2s; }
  .work-header a:hover { gap: 14px; }
  .work-header a::after { content: '→'; }
  .work-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 2px; }
  .work-card { position: relative; overflow: hidden; background: rgba(255,255,255,0.03); aspect-ratio: 16/10; cursor: pointer; }
  .work-card:first-child { grid-column: 1 / -1; aspect-ratio: 21/9; }
  .work-card-bg { position: absolute; inset: 0; transition: transform 0.6s ease; }
  .work-card:hover .work-card-bg { transform: scale(1.04); }
  .wc1 .work-card-bg { background: linear-gradient(135deg, #1a1814 0%, #2d2820 60%, rgba(200,169,110,0.15) 100%); }
  .wc2 .work-card-bg { background: linear-gradient(135deg, #141618 0%, #1e2530 100%); }
  .wc3 .work-card-bg { background: linear-gradient(135deg, #171514 0%, #251e18 100%); }
  .wc1-pattern { position: absolute; inset: 0; background-image: repeating-linear-gradient(45deg, rgba(200,169,110,0.04) 0px, rgba(200,169,110,0.04) 1px, transparent 1px, transparent 40px); }
  .work-card-info { position: absolute; bottom: 0; left: 0; right: 0; padding: 36px; background: linear-gradient(transparent, rgba(0,0,0,0.6)); }
  .work-label { font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--accent); margin-bottom: 8px; }
  .work-card-info h3 { font-family: 'Playfair Display', serif; font-size: 1.5rem; color: var(--cream); letter-spacing: -0.01em; }
  .work-card:first-child .work-card-info h3 { font-size: 2rem; }
  .work-card-info p { color: rgba(247,244,239,0.5); font-size: 0.85rem; margin-top: 4px; }

  .process { background: white; padding: 120px 60px; }
  .process-header { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: end; margin-bottom: 80px; }
  .process-header p { color: var(--mid); font-size: 1rem; line-height: 1.8; align-self: end; }
  .process-steps { display: grid; grid-template-columns: repeat(4, 1fr); }
  .process-step { padding: 0 40px; border-right: 1px solid var(--border); }
  .process-step:first-child { padding-left: 0; }
  .process-step:last-child { border-right: none; padding-right: 0; }
  .step-num { font-family: 'Playfair Display', serif; font-size: 3.5rem; color: var(--border); line-height: 1; margin-bottom: 24px; }
  .process-step h3 { font-family: 'Playfair Display', serif; font-size: 1.2rem; margin-bottom: 12px; }
  .process-step p { color: var(--mid); font-size: 0.9rem; line-height: 1.75; }

  .cta-section { background: var(--ink); display: grid; grid-template-columns: 1fr 1fr; min-height: 60vh; align-items: center; padding: 0; }
  .cta-left { padding: 100px 80px; border-right: 1px solid rgba(255,255,255,0.06); }
  .cta-left .section-tag { color: var(--accent); }
  .cta-left h2 { color: var(--cream); font-size: clamp(2.2rem, 4vw, 4rem); margin-bottom: 24px; margin-top: 16px; }
  .cta-left p { color: rgba(247,244,239,0.5); line-height: 1.8; max-width: 380px; margin-bottom: 40px; }
  .cta-right { padding: 100px 80px; display: flex; flex-direction: column; gap: 28px; }
  .contact-item { border-bottom: 1px solid rgba(255,255,255,0.06); padding-bottom: 28px; }
  .contact-item:last-child { border-bottom: none; padding-bottom: 0; }
  .contact-label { font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--accent); margin-bottom: 8px; }
  .contact-value { color: var(--cream); font-size: 1.1rem; text-decoration: none; transition: color 0.2s; }
  .contact-value:hover { color: var(--accent); }

  footer { background: var(--ink); color: rgba(247,244,239,0.3); border-top: 1px solid rgba(255,255,255,0.06); display: flex; justify-content: space-between; align-items: center; padding: 28px 60px; font-size: 0.8rem; letter-spacing: 0.04em; }
  footer a { color: rgba(247,244,239,0.3); text-decoration: none; transition: color 0.2s; }
  footer a:hover { color: var(--accent); }
  .footer-logo { font-family: 'Playfair Display', serif; font-size: 1rem; color: rgba(247,244,239,0.6); }
  .footer-logo span { color: var(--accent); }

  .fade-up { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
  .fade-up.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 900px) {
    nav { padding: 20px 24px; }
    .nav-links { display: none; }
    .hero { grid-template-columns: 1fr; }
    .hero-right { display: none; }
    .hero-left { padding: 40px 24px 60px; }
    section, .process, .cta-section { padding: 80px 24px; }
    .services-header, .process-header { grid-template-columns: 1fr; }
    .services-grid { grid-template-columns: 1fr; }
    .service-card { border-right: none; }
    .process-steps { grid-template-columns: 1fr 1fr; gap: 40px; }
    .process-step { border-right: none; padding: 0 !important; }
    .work-grid { grid-template-columns: 1fr; }
    .work-card:first-child { grid-column: 1; }
    .cta-section { grid-template-columns: 1fr; }
    .cta-left, .cta-right { padding: 60px 24px; }
    footer { flex-direction: column; gap: 12px; text-align: center; padding: 24px; }
  }
</style>
</head>
<body>

<nav id="nav">
  <a href="#" class="logo">Churnless<span>.</span></a>
  <ul class="nav-links">
    <li><a href="#services">Services</a></li>
    <li><a href="#work">Work</a></li>
    <li><a href="#process">Process</a></li>
    <li><a href="#contact" class="nav-cta">Let's Talk</a></li>
  </ul>
</nav>

<section class="hero">
  <div class="hero-left">
    <div class="hero-tag">Growth Operating Agency</div>
    <h1>We build your <em>growth engine.</em></h1>
    <p class="hero-sub">We design and implement the systems that drive revenue — across marketing, sales, and retention — using data, automation, and strategic experimentation.</p>
    <div class="hero-actions">
      <a href="#contact" class="btn-primary">Start a Project</a>
      <a href="#work" class="btn-ghost">See Our Work</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-big-text">Growth</div>
    <div class="hero-right-inner">
      <div class="hr-tag">Currently Accepting Clients</div>
      <div class="hr-title">Q2 2025 Roster</div>
      <div class="hr-sub">Limited to 4 new engagements per quarter to maintain the quality our clients deserve.</div>
    </div>
    <div class="hero-stats">
      <div class="stat-box"><div class="stat-num">94%</div><div class="stat-label">Client Retention</div></div>
      <div class="stat-box"><div class="stat-num">3.2×</div><div class="stat-label">Avg. Revenue Lift</div></div>
      <div class="stat-box"><div class="stat-num">40+</div><div class="stat-label">Brands Grown</div></div>
      <div class="stat-box"><div class="stat-num">6yr</div><div class="stat-label">In the Field</div></div>
    </div>
  </div>
</section>

<section class="services" id="services">
  <div class="services-header fade-up">
    <div>
      <div class="section-tag">What We Do</div>
      <h2>Systems that turn traffic into <em>revenue</em></h2>
    </div>
    <p>We don't just run campaigns — we build and optimize the full revenue operating system. Every service connects marketing, sales, and retention into one compounding engine.</p>
  </div>
  <div class="services-grid">
    <div class="service-card fade-up">
      <div class="service-num">01</div>
      <h3>Growth Strategy</h3>
      <p>We audit your full revenue system, identify the highest-leverage opportunities, and build a clear roadmap that connects marketing, sales, and retention.</p>
    </div>
    <div class="service-card fade-up">
      <div class="service-num">02</div>
      <h3>Marketing Systems</h3>
      <p>Paid media, SEO, and content — architected as an integrated acquisition engine designed to drive compounding, predictable traffic and leads.</p>
    </div>
    <div class="service-card fade-up">
      <div class="service-num">03</div>
      <h3>Sales Enablement</h3>
      <p>We build the pipelines, sequences, and automation that move leads through your funnel faster and convert them into paying customers consistently.</p>
    </div>
    <div class="service-card fade-up">
      <div class="service-num">04</div>
      <h3>Customer Retention</h3>
      <p>Lifecycle programs, CRM automation, and churn-reduction strategies that turn one-time buyers into long-term, high-LTV customers.</p>
    </div>
    <div class="service-card fade-up">
      <div class="service-num">05</div>
      <h3>Data & Automation</h3>
      <p>We build the data infrastructure and automation workflows that eliminate guesswork and let your growth systems run with minimal manual effort.</p>
    </div>
    <div class="service-card fade-up">
      <div class="service-num">06</div>
      <h3>Strategic Experimentation</h3>
      <p>A structured testing framework across your funnel — so you're always running experiments, finding winners, and scaling what works.</p>
    </div>
  </div>
</section>

<section class="work" id="work">
  <div class="work-header fade-up">
    <div>
      <div class="section-tag">Selected Work</div>
      <h2>Results we're <em>proud of</em></h2>
    </div>
    <a href="#contact">View All Cases</a>
  </div>
  <div class="work-grid">
    <div class="work-card wc1 fade-up">
      <div class="work-card-bg"></div>
      <div class="wc1-pattern"></div>
      <div class="work-card-info">
        <div class="work-label">E-Commerce · Paid Media · Email</div>
        <h3>Meridian Supply Co.</h3>
        <p>218% increase in ROAS over 6 months, scaling from $40K to $180K monthly ad spend profitably.</p>
      </div>
    </div>
    <div class="work-card wc2 fade-up">
      <div class="work-card-bg"></div>
      <div class="work-card-info">
        <div class="work-label">SaaS · Growth Strategy</div>
        <h3>Fieldnote App</h3>
        <p>Reduced churn by 34% through lifecycle email redesign.</p>
      </div>
    </div>
    <div class="work-card wc3 fade-up">
      <div class="work-card-bg"></div>
      <div class="work-card-info">
        <div class="work-label">DTC · SEO · Content</div>
        <h3>Haven Wellness</h3>
        <p>Organic traffic tripled in 9 months via content strategy.</p>
      </div>
    </div>
  </div>
</section>

<section class="process" id="process">
  <div class="process-header fade-up">
    <div>
      <div class="section-tag">How We Work</div>
      <h2>A process built for <em>clarity</em></h2>
    </div>
    <p>We don't hand you a strategy deck and disappear. We operate inside your business as a growth partner — building, running, and improving your revenue systems over time.</p>
  </div>
  <div class="process-steps">
    <div class="process-step fade-up">
      <div class="step-num">01</div>
      <h3>Diagnose</h3>
      <p>We map your entire revenue system — from first touch to retention — and pinpoint exactly where the leaks and biggest opportunities are.</p>
    </div>
    <div class="process-step fade-up">
      <div class="step-num">02</div>
      <h3>Architect</h3>
      <p>We design your growth engine: the channels, systems, automation, and experiments that will move the needle in the right order.</p>
    </div>
    <div class="process-step fade-up">
      <div class="step-num">03</div>
      <h3>Operate</h3>
      <p>We build and run everything — campaigns, sequences, funnels, and tests — iterating fast based on real data, not assumptions.</p>
    </div>
    <div class="process-step fade-up">
      <div class="step-num">04</div>
      <h3>Compound</h3>
      <p>Winners get systemised and scaled. We hand you a self-reinforcing growth engine that gets stronger and more efficient over time.</p>
    </div>
  </div>
</section>

<div class="cta-section" id="contact">
  <div class="cta-left fade-up">
    <div class="section-tag">Let's Work Together</div>
    <h2>Ready to build a real <em>growth engine?</em></h2>
    <p>Tell us where your business is today and where you want to take it. We'll come back with an honest assessment of what's holding you back and what we'd do about it.</p>
    <a href="mailto:hello@churnlessstudio.com" class="btn-primary">Send Us a Message</a>
  </div>
  <div class="cta-right fade-up">
    <div class="contact-item">
      <div class="contact-label">Email</div>
      <a href="mailto:hello@churnlessstudio.com" class="contact-value">hello@churnlessstudio.com</a>
    </div>
    <div class="contact-item">
      <div class="contact-label">New Business</div>
      <a href="mailto:work@churnlessstudio.com" class="contact-value">work@churnlessstudio.com</a>
    </div>
    <div class="contact-item">
      <div class="contact-label">Based in</div>
      <span class="contact-value">Available Worldwide</span>
    </div>
    <div class="contact-item">
      <div class="contact-label">Follow</div>
      <div style="display:flex;gap:20px;margin-top:4px">
        <a href="#" class="contact-value" style="font-size:0.9rem">Twitter</a>
        <a href="#" class="contact-value" style="font-size:0.9rem">LinkedIn</a>
        <a href="#" class="contact-value" style="font-size:0.9rem">Instagram</a>
      </div>
    </div>
  </div>
</div>

<footer>
  <div class="footer-logo">Churnless<span>.</span></div>
  <div>© 2025 Churnless Studio. All rights reserved.</div>
  <div style="display:flex;gap:24px">
    <a href="#">Privacy</a>
    <a href="#">Terms</a>
  </div>
</footer>

<script>
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => nav.classList.toggle('scrolled', window.scrollY > 20));
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => { if (e.isIntersecting) setTimeout(() => e.target.classList.add('visible'), i * 80); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));
</script>
</body>
</html>
