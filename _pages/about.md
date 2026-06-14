---
permalink: /
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,ital,wght@9..144,0,400;9..144,0,600;9..144,1,400&display=swap" rel="stylesheet">

<style>
  /* ---------- Scoped homepage styles ---------- */
  .home {
    --ink: #1a2332;
    --paper: #faf7f0;
    --mist: #eef2f6;
    --rule: #d8dde3;
    --accent: #b04a3a;          /* warm rust accent */
    --accent-soft: #c87a6a;
    --primary: #4a6fa5;
    --primary-dark: #1e3a5f;
  }

  /* ---------- Hero cover image ---------- */
  .hero {
    margin: 0 0 2rem;
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0 10px 30px -12px rgba(15, 25, 45, .45);
    background: #0a1228;
  }
  .hero img {
    display: block;
    width: 100%;
    height: auto;
    transition: transform 6s ease;
  }
  .hero:hover img { transform: scale(1.025); }   /* gentle, slow zoom */

  /* ---------- Section headings (default font + accent bar) ---------- */
  .home h2 {
    font-size: 1.5rem;
    margin: 2.4rem 0 1rem;
    color: var(--ink);
    position: relative;
    padding-left: 18px;
  }
  .home h2::before {
    content: "";
    position: absolute;
    left: 0; top: 0.45em;
    height: 0.7em; width: 4px;
    background: var(--accent);
    border-radius: 2px;
  }

  /* ---------- Welcome / overview ---------- */
  .welcome { max-width: 70ch; line-height: 1.7; color: #2d3a4a; }
  .welcome p { font-size: 1.05rem; margin: 0; }

  /* ---------- Research themes (2x2, compact, equal-height) ---------- */
  .themes {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px;
    margin: 1rem 0 2rem;
  }
  @media (max-width: 600px) {
    .themes { grid-template-columns: 1fr; }
  }
  .theme {
    padding: 14px 16px 16px;
    border-radius: 10px;
    background: var(--mist);
    border: 1px solid transparent;
    transition: transform .25s ease, box-shadow .25s ease,
                border-color .25s ease, background .25s ease;
    opacity: 0;
    animation: fadeUp .6s ease forwards;
    display: flex;
    flex-direction: column;
    gap: 4px;
  }
  .theme:nth-child(1) { animation-delay: .05s; }
  .theme:nth-child(2) { animation-delay: .15s; }
  .theme:nth-child(3) { animation-delay: .25s; }
  .theme:nth-child(4) { animation-delay: .35s; }
  .theme:hover {
    transform: translateY(-3px);
    background: #fff;
    border-color: var(--primary);
    box-shadow: 0 8px 24px -10px rgba(30, 58, 95, .25);
  }
  .theme .icon {
    font-size: 1.3rem;
    display: block;
    transition: transform .3s ease;
  }
  .theme:hover .icon { transform: scale(1.15) rotate(-4deg); }
  .theme h3 { font-size: .98rem; margin: 0; color: var(--ink); }
  .theme p {
    font-size: .87rem;
    line-height: 1.45;
    margin: 0;
    color: #4a5568;
    flex-grow: 1;
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(12px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ---------- Featured question (KEEPS Fraunces serif) ---------- */
  .question-card {
    margin: 2rem 0;
    padding: 28px 32px;
    background: linear-gradient(135deg, #faf7f0 0%, #f0ebe0 100%);
    border-radius: 12px;
    border-left: 4px solid var(--accent);
    position: relative;
    overflow: hidden;
  }
  .question-card::before {
    content: "\201C";
    font-family: 'Fraunces', Georgia, serif;
    position: absolute;
    top: -28px; right: 18px;
    font-size: 9rem; line-height: 1;
    color: var(--accent);
    opacity: .12;
    pointer-events: none;
  }
  .question-card .label {
    font-family: 'Fraunces', Georgia, serif;
    font-size: .75rem;
    text-transform: uppercase;
    letter-spacing: .14em;
    color: var(--accent);
    font-weight: 600;
    margin-bottom: 8px;
  }
  .question-card .question {
    font-family: 'Fraunces', Georgia, serif;
    font-size: 1.3rem;
    line-height: 1.45;
    color: var(--ink);
    font-style: italic;
    margin: 0 0 .8rem;
  }
  .question-card .answer {
    font-family: 'Fraunces', Georgia, serif;
    font-size: 1rem;
    line-height: 1.6;
    color: #3a4756;
    margin: 0;
  }

  /* ---------- Current projects (expandable) ---------- */
  .projects { margin: 1rem 0 2rem; }
  .projects details {
    background: var(--mist);
    border-radius: 8px;
    padding: 14px 18px;
    margin-bottom: 8px;
    border: 1px solid transparent;
    transition: background .2s ease, border-color .2s ease;
  }
  .projects details[open] { background: #fff; border-color: var(--rule); }
  .projects summary {
    cursor: pointer;
    font-weight: 600;
    color: var(--ink);
    list-style: none;
    display: flex;
    align-items: center;
    gap: 12px;
    user-select: none;
  }
  .projects summary::-webkit-details-marker { display: none; }
  .projects summary::before {
    content: "+";
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 22px; height: 22px;
    background: var(--primary);
    color: #fff;
    border-radius: 50%;
    font-size: .95rem;
    line-height: 1;
    transition: transform .25s ease, background .25s ease;
    flex-shrink: 0;
  }
  .projects details[open] summary::before {
    transform: rotate(45deg);
    background: var(--accent);
  }
  .projects .project-body {
    padding: 10px 0 4px 34px;
    font-size: .92rem;
    line-height: 1.6;
    color: #475160;
  }

  /* ---------- Project hint line ---------- */
  .projects-hint {
    font-size: .92rem;
    color: #5a6778;
    margin: -.4rem 0 1rem;
  }

  /* ---------- Connect ---------- */
  .connect {
    margin-top: 2.5rem;
    padding: 28px;
    text-align: center;
    background: var(--paper);
    border-radius: 12px;
    border: 1px dashed var(--accent-soft);
  }
  .connect h3 { font-size: 1.3rem; margin: 0 0 8px; color: var(--ink); }
  .connect p {
    margin: 0 auto 14px;
    color: #4a5568;
    max-width: 52ch;
    font-size: .95rem;
  }
  .connect .links { display: inline-flex; gap: 10px; flex-wrap: wrap; justify-content: center; }
  .connect .links a {
    display: inline-block;
    padding: 8px 16px;
    background: #fff;
    border: 1px solid var(--rule);
    border-radius: 20px;
    color: var(--ink);
    text-decoration: none;
    font-size: .9rem;
    transition: all .2s ease;
  }
  .connect .links a:hover {
    background: var(--ink);
    color: #fff;
    border-color: var(--ink);
    transform: translateY(-1px);
  }

  /* ---------- Keep Follow dropdown above page content ---------- */
  .author__urls-wrapper { position: relative; z-index: 9999; }
  .author__urls.social-icons {
    z-index: 9999 !important;
    background-color: #fff !important;
  }
  html[data-theme="dark"] .author__urls.social-icons {
    background-color: #2a2a2a !important;
  }
  .home, .hero { position: static; }

  /* ---------- Dark mode overrides ---------- */
  html[data-theme="dark"] .home {
    --ink: #f2f4f7;
    --paper: #3a3a3a;
    --mist: #404040;
    --rule: #5a5a5a;
    --accent: #e08a7a;        /* lifted rust so it reads on dark */
    --accent-soft: #c87a6a;
    --primary: #6f9ad4;
    --primary-dark: #9bbce0;
  }

  html[data-theme="dark"] .welcome { color: #e6e9ed; }

  html[data-theme="dark"] .theme {
    background: var(--mist);
  }
  html[data-theme="dark"] .theme:hover {
    background: #4a4a4a;
    box-shadow: 0 8px 24px -10px rgba(0, 0, 0, .5);
  }
  html[data-theme="dark"] .theme p { color: #c4ccd6; }

  html[data-theme="dark"] .question-card {
    background: linear-gradient(135deg, #3f3f3f 0%, #363636 100%);
  }
  html[data-theme="dark"] .question-card .answer { color: #c8d0da; }

  html[data-theme="dark"] .projects details { background: var(--mist); }
  html[data-theme="dark"] .projects details[open] {
    background: #4a4a4a;
    border-color: var(--rule);
  }
  html[data-theme="dark"] .projects .project-body { color: #c4ccd6; }
  html[data-theme="dark"] .projects summary { color: var(--ink); }
  html[data-theme="dark"] .projects-hint { color: #b8c0ca; }

  html[data-theme="dark"] .connect {
    background: #3a3a3a;
    border-color: var(--accent-soft);
  }
  html[data-theme="dark"] .connect p { color: #c4ccd6; }
  html[data-theme="dark"] .connect .links a {
    background: #4a4a4a;
    border-color: var(--rule);
    color: var(--ink);
  }
  html[data-theme="dark"] .connect .links a:hover {
    background: var(--ink);
    color: #2a2a2a;
    border-color: var(--ink);
  }

  /* ---------- Respect reduced motion ---------- */
  @media (prefers-reduced-motion: reduce) {
    .theme, .theme .icon, .connect .links a,
    .projects details, .projects summary::before, .hero img {
      transition: none;
      animation: none;
    }
    .theme { opacity: 1; }
  }
</style>

<div class="home">

  <div class="hero">
    <img src="{{ site.baseurl }}/images/hero.jpg" alt="Glowing brain in a starry cosmos with three scientists observing it from a brain-shaped landscape">
  </div>

  <h2>Research Overview</h2>
  <div class="welcome">
    <p>I am a PhD student in Neuroscience at the University of Geneva, studying how vascular and metabolic health modify changes in brain structure and cognitive function across the adult lifespan. My research integrates longitudinal MRI, cognitive assessments, and biological markers — including blood-based and genetic indicators of vascular health, lifestyle and environmental factors — to characterize individual aging.</p>
  </div>

  <h2>Research Themes</h2>
  <div class="themes">
    <div class="theme">
      <span class="icon">🧠</span>
      <h3>Brain Aging</h3>
      <p>Structural brain changes across adulthood and later life.</p>
    </div>
    <div class="theme">
      <span class="icon">📊</span>
      <h3>Cognitive Change</h3>
      <p>Individual differences in cognitive trajectories over time.</p>
    </div>
    <div class="theme">
      <span class="icon">❤️</span>
      <h3>Health Modifiers</h3>
      <p>Vascular, metabolic, lifestyle, and environmental influences.</p>
    </div>
    <div class="theme">
      <span class="icon">📈</span>
      <h3>Longitudinal Methods</h3>
      <p>Statistical models for dynamic change over time.</p>
    </div>
  </div>

  <div class="question-card">
    <div class="label">The question driving my work</div>
    <p class="question">Why do some people maintain brain and cognitive health well into later life, while others experience accelerated decline?</p>
    <p class="answer">My research approaches this by integrating neuroimaging, cognitive testing, biological markers, and health data collected over many years — looking for the patterns that distinguish resilience from vulnerability.</p>
  </div>

  <h2>Current Projects</h2>
  <p class="projects-hint">Click any project to learn more.</p>
  <div class="projects">
    <details>
      <summary>Brain iron accumulation and cognitive aging</summary>
      <div class="project-body">Exploring how iron deposition in specific brain regions tracks with cognitive change across the adult lifespan.</div>
    </details>
    <details>
      <summary>Regional brain atrophy across adulthood</summary>
      <div class="project-body">Mapping where and when structural decline begins, and which regions are most sensitive to vascular and metabolic risk.</div>
    </details>
    <details>
      <summary>Vascular and metabolic risk factors</summary>
      <div class="project-body">Quantifying how blood pressure, glucose, lipids, and related markers shape brain trajectories over time.</div>
    </details>
    <details>
      <summary>Longitudinal neuroimaging and cognition</summary>
      <div class="project-body">Linking repeated MRI scans with repeated cognitive assessments to capture co-evolving change.</div>
    </details>
    <details>
      <summary>Structural equation modeling and dynamic longitudinal methods</summary>
      <div class="project-body">Applying advanced statistical frameworks to disentangle within-person change from between-person differences.</div>
    </details>
  </div>

  <div class="connect">
    <h3>Let's connect</h3>
    <p>I'm always happy to discuss neuroimaging, longitudinal research, and brain &amp; cognitive aging — whether for collaboration, a question, or just a good scientific conversation.</p>
    <div class="links">
      <a href="mailto:ademgashi@unige.ch">Email</a>
      <a href="https://orcid.org/0009-0000-1872-9391" target="_blank" rel="noopener">ORCID</a>
      <a href="https://scholar.google.com/citations?user=IXUL7KIAAAAJ&hl=en" target="_blank" rel="noopener">Google Scholar</a>
      <a href="https://www.linkedin.com/in/adem-gashi" target="_blank" rel="noopener">LinkedIn</a>
    </div>
  </div>

</div>
