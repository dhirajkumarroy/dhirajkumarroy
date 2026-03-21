<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Dhiraj Kumar – Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #030712;
    --surface: #0d1117;
    --card: #111827;
    --border: #1f2937;
    --accent: #38bdf8;
    --accent2: #818cf8;
    --accent3: #34d399;
    --text: #f1f5f9;
    --muted: #64748b;
    --glow: rgba(56,189,248,0.18);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── STARFIELD ── */
  #stars {
    position: fixed; inset: 0; z-index: 0;
    pointer-events: none;
    background: transparent;
  }
  .star {
    position: absolute;
    border-radius: 50%;
    background: #fff;
    animation: twinkle var(--d, 3s) ease-in-out infinite;
    opacity: 0;
  }
  @keyframes twinkle {
    0%,100% { opacity: 0; transform: scale(0.8); }
    50% { opacity: var(--o, 0.6); transform: scale(1.2); }
  }

  /* ── LAYOUT ── */
  .container {
    position: relative; z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 80px;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    margin-bottom: 72px;
  }

  .avatar-ring {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 110px; height: 110px;
    border-radius: 50%;
    background: conic-gradient(var(--accent), var(--accent2), var(--accent3), var(--accent));
    padding: 3px;
    margin-bottom: 28px;
    animation: spin 8s linear infinite;
    cursor: pointer;
    transition: transform .3s;
  }
  .avatar-ring:hover { transform: scale(1.1); }
  @keyframes spin { to { filter: hue-rotate(360deg); } }
  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--bg);
    display: flex; align-items: center; justify-content: center;
    font-size: 42px;
  }

  .hero h1 {
    font-size: clamp(2rem, 5vw, 3.2rem);
    font-weight: 800;
    letter-spacing: -1px;
    line-height: 1.1;
    margin-bottom: 12px;
  }
  .hero h1 span { color: var(--accent); }

  .tagline {
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    color: var(--muted);
    margin-bottom: 28px;
    letter-spacing: 0.5px;
  }

  /* typing */
  .typewriter {
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: 1rem;
    color: var(--accent3);
    border-right: 2px solid var(--accent3);
    white-space: nowrap;
    overflow: hidden;
    animation: blink .7s step-end infinite;
    max-width: 0;
  }
  .typewriter.typing { animation: typing 2.5s steps(40,end) forwards, blink .7s step-end infinite; }
  @keyframes typing { to { max-width: 600px; } }
  @keyframes blink { 50% { border-color: transparent; } }

  .badges {
    display: flex; flex-wrap: wrap; gap: 10px;
    justify-content: center;
    margin-top: 24px;
  }
  .badge {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 6px 14px;
    border-radius: 999px;
    font-size: 0.75rem;
    font-family: 'Space Mono', monospace;
    color: var(--accent);
    transition: all .2s;
    cursor: default;
  }
  .badge:hover {
    background: var(--accent);
    color: var(--bg);
    border-color: var(--accent);
    transform: translateY(-2px);
    box-shadow: 0 0 12px var(--glow);
  }

  /* ── SECTION TITLES ── */
  .section-label {
    display: flex; align-items: center; gap: 12px;
    font-size: 0.7rem;
    font-family: 'Space Mono', monospace;
    color: var(--muted);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 20px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .section-title {
    font-size: 1.6rem;
    font-weight: 800;
    margin-bottom: 28px;
  }

  section { margin-bottom: 70px; }

  /* ── ABOUT ── */
  .about-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 16px;
  }
  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    transition: all .25s;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    transform: scaleX(0);
    transition: transform .3s;
    transform-origin: left;
  }
  .about-card:hover::before { transform: scaleX(1); }
  .about-card:hover {
    border-color: var(--accent);
    transform: translateY(-4px);
    box-shadow: 0 8px 32px var(--glow);
  }
  .about-card .icon { font-size: 1.6rem; margin-bottom: 10px; }
  .about-card p { font-size: 0.9rem; color: var(--muted); line-height: 1.6; }

  /* ── TECH STACK ── */
  .tech-grid {
    display: flex; flex-wrap: wrap; gap: 12px;
  }
  .tech-chip {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 10px 16px;
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    color: var(--text);
    display: flex; align-items: center; gap: 8px;
    transition: all .2s;
    cursor: default;
  }
  .tech-chip span.dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .tech-chip:hover {
    transform: translateY(-3px) scale(1.04);
    border-color: var(--accent);
    box-shadow: 0 4px 20px var(--glow);
    color: var(--accent);
  }

  /* ── PROJECTS ── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 20px;
  }
  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    transition: all .3s;
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .project-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at var(--mx,50%) var(--my,50%), rgba(56,189,248,.07) 0%, transparent 70%);
    pointer-events: none;
    opacity: 0;
    transition: opacity .3s;
  }
  .project-card:hover::after { opacity: 1; }
  .project-card:hover {
    border-color: var(--accent);
    transform: translateY(-6px);
    box-shadow: 0 12px 40px rgba(56,189,248,.12);
  }
  .project-emoji { font-size: 2rem; margin-bottom: 14px; }
  .project-card h3 { font-size: 1.05rem; font-weight: 700; margin-bottom: 10px; }
  .project-card p { font-size: 0.82rem; color: var(--muted); line-height: 1.7; }
  .project-tags { display: flex; gap: 6px; flex-wrap: wrap; margin-top: 16px; }
  .project-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.68rem;
    padding: 3px 8px;
    border-radius: 4px;
    background: rgba(56,189,248,.1);
    color: var(--accent);
    border: 1px solid rgba(56,189,248,.2);
  }

  /* ── LEARNING ── */
  .learning-list { display: flex; flex-direction: column; gap: 14px; }
  .learning-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px 20px;
    display: flex; align-items: center; gap: 16px;
    transition: all .2s;
  }
  .learning-item:hover {
    border-color: var(--accent3);
    transform: translateX(6px);
    box-shadow: -4px 0 0 var(--accent3);
  }
  .learning-bar-wrap {
    flex: 1;
    height: 6px;
    background: var(--border);
    border-radius: 3px;
    overflow: hidden;
  }
  .learning-bar {
    height: 100%;
    border-radius: 3px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    width: 0;
    transition: width 1.4s cubic-bezier(.4,0,.2,1);
  }
  .learning-item .label {
    font-size: 0.85rem;
    font-family: 'Space Mono', monospace;
    min-width: 160px;
  }
  .learning-item .pct {
    font-size: 0.75rem;
    color: var(--muted);
    min-width: 36px;
    text-align: right;
    font-family: 'Space Mono', monospace;
  }

  /* ── STATS ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 16px;
    margin-bottom: 28px;
  }
  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 22px 16px;
    text-align: center;
    transition: all .2s;
  }
  .stat-card:hover {
    border-color: var(--accent2);
    box-shadow: 0 0 24px rgba(129,140,248,.14);
    transform: scale(1.04);
  }
  .stat-card .num {
    font-size: 2rem;
    font-weight: 800;
    color: var(--accent);
    font-family: 'Space Mono', monospace;
  }
  .stat-card .lbl { font-size: 0.75rem; color: var(--muted); margin-top: 4px; }

  /* ── FOOTER / CTA ── */
  .cta {
    text-align: center;
    padding: 48px 24px;
    border: 1px solid var(--border);
    border-radius: 20px;
    background: var(--card);
    position: relative;
    overflow: hidden;
  }
  .cta::before {
    content: '';
    position: absolute;
    top: -60px; left: 50%;
    transform: translateX(-50%);
    width: 200px; height: 200px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(56,189,248,.2), transparent 70%);
    pointer-events: none;
  }
  .cta h2 { font-size: 1.8rem; font-weight: 800; margin-bottom: 12px; }
  .cta p { color: var(--muted); margin-bottom: 28px; font-size: 0.9rem; }
  .cta-btn {
    display: inline-block;
    background: var(--accent);
    color: var(--bg);
    font-family: 'Space Mono', monospace;
    font-weight: 700;
    font-size: 0.85rem;
    padding: 14px 32px;
    border-radius: 999px;
    text-decoration: none;
    border: none;
    cursor: pointer;
    transition: all .2s;
    letter-spacing: 1px;
  }
  .cta-btn:hover {
    transform: scale(1.06);
    box-shadow: 0 0 30px rgba(56,189,248,.45);
  }

  /* ── CURSOR TRAIL ── */
  .cursor-dot {
    position: fixed;
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--accent);
    pointer-events: none;
    z-index: 9999;
    transition: transform .1s;
    mix-blend-mode: screen;
  }

  /* ── SCROLL REVEAL ── */
  .reveal { opacity: 0; transform: translateY(30px); transition: opacity .7s ease, transform .7s ease; }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 600px) {
    .hero h1 { font-size: 1.8rem; }
    .learning-item .label { min-width: 110px; }
  }
