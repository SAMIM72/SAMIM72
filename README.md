<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>Samim — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=VT323&display=swap" rel="stylesheet"/>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}

:root{
  --green:#00ff41;
  --green2:#00cc33;
  --green-dim:#003a00;
  --bg:#000500;
  --card:#020d02;
  --border:#00ff4133;
  --amber:#ffb800;
  --cyan:#00ffff;
  --red:#ff2244;
  --text:#b8ffb8;
  --muted:#3a7a3a;
}

html{scroll-behavior:smooth}

body{
  background:var(--bg);
  color:var(--green);
  font-family:'Share Tech Mono',monospace;
  min-height:100vh;
  overflow-x:hidden;
  cursor:crosshair;
}

/* ── SCANLINES ── */
body::after{
  content:'';
  position:fixed;
  inset:0;
  background:repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0,0,0,0.15) 2px,
    rgba(0,0,0,0.15) 4px
  );
  pointer-events:none;
  z-index:9999;
  animation:scanroll 8s linear infinite;
}
@keyframes scanroll{
  from{background-position:0 0}
  to{background-position:0 100vh}
}

/* ── MATRIX CANVAS ── */
#matrix-canvas{
  position:fixed;
  top:0;left:0;
  width:100%;height:100%;
  opacity:0.07;
  z-index:0;
  pointer-events:none;
}

/* ── CONTAINER ── */
.container{
  max-width:860px;
  margin:0 auto;
  padding:40px 20px 80px;
  position:relative;
  z-index:1;
}

/* ── TERMINAL WINDOW WRAPPER ── */
.terminal{
  background:var(--card);
  border:1px solid var(--green);
  border-radius:4px;
  margin-bottom:24px;
  box-shadow:0 0 30px rgba(0,255,65,0.1), inset 0 0 30px rgba(0,0,0,0.5);
  animation:termAppear 0.4s ease both;
}

@keyframes termAppear{
  from{opacity:0;transform:scaleY(0.95);filter:blur(4px)}
  to{opacity:1;transform:scaleY(1);filter:blur(0)}
}

.terminal:nth-child(1){animation-delay:0.1s}
.terminal:nth-child(2){animation-delay:0.2s}
.terminal:nth-child(3){animation-delay:0.3s}
.terminal:nth-child(4){animation-delay:0.4s}
.terminal:nth-child(5){animation-delay:0.5s}
.terminal:nth-child(6){animation-delay:0.6s}
.terminal:nth-child(7){animation-delay:0.7s}

