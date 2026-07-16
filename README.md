<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Safoora Kounain — Data Analyst</title>
<meta name="description" content="Safoora Kounain — Data Analyst. Python, SQL, Power BI, Excel.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #08070c;
    --surface: #100e19;
    --surface-2: #17142450;
    --surface-border: #262138;
    --text: #e9e6f5;
    --text-dim: #8d86ab;
    --text-faint: #56516f;
    --violet: #9b87f5;
    --indigo: #6c63ff;
    --violet-soft: #9b87f522;
    --amber: #e8b96b;
    --mono: 'JetBrains Mono', monospace;
    --display: 'Space Grotesk', sans-serif;
    --body: 'Inter', sans-serif;
  }

  *{ margin:0; padding:0; box-sizing:border-box; }

  @media (prefers-reduced-motion: reduce){
    *{ animation-duration: 0.01ms !important; animation-iteration-count: 1 !important; transition-duration: 0.01ms !important; scroll-behavior: auto !important; }
  }

  html{ scroll-behavior: smooth; }

  body{
    background: var(--bg);
    color: var(--text);
    font-family: var(--body);
    line-height: 1.6;
    overflow-x: hidden;
    background-image:
      linear-gradient(var(--surface-2) 1px, transparent 1px),
      linear-gradient(90deg, var(--surface-2) 1px, transparent 1px);
    background-size: 64px 64px;
    background-position: center top;
  }

  a{ color: inherit; text-decoration: none; }

  ::selection{ background: var(--violet); color: #08070c; }

  :focus-visible{
    outline: 2px solid var(--violet);
    outline-offset: 3px;
    border-radius: 2px;
  }

  .wrap{ max-width: 1040px; margin: 0 auto; padding: 0 28px; }

  /* ---------- NAV ---------- */
  nav{
    position: sticky; top: 0; z-index: 50;
    backdrop-filter: blur(14px);
    background: rgba(8,7,12,0.72);
    border-bottom: 1px solid var(--surface-border);
  }
  nav .wrap{
    display:flex; align-items:center; justify-content:space-between;
    height: 60px;
  }
  .nav-brand{
    font-family: var(--mono); font-size: 14px; color: var(--text-dim);
  }
  .nav-brand b{ color: var(--violet); font-weight:600; }
  .nav-links{ display:flex; gap: 28px; font-family: var(--mono); font-size: 13px; color: var(--text-dim); }
  .nav-links a:hover{ color: var(--violet); }
  .nav-links a{ transition: color .2s ease; }

  /* ---------- HERO / QUERY CONSOLE ---------- */
  .hero{
    padding: 100px 0 70px;
  }
  .prompt-line{
    font-family: var(--mono); font-size: 13px; color: var(--text-faint);
    margin-bottom: 18px; letter-spacing: .02em;
  }
  .prompt-line .dot{
    display:inline-block; width:7px; height:7px; border-radius:50%;
    background: var(--violet); margin-right:8px;
    box-shadow: 0 0 8px var(--violet);
    animation: pulse 2.4s ease-in-out infinite;
  }
  @keyframes pulse{ 0%,100%{ opacity:1 } 50%{ opacity:.35 } }

  .console{
    border: 1px solid var(--surface-border);
    background: var(--surface);
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 40px 100px -40px rgba(108,99,255,0.25);
  }
  .console-head{
    display:flex; align-items:center; gap:8px;
    padding: 12px 16px;
    border-bottom: 1px solid var(--surface-border);
    font-family: var(--mono); font-size: 12px; color: var(--text-faint);
  }
  .console-head span.chip{
    width:10px; height:10px; border-radius:50%; background:#332e46; display:inline-block;
  }
  .console-body{
    padding: 28px 24px 30px;
    font-family: var(--mono);
  }
  .query-kw{ color: var(--violet); }
  .query-fn{ color: var(--amber); }
  .query-str{ color: #7fdbb5; }
  #typed-query{ font-size: clamp(16px, 2.4vw, 21px); white-space: pre-wrap; word-break: break-word; }
  .cursor{
    display:inline-block; width: 9px; height: 1.1em; background: var(--violet);
    vertical-align: text-bottom; animation: blink 1s step-end infinite;
  }
  @keyframes blink{ 50%{ opacity: 0 } }

  .results{
    margin-top: 26px; border-top: 1px dashed var(--surface-border); padding-top: 20px;
    opacity: 0; transform: translateY(8px);
    transition: opacity .5s ease, transform .5s ease;
  }
  .results.show{ opacity: 1; transform: translateY(0); }
  .results-meta{ font-size: 11px; color: var(--text-faint); margin-bottom: 12px; }
  .row{
    display:grid; grid-template-columns: 130px 1fr; gap: 14px;
    padding: 7px 0; font-size: 13.5px;
    border-bottom: 1px solid #17142450;
  }
  .row:last-child{ border-bottom: none; }
  .row .k{ color: var(--text-faint); }
  .row .v{ color: var(--text); font-family: var(--body); }
  .row .v b{ color: var(--violet); font-weight: 600; }

  .hero-cta{ display:flex; gap:14px; margin-top: 30px; flex-wrap: wrap; }
  .btn{
    font-family: var(--mono); font-size: 13px; padding: 11px 20px;
    border-radius: 6px; border: 1px solid var(--surface-border);
    transition: border-color .2s ease, transform .2s ease, background .2s ease;
    display:inline-flex; align-items:center; gap:8px;
  }
  .btn:hover{ transform: translateY(-1px); }
  .btn-primary{ background: linear-gradient(135deg, var(--indigo), var(--violet)); border:none; color:#0a0812; font-weight:600; }
  .btn-primary:hover{ box-shadow: 0 10px 30px -8px rgba(155,135,245,.55); }
  .btn-ghost{ color: var(--text-dim); }
  .btn-ghost:hover{ border-color: var(--violet); color: var(--violet); }

  /* ---------- SECTION SHELL ---------- */
  section{ padding: 90px 0; border-top: 1px solid var(--surface-border); }
  .eyebrow{
    font-family: var(--mono); font-size: 12px; color: var(--violet);
    display:flex; align-items:center; gap:10px; margin-bottom: 14px; text-transform: lowercase;
  }
  .eyebrow::before{ content: ''; width: 22px; height: 1px; background: var(--violet); opacity:.6; }
  h2{
    font-family: var(--display); font-weight: 600; font-size: clamp(24px, 3.4vw, 34px);
    margin-bottom: 10px; letter-spacing: -0.01em;
  }
  .section-sub{ color: var(--text-dim); max-width: 560px; font-size: 14.5px; margin-bottom: 44px; }

  /* ---------- ABOUT (schema style) ---------- */
  .schema{
    display:grid; grid-template-columns: 1fr 1fr; gap: 0;
    border: 1px solid var(--surface-border); border-radius: 10px; overflow: hidden;
  }
  @media (max-width: 720px){ .schema{ grid-template-columns: 1fr; } }
  .schema-col{ padding: 26px 26px; }
  .schema-col + .schema-col{ border-left: 1px solid var(--surface-border); }
  @media (max-width: 720px){ .schema-col + .schema-col{ border-left:none; border-top: 1px solid var(--surface-border);} }
  .schema-title{ font-family: var(--mono); font-size: 11.5px; color: var(--text-faint); margin-bottom: 16px; text-transform: uppercase; letter-spacing: .08em; }
  .field{ display:flex; gap: 10px; padding: 9px 0; font-size: 14px; border-bottom: 1px solid #17142450; }
  .field:last-child{ border-bottom:none; }
  .field .fname{ font-family: var(--mono); color: var(--amber); min-width: 92px; font-size: 12.5px; }
  .field .ftype{ color: var(--text-dim); }
  .bio-text{ font-size: 15px; color: var(--text-dim); line-height: 1.75; }
  .bio-text b{ color: var(--text); font-weight: 600; }

  /* ---------- TECH STACK ---------- */
  .stack-grid{ display:grid; grid-template-columns: repeat(2, 1fr); gap: 16px; }
  @media (max-width: 640px){ .stack-grid{ grid-template-columns: 1fr; } }
  .stack-table{
    border: 1px solid var(--surface-border); border-radius: 10px; padding: 20px 22px; background: var(--surface);
  }
  .stack-table h3{
    font-family: var(--mono); font-size: 12px; color: var(--text-faint); margin-bottom: 14px;
    text-transform: uppercase; letter-spacing: .07em;
  }
  .pills{ display:flex; flex-wrap:wrap; gap:8px; }
  .pill{
    font-family: var(--mono); font-size: 12px; padding: 6px 11px; border-radius: 5px;
    border: 1px solid var(--surface-border); color: var(--text-dim);
    transition: all .2s ease;
  }
  .pill:hover{ border-color: var(--violet); color: var(--violet); }

  /* ---------- PROJECTS ---------- */
  .proj-list{ display:flex; flex-direction:column; gap: 14px; }
  .proj{
    border: 1px solid var(--surface-border); border-radius: 10px; background: var(--surface);
    overflow:hidden;
  }
  .proj-head{
    display:flex; align-items:center; justify-content:space-between; gap: 16px;
    padding: 20px 22px; cursor: pointer;
  }
  .proj-head:hover{ background: #ffffff03; }
  .proj-title{ font-family: var(--display); font-size: 17px; font-weight: 600; }
  .proj-num{ font-family: var(--mono); color: var(--text-faint); font-size: 12px; margin-right: 12px; }
  .proj-stack{ font-family: var(--mono); font-size: 11.5px; color: var(--violet); }
  .chevron{ color: var(--text-faint); transition: transform .25s ease; flex-shrink:0; }
  .proj.open .chevron{ transform: rotate(180deg); }
  .proj-body{
    max-height: 0; overflow: hidden; transition: max-height .35s ease;
  }
  .proj.open .proj-body{ max-height: 320px; }
  .proj-body-inner{ padding: 0 22px 24px; }
  .proj-desc{ color: var(--text-dim); font-size: 14px; margin-bottom: 16px; max-width: 620px; }
  .kv-row{ display:flex; gap: 10px; font-size: 13px; padding: 6px 0; border-bottom: 1px solid #17142450; }
  .kv-row .k{ font-family: var(--mono); color: var(--text-faint); min-width: 90px; }
  .kv-row .v{ color: var(--text); }
  .proj-link{ display:inline-flex; align-items:center; gap:6px; margin-top:14px; font-family: var(--mono); font-size: 12.5px; color: var(--violet); }
  .proj-link:hover{ text-decoration: underline; }

  /* ---------- LOG / EXPERIENCE ---------- */
  .log{ font-family: var(--mono); font-size: 13.5px; }
  .log-entry{
    display:grid; grid-template-columns: 108px 1fr; gap: 18px;
    padding: 16px 0; border-bottom: 1px solid #17142450;
  }
  .log-entry:last-child{ border-bottom: none; }
  .log-time{ color: var(--text-faint); }
  .log-title{ font-family: var(--display); color: var(--text); font-weight:600; font-size:15px; margin-bottom:4px; }
  .log-org{ color: var(--violet); font-size: 12.5px; margin-bottom: 8px; }
  .log-desc{ color: var(--text-dim); font-family: var(--body); font-size: 13.5px; line-height:1.6; }

  /* ---------- ACHIEVEMENTS / CERTS ---------- */
  .grid-cards{ display:grid; grid-template-columns: repeat(3, 1fr); gap: 14px; }
  @media (max-width: 780px){ .grid-cards{ grid-template-columns: 1fr 1fr; } }
  @media (max-width: 520px){ .grid-cards{ grid-template-columns: 1fr; } }
  .card{
    border: 1px solid var(--surface-border); border-radius: 10px; padding: 20px; background: var(--surface);
  }
  .card .tag{ font-family: var(--mono); font-size: 10.5px; color: var(--text-faint); text-transform:uppercase; letter-spacing:.06em; margin-bottom:8px; display:block; }
  .card .headline{ font-family: var(--display); font-weight:600; font-size: 15px; margin-bottom: 6px; }
  .card .sub{ font-size: 13px; color: var(--text-dim); }

  .cert-group{ margin-bottom: 22px; }
  .cert-group:last-child{ margin-bottom: 0; }
  .cert-provider{ font-family: var(--mono); font-size: 12px; color: var(--text-faint); margin-bottom: 10px; text-transform: uppercase; letter-spacing:.06em; }
  .cert-badges{ display:flex; flex-wrap:wrap; gap: 10px; }
  .cert-badge{
    border: 1px solid var(--surface-border); border-radius: 7px; padding: 10px 14px;
    font-size: 13px; display:flex; align-items:center; gap: 10px; background: var(--surface);
  }
  .cert-badge .yr{ font-family: var(--mono); font-size: 11px; color: var(--violet); }

  /* ---------- CONTACT / FOOTER ---------- */
  .contact-console{
    border: 1px solid var(--surface-border); border-radius: 10px; background: var(--surface);
    padding: 34px 30px; text-align:center;
  }
  .contact-console .prompt-line{ justify-content:center; display:flex; }
  .contact-console h2{ margin-bottom: 16px; }
  .contact-links{ display:flex; gap: 14px; justify-content:center; flex-wrap:wrap; margin-top: 24px; }

  footer{
    padding: 40px 0 60px; text-align:center;
    font-family: var(--mono); font-size: 12px; color: var(--text-faint);
  }
  footer .quote{ font-family: var(--display); font-style: italic; color: var(--text-dim); font-size: 14px; margin-bottom: 14px; }

  .reveal{ opacity: 0; transform: translateY(16px); transition: opacity .6s ease, transform .6s ease; }
  .reveal.in{ opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<nav>
  <div class="wrap">
    <div class="nav-brand">&gt; <b>safoora</b>.db</div>
    <div class="nav-links">
      <a href="#about">about</a>
      <a href="#stack">stack</a>
      <a href="#projects">projects</a>
      <a href="#experience">experience</a>
      <a href="#certifications">certs</a>
      <a href="#contact">connect</a>
    </div>
  </div>
</nav>

<header class="hero">
  <div class="wrap">
    <div class="prompt-line"><span class="dot"></span>connection established — analytics_console v1.0</div>
    <div class="console">
      <div class="console-head">
        <span class="chip"></span><span class="chip"></span><span class="chip"></span>
        <span style="margin-left:8px;">query.sql</span>
      </div>
      <div class="console-body">
        <div id="typed-query"></div>
        <div class="results" id="results">
          <div class="results-meta">6 rows returned</div>
          <div class="row"><div class="k">name</div><div class="v"><b>Safoora Kounain</b></div></div>
          <div class="row"><div class="k">role</div><div class="v">Data Analyst — Fresher</div></div>
          <div class="row"><div class="k">education</div><div class="v">B.Tech CSE, MLR Institute of Technology · CGPA 8.84</div></div>
          <div class="row"><div class="k">location</div><div class="v">Hyderabad, India</div></div>
          <div class="row"><div class="k">tools</div><div class="v">Python · SQL · Power BI · Excel</div></div>
          <div class="row"><div class="k">target</div><div class="v">Entry-level Data Analyst roles at MNCs</div></div>
        </div>
      </div>
    </div>
    <div class="hero-cta">
      <a class="btn btn-primary" href="#projects">View projects →</a>
      <a class="btn btn-ghost" href="mailto:safoorakounain7@gmail.com">Email me</a>
      <a class="btn btn-ghost" href="https://github.com/AnalyticsForge13" target="_blank" rel="noopener">GitHub</a>
    </div>
  </div>
</header>

<section id="about">
  <div class="wrap">
    <div class="eyebrow">about</div>
    <h2 class="reveal">Reading the schema</h2>
    <p class="section-sub reveal">Who I am, structured the way I'd structure any dataset — fields first, story second.</p>

    <div class="schema reveal">
      <div class="schema-col">
        <div class="schema-title">profile fields</div>
        <div class="field"><div class="fname">degree</div><div class="ftype">B.Tech, Computer Science &amp; Engineering</div></div>
        <div class="field"><div class="fname">institute</div><div class="ftype">MLR Institute of Technology</div></div>
        <div class="field"><div class="fname">duration</div><div class="ftype">2023 – 2027 (Expected)</div></div>
        <div class="field"><div class="fname">cgpa</div><div class="ftype">8.84 / 10</div></div>
        <div class="field"><div class="fname">prior_ed</div><div class="ftype">Alphores Junior College · 85.30%</div></div>
        <div class="field"><div class="fname">status</div><div class="ftype">Actively job-seeking</div></div>
      </div>
      <div class="schema-col">
        <div class="schema-title">summary</div>
        <p class="bio-text">
          I'm a Computer Science undergraduate who works the <b>full analytics pipeline</b> — cleaning
          messy data, exploring it until it tells a straight story, and shipping that story as a
          dashboard someone can actually act on. My toolkit centers on <b>Python, SQL, Power BI, and Excel</b>,
          sharpened through hands-on projects and industry job simulations, including Deloitte's
          Data Analytics Job Simulation. I'm currently looking for an entry-level data analyst role
          where I can turn raw tables into decisions.
        </p>
      </div>
    </div>
  </div>
</section>

<section id="stack">
  <div class="wrap">
    <div class="eyebrow">tech stack</div>
    <h2 class="reveal">Tools of the trade</h2>
    <p class="section-sub reveal">Grouped the way I'd group them on a real project — not a wall of badges.</p>

    <div class="stack-grid reveal">
      <div class="stack-table">
        <h3>Languages &amp; Databases</h3>
        <div class="pills">
          <span class="pill">Python</span><span class="pill">SQL</span>
        </div>
      </div>
      <div class="stack-table">
        <h3>Libraries</h3>
        <div class="pills">
          <span class="pill">Pandas</span><span class="pill">NumPy</span><span class="pill">Matplotlib</span>
          <span class="pill">Seaborn</span><span class="pill">Scikit-learn</span>
        </div>
      </div>
      <div class="stack-table">
        <h3>Visualization &amp; BI</h3>
        <div class="pills">
          <span class="pill">Power BI</span><span class="pill">Tableau</span><span class="pill">Excel</span>
        </div>
      </div>
      <div class="stack-table">
        <h3>Tools &amp; Workflow</h3>
        <div class="pills">
          <span class="pill">Jupyter Notebook</span><span class="pill">Git</span><span class="pill">GitHub</span>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="projects">
  <div class="wrap">
    <div class="eyebrow">featured work</div>
    <h2 class="reveal">Projects</h2>
    <p class="section-sub reveal">Four end-to-end analyses — click to expand the stack and pipeline for each.</p>

    <div class="proj-list reveal" id="proj-list"></div>
  </div>
</section>

<section id="experience">
  <div class="wrap">
    <div class="eyebrow">experience log</div>
    <h2 class="reveal">Simulated professional practice</h2>
    <p class="section-sub reveal">Industry-backed virtual job simulations, in chronological order.</p>

    <div class="log reveal">
      <div class="log-entry">
        <div class="log-time">2025</div>
        <div>
          <div class="log-title">Data Analytics Job Simulation</div>
          <div class="log-org">Deloitte</div>
          <div class="log-desc">Practiced translating business problems into analytical tasks and worked through data-driven client scenarios.</div>
        </div>
      </div>
      <div class="log-entry">
        <div class="log-time">2026</div>
        <div>
          <div class="log-title">Data Visualisation: Empowering Business with Effective Insights</div>
          <div class="log-org">Tata</div>
          <div class="log-desc">Focused on using data visualization to drive business insight and decision-making.</div>
        </div>
      </div>
      <div class="log-entry">
        <div class="log-time">2026</div>
        <div>
          <div class="log-title">GenAI-Powered Data Analytics Job Simulation</div>
          <div class="log-org">Tata</div>
          <div class="log-desc">Applied generative AI techniques within a data analytics workflow.</div>
        </div>
      </div>
      <div class="log-entry">
        <div class="log-time">2026</div>
        <div>
          <div class="log-title">Quantitative Research Job Simulation</div>
          <div class="log-org">JPMorgan Chase &amp; Co.</div>
          <div class="log-desc">Covered quantitative research methods and analysis.</div>
        </div>
      </div>
      <div class="log-entry">
        <div class="log-time">2026</div>
        <div>
          <div class="log-title">Advisors &amp; Consulting Services Job Simulation</div>
          <div class="log-org">Mastercard</div>
          <div class="log-desc">Covered advisory and consulting analytics workflows.</div>
        </div>
      </div>
      <div class="log-entry">
        <div class="log-time">2026</div>
        <div>
          <div class="log-title">Data Analytics Virtual Experience Program</div>
          <div class="log-org">Quantium</div>
          <div class="log-desc">Applied data analytics in a virtual experience program setting.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="achievements">
  <div class="wrap">
    <div class="eyebrow">achievements</div>
    <h2 class="reveal">Recognition</h2>

    <div class="grid-cards reveal">
      <div class="card">
        <span class="tag">Academics</span>
        <div class="headline">8.84 / 10 CGPA</div>
        <div class="sub">B.Tech Computer Science &amp; Engineering</div>
      </div>
      <div class="card">
        <span class="tag">Academics</span>
        <div class="headline">85.30%</div>
        <div class="sub">Intermediate Education, Alphores Junior College</div>
      </div>
      <div class="card">
        <span class="tag">Industry</span>
        <div class="headline">6 simulations completed</div>
        <div class="sub">Deloitte, Tata, JPMorgan Chase, Mastercard, Quantium</div>
      </div>
    </div>
  </div>
</section>

<section id="certifications">
  <div class="wrap">
    <div class="eyebrow">certifications</div>
    <h2 class="reveal">Simulations &amp; credentials</h2>
    <p class="section-sub reveal">Grouped by provider.</p>

    <div class="reveal">
      <div class="cert-group">
        <div class="cert-provider">Deloitte</div>
        <div class="cert-badges">
          <div class="cert-badge">Data Analytics Job Simulation <span class="yr">2025</span></div>
        </div>
      </div>
      <div class="cert-group">
        <div class="cert-provider">Tata</div>
        <div class="cert-badges">
          <div class="cert-badge">Data Visualisation: Empowering Business with Effective Insights <span class="yr">2026</span></div>
          <div class="cert-badge">GenAI-Powered Data Analytics Job Simulation <span class="yr">2026</span></div>
        </div>
      </div>
      <div class="cert-group">
        <div class="cert-provider">JPMorgan Chase &amp; Co.</div>
        <div class="cert-badges">
          <div class="cert-badge">Quantitative Research Job Simulation <span class="yr">2026</span></div>
        </div>
      </div>
      <div class="cert-group">
        <div class="cert-provider">Mastercard</div>
        <div class="cert-badges">
          <div class="cert-badge">Advisors &amp; Consulting Services Job Simulation <span class="yr">2026</span></div>
        </div>
      </div>
      <div class="cert-group">
        <div class="cert-provider">Quantium</div>
        <div class="cert-badges">
          <div class="cert-badge">Data Analytics Virtual Experience Program <span class="yr">2026</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="contact">
  <div class="wrap">
    <div class="contact-console reveal">
      <div class="prompt-line"><span class="dot"></span>ready for next connection</div>
      <h2>Let's talk data</h2>
      <p class="section-sub" style="margin:0 auto;">Open to entry-level data analyst and BI roles — reach out directly.</p>
      <div class="contact-links">
        <a class="btn btn-primary" href="mailto:safoorakounain7@gmail.com">Email</a>
        <a class="btn btn-ghost" href="#" target="_blank" rel="noopener">LinkedIn</a>
        <a class="btn btn-ghost" href="https://github.com/AnalyticsForge13" target="_blank" rel="noopener">GitHub</a>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="quote">"Data tells the story; analysis decides the next chapter."</div>
  <div>© 2026 Safoora Kounain — built with SQL on the mind</div>
</footer>

<script>
  // Typing effect for hero query
  const target = document.getElementById('typed-query');
  const html = 'SELECT * FROM <span class="query-fn">analysts</span>\nWHERE name = <span class="query-str">\'Safoora Kounain\'</span>\n  AND role = <span class="query-str">\'Data Analyst\'</span>\nORDER BY <span class="query-kw">readiness</span> DESC;';
  const plain = 'SELECT * FROM analysts\nWHERE name = \'Safoora Kounain\'\n  AND role = \'Data Analyst\'\nORDER BY readiness DESC;';

  function typeQuery(){
    const reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    if(reduce){
      target.innerHTML = html;
      document.getElementById('results').classList.add('show');
      return;
    }
    let i = 0;
    const cursor = document.createElement('span');
    cursor.className = 'cursor';
    function step(){
      if(i <= plain.length){
        target.textContent = plain.slice(0, i);
        target.appendChild(cursor);
        i++;
        setTimeout(step, 18);
      } else {
        target.innerHTML = html;
        setTimeout(() => {
          document.getElementById('results').classList.add('show');
        }, 200);
      }
    }
    step();
  }
  window.addEventListener('load', typeQuery);

  // Scroll reveal
  const revealEls = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); } });
  }, { threshold: 0.12 });
  revealEls.forEach(el => io.observe(el));

  // Projects data + accordion
  const projects = [
    {
      title: 'Customer Churn Analysis',
      stack: 'Python · SQL · Power BI',
      desc: 'End-to-end customer churn analytics solution built to identify high-risk customers and support data-driven retention strategy.',
      pipeline: 'Data cleaning → SQL querying → churn analysis → Power BI dashboard',
      repo: 'https://github.com/AnalyticsForge13'
    },
    {
      title: 'HR Analytics Dashboard',
      stack: 'Power BI',
      desc: 'Interactive HR dashboard designed to monitor workforce KPIs, employee attrition, and organizational performance.',
      pipeline: 'Data modeling → DAX measures → interactive dashboard',
      repo: 'https://github.com/AnalyticsForge13'
    },
    {
      title: 'Supply Chain Performance Analysis',
      stack: 'Python · Pandas · Scikit-learn',
      desc: 'Predictive supply chain analytics solution built to identify late delivery risks and optimize logistics performance using machine learning.',
      pipeline: 'Preprocessing → feature engineering → ML model → risk scoring',
      repo: 'https://github.com/AnalyticsForge13'
    },
    {
      title: 'Retail Sales Analysis',
      stack: 'SQL · Power BI',
      desc: 'Analysis of retail sales trends with interactive dashboards built to support revenue optimization and business decision-making.',
      pipeline: 'SQL extraction → trend analysis → Power BI dashboard',
      repo: 'https://github.com/AnalyticsForge13'
    }
  ];

  const list = document.getElementById('proj-list');
  projects.forEach((p, idx) => {
    const el = document.createElement('div');
    el.className = 'proj';
    el.innerHTML = `
      <div class="proj-head" role="button" tabindex="0" aria-expanded="false">
        <div>
          <span class="proj-num">0${idx + 1}</span><span class="proj-title">${p.title}</span>
        </div>
        <div style="display:flex; align-items:center; gap:16px;">
          <span class="proj-stack">${p.stack}</span>
          <svg class="chevron" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 9l6 6 6-6"/></svg>
        </div>
      </div>
      <div class="proj-body">
        <div class="proj-body-inner">
          <p class="proj-desc">${p.desc}</p>
          <div class="kv-row"><div class="k">stack</div><div class="v">${p.stack}</div></div>
          <div class="kv-row"><div class="k">pipeline</div><div class="v">${p.pipeline}</div></div>
          <a class="proj-link" href="${p.repo}" target="_blank" rel="noopener">View repository →</a>
        </div>
      </div>
    `;
    const head = el.querySelector('.proj-head');
    function toggle(){
      const isOpen = el.classList.toggle('open');
      head.setAttribute('aria-expanded', isOpen);
    }
    head.addEventListener('click', toggle);
    head.addEventListener('keydown', (e) => { if(e.key === 'Enter' || e.key === ' '){ e.preventDefault(); toggle(); } });
    list.appendChild(el);
  });
</script>

</body>
</html>
