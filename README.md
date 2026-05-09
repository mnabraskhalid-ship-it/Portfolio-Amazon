<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Muhammad Nabras Khalid — Amazon Catalog Manager</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #C9A84C;
    --gold-light: #E8C96A;
    --gold-pale: #FDF6E3;
    --amazon-orange: #FF9900;
    --dark: #0D0D0D;
    --dark-2: #141414;
    --dark-3: #1E1E1E;
    --dark-4: #272727;
    --text-primary: #F5F0E8;
    --text-muted: #9A9080;
    --text-dim: #6A6055;
    --border: rgba(201,168,76,0.15);
    --border-strong: rgba(201,168,76,0.35);
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--dark);
    color: var(--text-primary);
    overflow-x: hidden;
    line-height: 1.6;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 20px 60px;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(13,13,13,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 0.5px solid var(--border);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 18px; font-weight: 700;
    color: var(--gold);
    letter-spacing: 0.5px;
  }

  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    font-size: 13px; font-weight: 500; letter-spacing: 1.2px; text-transform: uppercase;
    color: var(--text-muted); text-decoration: none;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: var(--gold); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 120px 60px 80px;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute; inset: 0;
    background:
      radial-gradient(ellipse 60% 50% at 80% 50%, rgba(201,168,76,0.06) 0%, transparent 70%),
      radial-gradient(ellipse 40% 60% at 20% 80%, rgba(255,153,0,0.04) 0%, transparent 60%);
  }

  .hero-grid-overlay {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
    background-size: 80px 80px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 0%, transparent 100%);
  }

  .hero-content { position: relative; max-width: 700px; }

  .hero-tag {
    display: inline-flex; align-items: center; gap: 10px;
    padding: 8px 16px;
    border: 0.5px solid var(--border-strong);
    border-radius: 100px;
    font-size: 11px; font-weight: 600; letter-spacing: 2px; text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 32px;
    background: rgba(201,168,76,0.05);
    animation: fadeUp 0.8s ease both;
  }

  .hero-tag-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--amazon-orange);
    animation: pulse 2s ease infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(48px, 6vw, 80px);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -1px;
    margin-bottom: 12px;
    animation: fadeUp 0.8s 0.1s ease both;
  }

  h1 .gold { color: var(--gold); }

  .hero-subtitle {
    font-size: 15px; font-weight: 400; color: var(--text-muted);
    margin-bottom: 40px;
    max-width: 520px;
    line-height: 1.8;
    animation: fadeUp 0.8s 0.2s ease both;
  }

  .hero-stats {
    display: flex; gap: 48px;
    margin-bottom: 48px;
    animation: fadeUp 0.8s 0.3s ease both;
  }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 36px; font-weight: 700;
    color: var(--gold);
    line-height: 1;
  }

  .stat-label {
    font-size: 11px; font-weight: 500; letter-spacing: 1.5px;
    text-transform: uppercase; color: var(--text-muted);
    margin-top: 4px;
  }

  .hero-cta {
    display: flex; gap: 16px; flex-wrap: wrap;
    animation: fadeUp 0.8s 0.4s ease both;
  }

  .btn-primary {
    padding: 14px 32px;
    background: var(--gold);
    color: var(--dark);
    border: none; border-radius: 4px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase;
    cursor: pointer; text-decoration: none;
    transition: background 0.3s, transform 0.2s;
    display: inline-block;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); }

  .btn-outline {
    padding: 14px 32px;
    background: transparent;
    color: var(--gold);
    border: 0.5px solid var(--border-strong);
    border-radius: 4px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase;
    cursor: pointer; text-decoration: none;
    transition: border-color 0.3s, background 0.3s, transform 0.2s;
    display: inline-block;
  }
  .btn-outline:hover { background: rgba(201,168,76,0.08); border-color: var(--gold); transform: translateY(-2px); }

  /* ── SECTIONS ── */
  section { padding: 100px 60px; }

  .section-label {
    font-size: 10px; font-weight: 600; letter-spacing: 3px; text-transform: uppercase;
    color: var(--gold); margin-bottom: 16px;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(32px, 4vw, 48px);
    font-weight: 700;
    line-height: 1.1;
    margin-bottom: 20px;
    max-width: 600px;
  }

  .section-desc {
    font-size: 15px; color: var(--text-muted); line-height: 1.8;
    max-width: 580px; margin-bottom: 60px;
  }

  /* ── BRANDS ── */
  .brands-section { background: var(--dark-2); border-top: 0.5px solid var(--border); border-bottom: 0.5px solid var(--border); }

  .brands-label {
    font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
    color: var(--text-dim); text-align: center; margin-bottom: 40px;
  }

  .brands-grid {
    display: flex; flex-wrap: wrap; justify-content: center; align-items: center;
    gap: 16px;
  }

  .brand-pill {
    padding: 12px 28px;
    border: 0.5px solid var(--border);
    border-radius: 100px;
    font-size: 13px; font-weight: 500; letter-spacing: 0.5px;
    color: var(--text-muted);
    background: var(--dark-3);
    transition: border-color 0.3s, color 0.3s, transform 0.2s;
    cursor: default;
  }
  .brand-pill:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-3px); }

  .brand-pill.featured {
    border-color: var(--border-strong);
    color: var(--gold);
    background: rgba(201,168,76,0.06);
  }

  /* ── SERVICES ── */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 0.5px solid var(--border);
  }

  .service-card {
    background: var(--dark);
    padding: 40px 36px;
    transition: background 0.3s;
    position: relative;
    overflow: hidden;
  }

  .service-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--gold);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s;
  }

  .service-card:hover { background: var(--dark-2); }
  .service-card:hover::before { transform: scaleX(1); }

  .service-icon {
    width: 44px; height: 44px;
    border: 0.5px solid var(--border-strong);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 24px;
    font-size: 20px;
    background: rgba(201,168,76,0.05);
  }

  .service-title {
    font-family: 'Playfair Display', serif;
    font-size: 18px; font-weight: 700;
    margin-bottom: 12px;
    color: var(--text-primary);
  }

  .service-desc {
    font-size: 13px; color: var(--text-muted); line-height: 1.7;
  }

  /* ── EXPERTISE ── */
  .expertise-section { background: var(--dark-2); }

  .expertise-wrap {
    display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: start;
  }

  .expertise-list { display: flex; flex-direction: column; gap: 0; }

  .exp-item {
    display: flex; align-items: flex-start; gap: 20px;
    padding: 24px 0;
    border-bottom: 0.5px solid var(--border);
    transition: padding-left 0.3s;
    cursor: default;
  }
  .exp-item:hover { padding-left: 8px; }
  .exp-item:first-child { border-top: 0.5px solid var(--border); }

  .exp-num {
    font-family: 'Playfair Display', serif;
    font-size: 11px; font-weight: 700; color: var(--text-dim);
    min-width: 24px; padding-top: 2px;
  }

  .exp-text { font-size: 14px; font-weight: 500; color: var(--text-primary); }
  .exp-sub { font-size: 12px; color: var(--text-muted); margin-top: 3px; }

  .exp-arrow {
    margin-left: auto;
    color: var(--text-dim);
    font-size: 16px;
    transition: color 0.3s, transform 0.3s;
    padding-top: 2px;
  }
  .exp-item:hover .exp-arrow { color: var(--gold); transform: translateX(4px); }

  /* Profile card */
  .profile-card {
    background: var(--dark-3);
    border: 0.5px solid var(--border);
    border-radius: 2px;
    padding: 48px 40px;
    position: sticky; top: 100px;
  }

  .profile-avatar {
    width: 80px; height: 80px; border-radius: 50%;
    background: linear-gradient(135deg, var(--gold) 0%, #8B6914 100%);
    display: flex; align-items: center; justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 28px; font-weight: 700; color: var(--dark);
    margin-bottom: 24px;
  }

  .profile-name {
    font-family: 'Playfair Display', serif;
    font-size: 22px; font-weight: 700; margin-bottom: 4px;
  }

  .profile-role {
    font-size: 12px; letter-spacing: 1.5px; text-transform: uppercase;
    color: var(--gold); margin-bottom: 8px;
  }

  .profile-location {
    font-size: 13px; color: var(--text-muted); margin-bottom: 28px;
    display: flex; align-items: center; gap: 6px;
  }

  .profile-divider {
    border: none; border-top: 0.5px solid var(--border); margin-bottom: 28px;
  }

  .profile-meta { display: flex; flex-direction: column; gap: 14px; }

  .meta-row { display: flex; align-items: baseline; justify-content: space-between; }
  .meta-key { font-size: 11px; letter-spacing: 1px; text-transform: uppercase; color: var(--text-dim); }
  .meta-val { font-size: 13px; font-weight: 500; color: var(--text-primary); }

  /* ── CONTACT ── */
  .contact-section {
    background: var(--dark);
    border-top: 0.5px solid var(--border);
  }

  .contact-inner {
    max-width: 600px; margin: 0 auto; text-align: center;
  }

  .contact-inner .section-title { margin: 0 auto 16px; }
  .contact-inner .section-desc { margin: 0 auto 40px; }

  .contact-links {
    display: flex; flex-wrap: wrap; justify-content: center; gap: 16px;
  }

  .contact-link {
    display: flex; align-items: center; gap: 10px;
    padding: 14px 28px;
    border: 0.5px solid var(--border);
    border-radius: 4px;
    font-size: 13px; font-weight: 500;
    color: var(--text-muted);
    text-decoration: none;
    background: var(--dark-2);
    transition: border-color 0.3s, color 0.3s, transform 0.2s;
  }
  .contact-link:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-3px); }

  .contact-icon { font-size: 18px; }

  /* ── FOOTER ── */
  footer {
    padding: 32px 60px;
    border-top: 0.5px solid var(--border);
    display: flex; align-items: center; justify-content: space-between;
    background: var(--dark-2);
  }

  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: 15px; font-weight: 700; color: var(--gold);
  }

  .footer-copy { font-size: 12px; color: var(--text-dim); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── RESPONSIVE ── */
  @media (max-width: 900px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    section { padding: 72px 24px; }
    .hero { padding: 100px 24px 60px; }
    .hero-stats { gap: 28px; flex-wrap: wrap; }
    footer { padding: 24px; flex-direction: column; gap: 8px; text-align: center; }
    .expertise-wrap { grid-template-columns: 1fr; gap: 48px; }
    .profile-card { position: static; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">MNK</div>
  <ul class="nav-links">
    <li><a href="#brands">Brands</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#expertise">Expertise</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid-overlay"></div>
  <div class="hero-content">
    <div class="hero-tag">
      <span class="hero-tag-dot"></span>
      Available for New Projects
    </div>
    <h1>Muhammad<br>Nabras <span class="gold">Khalid</span></h1>
    <p class="hero-subtitle">
      Amazon Catalog Manager with 3+ years of hands-on experience driving catalog excellence, suppression recovery, and brand protection across 9 global Amazon marketplaces — US, UK, CA, IT, ES, DE, FR, AU & JP.
    </p>
    <div class="hero-stats">
      <div>
        <div class="stat-num">3+</div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div>
        <div class="stat-num">9+</div>
        <div class="stat-label">Brands Managed</div>
      </div>
      <div>
        <div class="stat-num">9</div>
        <div class="stat-label">Global Marketplaces</div>
      </div>
    </div>
    <div class="hero-cta">
      <a href="#contact" class="btn-primary">Hire Me</a>
      <a href="#services" class="btn-outline">View Services</a>
    </div>
  </div>
</section>

<!-- BRANDS -->
<section class="brands-section" id="brands" style="padding: 72px 60px;">
  <p class="brands-label">Brands I've Worked With</p>
  <div class="brands-grid">
    <div class="brand-pill featured">★ Grace & Stella — USA #1 Under Eye Mask</div>
    <div class="brand-pill">LEGUSHE</div>
    <div class="brand-pill">PREFECT REMEDY</div>
    <div class="brand-pill">PILPOC</div>
    <div class="brand-pill">PROTECT LIFE</div>
    <div class="brand-pill">Ballotte</div>
    <div class="brand-pill">Rockland Toys for Less</div>
    <div class="brand-pill">Venus Visage</div>
    <div class="brand-pill">The EZPIK</div>
  </div>
</section>

<!-- MARKETPLACES -->
<section style="padding: 72px 60px; background: var(--dark);">
  <p class="section-label" style="text-align:center;">Global Reach</p>
  <h2 class="section-title reveal" style="text-align:center; margin: 0 auto 12px;">Active on 9 Amazon<br>Marketplaces Worldwide</h2>
  <p class="section-desc reveal" style="text-align:center; margin: 0 auto 52px;">I manage catalogs across every major Amazon marketplace — handling regional compliance, locale-specific content, and multi-market listing strategy.</p>
  <div class="reveal" style="display:grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 12px; max-width: 900px; margin: 0 auto;">
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇺🇸</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">United States</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.com</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇬🇧</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">United Kingdom</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.co.uk</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇨🇦</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">Canada</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.ca</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇩🇪</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">Germany</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.de</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇫🇷</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">France</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.fr</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇮🇹</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">Italy</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.it</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇪🇸</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">Spain</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.es</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇦🇺</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">Australia</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.com.au</div>
    </div>
    <div style="background:var(--dark-3); border:0.5px solid var(--border); border-radius:8px; padding:24px 16px; text-align:center; transition: border-color 0.3s, transform 0.2s;" onmouseenter="this.style.borderColor='var(--gold)';this.style.transform='translateY(-4px)'" onmouseleave="this.style.borderColor='var(--border)';this.style.transform='translateY(0)'">
      <div style="font-size:32px; margin-bottom:10px;">🇯🇵</div>
      <div style="font-size:13px; font-weight:600; color:var(--text-primary);">Japan</div>
      <div style="font-size:11px; color:var(--gold); letter-spacing:1px; margin-top:4px;">amazon.co.jp</div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <p class="section-label reveal">What I Do</p>
  <h2 class="section-title reveal">Full-Spectrum Amazon<br>Catalog Management</h2>
  <p class="section-desc reveal">From new listing creation to hijacker removal and A+ content — I handle every layer of your Amazon catalog so your brand stays competitive and compliant.</p>

  <div class="services-grid reveal">
    <div class="service-card">
      <div class="service-icon">📦</div>
      <div class="service-title">Listing Creation & Optimization</div>
      <p class="service-desc">Creating new listings from scratch with SEO-optimized titles, compelling bullet points, and accurate back-end attributes to maximize discoverability and conversion.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🖼️</div>
      <div class="service-title">Image & A+ Content</div>
      <p class="service-desc">Fixing non-compliant images and updating Premium A+ (PA+) and A+ Content to ensure brand storytelling meets Amazon's latest standards and drives higher conversions.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🛡️</div>
      <div class="service-title">Hijacker Removal</div>
      <p class="service-desc">Identifying and removing unauthorized sellers on your listings to protect brand integrity, Buy Box ownership, and customer trust.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">⚙️</div>
      <div class="service-title">Suppressed & Blocked Listings</div>
      <p class="service-desc">Diagnosing and resolving suppressed or blocked listings due to policy violations, incomplete attributes, or compliance issues — getting your products back live fast.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">📊</div>
      <div class="service-title">Sales & Rank Tracking</div>
      <p class="service-desc">Maintaining and updating Sales & Rank Trackers for real-time performance monitoring, enabling data-driven decisions across your entire catalog.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🎯</div>
      <div class="service-title">Deals, Promotions & Coupons</div>
      <p class="service-desc">Planning and managing Lightning Deals, promotions, giveaways, and coupons to drive traffic, increase BSR, and grow revenue strategically.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🏥</div>
      <div class="service-title">Account Health Management</div>
      <p class="service-desc">Monitoring and resolving account health issues — policy violations, performance metrics, and compliance flags — to protect your seller account standing.</p>
    </div>
    <div class="service-card">
      <div class="service-icon">🚚</div>
      <div class="service-title">MCF Order Management</div>
      <p class="service-desc">Managing Multi-Channel Fulfillment (MCF) orders to ensure seamless inventory fulfillment across all sales channels beyond Amazon.com.</p>
    </div>
  </div>
</section>

<!-- EXPERTISE -->
<section class="expertise-section" id="expertise">
  <div class="expertise-wrap">
    <div>
      <p class="section-label reveal">Deep Expertise</p>
      <h2 class="section-title reveal">Every Task,<br>Handled with Precision</h2>
      <p class="section-desc reveal">3 years of focused Amazon catalog work means I've seen — and solved — every catalog challenge brands face on the platform.</p>

      <div class="expertise-list">
        <div class="exp-item reveal">
          <span class="exp-num">01</span>
          <div>
            <div class="exp-text">Titles, Bullets & Back-End Attributes</div>
            <div class="exp-sub">Keyword-rich, policy-compliant, conversion-focused</div>
          </div>
          <span class="exp-arrow">→</span>
        </div>
        <div class="exp-item reveal">
          <span class="exp-num">02</span>
          <div>
            <div class="exp-text">Existing Listing Updates</div>
            <div class="exp-sub">Refreshing outdated content to current Amazon standards</div>
          </div>
          <span class="exp-arrow">→</span>
        </div>
        <div class="exp-item reveal">
          <span class="exp-num">03</span>
          <div>
            <div class="exp-text">PA+ / A+ Content</div>
            <div class="exp-sub">Updating and fixing enhanced brand content modules</div>
          </div>
          <span class="exp-arrow">→</span>
        </div>
        <div class="exp-item reveal">
          <span class="exp-num">04</span>
          <div>
            <div class="exp-text">Hijacker Removal</div>
            <div class="exp-sub">Protecting Buy Box and brand reputation</div>
          </div>
          <span class="exp-arrow">→</span>
        </div>
        <div class="exp-item reveal">
          <span class="exp-num">05</span>
          <div>
            <div class="exp-text">Suppression & Block Fixing</div>
            <div class="exp-sub">Rapid resolution of listing compliance issues</div>
          </div>
          <span class="exp-arrow">→</span>
        </div>
        <div class="exp-item reveal">
          <span class="exp-num">06</span>
          <div>
            <div class="exp-text">Giveaways & Promotions</div>
            <div class="exp-sub">Strategic campaign management for ranking growth</div>
          </div>
          <span class="exp-arrow">→</span>
        </div>
      </div>
    </div>

    <div>
      <div class="profile-card reveal">
        <div class="profile-avatar">MN</div>
        <div class="profile-name">Muhammad Nabras Khalid</div>
        <div class="profile-role">Amazon Catalog Manager</div>
        <div class="profile-location">📍 Faisalabad, Pakistan</div>
        <hr class="profile-divider">
        <div class="profile-meta">
          <div class="meta-row">
            <span class="meta-key">Experience</span>
            <span class="meta-val">3+ Years</span>
          </div>
          <div class="meta-row">
            <span class="meta-key">Specialization</span>
            <span class="meta-val">Amazon Catalog</span>
          </div>
          <div class="meta-row">
            <span class="meta-key">Top Client</span>
            <span class="meta-val">Grace & Stella</span>
          </div>
          <div class="meta-row">
            <span class="meta-key">Marketplaces</span>
            <span class="meta-val">9 Global Markets</span>
          </div>
          <div class="meta-row">
            <span class="meta-key">Availability</span>
            <span class="meta-val" style="color: #4ade80;">Open to Work</span>
          </div>
        </div>
        <hr class="profile-divider" style="margin-top: 28px;">
        <a href="mailto:m.nabraskhalid@gmail.com" class="btn-primary" style="display: block; text-align: center; margin-top: 0;">Get in Touch</a>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact-section" id="contact">
  <div class="contact-inner">
    <p class="section-label">Let's Work Together</p>
    <h2 class="section-title reveal">Ready to Elevate<br>Your Amazon Catalog?</h2>
    <p class="section-desc reveal">Whether you need a full catalog audit, listing creation, or urgent suppression fixes — I'm available to help your brand succeed on Amazon.</p>
    <div class="contact-links reveal">
      <a href="mailto:m.nabraskhalid@gmail.com" class="contact-link" title="m.nabraskhalid@gmail.com" style="flex-direction:column; padding: 20px 32px; gap:8px;">
        <span style="font-size:28px;">✉️</span>
        <span style="font-size:11px; letter-spacing:1.5px; text-transform:uppercase; font-weight:600;">Email</span>
      </a>
      <a href="https://pk.linkedin.com/in/muhammad-nabras-khalid-b4ba1119b" target="_blank" class="contact-link" title="muhammad-nabras-khalid" style="flex-direction:column; padding: 20px 32px; gap:8px;">
        <span style="font-size:28px;">💼</span>
        <span style="font-size:11px; letter-spacing:1.5px; text-transform:uppercase; font-weight:600;">LinkedIn</span>
      </a>
      <a href="https://wa.me/923251806203" target="_blank" class="contact-link" title="+92 325 1806203" style="flex-direction:column; padding: 20px 32px; gap:8px;">
        <span style="font-size:28px;">📱</span>
        <span style="font-size:11px; letter-spacing:1.5px; text-transform:uppercase; font-weight:600;">WhatsApp</span>
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Muhammad Nabras Khalid</div>
  <div class="footer-copy">© 2025 · Amazon Catalog Manager · Faisalabad, Pakistan</div>
</footer>

<script>
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