</style>
</head>
<body>

<!-- Cursor trail -->
<div class="cursor-dot" id="cursorDot"></div>

<!-- Stars -->
<div id="stars"></div>

<div class="container">

  <!-- ── HERO ── -->
  <div class="hero reveal">
    <div class="avatar-ring" title="Click me!">
      <div class="avatar-inner">🧠</div>
    </div>
    <h1>Hey, I'm <span>Dhiraj Kumar</span> 👋</h1>
    <p class="tagline">B.Tech CSE · 4th Year &nbsp;/&nbsp; ML & AI Enthusiast &nbsp;/&nbsp; Data Explorer</p>
    <div>
      <span class="typewriter" id="typer"></span>
    </div>
    <div class="badges">
      <div class="badge">🤖 Machine Learning</div>
      <div class="badge">📊 Data Science</div>
      <div class="badge">🔧 Backend Systems</div>
      <div class="badge">📱 Android Dev</div>
      <div class="badge">🚀 Open Source</div>
    </div>
  </div>

  <!-- ── ABOUT ── -->
  <section class="reveal">
    <div class="section-label">01 &nbsp; about</div>
    <div class="about-grid">
      <div class="about-card">
        <div class="icon">✨</div>
        <p>Curious mind passionate about <strong>Machine Learning & Artificial Intelligence</strong></p>
      </div>
      <div class="about-card">
        <div class="icon">🔨</div>
        <p>Enjoy building <strong>real-world, problem-driven projects</strong> that create actual impact</p>
      </div>
      <div class="about-card">
        <div class="icon">🌐</div>
        <p>Exploring <strong>Data Science, Backend Systems</strong> and Smart Applications</p>
      </div>
      <div class="about-card">
        <div class="icon">📐</div>
        <p>Focus on <strong>strong fundamentals</strong>, clean code, and continuous learning</p>
      </div>
    </div>
  </section>

  <!-- ── STATS ── -->
  <section class="reveal">
    <div class="section-label">02 &nbsp; by the numbers</div>
    <div class="stats-row">
      <div class="stat-card">
        <div class="num" data-target="4">0</div>
        <div class="lbl">Projects Built</div>
      </div>
      <div class="stat-card">
        <div class="num" data-target="3">0</div>
        <div class="lbl">Languages</div>
      </div>
      <div class="stat-card">
        <div class="num" data-target="7">0</div>
        <div class="lbl">Tech Skills</div>
      </div>
      <div class="stat-card">
        <div class="num" data-target="1">0</div>
        <div class="lbl">Portfolio Site</div>
      </div>
    </div>
  </section>

  <!-- ── TECH STACK ── -->
  <section class="reveal">
    <div class="section-label">03 &nbsp; tech stack</div>
    <div class="tech-grid">
      <div class="tech-chip"><span class="dot" style="background:#3776ab"></span>Python</div>
      <div class="tech-chip"><span class="dot" style="background:#f89820"></span>Java</div>
      <div class="tech-chip"><span class="dot" style="background:#7f52ff"></span>Kotlin</div>
      <div class="tech-chip"><span class="dot" style="background:#f0db4f"></span>JavaScript</div>
      <div class="tech-chip"><span class="dot" style="background:#e34c26"></span>HTML</div>
      <div class="tech-chip"><span class="dot" style="background:#264de4"></span>CSS</div>
      <div class="tech-chip"><span class="dot" style="background:#f05032"></span>Git</div>
      <div class="tech-chip"><span class="dot" style="background:#38bdf8"></span>ML / NLP</div>
      <div class="tech-chip"><span class="dot" style="background:#34d399"></span>TF-IDF</div>
      <div class="tech-chip"><span class="dot" style="background:#818cf8"></span>Logistic Regression</div>
      <div class="tech-chip"><span class="dot" style="background:#fb923c"></span>Android Studio</div>
    </div>
  </section>

  <!-- ── PROJECTS ── -->
  <section class="reveal">
    <div class="section-label">04 &nbsp; featured projects</div>
    <div class="projects-grid">
      <div class="project-card">
        <div class="project-emoji">🤖</div>
        <h3>IntelliBot – Hybrid AI Chat</h3>
        <p>Offline ML-based intent prediction combined with online LLM integration, powered by NLP-driven conversation flow.</p>
        <div class="project-tags">
          <span class="project-tag">Python</span>
          <span class="project-tag">NLP</span>
          <span class="project-tag">LLM</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-emoji">📰</div>
        <h3>Digital Drift</h3>
        <p>Modern static blog platform with real-time search, smart filters, dark mode, and fully responsive design.</p>
        <div class="project-tags">
          <span class="project-tag">HTML</span>
          <span class="project-tag">CSS</span>
          <span class="project-tag">JS</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-emoji">🎮</div>
        <h3>Tic Tac Toe (Android)</h3>
        <p>Kotlin-based native Android game with persistent score tracking, reset flow, and a clean modern UI.</p>
        <div class="project-tags">
          <span class="project-tag">Kotlin</span>
          <span class="project-tag">Android</span>
        </div>
      </div>
      <div class="project-card">
        <div class="project-emoji">📝</div>
        <h3>To-Do List App</h3>
        <p>Interactive task manager built with vanilla HTML/CSS/JS — demonstrating DOM mastery and clean UI fundamentals.</p>
        <div class="project-tags">
          <span class="project-tag">HTML</span>
          <span class="project-tag">CSS</span>
          <span class="project-tag">JavaScript</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ── LEARNING ── -->
  <section class="reveal">
    <div class="section-label">05 &nbsp; currently learning</div>
    <div class="learning-list" id="learningList">
      <div class="learning-item">
        <div class="label">Advanced ML</div>
        <div class="learning-bar-wrap"><div class="learning-bar" data-pct="75"></div></div>
        <div class="pct">75%</div>
      </div>
      <div class="learning-item">
        <div class="label">Backend APIs</div>
        <div class="learning-bar-wrap"><div class="learning-bar" data-pct="60"></div></div>
        <div class="pct">60%</div>
      </div>
      <div class="learning-item">
        <div class="label">Clean Architecture</div>
        <div class="learning-bar-wrap"><div class="learning-bar" data-pct="50"></div></div>
        <div class="pct">50%</div>
      </div>
      <div class="learning-item">
        <div class="label">Deep Learning</div>
        <div class="learning-bar-wrap"><div class="learning-bar" data-pct="40"></div></div>
        <div class="pct">40%</div>
      </div>
    </div>
  </section>

  <!-- ── CTA ── -->
  <div class="cta reveal">
    <h2>Let's connect 🚀</h2>
    <p>Explore my repositories, check out my portfolio, or just say hi.</p>
    <a class="cta-btn" href="https://backend-portfolio-dft.pages.dev/" target="_blank">Visit My Portfolio →</a>
  </div>

