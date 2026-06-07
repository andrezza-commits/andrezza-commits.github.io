# andrezza-commits.github.io<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cevora | Sites que Convertem</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --cyan: #00FFEA;
    --cyan-dim: #00C9B8;
    --cyan-dark: #007A6F;
    --black: #050808;
    --black-2: #0D1111;
    --black-3: #141A1A;
    --black-4: #1C2424;
    --text: #E8F0EF;
    --text-muted: #7A9A97;
    --border: rgba(0, 255, 234, 0.12);
    --border-hover: rgba(0, 255, 234, 0.35);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: default;
  }

  /* ── CURSOR ── */
  .cursor {
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--cyan);
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, width 0.2s, height 0.2s, opacity 0.2s;
    mix-blend-mode: difference;
  }

  /* ── GRID BG ── */
  .grid-bg {
    position: fixed; inset: 0; z-index: 0;
    background-image:
      linear-gradient(rgba(0,255,234,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,234,0.04) 1px, transparent 1px);
    background-size: 48px 48px;
    pointer-events: none;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.25rem 5vw;
    background: rgba(5,8,8,0.85);
    backdrop-filter: blur(14px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: 'Space Mono', monospace;
    font-size: 1.35rem;
    color: var(--cyan);
    letter-spacing: -0.02em;
    text-decoration: none;
  }
  .nav-logo span { color: var(--text); }

  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--cyan); }

  .nav-cta {
    background: transparent;
    border: 1px solid var(--cyan);
    color: var(--cyan);
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    padding: 0.55rem 1.2rem;
    cursor: pointer;
    transition: background 0.2s, color 0.2s;
    letter-spacing: 0.06em;
    text-decoration: none;
  }
  .nav-cta:hover { background: var(--cyan); color: var(--black); }

  /* ── HERO ── */
  #hero {
    position: relative; z-index: 1;
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: flex-start;
    padding: 8rem 5vw 4rem;
    overflow: hidden;
  }

  .hero-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    color: var(--cyan);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex; align-items: center; gap: 0.6rem;
  }
  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 28px; height: 1px;
    background: var(--cyan);
  }

  .hero-title {
    font-size: clamp(3rem, 8vw, 7rem);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    max-width: 800px;
    margin-bottom: 2rem;
  }
  .hero-title .accent { color: var(--cyan); }

  .hero-sub {
    font-size: 1.1rem;
    color: var(--text-muted);
    max-width: 480px;
    line-height: 1.7;
    margin-bottom: 2.8rem;
  }

  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }

  .btn-primary {
    background: var(--cyan);
    color: var(--black);
    border: none;
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    padding: 0.9rem 2rem;
    cursor: pointer;
    transition: background 0.2s, transform 0.15s;
    text-decoration: none;
  }
  .btn-primary:hover { background: var(--cyan-dim); transform: translateY(-2px); }

  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border-hover);
    font-family: 'Space Mono', monospace;
    font-size: 0.85rem;
    letter-spacing: 0.05em;
    padding: 0.9rem 2rem;
    cursor: pointer;
    transition: border-color 0.2s, color 0.2s;
    text-decoration: none;
  }
  .btn-ghost:hover { border-color: var(--cyan); color: var(--cyan); }

  /* ── FLOATING CIRCLES ── */
  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
  }
  .orb-1 {
    width: 500px; height: 500px;
    background: rgba(0,255,234,0.06);
    right: -120px; top: 20%;
    animation: float 8s ease-in-out infinite;
  }
  .orb-2 {
    width: 300px; height: 300px;
    background: rgba(0,200,184,0.04);
    right: 20%; top: 60%;
    animation: float 12s ease-in-out infinite reverse;
  }
  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-40px); }
  }

  /* ── SCAN LINE ── */
  .scanline {
    position: absolute; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
    top: 0;
    animation: scan 6s linear infinite;
    opacity: 0.3;
  }
  @keyframes scan {
    0% { top: 0; opacity: 0; }
    10% { opacity: 0.3; }
    90% { opacity: 0.3; }
    100% { top: 100%; opacity: 0; }
  }

  /* ── STATS ── */
  .stats-bar {
    position: relative; z-index: 1;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    display: flex; align-items: stretch;
  }
  .stat-item {
    flex: 1;
    padding: 2rem;
    text-align: center;
    border-right: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }
  .stat-item:last-child { border-right: none; }
  .stat-item:hover { background: rgba(0,255,234,0.04); }
  .stat-num {
    font-family: 'Space Mono', monospace;
    font-size: 2.4rem;
    color: var(--cyan);
    display: block;
    line-height: 1;
    margin-bottom: 0.4rem;
  }
  .stat-label {
    font-size: 0.8rem;
    color: var(--text-muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* ── SECTION ── */
  section { position: relative; z-index: 1; padding: 6rem 5vw; }

  .section-tag {
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    color: var(--cyan);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1rem;
  }

  .section-title {
    font-size: clamp(1.8rem, 3.5vw, 3rem);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.02em;
    margin-bottom: 1rem;
  }

  .section-sub {
    font-size: 1rem;
    color: var(--text-muted);
    max-width: 480px;
    line-height: 1.7;
    margin-bottom: 3rem;
  }

  /* ── SERVIÇOS ── */
  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
  }

  .service-card {
    background: var(--black-2);
    padding: 2.5rem 2rem;
    transition: background 0.3s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }
  .service-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 0; height: 2px;
    background: var(--cyan);
    transition: width 0.4s ease;
  }
  .service-card:hover { background: var(--black-3); }
  .service-card:hover::after { width: 100%; }

  .service-icon {
    font-family: 'Space Mono', monospace;
    font-size: 1.8rem;
    color: var(--cyan);
    margin-bottom: 1.2rem;
    display: block;
  }

  .service-title {
    font-size: 1.1rem;
    font-weight: 800;
    margin-bottom: 0.7rem;
  }

  .service-desc {
    font-size: 0.88rem;
    color: var(--text-muted);
    line-height: 1.65;
  }

  /* ── PROCESSO ── */
  #processo { background: var(--black-2); }

  .process-list {
    display: flex;
    flex-direction: column;
    gap: 0;
    max-width: 760px;
  }

  .process-step {
    display: grid;
    grid-template-columns: 56px 1fr;
    gap: 0 1.5rem;
    padding: 2rem 0;
    border-bottom: 1px solid var(--border);
    position: relative;
  }
  .process-step:last-child { border-bottom: none; }

  .step-num {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    color: var(--cyan);
    padding-top: 0.2rem;
    letter-spacing: 0.05em;
  }

  .step-title {
    font-size: 1.1rem;
    font-weight: 800;
    margin-bottom: 0.4rem;
  }

  .step-desc {
    font-size: 0.9rem;
    color: var(--text-muted);
    line-height: 1.6;
  }

  /* ── PORTFOLIO PLACEHOLDER ── */
  #portfolio { }

  .portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem;
    margin-top: 1rem;
  }

  .portfolio-card {
    background: var(--black-3);
    border: 1px solid var(--border);
    aspect-ratio: 16/10;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: border-color 0.3s;
  }
  .portfolio-card:hover { border-color: var(--border-hover); }
  .portfolio-card:hover .portfolio-overlay { opacity: 1; }

  .portfolio-mock {
    width: 100%; height: 100%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    color: var(--border-hover);
    letter-spacing: 0.1em;
    flex-direction: column;
    gap: 0.5rem;
  }

  .portfolio-mock-bar {
    width: 70%; height: 6px;
    background: var(--border);
    border-radius: 2px;
    position: relative;
    overflow: hidden;
  }
  .portfolio-mock-bar::after {
    content: '';
    position: absolute; left: 0; top: 0;
    height: 100%;
    background: var(--cyan);
    animation: barpulse 2s ease-in-out infinite;
  }
  .portfolio-mock-bar:nth-child(2)::after { width: 65%; animation-delay: 0.2s; }
  .portfolio-mock-bar:nth-child(3)::after { width: 45%; animation-delay: 0.4s; }
  .portfolio-mock-bar:nth-child(4)::after { width: 80%; animation-delay: 0.6s; }

  @keyframes barpulse {
    0%, 100% { opacity: 0.3; }
    50% { opacity: 1; }
  }

  .portfolio-label {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    padding: 1rem 1.2rem;
    background: linear-gradient(transparent, rgba(5,8,8,0.95));
    font-size: 0.85rem;
    font-weight: 600;
  }
  .portfolio-sub {
    font-size: 0.75rem;
    color: var(--text-muted);
    font-family: 'Space Mono', monospace;
  }

  .portfolio-overlay {
    position: absolute; inset: 0;
    background: rgba(0,255,234,0.07);
    opacity: 0;
    transition: opacity 0.3s;
    display: flex; align-items: center; justify-content: center;
  }
  .portfolio-overlay span {
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    color: var(--cyan);
    letter-spacing: 0.1em;
    border: 1px solid var(--cyan);
    padding: 0.5rem 1.2rem;
  }

  /* ── CTA FINAL ── */
  #cta {
    background: var(--black-2);
    text-align: center;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
  }

  .cta-terminal {
    font-family: 'Space Mono', monospace;
    font-size: 0.8rem;
    color: var(--text-muted);
    background: var(--black-4);
    border: 1px solid var(--border);
    display: inline-block;
    padding: 0.5rem 1.2rem;
    margin-bottom: 2rem;
    text-align: left;
    max-width: 380px;
    width: 100%;
  }
  .cta-terminal .prompt { color: var(--cyan); }
  .cta-terminal .cursor-blink {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--cyan);
    vertical-align: middle;
    animation: blink 1s step-end infinite;
    margin-left: 2px;
  }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

  #cta .section-title { margin: 0 auto 1rem; max-width: 600px; }
  #cta .section-sub { margin: 0 auto 2.5rem; }

  /* ── FOOTER ── */
  footer {
    position: relative; z-index: 1;
    padding: 2rem 5vw;
    border-top: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .footer-logo {
    font-family: 'Space Mono', monospace;
    font-size: 1rem;
    color: var(--cyan);
  }

  .footer-copy {
    font-size: 0.78rem;
    color: var(--text-muted);
    font-family: 'Space Mono', monospace;
  }

  /* ── SCROLL FADE IN ── */
  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── RESPONSIVO ── */
  @media (max-width: 640px) {
    nav { padding: 1rem 4vw; }
    .nav-links { display: none; }
    .stats-bar { flex-direction: column; }
    .stat-item { border-right: none; border-bottom: 1px solid var(--border); }
    .stat-item:last-child { border-bottom: none; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="grid-bg"></div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">CEV<span>ORA</span></a>
  <ul class="nav-links">
    <li><a href="#servicos">Serviços</a></li>
    <li><a href="#processo">Processo</a></li>
    <li><a href="#portfolio">Portfólio</a></li>
    <li><a href="#cta">Contato</a></li>
  </ul>
  <a href="#cta" class="nav-cta">Iniciar Projeto →</a>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="scanline"></div>
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>

  <div class="hero-tag">Agência Digital · Est. 2024</div>

  <h1 class="hero-title">
    Sites que<br>
    <span class="accent">convertem.</span><br>
    Ponto final.
  </h1>

  <p class="hero-sub">
    Criamos landing pages e sites que transformam visitantes em clientes.
    Design preciso, tecnologia moderna, resultados reais.
  </p>

  <div class="hero-actions">
    <a href="#cta" class="btn-primary">Quero meu site</a>
    <a href="#portfolio" class="btn-ghost">Ver portfólio</a>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item reveal">
    <span class="stat-num">97%</span>
    <span class="stat-label">Taxa de satisfação</span>
  </div>
  <div class="stat-item reveal">
    <span class="stat-num">+3x</span>
    <span class="stat-label">Conversão média</span>
  </div>
  <div class="stat-item reveal">
    <span class="stat-num">48h</span>
    <span class="stat-label">Primeiro rascunho</span>
  </div>
  <div class="stat-item reveal">
    <span class="stat-num">∞</span>
    <span class="stat-label">Suporte contínuo</span>
  </div>
</div>

<!-- SERVIÇOS -->
<section id="servicos">
  <p class="section-tag reveal">// O que fazemos</p>
  <h2 class="section-title reveal">Nossos serviços</h2>
  <p class="section-sub reveal">Do conceito ao ar — entregamos cada projeto com atenção cirúrgica a cada detalhe.</p>

  <div class="services-grid">
    <div class="service-card reveal">
      <span class="service-icon">&lt;/&gt;</span>
      <h3 class="service-title">Landing Pages</h3>
      <p class="service-desc">Páginas criadas para converter. Cada elemento pensado para guiar o visitante à ação certa no momento certo.</p>
    </div>
    <div class="service-card reveal">
      <span class="service-icon">⬡</span>
      <h3 class="service-title">Sites Institucionais</h3>
      <p class="service-desc">Presença digital profissional que comunica credibilidade e diferencia sua marca da concorrência.</p>
    </div>
    <div class="service-card reveal">
      <span class="service-icon">◈</span>
      <h3 class="service-title">UI/UX Design</h3>
      <p class="service-desc">Interfaces que as pessoas entendem na primeira visita — intuitivas, bonitas e funcionais ao mesmo tempo.</p>
    </div>
    <div class="service-card reveal">
      <span class="service-icon">⚡</span>
      <h3 class="service-title">Performance & SEO</h3>
      <p class="service-desc">Sites rápidos, indexáveis e bem posicionados. Velocidade de carregamento e visibilidade orgânica que geram tráfego real.</p>
    </div>
  </div>
</section>

<!-- PROCESSO -->
<section id="processo">
  <p class="section-tag reveal">// Como trabalhamos</p>
  <h2 class="section-title reveal">Do briefing ao ar<br>em 4 etapas</h2>
  <p class="section-sub reveal">Um processo claro e direto, com você no controle de cada decisão.</p>

  <div class="process-list">
    <div class="process-step reveal">
      <span class="step-num">01 /</span>
      <div>
        <h3 class="step-title">Descoberta</h3>
        <p class="step-desc">Entendemos seu negócio, público-alvo e objetivos. Quanto mais soubermos sobre você, mais cirúrgico será o projeto.</p>
      </div>
    </div>
    <div class="process-step reveal">
      <span class="step-num">02 /</span>
      <div>
        <h3 class="step-title">Estratégia & Wireframe</h3>
        <p class="step-desc">Definimos estrutura, hierarquia e fluxo de conteúdo antes de qualquer pixel de design. A base de tudo.</p>
      </div>
    </div>
    <div class="process-step reveal">
      <span class="step-num">03 /</span>
      <div>
        <h3 class="step-title">Design & Desenvolvimento</h3>
        <p class="step-desc">Transformamos estratégia em interface. Codificamos com tecnologias modernas, performáticas e escaláveis.</p>
      </div>
    </div>
    <div class="process-step reveal">
      <span class="step-num">04 /</span>
      <div>
        <h3 class="step-title">Entrega & Suporte</h3>
        <p class="step-desc">Deploy, treinamento e suporte pós-lançamento. Seu site no ar e você independente para gerenciá-lo.</p>
      </div>
    </div>
  </div>
</section>

<!-- PORTFÓLIO -->
<section id="portfolio">
  <p class="section-tag reveal">// Trabalhos recentes</p>
  <h2 class="section-title reveal">Portfólio</h2>
  <p class="section-sub reveal">Uma amostra do que construímos. Cada projeto, uma solução sob medida.</p>

  <div class="portfolio-grid">
    <div class="portfolio-card reveal">
      <div class="portfolio-mock" style="padding: 1.5rem;">
        <div class="portfolio-mock-bar" style="width:80%"></div>
        <div class="portfolio-mock-bar" style="width:60%; margin-top:8px"></div>
        <div class="portfolio-mock-bar" style="width:72%; margin-top:8px"></div>
        <div class="portfolio-mock-bar" style="width:50%; margin-top:8px"></div>
      </div>
      <div class="portfolio-overlay"><span>VER PROJETO →</span></div>
      <div class="portfolio-label">
        Clínica Saúde+
        <div class="portfolio-sub">Landing Page · Saúde</div>
      </div>
    </div>
    <div class="portfolio-card reveal">
      <div class="portfolio-mock" style="padding: 1.5rem;">
        <div class="portfolio-mock-bar" style="width:90%"></div>
        <div class="portfolio-mock-bar" style="width:55%; margin-top:8px"></div>
        <div class="portfolio-mock-bar" style="width:80%; margin-top:8px"></div>
        <div class="portfolio-mock-bar" style="width:40%; margin-top:8px"></div>
      </div>
      <div class="portfolio-overlay"><span>VER PROJETO →</span></div>
      <div class="portfolio-label">
        TechFlow SaaS
        <div class="portfolio-sub">Site Institucional · Tech</div>
      </div>
    </div>
    <div class="portfolio-card reveal">
      <div class="portfolio-mock" style="padding: 1.5rem;">
        <div class="portfolio-mock-bar" style="width:65%"></div>
        <div class="portfolio-mock-bar" style="width:85%; margin-top:8px"></div>
        <div class="portfolio-mock-bar" style="width:50%; margin-top:8px"></div>
        <div class="portfolio-mock-bar" style="width:75%; margin-top:8px"></div>
      </div>
      <div class="portfolio-overlay"><span>VER PROJETO →</span></div>
      <div class="portfolio-label">
        Studio Arq
        <div class="portfolio-sub">Landing Page · Arquitetura</div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section id="cta">
  <div class="cta-terminal">
    <span class="prompt">$ </span>novo_projeto --start<span class="cursor-blink"></span>
  </div>
  <h2 class="section-title reveal">Pronto para<br>começar?</h2>
  <p class="section-sub reveal" style="margin:0 auto 2.5rem;">
    Fale com a gente. Sem enrolação, sem promessas vazias. Apenas resultados.
  </p>
  <div style="display:flex; gap:1rem; justify-content:center; flex-wrap:wrap;">
    <a href="mailto:oi@cevora.com.br" class="btn-primary">Falar com a Cevora</a>
    <a href="https://wa.me/5518900000000" class="btn-ghost">WhatsApp ↗</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span class="footer-logo">CEVORA</span>
  <span class="footer-copy">© 2024 Cevora · Todos os direitos reservados</span>
</footer>

<script>
  const cursor = document.getElementById('cursor');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
  });

  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
