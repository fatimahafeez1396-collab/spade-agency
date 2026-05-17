# spade-agency<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>SPADE Agency</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"/>
  <style>
    /* ============================================================
       CSS VARIABLES & RESET
    ============================================================ */
    :root {
      --bg-dark:    #070b14;
      --bg-card:    #0d1526;
      --bg-card2:   #101929;
      --blue:       #3b82f6;
      --blue-bright:#60a5fa;
      --purple:     #7c3aed;
      --accent:     #2563eb;
      --glow:       rgba(59,130,246,0.25);
      --text:       #e2e8f0;
      --muted:      #94a3b8;
      --border:     rgba(59,130,246,0.18);
      --white:      #ffffff;
      --font-head:  'Syne', sans-serif;
      --font-body:  'DM Sans', sans-serif;
    }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--bg-dark);
      color: var(--text);
      font-family: var(--font-body);
      font-size: 15px;
      line-height: 1.7;
      overflow-x: hidden;
    }
    a { text-decoration: none; color: inherit; }
    img { max-width: 100%; display: block; }
    ul { list-style: none; }

    /* ============================================================
       UTILITY
    ============================================================ */
    .container { max-width: 1140px; margin: 0 auto; padding: 0 24px; }
    .section-label {
      font-size: 11px; font-weight: 600; letter-spacing: 2.5px;
      text-transform: uppercase; color: var(--blue); margin-bottom: 10px;
    }
    .btn-primary {
      display: inline-flex; align-items: center; gap: 8px;
      background: var(--blue); color: #fff; font-family: var(--font-body);
      font-size: 14px; font-weight: 600; padding: 12px 26px;
      border-radius: 50px; border: none; cursor: pointer;
      transition: background .25s, box-shadow .25s, transform .2s;
    }
    .btn-primary:hover { background: #1d4ed8; box-shadow: 0 0 20px var(--glow); transform: translateY(-1px); }
    .btn-outline {
      display: inline-flex; align-items: center; gap: 8px;
      background: transparent; color: #fff; font-family: var(--font-body);
      font-size: 14px; font-weight: 600; padding: 11px 24px;
      border-radius: 50px; border: 1.5px solid rgba(255,255,255,0.25); cursor: pointer;
      transition: border-color .25s, background .25s, transform .2s;
    }
    .btn-outline:hover { border-color: var(--blue); background: rgba(59,130,246,0.1); transform: translateY(-1px); }
    .icon-circle {
      width: 40px; height: 40px; border-radius: 50%;
      background: rgba(59,130,246,0.15); border: 1.5px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 15px; color: var(--blue); flex-shrink: 0;
    }
    .star { color: #fbbf24; font-size: 13px; }

    /* Scroll animations */
    .reveal { opacity: 0; transform: translateY(30px); transition: opacity .6s ease, transform .6s ease; }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* ============================================================
       NAVBAR
    ============================================================ */
    nav {
      position: fixed; top: 0; left: 0; width: 100%; z-index: 1000;
      background: rgba(7,11,20,0.85); backdrop-filter: blur(14px);
      border-bottom: 1px solid var(--border);
    }
    .nav-inner {
      display: flex; align-items: center; justify-content: space-between;
      height: 64px;
    }
    .logo {
      font-family: var(--font-head); font-size: 20px; font-weight: 800;
      color: #fff; display: flex; align-items: center; gap: 8px;
    }
    .logo span { color: var(--blue); }
    .logo-icon {
      width: 28px; height: 28px; background: var(--blue);
      border-radius: 6px; display: flex; align-items: center; justify-content: center;
      font-size: 13px; font-weight: 900; color: #fff;
    }
    .nav-links { display: flex; align-items: center; gap: 30px; }
    .nav-links a {
      font-size: 13px; font-weight: 500; color: var(--muted);
      transition: color .2s; letter-spacing: .3px;
    }
    .nav-links a:hover, .nav-links a.active { color: #fff; }
    .nav-actions { display: flex; align-items: center; gap: 14px; }
    .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 4px; }
    .hamburger span { width: 22px; height: 2px; background: #fff; border-radius: 2px; transition: .3s; }
    .mobile-menu {
      display: none; flex-direction: column; gap: 0;
      background: var(--bg-card); border-top: 1px solid var(--border);
    }
    .mobile-menu.open { display: flex; }
    .mobile-menu a {
      padding: 14px 24px; font-size: 14px; color: var(--muted);
      border-bottom: 1px solid var(--border); transition: color .2s;
    }
    .mobile-menu a:hover { color: #fff; }

    /* ============================================================
       HERO
    ============================================================ */
    .hero {
      min-height: 100vh; position: relative; overflow: hidden;
      display: flex; align-items: center; padding-top: 64px;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background: radial-gradient(ellipse 80% 60% at 50% 0%, rgba(59,130,246,0.18) 0%, transparent 70%),
                  radial-gradient(ellipse 60% 50% at 80% 50%, rgba(124,58,237,0.12) 0%, transparent 60%),
                  radial-gradient(ellipse 50% 40% at 20% 80%, rgba(59,130,246,0.1) 0%, transparent 60%),
                  linear-gradient(180deg, #070b14 0%, #0a1020 100%);
    }
    /* Stars */
    .hero-bg::before {
      content: '';
      position: absolute; inset: 0;
      background-image:
        radial-gradient(1px 1px at 10% 15%, rgba(255,255,255,.5) 0%, transparent 100%),
        radial-gradient(1px 1px at 25% 35%, rgba(255,255,255,.3) 0%, transparent 100%),
        radial-gradient(1px 1px at 40% 10%, rgba(255,255,255,.4) 0%, transparent 100%),
        radial-gradient(1px 1px at 60% 25%, rgba(255,255,255,.3) 0%, transparent 100%),
        radial-gradient(1px 1px at 75% 5%, rgba(255,255,255,.5) 0%, transparent 100%),
        radial-gradient(1px 1px at 85% 40%, rgba(255,255,255,.3) 0%, transparent 100%),
        radial-gradient(1px 1px at 90% 70%, rgba(255,255,255,.4) 0%, transparent 100%),
        radial-gradient(1px 1px at 15% 65%, rgba(255,255,255,.3) 0%, transparent 100%),
        radial-gradient(1px 1px at 50% 80%, rgba(255,255,255,.2) 0%, transparent 100%),
        radial-gradient(1px 1px at 30% 90%, rgba(255,255,255,.3) 0%, transparent 100%);
    }
    .hero-content { position: relative; text-align: center; max-width: 760px; margin: 0 auto; padding: 80px 0 60px; }
    .hero h1 {
      font-family: var(--font-head); font-size: clamp(32px, 5vw, 54px);
      font-weight: 800; line-height: 1.18; margin-bottom: 18px; color: #fff;
    }
    .hero h1 .blue { color: var(--blue-bright); }
    .hero h1 .blue-dark { color: #4f8ef0; }
    .hero p { font-size: 15px; color: var(--muted); max-width: 520px; margin: 0 auto 32px; }
    .hero-btns { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; margin-bottom: 56px; }
    /* Tech logos strip */
    .tech-strip {
      display: flex; align-items: center; justify-content: center; gap: 28px;
      flex-wrap: wrap; padding: 18px 0; border-top: 1px solid var(--border);
    }
    .tech-strip img, .tech-strip i {
      height: 22px; opacity: .55; filter: brightness(0) invert(1);
      transition: opacity .2s;
    }
    .tech-strip i { font-size: 22px; color: #fff; }
    .tech-strip span { font-size: 13px; color: var(--muted); opacity: .7; font-weight: 500; }

    /* ============================================================
       BADGE STRIP
    ============================================================ */
    .badge-strip {
      background: #0b1422; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border);
      padding: 0;
    }
    .badge-strip-inner {
      display: flex; align-items: stretch;
    }
    .badge-item {
      flex: 1; display: flex; align-items: center; justify-content: center;
      gap: 10px; padding: 14px 20px; font-size: 13px; font-weight: 600; color: #fff;
    }
    .badge-item:not(:last-child) { border-right: 1px solid var(--border); }
    .badge-item.blue-bg { background: var(--blue); }
    .badge-item i { font-size: 15px; color: var(--blue); }
    .badge-item.blue-bg i { color: #fff; }

    /* ============================================================
       WHO WE WORK WITH
    ============================================================ */
    .who { padding: 80px 0; }
    .who-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 32px; align-items: center; }
    .who-images {
      display: grid; grid-template-columns: 1fr 1fr; gap: 10px;
    }
    .who-img {
      border-radius: 12px; overflow: hidden; position: relative;
    }
    .who-img img { width: 100%; height: 150px; object-fit: cover; }
    .who-img:first-child { grid-row: span 2; }
    .who-img:first-child img { height: 100%; }
    .who-right h2 { font-family: var(--font-head); font-size: 30px; font-weight: 800; color: #fff; margin-bottom: 24px; }
    .who-item {
      display: flex; gap: 14px; align-items: flex-start;
      padding: 14px 16px; border-radius: 10px; margin-bottom: 10px;
      background: var(--bg-card); border: 1px solid var(--border);
      transition: border-color .25s, background .25s;
    }
    .who-item:hover { border-color: var(--blue); background: rgba(59,130,246,0.07); }
    .who-item h4 { font-size: 13px; font-weight: 700; color: #fff; margin-bottom: 2px; text-transform: uppercase; letter-spacing: .5px; }
    .who-item p { font-size: 12.5px; color: var(--muted); }

    /* ============================================================
       SERVICES
    ============================================================ */
    .services { padding: 80px 0; background: var(--bg-card); }
    .services-grid { display: grid; grid-template-columns: 280px 1fr; gap: 40px; align-items: start; }
    .services-left h2 { font-family: var(--font-head); font-size: 26px; font-weight: 800; color: #fff; margin-bottom: 18px; }
    .service-link {
      display: block; padding: 10px 0; color: var(--muted); font-size: 14px;
      border-bottom: 1px solid var(--border); transition: color .2s; cursor: pointer;
    }
    .service-link:hover, .service-link.active { color: var(--blue-bright); }
    .services-right { display: grid; grid-template-columns: 1fr 1fr; gap: 0; border-radius: 14px; overflow: hidden; }
    .services-img { position: relative; }
    .services-img img { width: 100%; height: 280px; object-fit: cover; }
    .services-img::after {
      content: ''; position: absolute; inset: 0;
      background: linear-gradient(135deg, rgba(59,130,246,0.3), rgba(124,58,237,0.2));
    }
    .services-text {
      background: var(--bg-dark); padding: 30px; display: flex; flex-direction: column; justify-content: center;
    }
    .services-text p { color: var(--muted); font-size: 14px; margin-bottom: 16px; }
    .services-text ul { margin-bottom: 20px; }
    .services-text ul li {
      color: var(--text); font-size: 13.5px; padding: 5px 0;
      display: flex; align-items: center; gap: 8px;
    }
    .services-text ul li::before { content: '●'; color: var(--blue); font-size: 8px; }
    .services-tagline { font-size: 12px; color: var(--muted); font-style: italic; margin-top: 8px; }

    /* ============================================================
       PROCESS
    ============================================================ */
    .process { padding: 80px 0; }
    .process h2 { font-family: var(--font-head); font-size: 28px; font-weight: 800; color: #fff; text-align: center; margin-bottom: 8px; }
    .process-steps {
      display: grid; grid-template-columns: repeat(5, 1fr); gap: 16px; margin-top: 50px;
    }
    .step {
      text-align: center; padding: 24px 16px;
      background: var(--bg-card); border: 1px solid var(--border);
      border-radius: 14px; transition: border-color .25s, transform .25s;
      position: relative;
    }
    .step:hover { border-color: var(--blue); transform: translateY(-4px); }
    .step-num {
      font-size: 10px; color: var(--blue); font-weight: 700; letter-spacing: 1px;
      text-transform: uppercase; margin-bottom: 16px;
    }
    .step-icon {
      width: 54px; height: 54px; border-radius: 50%;
      background: rgba(59,130,246,0.12); border: 1.5px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 20px; color: var(--blue); margin: 0 auto 16px;
      transition: background .25s, border-color .25s;
    }
    .step:hover .step-icon { background: rgba(59,130,246,0.25); border-color: var(--blue); }
    .step h4 { font-family: var(--font-head); font-size: 13px; font-weight: 700; color: #fff; margin-bottom: 6px; }
    .step p { font-size: 12px; color: var(--muted); }
    /* connector line */
    .step:not(:last-child)::after {
      content: '→'; position: absolute; right: -14px; top: 50%;
      transform: translateY(-50%); color: var(--blue); font-size: 18px; z-index: 1;
    }

    /* ============================================================
       WHY US
    ============================================================ */
    .why { padding: 80px 0; background: var(--bg-card); }
    .why-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 48px; align-items: center; }
    .why-img { position: relative; border-radius: 16px; overflow: hidden; }
    .why-img img { width: 100%; height: 360px; object-fit: cover; }
    .why-img::after {
      content: ''; position: absolute; inset: 0;
      background: linear-gradient(135deg, rgba(59,130,246,0.25) 0%, transparent 60%);
    }
    .why-right h2 { font-family: var(--font-head); font-size: 28px; font-weight: 800; color: #fff; margin-bottom: 24px; }
    .why-item {
      display: flex; align-items: center; gap: 12px;
      padding: 12px 0; border-bottom: 1px solid var(--border); font-size: 14px; color: var(--text);
    }
    .why-item i { color: var(--blue); font-size: 15px; }

    /* ============================================================
       PROJECTS
    ============================================================ */
    .projects { padding: 80px 0; }
    .projects-header { display: flex; align-items: flex-end; justify-content: space-between; margin-bottom: 36px; }
    .projects-header h2 { font-family: var(--font-head); font-size: 28px; font-weight: 800; color: #fff; max-width: 340px; line-height: 1.2; }
    .projects-header p { color: var(--muted); font-size: 14px; max-width: 260px; }
    .projects-left { display: flex; flex-direction: column; gap: 8px; }
    .projects-left ul { margin: 12px 0; }
    .projects-left ul li {
      color: var(--muted); font-size: 13px; padding: 4px 0;
      display: flex; gap: 8px; align-items: center;
    }
    .projects-left ul li::before { content: '●'; color: var(--blue); font-size: 7px; }
    .projects-grid { display: grid; grid-template-columns: 320px 1fr; gap: 20px; }
    .projects-right { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    .project-card {
      border-radius: 12px; overflow: hidden; position: relative;
      background: var(--bg-card); border: 1px solid var(--border);
      transition: border-color .25s, transform .25s;
    }
    .project-card:hover { border-color: var(--blue); transform: translateY(-3px); }
    .project-card img { width: 100%; height: 160px; object-fit: cover; }
    .project-card-label {
      position: absolute; bottom: 0; left: 0; right: 0;
      background: linear-gradient(0deg, rgba(7,11,20,.95) 60%, transparent);
      padding: 30px 14px 14px; font-size: 12px; font-weight: 600; color: #fff;
    }
    .projects-big { grid-row: span 2; }
    .projects-big img { height: 100%; min-height: 340px; }

    /* ============================================================
       TESTIMONIALS
    ============================================================ */
    .testimonials { padding: 80px 0; background: var(--bg-card); }
    .testimonials-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 36px; }
    .testimonials-header h2 { font-family: var(--font-head); font-size: 28px; font-weight: 800; color: #fff; }
    .testimonials-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
    .testi-card {
      background: var(--bg-dark); border: 1px solid var(--border);
      border-radius: 14px; padding: 24px;
      transition: border-color .25s, transform .25s;
    }
    .testi-card:hover { border-color: var(--blue); transform: translateY(-3px); }
    .testi-stars { margin-bottom: 14px; }
    .testi-card blockquote { font-size: 14px; color: var(--text); line-height: 1.7; margin-bottom: 18px; font-style: italic; }
    .testi-author { display: flex; align-items: center; gap: 12px; }
    .testi-avatar {
      width: 38px; height: 38px; border-radius: 50%;
      background: linear-gradient(135deg, var(--blue), var(--purple));
      display: flex; align-items: center; justify-content: center;
      font-size: 14px; font-weight: 700; color: #fff; flex-shrink: 0;
    }
    .testi-author h5 { font-size: 13px; font-weight: 700; color: #fff; }
    .testi-author span { font-size: 11.5px; color: var(--muted); }
    .testi-dots { display: flex; gap: 6px; justify-content: center; margin-top: 28px; }
    .dot { width: 8px; height: 8px; border-radius: 50%; background: var(--border); cursor: pointer; transition: background .2s; }
    .dot.active { background: var(--blue); width: 24px; border-radius: 4px; }

    /* ============================================================
       BLOG
    ============================================================ */
    .blog { padding: 80px 0; }
    .blog-header { display: flex; align-items: flex-start; gap: 48px; margin-bottom: 36px; }
    .blog-header-left { flex: 1; }
    .blog-header-left h2 { font-family: var(--font-head); font-size: 28px; font-weight: 800; color: #fff; margin-bottom: 10px; }
    .blog-header-left p { color: var(--muted); font-size: 14px; max-width: 280px; }
    .blog-header-right {
      flex: 0 0 auto; background: rgba(59,130,246,0.12); border: 1px solid var(--border);
      border-radius: 12px; padding: 18px 22px; font-size: 13px; color: var(--text);
      font-style: italic; max-width: 220px;
    }
    .blog-header-right strong { display: block; color: var(--blue); font-style: normal; margin-bottom: 4px; font-size: 12px; }
    .blog-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
    .blog-card {
      background: var(--bg-card); border: 1px solid var(--border);
      border-radius: 14px; overflow: hidden;
      transition: border-color .25s, transform .25s;
    }
    .blog-card:hover { border-color: var(--blue); transform: translateY(-3px); }
    .blog-card img { width: 100%; height: 150px; object-fit: cover; }
    .blog-card-body { padding: 18px; }
    .blog-tag {
      display: inline-block; font-size: 10px; font-weight: 700; letter-spacing: 1px;
      text-transform: uppercase; color: var(--blue);
      background: rgba(59,130,246,0.12); padding: 3px 10px; border-radius: 50px; margin-bottom: 10px;
    }
    .blog-card-body h4 { font-family: var(--font-head); font-size: 14px; font-weight: 700; color: #fff; margin-bottom: 8px; line-height: 1.4; }
    .blog-card-body a { font-size: 12.5px; color: var(--blue); font-weight: 600; }
    .blog-card-body a:hover { text-decoration: underline; }

    /* ============================================================
       CTA
    ============================================================ */
    .cta-section {
      padding: 90px 0; position: relative; overflow: hidden;
      background: linear-gradient(135deg, #0a1020 0%, #060a15 100%);
      border-top: 1px solid var(--border);
    }
    .cta-section::before {
      content: ''; position: absolute; left: -100px; bottom: -100px;
      width: 450px; height: 450px; border-radius: 50%;
      background: radial-gradient(circle, rgba(59,130,246,0.15) 0%, transparent 70%);
    }
    .cta-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; position: relative; }
    .cta-left h2 { font-family: var(--font-head); font-size: 34px; font-weight: 800; color: #fff; margin-bottom: 16px; line-height: 1.2; }
    .cta-left p { color: var(--muted); font-size: 14px; margin-bottom: 24px; }
    .cta-checks { display: flex; flex-direction: column; gap: 8px; margin-bottom: 28px; }
    .cta-check { display: flex; align-items: center; gap: 10px; font-size: 13.5px; color: var(--text); }
    .cta-check i { color: var(--blue); font-size: 13px; }
    .cta-right { position: relative; }
    .cta-visual {
      width: 100%; height: 320px; border-radius: 16px;
      background: linear-gradient(135deg, rgba(59,130,246,0.15) 0%, rgba(124,58,237,0.1) 100%);
      border: 1px solid var(--border);
      display: flex; align-items: center; justify-content: center;
    }
    .cta-glow-circle {
      width: 200px; height: 200px; border-radius: 50%;
      background: radial-gradient(circle, rgba(59,130,246,0.3) 0%, transparent 70%);
      display: flex; align-items: center; justify-content: center;
    }
    .cta-glow-circle i { font-size: 60px; color: var(--blue); opacity: .8; }

    /* ============================================================
       FOOTER
    ============================================================ */
    footer {
      background: #060a14; border-top: 1px solid var(--border); padding: 56px 0 24px;
    }
    .footer-grid { display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 40px; margin-bottom: 40px; }
    .footer-brand p { color: var(--muted); font-size: 13.5px; margin: 14px 0 20px; max-width: 260px; }
    .footer-socials { display: flex; gap: 10px; }
    .footer-social {
      width: 36px; height: 36px; border-radius: 8px;
      background: var(--bg-card); border: 1px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 14px; color: var(--muted); transition: color .2s, border-color .2s;
    }
    .footer-social:hover { color: var(--blue); border-color: var(--blue); }
    .footer-col h5 { font-family: var(--font-head); font-size: 14px; font-weight: 700; color: #fff; margin-bottom: 16px; }
    .footer-col a { display: block; font-size: 13px; color: var(--muted); padding: 5px 0; transition: color .2s; }
    .footer-col a:hover { color: var(--blue-bright); }
    .footer-bottom {
      border-top: 1px solid var(--border); padding-top: 20px;
      display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 10px;
    }
    .footer-bottom p { font-size: 12.5px; color: var(--muted); }

    /* ============================================================
       RESPONSIVE
    ============================================================ */
    @media (max-width: 900px) {
      .nav-links, .nav-actions .btn-primary { display: none; }
      .hamburger { display: flex; }
      .who-grid, .services-grid, .why-grid, .cta-grid { grid-template-columns: 1fr; }
      .services-right { grid-template-columns: 1fr; }
      .projects-grid { grid-template-columns: 1fr; }
      .projects-right { grid-template-columns: 1fr 1fr; }
      .projects-big { grid-row: span 1; }
      .projects-big img { min-height: 200px; height: 200px; }
      .testimonials-grid, .blog-grid { grid-template-columns: 1fr; }
      .process-steps { grid-template-columns: 1fr 1fr; }
      .step:not(:last-child)::after { display: none; }
      .footer-grid { grid-template-columns: 1fr 1fr; }
      .badge-strip-inner { flex-direction: column; }
      .badge-item:not(:last-child) { border-right: none; border-bottom: 1px solid var(--border); }
      .blog-header { flex-direction: column; gap: 20px; }
      .projects-header { flex-direction: column; gap: 16px; }
    }
    @media (max-width: 600px) {
      .who-images { grid-template-columns: 1fr; }
      .who-img:first-child { grid-row: span 1; }
      .who-img:first-child img { height: 180px; }
      .process-steps { grid-template-columns: 1fr; }
      .footer-grid { grid-template-columns: 1fr; }
      .hero h1 { font-size: 28px; }
      .testimonials-grid { grid-template-columns: 1fr; }
      .blog-grid { grid-template-columns: 1fr; }
      .projects-right { grid-template-columns: 1fr; }
      .cta-right { display: none; }
    }
  </style>
</head>
<body>

<!-- ============================================================
     NAVBAR
============================================================ -->
<nav id="navbar">
  <div class="container nav-inner">
    <a href="#" class="logo">
      <div class="logo-icon">S</div>
      SPADE
    </a>
    <div class="nav-links">
      <a href="#hero" class="active">Home</a>
      <a href="#who">About</a>
      <a href="#services">What We Do</a>
      <a href="#projects">Work</a>
      <a href="#blog">Blog</a>
      <a href="#cta">Contact</a>
    </div>
    <div class="nav-actions">
      <a href="#cta" class="btn-primary">Contact <i class="fas fa-arrow-right"></i></a>
      <div class="hamburger" id="hamburger" onclick="toggleMenu()">
        <span></span><span></span><span></span>
      </div>
    </div>
  </div>
  <div class="mobile-menu" id="mobileMenu">
    <a href="#hero" onclick="toggleMenu()">Home</a>
    <a href="#who" onclick="toggleMenu()">About</a>
    <a href="#services" onclick="toggleMenu()">What We Do</a>
    <a href="#projects" onclick="toggleMenu()">Work</a>
    <a href="#blog" onclick="toggleMenu()">Blog</a>
    <a href="#cta" onclick="toggleMenu()">Contact</a>
  </div>
</nav>

<!-- ============================================================
     HERO
============================================================ -->
<section class="hero" id="hero">
  <div class="hero-bg"></div>
  <div class="container">
    <div class="hero-content reveal">
      <h1>
        We Build Scalable <span class="blue">Web &amp; Mobile<br>Applications</span>
        That Help <span class="blue">Businesses</span><br>
        <span style="color:#fff;">*Grow</span> Not Just Look Good
      </h1>
      <p>We are a leading web and mobile app development company delivering innovative, user-friendly, and result-driven digital solutions.</p>
      <div class="hero-btns">
        <a href="#cta" class="btn-primary">Get Started <i class="fas fa-arrow-right"></i></a>
        <a href="#projects" class="btn-outline">Our Work <i class="fas fa-play-circle"></i></a>
      </div>
      <div class="tech-strip">
        <i class="fab fa-node-js"></i>
        <i class="fab fa-react"></i>
        <i class="fab fa-angular"></i>
        <i class="fab fa-vuejs"></i>
        <i class="fab fa-python"></i>
        <i class="fab fa-aws"></i>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     BADGE STRIP
============================================================ -->
<div class="badge-strip">
  <div class="container">
    <div class="badge-strip-inner">
      <div class="badge-item">
        <i class="fas fa-trophy"></i> Top App Developers
      </div>
      <div class="badge-item">
        <i class="fas fa-times" style="color:var(--muted)"></i> Web, Mobile &amp; Custom Software Experts
      </div>
      <div class="badge-item blue-bg">
        <i class="fas fa-palette"></i> UI/UX
      </div>
    </div>
  </div>
</div>

<!-- ============================================================
     WHO WE WORK WITH
============================================================ -->
<section class="who" id="who">
  <div class="container">
    <div class="who-grid reveal">
      <div class="who-images">
        <div class="who-img">
          <img src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=400&q=80" alt="Team meeting"/>
        </div>
        <div class="who-img">
          <img src="https://images.unsplash.com/photo-1573497019940-1c28c88b4f3e?w=400&q=80" alt="Developer"/>
        </div>
        <div class="who-img">
          <img src="https://images.unsplash.com/photo-1600880292203-757bb62b4baf?w=400&q=80" alt="Office"/>
        </div>
        <div class="who-img">
          <img src="https://images.unsplash.com/photo-1531482615713-2afd69097998?w=400&q=80" alt="Collaboration"/>
        </div>
      </div>
      <div class="who-right">
        <div class="section-label">WHO WE ARE</div>
        <h2>We Work With</h2>
        <div class="who-item">
          <div class="icon-circle"><i class="fas fa-rocket"></i></div>
          <div>
            <h4>Startups</h4>
            <p>Turning ideas into powerful digital products.</p>
          </div>
        </div>
        <div class="who-item">
          <div class="icon-circle"><i class="fas fa-lightbulb"></i></div>
          <div>
            <h4>Entrepreneurs</h4>
            <p>Building your vision with the right technology.</p>
          </div>
        </div>
        <div class="who-item">
          <div class="icon-circle"><i class="fas fa-building"></i></div>
          <div>
            <h4>Business &amp; SMEs</h4>
            <p>Digital solutions that drive real growth.</p>
          </div>
        </div>
        <div class="who-item">
          <div class="icon-circle"><i class="fas fa-crown"></i></div>
          <div>
            <h4>Brands/Enterprises</h4>
            <p>Scalable systems for complex business needs.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     SERVICES
============================================================ -->
<section class="services" id="services">
  <div class="container">
    <div class="services-grid reveal">
      <div class="services-left">
        <div class="section-label">OUR SERVICES</div>
        <h2>Our Services</h2>
        <a href="#" class="btn-primary" style="margin-bottom:24px;font-size:12px;padding:9px 18px;">VIEW ALL SERVICES</a>
        <div style="margin-top:20px;">
          <a class="service-link active" href="#">App Development</a>
          <a class="service-link" href="#">Web Development</a>
          <a class="service-link" href="#">UI/UX Design</a>
          <a class="service-link" href="#">Digital Marketing</a>
        </div>
      </div>
      <div class="services-right">
        <div class="services-img">
          <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?w=600&q=80" alt="Coding"/>
        </div>
        <div class="services-text">
          <p>We design and develop powerful digital products that drive growth.</p>
          <ul>
            <li>Custom Solutions</li>
            <li>Scalable &amp; Secure</li>
            <li>Modern Technology</li>
            <li>Agile Process</li>
          </ul>
          <a href="#cta" class="btn-primary" style="font-size:13px;padding:10px 20px;width:fit-content;">Get Started <i class="fas fa-arrow-right"></i></a>
          <p class="services-tagline">Have an idea? Let's bring it to life.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     PROCESS
============================================================ -->
<section class="process" id="process">
  <div class="container">
    <div class="reveal">
      <div class="section-label" style="text-align:center;">PROCESS</div>
      <h2>Our Simple 5 Step Process</h2>
      <div class="process-steps">
        <div class="step">
          <div class="step-num">01 Discover</div>
          <div class="step-icon"><i class="fas fa-search"></i></div>
          <h4>Discover</h4>
          <p>Understanding your goals</p>
        </div>
        <div class="step">
          <div class="step-num">02 Plan</div>
          <div class="step-icon"><i class="fas fa-sitemap"></i></div>
          <h4>Plan</h4>
          <p>Research &amp; strategy</p>
        </div>
        <div class="step">
          <div class="step-num">03 Design</div>
          <div class="step-icon"><i class="fas fa-paint-brush"></i></div>
          <h4>Design</h4>
          <p>UI/UX design</p>
        </div>
        <div class="step">
          <div class="step-num">04 Develop</div>
          <div class="step-icon"><i class="fas fa-code"></i></div>
          <h4>Develop</h4>
          <p>Building with clean code</p>
        </div>
        <div class="step">
          <div class="step-num">05 Launch</div>
          <div class="step-icon"><i class="fas fa-rocket"></i></div>
          <h4>Launch</h4>
          <p>Testing &amp; deployment</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     WHY US
============================================================ -->
<section class="why" id="why">
  <div class="container">
    <div class="why-grid reveal">
      <div class="why-img">
        <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?w=700&q=80" alt="Developer at laptop"/>
      </div>
      <div class="why-right">
        <div class="section-label">WHY CHOOSE US</div>
        <h2>Why Clients Choose Us</h2>
        <div class="why-item">
          <i class="fas fa-check-circle"></i> Experienced &amp; dedicated team
        </div>
        <div class="why-item">
          <i class="fas fa-check-circle"></i> On-time delivery, every time
        </div>
        <div class="why-item">
          <i class="fas fa-check-circle"></i> Transparent communication
        </div>
        <div class="why-item">
          <i class="fas fa-check-circle"></i> Quality that scales
        </div>
        <div class="why-item">
          <i class="fas fa-check-circle"></i> Long-term partnership
        </div>
        <a href="#who" class="btn-primary" style="margin-top:24px;">Learn More <i class="fas fa-arrow-right"></i></a>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     PROJECTS
============================================================ -->
<section class="projects" id="projects">
  <div class="container">
    <div class="reveal">
      <div class="projects-header">
        <div class="projects-left">
          <div class="section-label">OUR WORK</div>
          <h2>Real Projects. Real<br>Results. Drive Real Growth.</h2>
          <p style="color:var(--muted);font-size:14px;margin:10px 0 16px;">Solutions built to solve, scale, and succeed.</p>
          <ul>
            <li style="color:var(--muted);font-size:13px;padding:3px 0;display:flex;gap:8px;align-items:center;"><span style="color:var(--blue);font-size:8px;">●</span> High Performance</li>
            <li style="color:var(--muted);font-size:13px;padding:3px 0;display:flex;gap:8px;align-items:center;"><span style="color:var(--blue);font-size:8px;">●</span> Scalable Architecture</li>
            <li style="color:var(--muted);font-size:13px;padding:3px 0;display:flex;gap:8px;align-items:center;"><span style="color:var(--blue);font-size:8px;">●</span> User-Centric Design</li>
            <li style="color:var(--muted);font-size:13px;padding:3px 0;display:flex;gap:8px;align-items:center;"><span style="color:var(--blue);font-size:8px;">●</span> Measurable Results</li>
          </ul>
          <a href="#" class="btn-primary" style="margin-top:16px;font-size:13px;">View Our Work <i class="fas fa-arrow-right"></i></a>
        </div>
      </div>
      <div class="projects-grid">
        <div class="project-card projects-big">
          <img src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?w=500&q=80" alt="Fintech App"/>
          <div class="project-card-label">Fintech App</div>
        </div>
        <div class="projects-right">
          <div class="project-card">
            <img src="https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?w=500&q=80" alt="E-commerce Platform"/>
            <div class="project-card-label">E-commerce Platform</div>
          </div>
          <div class="project-card">
            <img src="https://images.unsplash.com/photo-1576091160399-112ba8d25d1d?w=500&q=80" alt="Healthcare Solution"/>
            <div class="project-card-label">Healthcare Solution</div>
          </div>
          <div class="project-card">
            <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=500&q=80" alt="Logistics Dashboard"/>
            <div class="project-card-label">Logistics Dashboard</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     TESTIMONIALS
============================================================ -->
<section class="testimonials" id="testimonials">
  <div class="container">
    <div class="reveal">
      <div class="testimonials-header">
        <h2>What Our Clients Say</h2>
        <a href="#" class="btn-outline" style="font-size:12px;padding:9px 18px;">VIEW ALL TESTIMONIALS</a>
      </div>
      <div class="testimonials-grid">
        <div class="testi-card">
          <div class="testi-stars">
            <span class="star">★★★★★</span>
          </div>
          <blockquote>"Spade delivered beyond our expectations. Their team was professional and detail-oriented throughout the entire project."</blockquote>
          <div class="testi-author">
            <div class="testi-avatar">R</div>
            <div>
              <h5>Rahul Mehta</h5>
              <span>CEO, Fintech Startup</span>
            </div>
          </div>
        </div>
        <div class="testi-card">
          <div class="testi-stars">
            <span class="star">★★★★★</span>
          </div>
          <blockquote>"Professional, responsive, and highly skilled team. They turned our vision into a stunning, functional product on time."</blockquote>
          <div class="testi-author">
            <div class="testi-avatar">A</div>
            <div>
              <h5>Anita Sharma</h5>
              <span>Founder, E-commerce Brand</span>
            </div>
          </div>
        </div>
        <div class="testi-card">
          <div class="testi-stars">
            <span class="star">★★★★★</span>
          </div>
          <blockquote>"Our go-to tech partner for every project. Spade consistently delivers high-quality solutions that drive real results."</blockquote>
          <div class="testi-author">
            <div class="testi-avatar">V</div>
            <div>
              <h5>Vikram Singh</h5>
              <span>CTO, Logistics Company</span>
            </div>
          </div>
        </div>
      </div>
      <div class="testi-dots">
        <div class="dot active"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     BLOG
============================================================ -->
<section class="blog" id="blog">
  <div class="container">
    <div class="reveal">
      <div class="blog-header">
        <div class="blog-header-left">
          <div class="section-label">BLOG</div>
          <h2>Insights &amp; Perspectives</h2>
          <p>Stay updated with the latest trends, tips, and insights from the world of technology and business.</p>
          <a href="#" class="btn-primary" style="margin-top:18px;font-size:13px;">Explore Blog <i class="fas fa-arrow-right"></i></a>
        </div>
        <div class="blog-header-right">
          <strong>💬 Our Readers</strong>
          "Great insights that help us grow digitally."<br>— Our Readers
        </div>
      </div>
      <div class="blog-grid">
        <div class="blog-card">
          <img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=500&q=80" alt="Blog post"/>
          <div class="blog-card-body">
            <span class="blog-tag">Development</span>
            <h4>How to Build Scalable Web Applications</h4>
            <a href="#">Read More →</a>
          </div>
        </div>
        <div class="blog-card">
          <img src="https://images.unsplash.com/photo-1504868584819-f8e8b4b6d7e3?w=500&q=80" alt="Blog post"/>
          <div class="blog-card-body">
            <span class="blog-tag">Trends</span>
            <h4>Top 10 Web Development Trends in 2024</h4>
            <a href="#">Read More →</a>
          </div>
        </div>
        <div class="blog-card">
          <img src="https://images.unsplash.com/photo-1561070791-2526d30994b5?w=500&q=80" alt="Blog post"/>
          <div class="blog-card-body">
            <span class="blog-tag">Design</span>
            <h4>UI/UX Design Trends to Watch in 2024</h4>
            <a href="#">Read More →</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     CTA / CONTACT
============================================================ -->
<section class="cta-section" id="cta">
  <div class="container">
    <div class="cta-grid reveal">
      <div class="cta-left">
        <div class="section-label">LET'S BUILD</div>
        <h2>Let's Build<br>Something Amazing</h2>
        <p>Have a project in mind? Let's turn your idea into a powerful digital solution.</p>
        <div class="cta-checks">
          <div class="cta-check"><i class="fas fa-check-circle"></i> Free Consultation</div>
          <div class="cta-check"><i class="fas fa-check-circle"></i> Tailored Solutions</div>
          <div class="cta-check"><i class="fas fa-check-circle"></i> On-time Delivery</div>
        </div>
        <a href="mailto:hello@spadeagency.com" class="btn-primary">Get In Touch <i class="fas fa-arrow-right"></i></a>
      </div>
      <div class="cta-right">
        <div class="cta-visual">
          <div class="cta-glow-circle">
            <i class="fas fa-rocket"></i>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ============================================================
     FOOTER
============================================================ -->
<footer>
  <div class="container">
    <div class="footer-grid">
      <div class="footer-brand">
        <a href="#" class="logo" style="font-size:18px;">
          <div class="logo-icon">S</div> SPADE
        </a>
        <p>A leading web and mobile app development company delivering innovative, user-friendly digital solutions.</p>
        <div class="footer-socials">
          <a href="#" class="footer-social"><i class="fab fa-twitter"></i></a>
          <a href="#" class="footer-social"><i class="fab fa-linkedin-in"></i></a>
          <a href="#" class="footer-social"><i class="fab fa-instagram"></i></a>
          <a href="#" class="footer-social"><i class="fab fa-github"></i></a>
        </div>
      </div>
      <div class="footer-col">
        <h5>Company</h5>
        <a href="#who">About Us</a>
        <a href="#services">Services</a>
        <a href="#projects">Our Work</a>
        <a href="#blog">Blog</a>
      </div>
      <div class="footer-col">
        <h5>Services</h5>
        <a href="#">App Development</a>
        <a href="#">Web Development</a>
        <a href="#">UI/UX Design</a>
        <a href="#">Digital Marketing</a>
      </div>
      <div class="footer-col">
        <h5>Contact</h5>
        <a href="mailto:hello@spadeagency.com">hello@spadeagency.com</a>
        <a href="tel:+11234567890">+1 (123) 456-7890</a>
        <a href="#">WhatsApp Us</a>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2024 SPADE Agency. All rights reserved.</p>
      <p>Privacy Policy · Terms of Service</p>
    </div>
  </div>
</footer>

<!-- ============================================================
     JAVASCRIPT
============================================================ -->
<script>
  /* ---------- Mobile menu ---------- */
  function toggleMenu() {
    document.getElementById('mobileMenu').classList.toggle('open');
  }

  /* ---------- Navbar scroll effect ---------- */
  window.addEventListener('scroll', () => {
    const nav = document.getElementById('navbar');
    nav.style.boxShadow = window.scrollY > 30
      ? '0 4px 30px rgba(0,0,0,0.4)' : 'none';
  });

  /* ---------- Scroll reveal ---------- */
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.12 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  /* ---------- Service link active ---------- */
  document.querySelectorAll('.service-link').forEach(link => {
    link.addEventListener('click', function(e) {
      e.preventDefault();
      document.querySelectorAll('.service-link').forEach(l => l.classList.remove('active'));
      this.classList.add('active');
    });
  });

  /* ---------- Testimonial dots ---------- */
  document.querySelectorAll('.dot').forEach((dot, i) => {
    dot.addEventListener('click', () => {
      document.querySelectorAll('.dot').forEach(d => d.classList.remove('active'));
      dot.classList.add('active');
    });
  });

  /* ---------- Smooth active nav on scroll ---------- */
  const sections = document.querySelectorAll('section[id], div[id]');
  window.addEventListener('scroll', () => {
    let current = '';
    sections.forEach(sec => {
      if (window.scrollY >= sec.offsetTop - 100) current = sec.getAttribute('id');
    });
    document.querySelectorAll('.nav-links a').forEach(a => {
      a.classList.remove('active');
      if (a.getAttribute('href') === '#' + current) a.classList.add('active');
    });
  });
</script>
</body>
</html>