</div>

<script>
  /* ── STARS ── */
  const starsEl = document.getElementById('stars');
  for (let i = 0; i < 120; i++) {
    const s = document.createElement('div');
    s.className = 'star';
    const size = Math.random() * 2.5 + 0.5;
    s.style.cssText = `
      left:${Math.random()*100}%;
      top:${Math.random()*100}%;
      width:${size}px; height:${size}px;
      --d:${(Math.random()*4+2).toFixed(1)}s;
      --o:${(Math.random()*.7+.3).toFixed(2)};
      animation-delay:${(Math.random()*5).toFixed(1)}s;
    `;
    starsEl.appendChild(s);
  }

  /* ── CURSOR DOT ── */
  const dot = document.getElementById('cursorDot');
  document.addEventListener('mousemove', e => {
    dot.style.left = e.clientX - 4 + 'px';
    dot.style.top  = e.clientY - 4 + 'px';
  });

  /* ── MOUSE GLOW ON PROJECT CARDS ── */
  document.querySelectorAll('.project-card').forEach(card => {
    card.addEventListener('mousemove', e => {
      const r = card.getBoundingClientRect();
      const x = ((e.clientX - r.left) / r.width * 100).toFixed(1);
      const y = ((e.clientY - r.top)  / r.height * 100).toFixed(1);
      card.style.setProperty('--mx', x + '%');
      card.style.setProperty('--my', y + '%');
    });
  });

  /* ── TYPEWRITER ── */
  const lines = [
    'Machine Learning Explorer',
    'AI & Data Science Enthusiast',
    'Building Projects That Matter',
    'Turning Ideas Into Code',
    'Always Learning. Always Improving.'
  ];
  let li = 0, ci = 0, deleting = false;
  const typer = document.getElementById('typer');
  function tick() {
    const line = lines[li];
    if (!deleting) {
      typer.textContent = line.slice(0, ++ci);
      if (ci === line.length) { deleting = true; setTimeout(tick, 1800); return; }
    } else {
      typer.textContent = line.slice(0, --ci);
      if (ci === 0) { deleting = false; li = (li + 1) % lines.length; }
    }
    setTimeout(tick, deleting ? 40 : 65);
  }
  tick();

  /* ── SCROLL REVEAL ── */
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));

  /* ── COUNTER ANIMATION ── */
  function animateCounters() {
    document.querySelectorAll('[data-target]').forEach(el => {
      const target = +el.getAttribute('data-target');
      let count = 0;
      const step = Math.ceil(target / 30);
      const iv = setInterval(() => {
        count = Math.min(count + step, target);
        el.textContent = count + (target > 10 ? '%' : '');
        if (count >= target) clearInterval(iv);
      }, 40);
    });
  }
  const statsSection = document.querySelector('.stats-row');
  const statsObs = new IntersectionObserver(entries => {
    if (entries[0].isIntersecting) { animateCounters(); statsObs.disconnect(); }
  }, { threshold: .3 });
  statsSection && statsObs.observe(statsSection);

  /* ── SKILL BAR ANIMATION ── */
  const barObs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.querySelectorAll('.learning-bar').forEach(bar => {
          bar.style.width = bar.dataset.pct + '%';
        });
        barObs.disconnect();
      }
    });
  }, { threshold: .2 });
  const ll = document.getElementById('learningList');
  if (ll) barObs.observe(ll);

  /* ── AVATAR EASTER EGG ── */
  const ring = document.querySelector('.avatar-ring');
  const emojis = ['🧠','🤖','🚀','🌟','💡','🔥','✨','🎯','⚡'];
  let ei = 0;
  ring.addEventListener('click', () => {
    ei = (ei + 1) % emojis.length;
    ring.querySelector('.avatar-inner').textContent = emojis[ei];
  });
</script>
</body>
</html>
