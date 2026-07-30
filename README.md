# warit-pengtham
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Portfolio — Full-Stack Developer</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg:       #0d0d0d;
      --surface:  #161616;
      --card:     #1c1c1c;
      --border:   #2a2a2a;
      --text:     #e8e8e8;
      --muted:    #666;
      --subtle:   #333;
      --accent:   #7c6fff;
      --accent2:  #4fffff;
      --mono:     'JetBrains Mono', monospace;
      --sans:     'Inter', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--sans);
      font-size: 15px;
      line-height: 1.7;
      -webkit-font-smoothing: antialiased;
    }

    a { color: inherit; text-decoration: none; }

    /* ─── NAV ─── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.1rem 2.5rem;
      background: rgba(13,13,13,0.88);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: var(--mono);
      font-size: 13px;
      color: var(--accent);
      letter-spacing: 0.04em;
    }
    .nav-links {
      display: flex; gap: 2rem; list-style: none;
    }
    .nav-links a {
      font-size: 13px; color: var(--muted);
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--text); }

    /* ─── HERO ─── */
    .hero {
      min-height: 100vh;
      display: flex; align-items: center;
      padding: 7rem 2.5rem 5rem;
      max-width: 900px; margin: 0 auto;
    }
    .hero-inner { width: 100%; }
    .eyebrow {
      font-family: var(--mono);
      font-size: 12px; color: var(--accent);
      letter-spacing: 0.1em; text-transform: uppercase;
      margin-bottom: 1.4rem;
    }
    h1 {
      font-size: clamp(2.6rem, 6vw, 4.2rem);
      font-weight: 600; line-height: 1.15;
      letter-spacing: -0.02em;
      margin-bottom: 0.4rem;
    }
    h1 span { color: var(--accent); }
    .tagline {
      font-size: clamp(1rem, 2.5vw, 1.25rem);
      color: var(--muted);
      margin-bottom: 2.2rem;
      max-width: 520px;
    }
    .hero-cta {
      display: flex; gap: 1rem; flex-wrap: wrap;
    }
    .btn {
      display: inline-flex; align-items: center; gap: 0.4rem;
      padding: 0.65rem 1.4rem;
      border-radius: 6px;
      font-size: 13px; font-weight: 500;
      cursor: pointer; transition: all 0.2s;
    }
    .btn-primary {
      background: var(--accent);
      color: #fff;
      border: 1px solid var(--accent);
    }
    .btn-primary:hover { opacity: 0.85; }
    .btn-ghost {
      background: transparent;
      color: var(--muted);
      border: 1px solid var(--border);
    }
    .btn-ghost:hover { border-color: var(--subtle); color: var(--text); }

    /* stack counter */
    .stack-row {
      display: flex; flex-wrap: wrap; gap: 0.5rem;
      margin-top: 2.8rem;
    }
    .lang-tag {
      font-family: var(--mono);
      font-size: 11px;
      padding: 0.3rem 0.7rem;
      border-radius: 4px;
      border: 1px solid var(--border);
      color: var(--muted);
      transition: all 0.2s;
    }
    .lang-tag:hover { border-color: var(--accent); color: var(--accent); }

    /* ─── SECTIONS ─── */
    section {
      max-width: 900px; margin: 0 auto;
      padding: 5rem 2.5rem;
      border-top: 1px solid var(--border);
    }
    .sec-label {
      font-family: var(--mono);
      font-size: 11px; color: var(--accent);
      letter-spacing: 0.1em; text-transform: uppercase;
      margin-bottom: 0.5rem;
    }
    h2 {
      font-size: 1.7rem; font-weight: 600;
      letter-spacing: -0.02em;
      margin-bottom: 2.5rem;
    }

    /* ─── ABOUT ─── */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
    }
    .about-text { color: #aaa; line-height: 1.8; }
    .about-text p + p { margin-top: 1rem; }
    .stats {
      display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem;
    }
    .stat-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.2rem;
    }
    .stat-num {
      font-size: 1.8rem; font-weight: 600;
      color: var(--text);
      font-variant-numeric: tabular-nums;
    }
    .stat-label {
      font-size: 12px; color: var(--muted); margin-top: 0.2rem;
    }

    /* ─── PROJECTS ─── */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 1.2rem;
    }
    .proj-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 1.5rem;
      transition: border-color 0.2s, transform 0.2s;
      cursor: pointer;
    }
    .proj-card:hover {
      border-color: var(--accent);
      transform: translateY(-2px);
    }
    .proj-header {
      display: flex; justify-content: space-between;
      align-items: flex-start; margin-bottom: 0.9rem;
    }
    .proj-icon {
      width: 36px; height: 36px;
      background: rgba(124,111,255,0.12);
      border-radius: 8px;
      display: flex; align-items: center; justify-content: center;
      font-size: 18px;
    }
    .proj-links { display: flex; gap: 0.6rem; }
    .proj-links a {
      font-size: 11px; color: var(--muted);
      border: 1px solid var(--border);
      padding: 0.2rem 0.55rem;
      border-radius: 4px;
      transition: all 0.2s;
    }
    .proj-links a:hover { border-color: var(--accent); color: var(--accent); }
    .proj-name {
      font-size: 15px; font-weight: 600;
      margin-bottom: 0.4rem;
    }
    .proj-desc {
      font-size: 13px; color: var(--muted);
      line-height: 1.65; margin-bottom: 1.1rem;
    }
    .proj-stack {
      display: flex; flex-wrap: wrap; gap: 0.35rem;
    }
    .proj-stack span {
      font-family: var(--mono);
      font-size: 10px; color: var(--muted);
      background: var(--surface);
      border: 1px solid var(--border);
      padding: 0.15rem 0.5rem;
      border-radius: 3px;
    }

    /* ─── SKILLS ─── */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1rem;
    }
    .skill-group {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.2rem 1.4rem;
    }
    .skill-group-title {
      font-size: 11px; font-weight: 600;
      text-transform: uppercase; letter-spacing: 0.06em;
      color: var(--accent); margin-bottom: 0.8rem;
    }
    .skill-group ul {
      list-style: none;
      display: flex; flex-direction: column; gap: 0.35rem;
    }
    .skill-group li {
      font-size: 13px; color: #aaa;
      display: flex; align-items: center; gap: 0.5rem;
    }
    .skill-group li::before {
      content: '';
      width: 5px; height: 5px;
      border-radius: 50%;
      background: var(--accent);
      opacity: 0.4;
      flex-shrink: 0;
    }

    /* ─── CONTACT ─── */
    .contact-box {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 3rem;
      text-align: center;
    }
    .contact-box p {
      color: var(--muted); max-width: 440px; margin: 0 auto 2rem;
      font-size: 14px; line-height: 1.75;
    }
    .social-row {
      display: flex; justify-content: center; gap: 1rem;
      flex-wrap: wrap;
    }
    .social-link {
      display: flex; align-items: center; gap: 0.5rem;
      font-size: 13px; color: var(--muted);
      border: 1px solid var(--border);
      padding: 0.55rem 1rem;
      border-radius: 6px;
      transition: all 0.2s;
    }
    .social-link:hover { border-color: var(--accent); color: var(--accent); }
    .social-link svg { width: 15px; height: 15px; }

    /* ─── FOOTER ─── */
    footer {
      max-width: 900px; margin: 0 auto;
      padding: 2rem 2.5rem;
      border-top: 1px solid var(--border);
      display: flex; justify-content: space-between; align-items: center;
      font-size: 12px; color: var(--muted);
    }
    footer span { font-family: var(--mono); }

    @media (max-width: 640px) {
      nav { padding: 1rem 1.2rem; }
      .hero, section { padding-left: 1.2rem; padding-right: 1.2rem; }
      .about-grid { grid-template-columns: 1fr; }
      .nav-links { display: none; }
      footer { flex-direction: column; gap: 0.5rem; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">&#47;&#47; dev.portfolio</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<div class="hero">
  <div class="hero-inner">
    <p class="eyebrow">Full-Stack Developer</p>
    <h1>Hi, I'm <span>Your Name</span>.<br />I build things for the web.</h1>
    <p class="tagline">Crafting clean, performant applications from database to UI — with a focus on developer experience and scalable architecture.</p>
    <div class="hero-cta">
      <a href="#projects" class="btn btn-primary">View projects →</a>
      <a href="#contact" class="btn btn-ghost">Get in touch</a>
    </div>
    <div class="stack-row">
      <span class="lang-tag">Python</span>
      <span class="lang-tag">JavaScript / TypeScript</span>
      <span class="lang-tag">Java / Kotlin</span>
      <span class="lang-tag">C++ / C#</span>
      <span class="lang-tag">React</span>
      <span class="lang-tag">Node.js</span>
    </div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <p class="sec-label">01 — About</p>
  <h2>A bit about me</h2>
  <div class="about-grid">
    <div class="about-text">
      <p>I'm a Full-Stack Developer passionate about building products that are both technically sound and delightful to use. I enjoy working across the entire stack — from system design to pixel-level UI detail.</p>
      <p>When I'm not coding, I'm exploring open-source projects, contributing to developer communities, or experimenting with new tools and frameworks.</p>
      <p>I'm currently open to new opportunities. If you have a project or role in mind, let's talk.</p>
    </div>
    <div class="stats">
      <div class="stat-card">
        <div class="stat-num">3+</div>
        <div class="stat-label">Years of experience</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">20+</div>
        <div class="stat-label">Projects shipped</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">4</div>
        <div class="stat-label">Languages mastered</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">∞</div>
        <div class="stat-label">Bugs squashed</div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <p class="sec-label">02 — Projects</p>
  <h2>Selected work</h2>
  <div class="projects-grid">

    <div class="proj-card">
      <div class="proj-header">
        <div class="proj-icon">🚀</div>
        <div class="proj-links">
          <a href="#" target="_blank">GitHub</a>
          <a href="#" target="_blank">Live</a>
        </div>
      </div>
      <div class="proj-name">Project Alpha</div>
      <div class="proj-desc">A full-stack web application with real-time collaboration features and a clean, minimal UI. Built for performance at scale.</div>
      <div class="proj-stack">
        <span>TypeScript</span><span>React</span><span>Node.js</span><span>PostgreSQL</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-header">
        <div class="proj-icon">🧠</div>
        <div class="proj-links">
          <a href="#" target="_blank">GitHub</a>
          <a href="#" target="_blank">Live</a>
        </div>
      </div>
      <div class="proj-name">ML Pipeline</div>
      <div class="proj-desc">An end-to-end machine learning pipeline for data ingestion, model training, and REST API serving with FastAPI and Docker.</div>
      <div class="proj-stack">
        <span>Python</span><span>FastAPI</span><span>scikit-learn</span><span>Docker</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-header">
        <div class="proj-icon">⚡</div>
        <div class="proj-links">
          <a href="#" target="_blank">GitHub</a>
        </div>
      </div>
      <div class="proj-name">System Monitor</div>
      <div class="proj-desc">A high-performance system monitoring daemon written in C++ with a Kotlin Android companion app for real-time metrics.</div>
      <div class="proj-stack">
        <span>C++</span><span>Kotlin</span><span>gRPC</span><span>Android</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-header">
        <div class="proj-icon">🔗</div>
        <div class="proj-links">
          <a href="#" target="_blank">GitHub</a>
          <a href="#" target="_blank">Live</a>
        </div>
      </div>
      <div class="proj-name">API Gateway</div>
      <div class="proj-desc">A microservices gateway built with Spring Boot and Kotlin — featuring rate limiting, JWT auth, and request routing.</div>
      <div class="proj-stack">
        <span>Kotlin</span><span>Spring Boot</span><span>Redis</span><span>JWT</span>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-header">
        <div class="proj-icon">🎨</div>
        <div class="proj-links">
          <a href="#" target="_blank">GitHub</a>
          <a href="#" target="_blank">Live</a>
        </div>
      </div>
      <div class="proj-name">Design System</div>
      <div class="proj-desc">A component library in TypeScript with Storybook documentation, covering 40+ UI components with dark mode support.</div>
      <div class="proj-stack">
        <span>TypeScript</span><span>React</span><span>Storybook</span><span>CSS</span>
      </div>
    </div>

    <div class="proj-card" style="border-color: var(--subtle); display:flex; align-items:center; justify-content:center; min-height: 180px;">
      <div style="text-align:center;">
        <div style="font-size:1.4rem; margin-bottom:0.5rem;">+</div>
        <div style="font-size:13px; color: var(--muted);">More on GitHub</div>
        <a href="#" style="font-size:12px; color:var(--accent); font-family:var(--mono);">github.com/username →</a>
      </div>
    </div>

  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <p class="sec-label">03 — Skills</p>
  <h2>Tech stack</h2>
  <div class="skills-grid">
    <div class="skill-group">
      <div class="skill-group-title">Languages</div>
      <ul>
        <li>Python</li>
        <li>TypeScript / JavaScript</li>
        <li>Java / Kotlin</li>
        <li>C++ / C#</li>
        <li>SQL</li>
      </ul>
    </div>
    <div class="skill-group">
      <div class="skill-group-title">Frontend</div>
      <ul>
        <li>React</li>
        <li>Next.js</li>
        <li>Tailwind CSS</li>
        <li>Vite</li>
        <li>HTML / CSS</li>
      </ul>
    </div>
    <div class="skill-group">
      <div class="skill-group-title">Backend</div>
      <ul>
        <li>Node.js / Express</li>
        <li>FastAPI / Django</li>
        <li>Spring Boot</li>
        <li>REST / GraphQL</li>
        <li>gRPC</li>
      </ul>
    </div>
    <div class="skill-group">
      <div class="skill-group-title">Data & Cloud</div>
      <ul>
        <li>PostgreSQL / MySQL</li>
        <li>Redis / MongoDB</li>
        <li>Docker / Kubernetes</li>
        <li>AWS / GCP</li>
        <li>CI/CD (GitHub Actions)</li>
      </ul>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <p class="sec-label">04 — Contact</p>
  <h2>Get in touch</h2>
  <div class="contact-box">
    <p>I'm currently open to freelance projects, full-time roles, and interesting collaborations. Drop me a message — I read everything.</p>
    <a href="mailto:your@email.com" class="btn btn-primary" style="display:inline-flex; margin-bottom:1.8rem;">your@email.com ↗</a>
    <div class="social-row">
      <a href="https://github.com/username" target="_blank" class="social-link">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844a9.59 9.59 0 0 1 2.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
        GitHub
      </a>
      <a href="https://linkedin.com/in/username" target="_blank" class="social-link">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a href="https://twitter.com/username" target="_blank" class="social-link">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        Twitter / X
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span>// your-name.dev</span>
  <span>Built with HTML & ☕</span>
</footer>

</body>
</html>