/* Terminal title bar */
.term-bar{
  background:#001a00;
  border-bottom:1px solid var(--border);
  padding:8px 14px;
  display:flex;
  align-items:center;
  gap:10px;
  font-size:0.75rem;
  color:var(--muted);
}
.term-dots{display:flex;gap:6px}
.dot{
  width:10px;height:10px;border-radius:50%;
  animation:dotPulse 3s ease-in-out infinite;
}
.dot-r{background:#ff5f56;animation-delay:0s}
.dot-y{background:#ffbd2e;animation-delay:0.3s}
.dot-g{background:#27c93f;animation-delay:0.6s}
@keyframes dotPulse{
  0%,100%{opacity:1}50%{opacity:0.5}
}
.term-title{flex:1;text-align:center;letter-spacing:2px;font-size:0.7rem}

/* Terminal body */
.term-body{padding:24px 28px}

/* ── HERO ── */
.hero-term .term-body{
  display:flex;
  flex-direction:column;
  align-items:center;
  text-align:center;
  gap:16px;
  padding:32px 28px;
}

/* ASCII avatar frame */
.ascii-frame{
  font-family:'VT323',monospace;
  font-size:0.85rem;
  line-height:1.2;
  color:var(--green2);
  text-shadow:0 0 8px var(--green);
  white-space:pre;
  animation:asciiGlow 2s ease-in-out infinite alternate;
}
@keyframes asciiGlow{
  from{text-shadow:0 0 6px var(--green), 0 0 12px var(--green)}
  to{text-shadow:0 0 12px var(--green), 0 0 24px var(--green), 0 0 40px var(--green)}
}

/* Glitch title */
.glitch-title{
  font-family:'Orbitron',monospace;
  font-size:clamp(1.8rem,5vw,3rem);
  font-weight:900;
  color:var(--green);
  text-transform:uppercase;
  letter-spacing:4px;
  position:relative;
  display:inline-block;
  text-shadow:0 0 20px var(--green);
  animation:glitch 4s infinite;
}
.glitch-title::before,
.glitch-title::after{
  content:attr(data-text);
  position:absolute;
  top:0;left:0;
  width:100%;height:100%;
}
.glitch-title::before{
  color:var(--cyan);
  animation:glitch-before 4s infinite;
  clip-path:polygon(0 0,100% 0,100% 35%,0 35%);
}
.glitch-title::after{
  color:var(--red);
  animation:glitch-after 4s infinite;
  clip-path:polygon(0 65%,100% 65%,100% 100%,0 100%);
}
@keyframes glitch{
  0%,90%,100%{transform:none;opacity:1}
  91%{transform:skewX(-2deg);opacity:0.9}
  93%{transform:skewX(2deg)}
  95%{transform:none}
  97%{transform:skewX(-1deg)}
}
@keyframes glitch-before{
  0%,90%,100%{transform:none;opacity:0}
  91%{transform:translate(-3px,0);opacity:0.8}
  93%{transform:translate(3px,0)}
  95%{transform:none;opacity:0}
}
@keyframes glitch-after{
  0%,90%,100%{transform:none;opacity:0}
  91%{transform:translate(3px,0);opacity:0.8}
  93%{transform:translate(-3px,0)}
  95%{transform:none;opacity:0}
}

.role-line{
  font-family:'VT323',monospace;
  font-size:1.5rem;
  color:var(--amber);
  letter-spacing:3px;
  text-shadow:0 0 10px var(--amber);
}

/* Typing cursor */
.cursor{
  display:inline-block;
  width:10px;height:1.2em;
  background:var(--green);
  vertical-align:middle;
  animation:blink 1s step-end infinite;
  margin-left:4px;
}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

/* Views badge */
.views-badge{
  display:inline-flex;align-items:center;gap:8px;
  background:#001200;
  border:1px solid var(--green2);
  border-radius:2px;
  padding:4px 14px;
  font-size:0.72rem;
  color:var(--muted);
  font-family:'Share Tech Mono',monospace;
}
.ping{
  width:8px;height:8px;border-radius:50%;
  background:var(--green);
  box-shadow:0 0 6px var(--green);
  animation:ping 1.5s ease-in-out infinite;
}
@keyframes ping{
  0%,100%{transform:scale(1);opacity:1}
  50%{transform:scale(1.5);opacity:0.5}
}

/* ── PROMPT LINE ── */
.prompt{
  color:var(--muted);
  font-size:0.8rem;
  margin-bottom:16px;
  display:flex;align-items:center;gap:6px;
}
.prompt::before{content:'root@samim:~$';color:var(--green);font-size:0.85rem}
.prompt span{color:var(--amber)}

/* ── SECTION TITLE ── */
.sec-title{
  font-family:'Orbitron',monospace;
  font-size:1rem;
  font-weight:700;
  color:var(--green);
  text-transform:uppercase;
  letter-spacing:3px;
  margin-bottom:20px;
  display:flex;align-items:center;gap:10px;
  text-shadow:0 0 10px var(--green);
}
.sec-title::after{
  content:'';flex:1;height:1px;
  background:linear-gradient(90deg,var(--green2),transparent);
}

/* ── ABOUT GRID ── */
.about-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
}
.about-row{
  background:#000d00;
  border:1px solid var(--border);
  border-radius:2px;
  padding:12px 14px;
  display:flex;align-items:flex-start;gap:10px;
  transition:border-color 0.2s,box-shadow 0.2s,transform 0.2s;
  animation:rowIn 0.5s ease both;
}
.about-row:hover{
  border-color:var(--green);
  box-shadow:0 0 15px rgba(0,255,65,0.15), inset 0 0 10px rgba(0,255,65,0.05);
  transform:translateX(4px);
}
@keyframes rowIn{
  from{opacity:0;transform:translateX(-20px)}
  to{opacity:1;transform:translateX(0)}
}
.about-row:nth-child(1){animation-delay:0.1s}
.about-row:nth-child(2){animation-delay:0.15s}
.about-row:nth-child(3){animation-delay:0.2s}
.about-row:nth-child(4){animation-delay:0.25s}
.about-row:nth-child(5){animation-delay:0.3s}
.about-row:nth-child(6){animation-delay:0.35s}

.row-icon{font-size:1.1rem;flex-shrink:0;margin-top:1px}
.row-key{
  font-size:0.67rem;color:var(--muted);
  text-transform:uppercase;letter-spacing:2px;
  margin-bottom:2px;
}
.row-val{font-size:0.85rem;color:var(--text)}
.row-val a{color:var(--cyan);text-decoration:none}
.row-val a:hover{color:var(--green);text-shadow:0 0 8px var(--green)}

/* ── TECH BADGES ── */
.stack-section{margin-bottom:18px}
.stack-label{
  font-size:0.68rem;color:var(--muted);
  text-transform:uppercase;letter-spacing:2px;
  margin-bottom:8px;
}
.badges{display:flex;flex-wrap:wrap;gap:7px}

.badge{
  display:inline-flex;align-items:center;gap:6px;
  padding:5px 12px;
  border:1px solid;
  border-radius:2px;
  font-size:0.78rem;
  font-family:'Share Tech Mono',monospace;
  transition:all 0.2s;
  position:relative;
  overflow:hidden;
}
.badge::before{
  content:'';
  position:absolute;
  top:-100%;left:0;width:100%;height:100%;
  background:linear-gradient(transparent,rgba(0,255,65,0.1),transparent);
  transition:top 0.3s;
}
.badge:hover::before{top:100%}
.badge:hover{
  transform:translateY(-2px) scale(1.03);
  box-shadow:0 0 12px currentColor;
}
.badge img{width:14px;height:14px;object-fit:contain}

.b-html{color:#f87171;border-color:rgba(248,113,113,0.3);background:rgba(248,113,113,0.05)}
.b-css{color:#60a5fa;border-color:rgba(96,165,250,0.3);background:rgba(96,165,250,0.05)}
.b-js{color:#fde047;border-color:rgba(253,224,71,0.3);background:rgba(253,224,71,0.05)}
.b-react{color:#7dd3fc;border-color:rgba(125,211,252,0.3);background:rgba(125,211,252,0.05)}
.b-node{color:#86efac;border-color:rgba(134,239,172,0.3);background:rgba(134,239,172,0.05)}
.b-cpp{color:#a5b4fc;border-color:rgba(165,180,252,0.3);background:rgba(165,180,252,0.05)}
.b-java{color:#fb923c;border-color:rgba(251,146,60,0.3);background:rgba(251,146,60,0.05)}
.b-git{color:#fca5a5;border-color:rgba(252,165,165,0.3);background:rgba(252,165,165,0.05)}
.b-gh{color:#e2e8f0;border-color:rgba(226,232,240,0.2);background:rgba(226,232,240,0.03)}
.b-vsc{color:#67e8f9;border-color:rgba(103,232,249,0.3);background:rgba(103,232,249,0.05)}
.b-post{color:#fdba74;border-color:rgba(253,186,116,0.3);background:rgba(253,186,116,0.05)}

/* ── PROJECT CARD ── */
.project-card{
  background:#000a00;
  border:1px solid var(--border);
  border-radius:2px;
  padding:20px 22px;
  position:relative;
  overflow:hidden;
  transition:border-color 0.3s,box-shadow 0.3s;
}
.project-card::before{
  content:'';
  position:absolute;
  top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,var(--green),transparent);
  animation:scanBeam 3s linear infinite;
}
@keyframes scanBeam{
  0%{transform:scaleX(0);transform-origin:left}
  50%{transform:scaleX(1);transform-origin:left}
  50.01%{transform:scaleX(1);transform-origin:right}
  100%{transform:scaleX(0);transform-origin:right}
}
.project-card:hover{
  border-color:var(--green);
  box-shadow:0 0 25px rgba(0,255,65,0.12);
}
.project-name{
  font-family:'Orbitron',monospace;
  font-size:0.9rem;
  font-weight:700;
  color:var(--green);
  margin-bottom:6px;
  text-shadow:0 0 8px var(--green);
}
.project-desc{font-size:0.85rem;color:var(--text);line-height:1.6}

/* ── STATS ── */
.stats-grid{
  display:grid;
  grid-template-columns:1fr 1fr 1fr;
  gap:10px;
}
.stats-grid img{
  width:100%;
  border-radius:2px;
  border:1px solid var(--border);
  transition:border-color 0.3s,box-shadow 0.3s;
  filter:hue-rotate(0deg);
  animation:hueShift 10s linear infinite;
}
@keyframes hueShift{
  0%{filter:hue-rotate(0deg) brightness(0.9)}
  50%{filter:hue-rotate(30deg) brightness(1)}
  100%{filter:hue-rotate(0deg) brightness(0.9)}
}
.stats-grid img:hover{
  border-color:var(--green);
  box-shadow:0 0 20px rgba(0,255,65,0.2);
}

/* ── CONNECT ── */
.connect-grid{
  display:flex;flex-wrap:wrap;gap:10px;justify-content:center;
}
.connect-link{
  display:inline-flex;align-items:center;gap:8px;
  padding:10px 20px;
  border:1px solid var(--border);
  border-radius:2px;
  font-family:'Share Tech Mono',monospace;
  font-size:0.82rem;
  text-decoration:none;
  color:var(--green);
  background:#000d00;
  transition:all 0.25s;
  position:relative;
  overflow:hidden;
}
.connect-link::after{
  content:'';
  position:absolute;
  bottom:0;left:0;width:0;height:1px;
  background:var(--green);
  transition:width 0.3s;
  box-shadow:0 0 8px var(--green);
}
.connect-link:hover::after{width:100%}
.connect-link:hover{
  border-color:var(--green);
  color:#fff;
  text-shadow:0 0 8px var(--green);
  box-shadow:0 0 20px rgba(0,255,65,0.15);
  transform:translateY(-2px);
}
.connect-link .ico{font-size:1rem}

/* ── MOTTO ── */
.motto{
  text-align:center;padding:28px;
  font-family:'VT323',monospace;
  font-size:1.8rem;
  color:var(--amber);
  text-shadow:0 0 15px var(--amber);
  letter-spacing:2px;
  position:relative;
}
.motto::before{
  content:'> ';
  color:var(--green);
  animation:blink 1s step-end infinite;
}
.motto-text{
  display:inline-block;
  animation:mottoGlow 3s ease-in-out infinite alternate;
}
@keyframes mottoGlow{
  from{text-shadow:0 0 10px var(--amber)}
  to{text-shadow:0 0 20px var(--amber),0 0 40px var(--amber)}
}

/* ── PARTICLE CLICK ── */
.particle{
  position:fixed;
  pointer-events:none;
  z-index:9998;
  font-family:'Share Tech Mono',monospace;
  font-size:0.7rem;
  color:var(--green);
  animation:particleFly 1s ease-out forwards;
}
@keyframes particleFly{
  0%{opacity:1;transform:translate(0,0) scale(1)}
  100%{opacity:0;transform:var(--tx) scale(0.3)}
}

/* ── LOADER ── */
#loader{
  position:fixed;inset:0;
  background:var(--bg);
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  z-index:10000;
  transition:opacity 0.5s;
}
.loader-text{
  font-family:'Orbitron',monospace;
  font-size:1rem;
  color:var(--green);
  text-shadow:0 0 15px var(--green);
  letter-spacing:4px;
  margin-bottom:20px;
}
.progress-bar{
  width:300px;height:2px;
  background:#001a00;
  border:1px solid var(--green2);
  overflow:hidden;
}
.progress-fill{
  height:100%;width:0;
  background:var(--green);
  box-shadow:0 0 10px var(--green);
  animation:load 1.5s ease-in-out forwards;
}
@keyframes load{
  0%{width:0}
  60%{width:80%}
  100%{width:100%}
}
.progress-pct{
  margin-top:8px;
  font-size:0.75rem;
  color:var(--muted);
  font-family:'Share Tech Mono',monospace;
}

/* ── RESPONSIVE ── */
@media(max-width:600px){
  .about-grid{grid-template-columns:1fr}
  .stats-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<!-- Boot Loader -->
<div id="loader">
  <div class="loader-text">INITIALIZING PROFILE...</div>
  <div class="progress-bar"><div class="progress-fill"></div></div>
  <div class="progress-pct" id="pct">0%</div>
</div>

<!-- Matrix Rain Canvas -->
<canvas id="matrix-canvas"></canvas>

<div class="container" id="main" style="opacity:0">

  <!-- ── HERO ── -->
  <div class="terminal hero-term">
    <div class="term-bar">
      <div class="term-dots">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
      </div>
      <div class="term-title">~/samim/profile.sh</div>
    </div>
    <div class="term-body">
      <div class="ascii-frame" id="ascii-art">loading avatar...</div>

      <div class="glitch-title" data-text="HI, I'M SAMIM">HI, I'M SAMIM <span style="display:inline-block;animation:wave 2s ease-in-out infinite;font-family:sans-serif">👋</span></div>
      <div class="role-line">// Full Stack Developer</div>

      <div class="views-badge">
        <div class="ping"></div>
        <span>Profile views active — samim-t</span>
        <span class="cursor"></span>
      </div>
    </div>
  </div>

  <!-- ── ABOUT ── -->
  <div class="terminal">
    <div class="term-bar">
      <div class="term-dots"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <div class="term-title">cat about.json</div>
    </div>
    <div class="term-body">
      <div class="sec-title"><span>👨‍💻</span> About Me</div>
      <div class="about-grid">
        <div class="about-row">
          <div class="row-icon">🎓</div>
          <div><div class="row-key">Education</div><div class="row-val">B.Tech CSE — MDU Rohtak</div></div>
        </div>
        <div class="about-row">
          <div class="row-icon">🔭</div>
          <div><div class="row-key">Working On</div><div class="row-val">Exploring new ideas</div></div>
        </div>
        <div class="about-row">
          <div class="row-icon">🌱</div>
          <div><div class="row-key">Learning</div><div class="row-val">Python &amp; AI</div></div>
        </div>
        <div class="about-row">
          <div class="row-icon">💬</div>
          <div><div class="row-key">Ask Me About</div><div class="row-val">HTML · CSS · JS · React · Node · Java · C++</div></div>
        </div>
        <div class="about-row">
          <div class="row-icon">📫</div>
          <div><div class="row-key">Email</div><div class="row-val"><a href="mailto:samim13093@gmail.com">samim13093@gmail.com</a></div></div>
        </div>
        <div class="about-row">
          <div class="row-icon">⚡</div>
          <div><div class="row-key">Fun Fact</div><div class="row-val">I enjoy Drawing ✏️</div></div>
        </div>
      </div>
    </div>
  </div>

  <!-- ── TECH STACK ── -->
  <div class="terminal">
    <div class="term-bar">
      <div class="term-dots"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <div class="term-title">ls tech-stack/</div>
    </div>
    <div class="term-body">
      <div class="sec-title"><span>🛠️</span> Tech Stack</div>

      <div class="stack-section">
        <div class="stack-label">// Frontend</div>
        <div class="badges">
          <span class="badge b-html">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg"> HTML5
          </span>
          <span class="badge b-css">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg"> CSS3
          </span>
          <span class="badge b-js">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg"> JavaScript
          </span>
          <span class="badge b-react">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg"> React
          </span>
        </div>
      </div>

      <div class="stack-section">
        <div class="stack-label">// Programming</div>
        <div class="badges">
          <span class="badge b-cpp">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg"> C++
          </span>
          <span class="badge b-java">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg"> Java
          </span>
        </div>
      </div>

      <div class="stack-section">
        <div class="stack-label">// Backend</div>
        <div class="badges">
          <span class="badge b-node">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg"> Node.js
          </span>
        </div>
      </div>

      <div class="stack-section">
        <div class="stack-label">// Tools</div>
        <div class="badges">
          <span class="badge b-git">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg"> Git
          </span>
          <span class="badge b-gh">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg"> GitHub
          </span>
          <span class="badge b-vsc">
            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg"> VS Code
          </span>
          <span class="badge b-post" style="font-size:0.78rem">📮 Postman</span>
        </div>
      </div>
    </div>
  </div>

  <!-- ── PROJECTS ── -->
  <div class="terminal">
    <div class="term-bar">
      <div class="term-dots"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <div class="term-title">git log --oneline projects/</div>
    </div>
    <div class="term-body">
      <div class="sec-title"><span>🚀</span> Projects</div>
      <div class="project-card">
        <div class="project-name">💻 Java &amp; C++ Programs</div>
        <div class="project-desc">Problem-solving with Java and C++ — data structures, algorithms, and core CS fundamentals.</div>
      </div>
    </div>
  </div>

  <!-- ── GITHUB STATS ── -->
  <div class="terminal">
    <div class="term-bar">
      <div class="term-dots"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <div class="term-title">curl github-stats/ashraful-alom-1</div>
    </div>
    <div class="term-body">
      <div class="sec-title"><span>📊</span> GitHub Stats</div>
      <div class="stats-grid">
        <img src="https://github-readme-stats.vercel.app/api?username=ashraful-alom-1&show_icons=true&theme=chartreuse-dark&hide_border=true&bg_color=00000000&title_color=00ff41&icon_color=00ff41&text_color=b8ffb8" alt="GitHub Stats" loading="lazy"/>
        <img src="https://github-readme-streak-stats.herokuapp.com?user=ashraful-alom-1&theme=terminal&hide_border=true&background=00000000&ring=00ff41&fire=ffb800&currStreakLabel=00ff41" alt="GitHub Streak" loading="lazy"/>
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ashraful-alom-1&layout=compact&theme=chartreuse-dark&hide_border=true&bg_color=00000000&title_color=00ff41&text_color=b8ffb8" alt="Top Languages" loading="lazy"/>
      </div>
    </div>
  </div>

  <!-- ── CONNECT ── -->
  <div class="terminal">
    <div class="term-bar">
      <div class="term-dots"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <div class="term-title">ssh connect@samim</div>
    </div>
    <div class="term-body">
      <div class="sec-title"><span>📡</span> Connect With Me</div>
      <div class="connect-grid">
        <a class="connect-link" href="https://www.linkedin.com/in/fulbabu-islam-96a9ba2ba" target="_blank">
          <span class="ico">🔗</span> LinkedIn
        </a>
        <a class="connect-link" href="mailto:fulbabui74@gmail.com">
          <span class="ico">📧</span> Gmail
        </a>
        <a class="connect-link" href="https://github.com/fulbabu-t" target="_blank">
          <span class="ico">🐙</span> GitHub
        </a>
        <a class="connect-link" href="#">
          <span class="ico">🌐</span> Portfolio
        </a>
      </div>
    </div>
  </div>

  <!-- ── MOTTO ── -->
  <div class="terminal">
    <div class="term-bar">
      <div class="term-dots"><div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div></div>
      <div class="term-title">echo $MOTTO</div>
    </div>
    <div class="term-body">
      <div class="motto"><span class="motto-text">"Build" → "Break" → "Learn" → "Repeat"</span></div>
    </div>
  </div>

</div><!-- /container -->

<script>
/* ── MATRIX RAIN ── */
const canvas = document.getElementById('matrix-canvas');
const ctx = canvas.getContext('2d');
function resizeCanvas(){canvas.width=window.innerWidth;canvas.height=window.innerHeight}
resizeCanvas();
window.addEventListener('resize',resizeCanvas);

const chars='アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン0123456789ABCDEF<>{}[]();';
const fontSize=14;
let cols=Math.floor(canvas.width/fontSize);
let drops=Array(cols).fill(1);

function drawMatrix(){
  ctx.fillStyle='rgba(0,5,0,0.05)';
  ctx.fillRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle='#00ff41';
  ctx.font=fontSize+'px Share Tech Mono,monospace';
  for(let i=0;i<drops.length;i++){
    const ch=chars[Math.floor(Math.random()*chars.length)];
    ctx.fillStyle=drops[i]*fontSize<50?'#00ffff':'#00ff41';
    ctx.fillText(ch,i*fontSize,drops[i]*fontSize);
    if(drops[i]*fontSize>canvas.height&&Math.random()>0.975) drops[i]=0;
    drops[i]++;
  }
}
setInterval(drawMatrix,50);

/* ── ASCII AVATAR ── */
const asciiFrames=[
`  ╔══════════╗
  ║  ◉    ◉  ║
  ║    ▽▽    ║
  ║  ╰────╯  ║
  ╚══════════╝`,
`  ╔══════════╗
  ║  ◎    ◎  ║
  ║    ▿▿    ║
  ║  ╰────╯  ║
  ╚══════════╝`,
`  ╔══════════╗
  ║  ○    ○  ║
  ║    ▾▾    ║
  ║  ╰────╯  ║
  ╚══════════╝`,
];
let fi=0;
const asciiEl=document.getElementById('ascii-art');
setInterval(()=>{
  fi=(fi+1)%asciiFrames.length;
  asciiEl.textContent=asciiFrames[fi];
},600);

/* ── BOOT LOADER ── */
const loader=document.getElementById('loader');
const pct=document.getElementById('pct');
const main=document.getElementById('main');
let p=0;
const iv=setInterval(()=>{
  p=Math.min(p+Math.random()*4+1,100);
  pct.textContent=Math.floor(p)+'%';
  if(p>=100){
    clearInterval(iv);
    setTimeout(()=>{
      loader.style.opacity='0';
      setTimeout(()=>{
        loader.style.display='none';
        main.style.opacity='1';
        main.style.transition='opacity 0.5s';
      },500);
    },300);
  }
},40);

/* ── CLICK PARTICLES ── */
const symbols=['0','1','</>','{}','[]','//','&&','||','!=','=>'];
document.addEventListener('click',e=>{
  for(let i=0;i<8;i++){
    const el=document.createElement('div');
    el.className='particle';
    el.textContent=symbols[Math.floor(Math.random()*symbols.length)];
    const angle=Math.random()*Math.PI*2;
    const dist=60+Math.random()*80;
    el.style.cssText=`left:${e.clientX}px;top:${e.clientY}px;--tx:translate(${Math.cos(angle)*dist}px,${Math.sin(angle)*dist}px)`;
    el.style.color=['#00ff41','#00ffff','#ffb800','#ff2244'][Math.floor(Math.random()*4)];
    document.body.appendChild(el);
    setTimeout(()=>el.remove(),1000);
  }
});

/* ── TYPED PROMPT (hero) ── */
// Stagger about rows
document.querySelectorAll('.about-row').forEach((r,i)=>{
  r.style.animationDelay=(0.1+i*0.07)+'s';
});
</script>
</body>
</html>
