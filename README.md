<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Shreevatsa N J — Data Science & AI</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Space+Mono:wght@400;700&family=Nunito:wght@400;600;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #060612;
    --bg2: #0d0d24;
    --cyan: #38BDF8;
    --pink: #F472B6;
    --violet: #A78BFA;
    --green: #34D399;
    --orange: #FB923C;
    --yellow: #FDE68A;
    --white: #F0F4FF;
    --muted: #8892B0;
    --card: rgba(255,255,255,0.04);
    --border: rgba(255,255,255,0.08);
    --glow-cyan: 0 0 40px rgba(56,189,248,0.35);
    --glow-pink: 0 0 40px rgba(244,114,182,0.35);
    --glow-violet: 0 0 40px rgba(167,139,250,0.35);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'Nunito', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  .cursor {
    width: 12px; height: 12px;
    background: var(--cyan);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none; z-index: 9999;
    transition: transform 0.1s ease;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid var(--cyan);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none; z-index: 9998;
    transition: transform 0.15s ease, opacity 0.3s;
    opacity: 0.5;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.4;
  }

  /* GRID LINES */
  body::after {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(rgba(56,189,248,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(56,189,248,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none; z-index: 0;
  }

  /* AMBIENT BLOBS */
  .blob {
    position: fixed; border-radius: 50%;
    filter: blur(120px); pointer-events: none;
    z-index: 0; opacity: 0.18;
    animation: blobFloat 12s ease-in-out infinite alternate;
  }
  .blob1 { width: 600px; height: 600px; background: var(--violet); top: -200px; left: -200px; animation-delay: 0s; }
  .blob2 { width: 500px; height: 500px; background: var(--cyan); bottom: -150px; right: -150px; animation-delay: -5s; }
  .blob3 { width: 400px; height: 400px; background: var(--pink); top: 40%; left: 40%; animation-delay: -8s; }

  @keyframes blobFloat {
    from { transform: translate(0,0) scale(1); }
    to   { transform: translate(40px, 30px) scale(1.08); }
  }

  /* LAYOUT */
  .container { max-width: 1100px; margin: 0 auto; padding: 0 2rem; position: relative; z-index: 1; }
  section { padding: 100px 0; }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 1.2rem 2rem;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(6,6,18,0.7);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 1.3rem;
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    letter-spacing: -0.5px;
  }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    font-family: 'Space Mono', monospace;
    font-size: 0.78rem; color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
    letter-spacing: 0.05em;
  }
  .nav-links a:hover { color: var(--cyan); }

  /* HERO */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding-top: 100px;
  }
  .hero-inner {
    display: grid;
    grid-template-columns: 1fr 340px;
    gap: 4rem; align-items: center;
  }
  .hero-tag {
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: 0.72rem;
    color: var(--cyan);
    border: 1px solid rgba(56,189,248,0.3);
    background: rgba(56,189,248,0.05);
    padding: 0.35rem 1rem;
    border-radius: 100px;
    letter-spacing: 0.12em;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.6s ease both;
  }
  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.8rem, 6vw, 5.5rem);
    font-weight: 800;
    line-height: 1.0;
    letter-spacing: -2px;
    animation: fadeUp 0.7s ease 0.1s both;
  }
  .hero-name span {
    background: linear-gradient(135deg, var(--cyan) 0%, var(--violet) 50%, var(--pink) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .hero-sub {
    margin-top: 1.5rem;
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 520px;
    line-height: 1.7;
    animation: fadeUp 0.7s ease 0.2s both;
  }
  .hero-sub strong { color: var(--white); }

  .hero-typing {
    margin-top: 1.5rem;
    font-family: 'Space Mono', monospace;
    font-size: 0.95rem;
    color: var(--green);
    animation: fadeUp 0.7s ease 0.3s both;
    display: flex; align-items: center; gap: 0.5rem;
  }
  .hero-typing::before { content: '> '; color: var(--cyan); }
  .typed-text { border-right: 2px solid var(--green); animation: blink 0.8s infinite; padding-right: 2px; }
  @keyframes blink { 50% { border-color: transparent; } }

  .hero-cta {
    margin-top: 2.5rem; display: flex; gap: 1rem; flex-wrap: wrap;
    animation: fadeUp 0.7s ease 0.4s both;
  }
  .btn {
    font-family: 'Syne', sans-serif; font-weight: 700;
    padding: 0.85rem 2rem; border-radius: 12px;
    font-size: 0.9rem; text-decoration: none;
    display: inline-flex; align-items: center; gap: 0.5rem;
    transition: all 0.25s ease; cursor: none;
    letter-spacing: 0.02em;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    color: #060612; border: none;
    box-shadow: 0 0 30px rgba(56,189,248,0.4);
  }
  .btn-primary:hover {
    transform: translateY(-3px) scale(1.03);
    box-shadow: 0 0 50px rgba(56,189,248,0.6);
  }
  .btn-ghost {
    background: transparent; color: var(--white);
    border: 1px solid var(--border);
  }
  .btn-ghost:hover {
    border-color: var(--cyan); color: var(--cyan);
    transform: translateY(-3px);
  }

  /* HERO CARD */
  .hero-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 24px;
    padding: 2rem;
    backdrop-filter: blur(10px);
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.8s ease 0.2s both;
  }
  .hero-card::before {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(56,189,248,0.07), rgba(167,139,250,0.07));
    border-radius: 24px;
  }
  .avatar-ring {
    width: 110px; height: 110px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--cyan), var(--violet), var(--pink));
    padding: 3px; margin: 0 auto 1.5rem;
    animation: spin 8s linear infinite;
    position: relative; z-index: 1;
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--bg2);
    display: flex; align-items: center; justify-content: center;
    font-size: 2.8rem;
    animation: spin 8s linear infinite reverse;
  }
  .card-name {
    font-family: 'Syne', sans-serif; font-weight: 700;
    text-align: center; font-size: 1.1rem; margin-bottom: 0.3rem;
    position: relative; z-index: 1;
  }
  .card-role {
    text-align: center; color: var(--cyan);
    font-size: 0.8rem; font-family: 'Space Mono', monospace;
    margin-bottom: 1.5rem; position: relative; z-index: 1;
  }
  .card-stats {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 0.8rem; position: relative; z-index: 1;
  }
  .stat {
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 12px; padding: 0.8rem;
    text-align: center;
  }
  .stat-num {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 1.4rem;
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .stat-lbl {
    font-size: 0.68rem; color: var(--muted);
    font-family: 'Space Mono', monospace;
    letter-spacing: 0.06em;
    margin-top: 0.15rem;
  }

  /* BADGES SECTION */
  .badges-row {
    display: flex; flex-wrap: wrap; gap: 0.75rem;
    margin-top: 2rem; animation: fadeUp 0.7s ease 0.5s both;
  }
  .badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    padding: 0.5rem 1rem; border-radius: 10px;
    font-family: 'Space Mono', monospace; font-size: 0.72rem;
    border: 1px solid;
    font-weight: 700; letter-spacing: 0.04em;
  }
  .badge-blue   { color: #60A5FA; border-color: rgba(96,165,250,0.35); background: rgba(96,165,250,0.07); }
  .badge-orange { color: var(--orange); border-color: rgba(251,146,60,0.35); background: rgba(251,146,60,0.07); }
  .badge-teal   { color: #2DD4BF; border-color: rgba(45,212,191,0.35); background: rgba(45,212,191,0.07); }
  .badge-purple { color: var(--violet); border-color: rgba(167,139,250,0.35); background: rgba(167,139,250,0.07); }
  .badge-amber  { color: var(--yellow); border-color: rgba(253,230,138,0.35); background: rgba(253,230,138,0.07); }

  /* SECTION HEADERS */
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.72rem; color: var(--cyan);
    letter-spacing: 0.2em; text-transform: uppercase;
    margin-bottom: 0.8rem;
    display: flex; align-items: center; gap: 0.8rem;
  }
  .section-label::after {
    content: ''; flex: 1; height: 1px;
    background: linear-gradient(90deg, rgba(56,189,248,0.4), transparent);
  }
  .section-title {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: clamp(2rem, 4vw, 3rem);
    letter-spacing: -1px; line-height: 1.1;
    margin-bottom: 0.8rem;
  }
  .section-desc { color: var(--muted); font-size: 1rem; max-width: 560px; line-height: 1.7; }

  /* ABOUT — YAML CARD */
  .yaml-card {
    background: #0d1117;
    border: 1px solid var(--border);
    border-radius: 20px; overflow: hidden;
    font-family: 'Space Mono', monospace; font-size: 0.82rem;
    box-shadow: var(--glow-cyan);
  }
  .yaml-header {
    background: rgba(56,189,248,0.08);
    border-bottom: 1px solid var(--border);
    padding: 0.8rem 1.2rem;
    display: flex; align-items: center; gap: 0.5rem;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot-r { background: #FF5F57; }
  .dot-y { background: #FFBD2E; }
  .dot-g { background: #28CA41; }
  .yaml-filename { margin-left: 0.5rem; color: var(--muted); font-size: 0.72rem; }
  .yaml-body { padding: 1.5rem 1.8rem; line-height: 2; }
  .y-key { color: var(--cyan); }
  .y-val { color: var(--green); }
  .y-str { color: var(--yellow); }
  .y-comment { color: var(--muted); }
  .y-list { color: var(--violet); }
  .y-em { color: var(--pink); }

  /* PROJECTS GRID */
  .projects-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; margin-top: 3rem; }
  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px; padding: 2rem;
    position: relative; overflow: hidden;
    transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s;
    cursor: none;
  }
  .project-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--cyan), var(--violet), var(--pink));
    opacity: 0; transition: opacity 0.3s;
  }
  .project-card:hover { transform: translateY(-8px); }
  .project-card:hover::before { opacity: 1; }
  .project-card.card-cyan:hover { box-shadow: var(--glow-cyan); border-color: rgba(56,189,248,0.3); }
  .project-card.card-violet:hover { box-shadow: var(--glow-violet); border-color: rgba(167,139,250,0.3); }
  .project-card.card-pink:hover { box-shadow: var(--glow-pink); border-color: rgba(244,114,182,0.3); }
  .project-card.card-green:hover { box-shadow: 0 0 40px rgba(52,211,153,0.3); border-color: rgba(52,211,153,0.3); }

  .proj-icon {
    width: 52px; height: 52px; border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.5rem; margin-bottom: 1.2rem;
  }
  .proj-icon-cyan   { background: rgba(56,189,248,0.15); }
  .proj-icon-violet { background: rgba(167,139,250,0.15); }
  .proj-icon-pink   { background: rgba(244,114,182,0.15); }
  .proj-icon-green  { background: rgba(52,211,153,0.15); }

  .proj-title {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 1.25rem; margin-bottom: 0.3rem;
  }
  .proj-subtitle { color: var(--muted); font-size: 0.85rem; margin-bottom: 1.2rem; }
  .proj-features { list-style: none; margin-bottom: 1.5rem; }
  .proj-features li {
    font-size: 0.82rem; color: var(--muted);
    padding: 0.25rem 0; display: flex; align-items: center; gap: 0.6rem;
  }
  .proj-features li::before { content: '✦'; font-size: 0.6rem; color: var(--cyan); }
  .proj-stack { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 1.5rem; }
  .stack-tag {
    font-family: 'Space Mono', monospace; font-size: 0.68rem;
    padding: 0.3rem 0.7rem; border-radius: 8px;
    background: rgba(255,255,255,0.05); border: 1px solid var(--border);
    color: var(--muted);
  }
  .proj-link {
    display: inline-flex; align-items: center; gap: 0.5rem;
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    color: var(--cyan); text-decoration: none;
    border: 1px solid rgba(56,189,248,0.3);
    padding: 0.5rem 1rem; border-radius: 8px;
    transition: all 0.2s;
  }
  .proj-link:hover { background: rgba(56,189,248,0.1); }

  /* TECH STACK */
  #stack { background: linear-gradient(180deg, transparent, rgba(167,139,250,0.04), transparent); }
  .stack-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-top: 3rem; }
  .stack-item {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 1.5rem;
    display: flex; align-items: center; gap: 1rem;
    transition: all 0.25s;
  }
  .stack-item:hover {
    transform: translateY(-4px) scale(1.02);
    border-color: rgba(56,189,248,0.3);
    box-shadow: var(--glow-cyan);
  }
  .stack-icon { font-size: 1.8rem; flex-shrink: 0; }
  .stack-name {
    font-family: 'Syne', sans-serif; font-weight: 700; font-size: 0.95rem;
  }
  .stack-level { font-size: 0.72rem; color: var(--muted); margin-top: 0.15rem; font-family: 'Space Mono', monospace; }
  .stack-bar {
    height: 3px; background: rgba(255,255,255,0.08);
    border-radius: 2px; margin-top: 0.5rem; overflow: hidden;
  }
  .stack-fill { height: 100%; border-radius: 2px; }
  .fill-cyan   { background: linear-gradient(90deg, var(--cyan), var(--violet)); }
  .fill-orange { background: linear-gradient(90deg, var(--orange), var(--yellow)); }
  .fill-blue   { background: linear-gradient(90deg, #60A5FA, var(--cyan)); }
  .fill-green  { background: linear-gradient(90deg, var(--green), #60A5FA); }
  .fill-pink   { background: linear-gradient(90deg, var(--pink), var(--violet)); }

  /* GITHUB STATS */
  .stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; margin-top: 3rem; }
  .stats-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 20px; overflow: hidden;
    transition: transform 0.3s;
  }
  .stats-card:hover { transform: translateY(-5px); }
  .stats-card img { width: 100%; display: block; }

  /* CODE BLOCK */
  .code-card {
    background: #0d1117;
    border: 1px solid var(--border);
    border-radius: 20px; overflow: hidden;
    font-family: 'Space Mono', monospace; font-size: 0.85rem;
    margin-top: 3rem;
    box-shadow: var(--glow-violet);
  }
  .code-header {
    background: rgba(167,139,250,0.08);
    border-bottom: 1px solid var(--border);
    padding: 0.8rem 1.2rem;
    display: flex; align-items: center; gap: 0.5rem;
  }
  .code-body { padding: 1.8rem; line-height: 2.2; }
  .c-kw  { color: var(--violet); }
  .c-fn  { color: var(--cyan); }
  .c-str { color: var(--green); }
  .c-cm  { color: var(--muted); }
  .c-br  { color: var(--pink); }

  /* GOALS */
  .goals-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-top: 3rem; }
  .goal-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 1.5rem;
    display: flex; flex-direction: column; gap: 0.8rem;
    transition: all 0.25s;
  }
  .goal-card:hover { transform: translateY(-5px); border-color: rgba(167,139,250,0.4); }
  .goal-icon { font-size: 1.8rem; }
  .goal-text { font-size: 0.9rem; font-weight: 600; line-height: 1.4; }
  .goal-bar { height: 4px; background: rgba(255,255,255,0.07); border-radius: 2px; overflow: hidden; margin-top: auto; }
  .goal-prog { height: 100%; border-radius: 2px; background: linear-gradient(90deg, var(--violet), var(--pink)); }

  /* CONNECT */
  .connect-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; margin-top: 3rem; }
  .connect-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 20px; padding: 2rem;
    display: flex; align-items: center; gap: 1.5rem;
    text-decoration: none; color: var(--white);
    transition: all 0.3s;
  }
  .connect-card:hover { transform: translateY(-6px); }
  .connect-card.linkedin:hover { border-color: rgba(0,119,181,0.5); box-shadow: 0 0 40px rgba(0,119,181,0.25); }
  .connect-card.gmail:hover   { border-color: rgba(234,67,53,0.5); box-shadow: 0 0 40px rgba(234,67,53,0.25); }
  .connect-icon-wrap {
    width: 56px; height: 56px; border-radius: 16px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.5rem; flex-shrink: 0;
  }
  .icon-linkedin { background: rgba(0,119,181,0.15); }
  .icon-gmail    { background: rgba(234,67,53,0.15); }
  .connect-name { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1.05rem; }
  .connect-handle { color: var(--muted); font-size: 0.8rem; margin-top: 0.2rem; }
  .connect-arrow { margin-left: auto; color: var(--muted); font-size: 1.2rem; transition: transform 0.2s; }
  .connect-card:hover .connect-arrow { transform: translate(4px, -4px); color: var(--cyan); }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 2.5rem 0; text-align: center;
    position: relative; z-index: 1;
  }
  .footer-text {
    font-family: 'Space Mono', monospace;
    font-size: 0.78rem; color: var(--muted);
  }
  .footer-text span {
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    font-weight: 700;
  }

  /* SCROLL ANIMATIONS */
  .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.6s ease, transform 0.6s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  @keyframes fadeUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

  /* SCROLL INDICATOR */
  .scroll-indicator {
    position: absolute; bottom: 2.5rem; left: 50%;
    transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    color: var(--muted); letter-spacing: 0.1em;
    animation: bounce 2s ease-in-out infinite;
  }
  .scroll-line { width: 1px; height: 50px; background: linear-gradient(180deg, var(--cyan), transparent); }
  @keyframes bounce { 0%,100% { transform: translateX(-50%) translateY(0); } 50% { transform: translateX(-50%) translateY(6px); } }

  @media (max-width: 900px) {
    .hero-inner { grid-template-columns: 1fr; }
    .hero-card { display: none; }
    .projects-grid, .stats-grid, .connect-grid { grid-template-columns: 1fr; }
    .stack-grid { grid-template-columns: repeat(2, 1fr); }
    .goals-grid { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<div class="blob blob1"></div>
<div class="blob blob2"></div>
<div class="blob blob3"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">SNJ ✦</div>
  <ul class="nav-links">
    <li><a href="#about">about</a></li>
    <li><a href="#projects">projects</a></li>
    <li><a href="#stack">stack</a></li>
    <li><a href="#stats">github</a></li>
    <li><a href="#connect">connect</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="container">
    <div class="hero-inner">
      <div>
        <div class="hero-tag">✦ Open to Opportunities</div>
        <h1 class="hero-name">
          Hey, I'm<br/>
          <span>Shreevatsa N J</span>
        </h1>
        <p class="hero-sub">
          <strong>Data Science Student</strong> building real AI products that actually slap.
          Creator of <strong>PathRadar</strong> &amp; <strong>NovoQuest</strong>.
          Obsessed with ML, clean code &amp; pushing commits. 🚀
        </p>
        <div class="hero-typing">
          <span class="typed-text" id="typedText">Building cool stuff</span>
        </div>
        <div class="badges-row">
          <span class="badge badge-blue">🐍 Python</span>
          <span class="badge badge-orange">☕ Java</span>
          <span class="badge badge-teal">🗄️ SQL</span>
          <span class="badge badge-purple">🤖 ML</span>
          <span class="badge badge-amber">📊 Tableau</span>
        </div>
        <div class="hero-cta">
          <a href="#projects" class="btn btn-primary">⚡ View Projects</a>
          <a href="#connect" class="btn btn-ghost">📡 Connect</a>
        </div>
      </div>
      <div class="hero-card">
        <div class="avatar-ring"><div class="avatar-inner">🧑‍💻</div></div>
        <div class="card-name">Shreevatsa N J</div>
        <div class="card-role">// data_scientist.init()</div>
        <div class="card-stats">
          <div class="stat"><div class="stat-num">4+</div><div class="stat-lbl">PROJECTS</div></div>
          <div class="stat"><div class="stat-num">3+</div><div class="stat-lbl">LANGUAGES</div></div>
          <div class="stat"><div class="stat-num">AI</div><div class="stat-lbl">FOCUSED</div></div>
          <div class="stat"><div class="stat-num">∞</div><div class="stat-lbl">LEARNING</div></div>
        </div>
      </div>
    </div>
    <div class="scroll-indicator">
      <div class="scroll-line"></div>
      scroll
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <div class="section-label">01 — About</div>
    <div class="section-title">Who am I?</div>
    <p class="section-desc">A quick &amp; honest breakdown of me, in the most dev way possible.</p>
    <div style="margin-top:2.5rem;" class="reveal">
      <div class="yaml-card">
        <div class="yaml-header">
          <div class="dot dot-r"></div>
          <div class="dot dot-y"></div>
          <div class="dot dot-g"></div>
          <span class="yaml-filename">about_me.yaml</span>
        </div>
        <div class="yaml-body">
          <div><span class="y-key">name:</span> <span class="y-str">Shreevatsa N J</span></div>
          <div><span class="y-key">role:</span> <span class="y-str">Data Science Student 🎓</span></div>
          <div><span class="y-key">passion:</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- AI Applications &amp; Products</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- Data Analytics &amp; Visualization</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- Full Stack Development</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- Problem Solving &amp; DSA</span></div>
          <div><span class="y-key">current_focus:</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- Machine Learning</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- Real World AI Products</span></div>
          <div>&nbsp;&nbsp;<span class="y-list">- DSA Grind 💪</span></div>
          <div><span class="y-key">status:</span> <span class="y-em">Building cool stuff &amp; pushing code 🚀</span></div>
          <div><span class="y-comment"># Always learning. Never stopping.</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="container">
    <div class="section-label">02 — Projects</div>
    <div class="section-title">Things I've Built 🔥</div>
    <p class="section-desc">Real projects. Real problems. Real code. Not just tutorial clones.</p>

    <div class="projects-grid">

      <!-- PathRadar -->
      <div class="project-card card-cyan reveal">
        <div class="proj-icon proj-icon-cyan">🧠</div>
        <div class="proj-title">PathRadar</div>
        <div class="proj-subtitle">AI-Based Resume Skill Gap Analyzer</div>
        <ul class="proj-features">
          <li>Resume Analysis &amp; Parsing</li>
          <li>Skill Gap Detection</li>
          <li>Job Recommendations</li>
          <li>Learning Roadmaps</li>
          <li>Industry Skill Explorer</li>
          <li>Course Recommendations</li>
          <li>Data Visualizations</li>
        </ul>
        <div class="proj-stack">
          <span class="stack-tag">Python</span>
          <span class="stack-tag">Flask</span>
          <span class="stack-tag">ML</span>
          <span class="stack-tag">SQL</span>
          <span class="stack-tag">JS</span>
        </div>
        <a href="https://github.com/ShreevatsaNJ/PathRadar" class="proj-link" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
          View Repo →
        </a>
      </div>

      <!-- NovoQuest -->
      <div class="project-card card-violet reveal">
        <div class="proj-icon proj-icon-violet">🎮</div>
        <div class="proj-title">NovoQuest</div>
        <div class="proj-subtitle">Personalized AI Learning Platform</div>
        <ul class="proj-features">
          <li>🔥 Daily Quests</li>
          <li>🏆 Boss Battles</li>
          <li>📈 Learning Dashboard</li>
          <li>⚡ Micro Challenges</li>
          <li>🎯 Personalized Learning Paths</li>
          <li>📊 Streak Tracking</li>
        </ul>
        <div class="proj-stack">
          <span class="stack-tag">HTML</span>
          <span class="stack-tag">CSS</span>
          <span class="stack-tag">JavaScript</span>
          <span class="stack-tag">AI Concepts</span>
          <span class="stack-tag">UI/UX</span>
        </div>
        <a href="https://github.com/ShreevatsaNJ/Novo-Quest" class="proj-link" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>
          View Repo →
        </a>
      </div>

      <!-- Blinkit Dashboard -->
      <div class="project-card card-pink reveal">
        <div class="proj-icon proj-icon-pink">📊</div>
        <div class="proj-title">Blinkit Dashboard</div>
        <div class="proj-subtitle">Sales &amp; Delivery Business Intelligence</div>
        <ul class="proj-features">
          <li>Sales Analysis</li>
          <li>Delivery Performance Metrics</li>
          <li>Product &amp; Category Insights</li>
          <li>Payment Analytics</li>
          <li>Interactive Visualizations</li>
        </ul>
        <div class="proj-stack">
          <span class="stack-tag">Tableau</span>
          <span class="stack-tag">BI</span>
          <span class="stack-tag">Data Analysis</span>
        </div>
      </div>

      <!-- Attendance System -->
      <div class="project-card card-green reveal">
        <div class="proj-icon proj-icon-green">📅</div>
        <div class="proj-title">Attendance System</div>
        <div class="proj-subtitle">CS50 Final Project</div>
        <ul class="proj-features">
          <li>Attendance Tracking</li>
          <li>Student Records Management</li>
          <li>User Authentication</li>
          <li>Responsive Design</li>
        </ul>
        <div class="proj-stack">
          <span class="stack-tag">HTML</span>
          <span class="stack-tag">CSS</span>
          <span class="stack-tag">JavaScript</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- TECH STACK -->
<section id="stack">
  <div class="container">
    <div class="section-label">03 — Stack</div>
    <div class="section-title">My Toolkit 🛠</div>
    <p class="section-desc">The weapons in my arsenal. Currently expanding rapidly.</p>
    <div class="stack-grid">
      <div class="stack-item reveal">
        <div class="stack-icon">🐍</div>
        <div>
          <div class="stack-name">Python</div>
          <div class="stack-level">Primary language</div>
          <div class="stack-bar"><div class="stack-fill fill-cyan" style="width:90%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">☕</div>
        <div>
          <div class="stack-name">Java</div>
          <div class="stack-level">OOP & backend</div>
          <div class="stack-bar"><div class="stack-fill fill-orange" style="width:72%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">🗄️</div>
        <div>
          <div class="stack-name">MySQL</div>
          <div class="stack-level">Database</div>
          <div class="stack-bar"><div class="stack-fill fill-blue" style="width:78%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">🤖</div>
        <div>
          <div class="stack-name">Machine Learning</div>
          <div class="stack-level">Active learning</div>
          <div class="stack-bar"><div class="stack-fill fill-green" style="width:60%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">📊</div>
        <div>
          <div class="stack-name">Tableau</div>
          <div class="stack-level">Data viz</div>
          <div class="stack-bar"><div class="stack-fill fill-pink" style="width:70%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">🌐</div>
        <div>
          <div class="stack-name">HTML/CSS/JS</div>
          <div class="stack-level">Frontend</div>
          <div class="stack-bar"><div class="stack-fill fill-cyan" style="width:75%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">🔧</div>
        <div>
          <div class="stack-name">Flask</div>
          <div class="stack-level">Backend framework</div>
          <div class="stack-bar"><div class="stack-fill fill-orange" style="width:65%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">🐙</div>
        <div>
          <div class="stack-name">Git &amp; GitHub</div>
          <div class="stack-level">Version control</div>
          <div class="stack-bar"><div class="stack-fill fill-blue" style="width:80%"></div></div>
        </div>
      </div>
      <div class="stack-item reveal">
        <div class="stack-icon">💻</div>
        <div>
          <div class="stack-name">VS Code</div>
          <div class="stack-level">Daily driver</div>
          <div class="stack-bar"><div class="stack-fill fill-green" style="width:95%"></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- GITHUB STATS -->
<section id="stats">
  <div class="container">
    <div class="section-label">04 — GitHub</div>
    <div class="section-title">GitHub Analytics 📈</div>
    <p class="section-desc">Numbers don't lie. Commits are my love language.</p>
    <div class="stats-grid reveal">
      <div class="stats-card">
        <img src="https://github-readme-stats.vercel.app/api?username=ShreevatsaNJ&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d0d24&title_color=38BDF8&icon_color=A78BFA&text_color=F0F4FF" alt="GitHub Stats"/>
      </div>
      <div class="stats-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ShreevatsaNJ&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d0d24&title_color=38BDF8&text_color=F0F4FF" alt="Top Languages"/>
      </div>
    </div>
    <div style="margin-top:1.5rem;" class="reveal">
      <div class="stats-card">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=ShreevatsaNJ&theme=tokyonight&hide_border=true&background=0d0d24&ring=38BDF8&fire=F472B6&currStreakLabel=38BDF8" alt="Streak Stats" style="width:100%;display:block;"/>
      </div>
    </div>

    <!-- Current Status Code Block -->
    <div class="code-card reveal">
      <div class="code-header">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span class="yaml-filename">current_status.java</span>
      </div>
      <div class="code-body">
        <div><span class="c-kw">while</span><span class="c-br">(</span>alive<span class="c-br">)</span> <span class="c-br">{</span></div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-fn">Learn</span><span class="c-br">()</span>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-cm">// never stop</span></div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-fn">Build</span><span class="c-br">()</span>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-cm">// ship real stuff</span></div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-fn">PushToGithub</span><span class="c-br">()</span>;&nbsp;<span class="c-cm">// daily ritual 🔥</span></div>
        <div>&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-fn">Repeat</span><span class="c-br">()</span>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="c-cm">// the grind continues</span></div>
        <div><span class="c-br">}</span></div>
      </div>
    </div>
  </div>
</section>

<!-- 2026 GOALS -->
<section id="goals">
  <div class="container">
    <div class="section-label">05 — Goals</div>
    <div class="section-title">2026 Roadmap 🎯</div>
    <p class="section-desc">The mission. The vision. The grind.</p>
    <div class="goals-grid">
      <div class="goal-card reveal">
        <div class="goal-icon">⚔️</div>
        <div class="goal-text">Master DSA &amp; crack interviews</div>
        <div class="goal-bar"><div class="goal-prog" style="width:40%"></div></div>
      </div>
      <div class="goal-card reveal">
        <div class="goal-icon">🤖</div>
        <div class="goal-text">Build More AI Products</div>
        <div class="goal-bar"><div class="goal-prog" style="width:55%"></div></div>
      </div>
      <div class="goal-card reveal">
        <div class="goal-icon">🌍</div>
        <div class="goal-text">Contribute to Open Source</div>
        <div class="goal-bar"><div class="goal-prog" style="width:20%"></div></div>
      </div>
      <div class="goal-card reveal">
        <div class="goal-icon">💼</div>
        <div class="goal-text">Secure Data Science Internship</div>
        <div class="goal-bar"><div class="goal-prog" style="width:30%"></div></div>
      </div>
      <div class="goal-card reveal">
        <div class="goal-icon">⭐</div>
        <div class="goal-text">Reach 1000+ GitHub Contributions</div>
        <div class="goal-bar"><div class="goal-prog" style="width:45%"></div></div>
      </div>
      <div class="goal-card reveal">
        <div class="goal-icon">📚</div>
        <div class="goal-text">Always Learning Something New</div>
        <div class="goal-bar"><div class="goal-prog" style="width:99%"></div></div>
      </div>
    </div>
  </div>
</section>

<!-- CONNECT -->
<section id="connect">
  <div class="container">
    <div class="section-label">06 — Connect</div>
    <div class="section-title">Let's Link 🌐</div>
    <p class="section-desc">Got a collab, opportunity, or just want to talk tech? Hit me up.</p>
    <div class="connect-grid">
      <a href="https://www.linkedin.com" class="connect-card linkedin reveal" target="_blank">
        <div class="connect-icon-wrap icon-linkedin">
          <svg width="26" height="26" viewBox="0 0 24 24" fill="#0077B5"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        </div>
        <div>
          <div class="connect-name">LinkedIn</div>
          <div class="connect-handle">Let's network &amp; grow</div>
        </div>
        <div class="connect-arrow">↗</div>
      </a>
      <a href="mailto:yourmail@gmail.com" class="connect-card gmail reveal">
        <div class="connect-icon-wrap icon-gmail">
          <svg width="26" height="26" viewBox="0 0 24 24" fill="#EA4335"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 010 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.910 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
        </div>
        <div>
          <div class="connect-name">Email</div>
          <div class="connect-handle">Drop me a message</div>
        </div>
        <div class="connect-arrow">↗</div>
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="container">
    <div class="footer-text">
      Built with 🔥 by <span>Shreevatsa N J</span> — Building. Learning. Improving.
      <br/><br/>
      ⭐ If you like my projects, give them a star on GitHub.
    </div>
  </div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx=0,my=0,rx=0,ry=0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.transform = `translate(${mx-6}px, ${my-6}px)`;
  });
  function lerpRing() {
    rx += (mx-rx)*0.12; ry += (my-ry)*0.12;
    ring.style.transform = `translate(${rx-18}px, ${ry-18}px)`;
    requestAnimationFrame(lerpRing);
  }
  lerpRing();
  document.querySelectorAll('a,button').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.transform += ' scale(2)'; ring.style.opacity='0.8'; });
    el.addEventListener('mouseleave', () => { ring.style.opacity='0.5'; });
  });

  // Typed text
  const phrases = [
    'Building cool stuff 🚀',
    'Breaking things & learning 💥',
    'Shipping AI products 🤖',
    'Pushing to GitHub at 2am 🌙',
    'Always in learning mode 📚',
  ];
  let pi=0,ci=0,del=false;
  const el = document.getElementById('typedText');
  function type() {
    const cur = phrases[pi];
    if (!del) {
      el.textContent = cur.slice(0, ++ci);
      if (ci===cur.length) { del=true; setTimeout(type,1800); return; }
    } else {
      el.textContent = cur.slice(0, --ci);
      if (ci===0) { del=false; pi=(pi+1)%phrases.length; setTimeout(type,400); return; }
    }
    setTimeout(type, del?45:80);
  }
  type();

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if(e.isIntersecting) { e.target.classList.add('visible'); } });
  }, { threshold: 0.12 });
  reveals.forEach(r => obs.observe(r));
</script>
</body>
</html>
