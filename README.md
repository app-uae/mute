<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ميوت — استعِد صمتك</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@200;300;400;500;700;800;900&family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">

<style>
/* ═══════════════════════════════════════════
   RESET & BASE
═══════════════════════════════════════════ */
*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

:root {
  --void: #03050C;
  --deep: #060B18;
  --surface: #0A1020;
  --card: #0F1830;
  --border: #1A2D50;
  --border-glow: rgba(0,210,175,0.25);

  --teal: #00D2AF;
  --teal-dim: rgba(0,210,175,0.08);
  --teal-mid: rgba(0,210,175,0.18);
  --blue: #3D8EFF;
  --blue-dim: rgba(61,142,255,0.1);
  --amber: #F5A623;
  --rose: #FF6B8A;
  --violet: #9B6EFF;

  --text-primary: #EDF2FC;
  --text-secondary: #7A9CC4;
  --text-muted: #3D5A80;

  --font-display: 'Playfair Display', serif;
  --font-arabic: 'Tajawal', sans-serif;
  --font-mono: 'Space Mono', monospace;
}

html { scroll-behavior: smooth; }

body {
  font-family: var(--font-arabic);
  background: var(--void);
  color: var(--text-primary);
  overflow-x: hidden;
  cursor: none;
}

/* ── Custom Cursor ── */
.cursor {
  position: fixed; top: 0; left: 0;
  width: 12px; height: 12px;
  background: var(--teal);
  border-radius: 50%;
  pointer-events: none; z-index: 9999;
  transform: translate(-50%, -50%);
  transition: transform 0.1s, width 0.3s, height 0.3s, opacity 0.3s;
  mix-blend-mode: screen;
}
.cursor-ring {
  position: fixed; top: 0; left: 0;
  width: 36px; height: 36px;
  border: 1.5px solid rgba(0,210,175,0.4);
  border-radius: 50%;
  pointer-events: none; z-index: 9998;
  transform: translate(-50%, -50%);
  transition: transform 0.15s ease-out, width 0.3s, height 0.3s;
}
body:has(a:hover) .cursor { width:6px; height:6px; }
body:has(button:hover) .cursor { width:20px; height:20px; }

/* ── Starfield Canvas ── */
#starCanvas {
  position: fixed; inset: 0;
  z-index: 0; pointer-events: none;
}

/* ═══════════════════════════════════════════
   NAV
═══════════════════════════════════════════ */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100;
  padding: 0 5%;
  display: flex; align-items: center; justify-content: space-between;
  height: 70px;
  background: rgba(3,5,12,0.7);
  backdrop-filter: blur(24px);
  border-bottom: 1px solid rgba(0,210,175,0.08);
}
.nav-logo {
  font-family: var(--font-mono);
  font-size: 22px; font-weight: 700;
  letter-spacing: 5px; color: var(--teal);
  text-decoration: none;
  display: flex; align-items: center; gap: 10px;
}
.nav-logo-icon {
  width: 34px; height: 34px; border-radius: 10px;
  background: linear-gradient(135deg, var(--teal), var(--blue));
  display: flex; align-items: center; justify-content: center;
  font-size: 16px;
  box-shadow: 0 0 20px rgba(0,210,175,0.3);
}
.nav-links {
  display: flex; align-items: center; gap: 36px;
  list-style: none;
}
.nav-links a {
  color: var(--text-secondary); text-decoration: none;
  font-size: 15px; font-weight: 500;
  transition: color 0.3s;
  position: relative;
}
.nav-links a::after {
  content:''; position:absolute; bottom:-2px; right:0; left:100%;
  height:1px; background: var(--teal);
  transition: left 0.3s;
}
.nav-links a:hover { color: var(--teal); }
.nav-links a:hover::after { left:0; }
.nav-cta {
  padding: 9px 22px; border-radius: 24px;
  background: transparent;
  border: 1px solid rgba(0,210,175,0.5);
  color: var(--teal) !important; font-family: var(--font-arabic);
  font-size: 14px; font-weight: 700; cursor: pointer;
  transition: all 0.3s !important;
}
.nav-cta:hover {
  background: rgba(0,210,175,0.12) !important;
  box-shadow: 0 0 20px rgba(0,210,175,0.2) !important;
}
.nav-cta::after { display:none !important; }

/* ═══════════════════════════════════════════
   HERO
═══════════════════════════════════════════ */
#hero {
  min-height: 100vh;
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  position: relative; z-index: 1;
  text-align: center;
  padding: 120px 5% 80px;
  overflow: hidden;
}

.hero-ambient {
  position: absolute; inset: 0; pointer-events: none;
}
.ambient-ring {
  position: absolute; border-radius: 50%;
  border: 1px solid rgba(0,210,175,0.06);
  left: 50%; top: 50%;
  transform: translate(-50%,-50%);
}
.ambient-ring:nth-child(1) { width: 300px; height: 300px; animation: ringPulse 8s ease-in-out infinite; }
.ambient-ring:nth-child(2) { width: 500px; height: 500px; animation: ringPulse 8s ease-in-out infinite 1s; }
.ambient-ring:nth-child(3) { width: 750px; height: 750px; animation: ringPulse 8s ease-in-out infinite 2s; }
.ambient-ring:nth-child(4) { width: 1050px; height: 1050px; animation: ringPulse 8s ease-in-out infinite 3s; }

@keyframes ringPulse {
  0%,100% { opacity:0.4; transform:translate(-50%,-50%) scale(1); }
  50% { opacity:0.8; transform:translate(-50%,-50%) scale(1.02); }
}

.hero-glow {
  position: absolute; width: 700px; height: 700px;
  background: radial-gradient(circle, rgba(0,210,175,0.06) 0%, transparent 70%);
  left: 50%; top: 50%; transform: translate(-50%,-50%);
  pointer-events: none;
}

.hero-badge {
  display: inline-flex; align-items: center; gap: 8px;
  background: rgba(0,210,175,0.07);
  border: 1px solid rgba(0,210,175,0.25);
  border-radius: 30px;
  padding: 7px 18px;
  font-size: 13px; color: var(--teal);
  font-family: var(--font-mono);
  margin-bottom: 36px;
  animation: fadeDown 1s ease 0.2s both;
}
.badge-pulse { width: 7px; height: 7px; border-radius: 50%; background: var(--teal); animation: badgePulse 2s infinite; }
@keyframes badgePulse { 0%,100%{box-shadow:0 0 0 0 rgba(0,210,175,0.5)} 50%{box-shadow:0 0 0 6px rgba(0,210,175,0)} }

.hero-eyebrow {
  font-size: clamp(13px,1.5vw,16px);
  color: var(--teal); font-family: var(--font-mono);
  letter-spacing: 4px; text-transform: uppercase;
  margin-bottom: 16px;
  animation: fadeDown 1s ease 0.4s both;
}

.hero-h1 {
  font-family: var(--font-display);
  font-size: clamp(52px,7vw,96px);
  font-weight: 900; line-height: 1.05;
  margin-bottom: 12px;
  animation: fadeDown 1s ease 0.6s both;
}
.hero-h1 em {
  font-style: italic; color: var(--teal);
  text-shadow: 0 0 60px rgba(0,210,175,0.4);
}

.hero-h1-ar {
  font-family: var(--font-arabic);
  font-size: clamp(28px,4vw,52px);
  font-weight: 300; color: var(--text-secondary);
  margin-bottom: 36px; letter-spacing: -0.5px;
  animation: fadeDown 1s ease 0.8s both;
}
.hero-h1-ar strong { color: var(--text-primary); font-weight: 700; }

.hero-desc {
  max-width: 560px;
  font-size: clamp(15px,1.8vw,18px);
  color: var(--text-secondary); line-height: 1.8;
  margin: 0 auto 48px;
  font-weight: 300;
  animation: fadeDown 1s ease 1s both;
}

.hero-actions {
  display: flex; align-items: center; gap: 16px; justify-content: center;
  flex-wrap: wrap;
  animation: fadeDown 1s ease 1.2s both;
}
.btn-primary {
  padding: 16px 36px; border-radius: 50px;
  background: linear-gradient(135deg, var(--teal), var(--blue));
  border: none; color: white;
  font-family: var(--font-arabic); font-size: 16px; font-weight: 700;
  cursor: pointer; position: relative; overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
  box-shadow: 0 8px 32px rgba(0,210,175,0.3);
}
.btn-primary::before {
  content:''; position:absolute; inset:0;
  background: linear-gradient(135deg, rgba(255,255,255,0.2), transparent);
  opacity: 0; transition: opacity 0.3s;
}
.btn-primary:hover { transform: translateY(-2px); box-shadow: 0 16px 48px rgba(0,210,175,0.4); }
.btn-primary:hover::before { opacity:1; }
.btn-secondary {
  padding: 15px 32px; border-radius: 50px;
  background: transparent; border: 1px solid var(--border);
  color: var(--text-secondary);
  font-family: var(--font-arabic); font-size: 16px; font-weight: 500;
  cursor: pointer; transition: all 0.3s;
}
.btn-secondary:hover { border-color: rgba(0,210,175,0.4); color: var(--teal); }

.hero-social-proof {
  margin-top: 60px;
  display: flex; align-items: center; gap: 20px; justify-content: center;
  animation: fadeDown 1s ease 1.4s both;
}
.proof-avatars { display: flex; }
.proof-avatar {
  width: 32px; height: 32px; border-radius: 50%;
  border: 2px solid var(--void);
  margin-left: -8px; font-size: 16px;
  display: flex; align-items: center; justify-content: center;
  background: var(--card);
}
.proof-text { font-size: 13px; color: var(--text-muted); }
.proof-text strong { color: var(--teal); }

.hero-scroll {
  position: absolute; bottom: 40px; left: 50%; transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 8px;
  animation: fadeDown 1s ease 2s both;
}
.scroll-line {
  width: 1px; height: 50px;
  background: linear-gradient(180deg, transparent, var(--teal), transparent);
  animation: scrollLine 2s ease-in-out infinite;
}
@keyframes scrollLine { 0%,100%{opacity:0.3} 50%{opacity:1} }
.scroll-label { font-size: 10px; color: var(--text-muted); font-family: var(--font-mono); letter-spacing: 3px; }

@keyframes fadeDown { from{opacity:0;transform:translateY(-20px)} to{opacity:1;transform:translateY(0)} }

/* ═══════════════════════════════════════════
   STATS STRIP
═══════════════════════════════════════════ */
.stats-strip {
  position: relative; z-index: 1;
  padding: 60px 5%;
  border-top: 1px solid var(--border);
  border-bottom: 1px solid var(--border);
  background: linear-gradient(180deg, var(--void), var(--deep));
  display: flex; align-items: center; justify-content: center;
  flex-wrap: wrap; gap: 0;
}
.stat-item {
  flex: 1; min-width: 160px;
  text-align: center; padding: 20px 32px;
  border-left: 1px solid var(--border);
  position: relative; overflow: hidden;
}
.stat-item:last-child { border-left: none; }
.stat-item::before {
  content:''; position:absolute; top:0; left:50%; transform:translateX(-50%);
  width:1px; height:40px;
  background: linear-gradient(180deg, transparent, var(--teal));
  opacity: 0; transition: opacity 0.4s;
}
.stat-item:hover::before { opacity:0.6; }
.stat-num {
  font-family: var(--font-mono);
  font-size: 42px; font-weight: 700;
  background: linear-gradient(135deg, var(--teal), var(--blue));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  line-height: 1;
}
.stat-label { font-size: 13px; color: var(--text-muted); margin-top: 8px; }

/* ═══════════════════════════════════════════
   PROBLEM SECTION
═══════════════════════════════════════════ */
#problem {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--deep);
  overflow: hidden;
}
.problem-bg-text {
  position: absolute;
  font-family: var(--font-mono);
  font-size: 200px; font-weight: 700;
  color: rgba(255,255,255,0.015);
  top: 50%; left: 50%; transform: translate(-50%,-50%);
  white-space: nowrap; pointer-events: none;
  letter-spacing: -10px;
}
.section-label {
  font-family: var(--font-mono); font-size: 12px;
  color: var(--teal); letter-spacing: 5px; text-transform: uppercase;
  margin-bottom: 20px; display: flex; align-items: center; gap: 12px;
}
.section-label::before {
  content:''; display:block; width:30px; height:1px; background: var(--teal);
}
.section-h2 {
  font-family: var(--font-display);
  font-size: clamp(36px,5vw,64px);
  font-weight: 900; line-height: 1.1; margin-bottom: 24px;
}
.section-h2 .accent { color: var(--teal); }
.section-body {
  font-size: 17px; color: var(--text-secondary);
  line-height: 1.9; max-width: 560px; font-weight: 300;
}

.problem-grid {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 60px; align-items: center; max-width: 1100px; margin: 0 auto;
}
.problem-cards {
  display: flex; flex-direction: column; gap: 16px;
}
.problem-card {
  padding: 24px;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 16px;
  display: flex; align-items: flex-start; gap: 16px;
  transition: all 0.4s;
  cursor: default;
}
.problem-card:hover {
  border-color: rgba(0,210,175,0.3);
  background: rgba(0,210,175,0.04);
  transform: translateX(-6px);
}
.pc-icon {
  width: 42px; height: 42px; border-radius: 12px; flex-shrink: 0;
  display: flex; align-items: center; justify-content: center; font-size: 20px;
}
.pc-num {
  font-family: var(--font-mono); font-size: 32px; font-weight: 700;
  line-height: 1;
}
.pc-label { font-size: 14px; color: var(--text-muted); margin-top: 2px; }

/* ═══════════════════════════════════════════
   SOLUTION / FEATURES
═══════════════════════════════════════════ */
#solution {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--void);
}
.features-intro { max-width: 600px; margin-bottom: 72px; }

.features-grid {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 2px;
  background: var(--border);
  border: 1px solid var(--border);
  border-radius: 20px; overflow: hidden;
  max-width: 1100px;
}
.feature-card {
  padding: 40px 32px;
  background: var(--void);
  transition: all 0.4s;
  cursor: default; position: relative; overflow: hidden;
}
.feature-card::before {
  content:''; position:absolute; bottom:0; left:0; right:0;
  height:2px; background: var(--gradient, linear-gradient(90deg, var(--teal), var(--blue)));
  transform: scaleX(0); transform-origin: left;
  transition: transform 0.4s;
}
.feature-card:hover { background: var(--card); }
.feature-card:hover::before { transform: scaleX(1); }

.fc-icon {
  width: 52px; height: 52px; border-radius: 16px;
  display: flex; align-items: center; justify-content: center; font-size: 24px;
  margin-bottom: 20px;
}
.fc-title { font-size: 18px; font-weight: 700; margin-bottom: 10px; }
.fc-desc { font-size: 14px; color: var(--text-muted); line-height: 1.7; }
.fc-tag {
  display: inline-block; margin-top: 14px;
  font-size: 11px; padding: 3px 10px; border-radius: 20px;
  font-family: var(--font-mono);
}

/* ═══════════════════════════════════════════
   APP PREVIEW
═══════════════════════════════════════════ */
#preview {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--deep);
  overflow: hidden;
}
.preview-glow {
  position: absolute;
  width: 800px; height: 800px;
  background: radial-gradient(circle, rgba(61,142,255,0.05), transparent 70%);
  top: 50%; right: -200px; transform: translateY(-50%);
  pointer-events: none;
}
.preview-layout {
  display: flex; align-items: center; gap: 80px;
  max-width: 1100px; margin: 0 auto;
}
.preview-phones {
  position: relative; flex-shrink: 0; width: 380px; height: 520px;
}
.preview-phone {
  position: absolute;
  width: 220px; height: 440px;
  border-radius: 32px;
  overflow: hidden;
  border: 1.5px solid var(--border-glow);
  box-shadow: 0 30px 80px rgba(0,0,0,0.7), 0 0 40px rgba(0,210,175,0.08);
  background: var(--card);
  display: flex; flex-direction: column;
}
.preview-phone:nth-child(1) { right: 80px; top: 0; z-index: 3; transform: rotate(-3deg); }
.preview-phone:nth-child(2) { right: 0; top: 40px; z-index: 2; transform: rotate(4deg); opacity: 0.8; }
.preview-phone:nth-child(3) { right: 150px; top: 60px; z-index: 1; transform: rotate(-6deg); opacity: 0.5; }

.pp-header {
  padding: 20px 16px 12px;
  background: linear-gradient(180deg, var(--surface), transparent);
}
.pp-status { font-family: var(--font-mono); font-size: 9px; color: var(--text-muted); display: flex; justify-content: space-between; margin-bottom: 10px; }
.pp-title { font-size: 14px; font-weight: 700; color: var(--text-primary); }
.pp-sub { font-size: 11px; color: var(--teal); margin-top: 2px; }

.pp-ring-area {
  display: flex; justify-content: center; padding: 16px;
}
.pp-ring-svg { transform: rotate(-90deg); }
.pp-ring-svg circle { fill: none; stroke-width: 6; stroke-linecap: round; }
.ring-bg-pp { stroke: var(--border); }
.ring-fg-pp { stroke: var(--teal); stroke-dasharray: 188; stroke-dashoffset: 75; }

.pp-stats {
  display: flex; gap: 8px; padding: 0 14px;
}
.pp-stat { flex: 1; padding: 10px 8px; background: rgba(255,255,255,0.03); border-radius: 10px; border: 1px solid var(--border); text-align: center; }
.pp-stat-v { font-size: 14px; font-weight: 800; }
.pp-stat-l { font-size: 9px; color: var(--text-muted); margin-top: 2px; }

.pp-nav {
  margin-top: auto;
  display: flex; justify-content: space-around;
  padding: 10px 0 14px;
  border-top: 1px solid var(--border);
  background: rgba(6,11,24,0.9);
}
.pp-nav-i { font-size: 18px; opacity: 0.4; }
.pp-nav-i.active { opacity: 1; filter: drop-shadow(0 0 4px var(--teal)); }

.preview-text { flex: 1; }
.preview-features { margin-top: 36px; display: flex; flex-direction: column; gap: 16px; }
.pf-item {
  display: flex; align-items: center; gap: 14px;
  padding: 14px 18px;
  background: var(--card); border-radius: 12px;
  border: 1px solid var(--border);
  transition: all 0.3s;
}
.pf-item:hover { border-color: rgba(0,210,175,0.3); transform: translateX(-4px); }
.pf-icon { font-size: 20px; }
.pf-text { font-size: 14px; font-weight: 500; }
.pf-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--teal); margin-right: auto; flex-shrink: 0; }

/* ═══════════════════════════════════════════
   HOW IT WORKS
═══════════════════════════════════════════ */
#how {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--void);
}
.steps-container { max-width: 900px; margin: 0 auto; }
.step-row {
  display: flex; gap: 40px; align-items: flex-start;
  padding: 48px 0; border-bottom: 1px solid var(--border);
  position: relative;
}
.step-row:last-child { border-bottom: none; }
.step-num {
  font-family: var(--font-mono); font-size: 64px; font-weight: 700;
  color: rgba(0,210,175,0.08); line-height: 1; flex-shrink: 0; width: 80px;
  transition: color 0.4s;
}
.step-row:hover .step-num { color: rgba(0,210,175,0.2); }
.step-content { flex: 1; padding-top: 8px; }
.step-icon { font-size: 28px; margin-bottom: 12px; }
.step-title { font-size: 22px; font-weight: 700; margin-bottom: 10px; }
.step-desc { font-size: 15px; color: var(--text-secondary); line-height: 1.8; }
.step-tag {
  display: inline-block; margin-top: 12px;
  font-family: var(--font-mono); font-size: 11px;
  color: var(--teal); background: var(--teal-dim); border: 1px solid rgba(0,210,175,0.2);
  padding: 4px 12px; border-radius: 20px;
}

/* ═══════════════════════════════════════════
   TESTIMONIALS
═══════════════════════════════════════════ */
#testimonials {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--deep);
  overflow: hidden;
}
.test-track {
  display: flex; gap: 24px; overflow-x: auto;
  padding-bottom: 20px; scroll-snap-type: x mandatory;
  scrollbar-width: none;
}
.test-track::-webkit-scrollbar { display:none; }
.test-card {
  min-width: 320px; padding: 32px;
  background: var(--card); border-radius: 20px;
  border: 1px solid var(--border);
  scroll-snap-align: start; flex-shrink: 0;
  transition: all 0.4s; cursor: default;
}
.test-card:hover { border-color: rgba(0,210,175,0.25); transform: translateY(-4px); }
.test-stars { color: var(--amber); font-size: 14px; margin-bottom: 16px; }
.test-quote {
  font-size: 15px; color: var(--text-secondary); line-height: 1.8;
  margin-bottom: 20px; font-weight: 300;
  font-family: var(--font-display); font-style: italic;
}
.test-author { display: flex; align-items: center; gap: 12px; }
.test-avatar { width: 40px; height: 40px; border-radius: 50%; font-size: 20px; display: flex; align-items: center; justify-content: center; }
.test-name { font-size: 14px; font-weight: 700; }
.test-role { font-size: 12px; color: var(--text-muted); }
.test-result { font-size: 12px; color: var(--teal); margin-top: 2px; font-weight: 600; }

/* ═══════════════════════════════════════════
   PRICING
═══════════════════════════════════════════ */
#pricing {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--void);
}
.pricing-grid {
  display: flex; gap: 20px; justify-content: center; max-width: 900px; margin: 0 auto; flex-wrap: wrap;
}
.price-card {
  flex: 1; min-width: 240px; max-width: 300px;
  padding: 40px 32px; border-radius: 20px;
  border: 1px solid var(--border);
  background: var(--card);
  text-align: center; transition: all 0.4s;
  position: relative; overflow: hidden;
}
.price-card.featured {
  border-color: rgba(0,210,175,0.5);
  background: linear-gradient(180deg, rgba(0,210,175,0.07), var(--card));
  transform: scale(1.04);
}
.price-card.featured::before {
  content:''; position:absolute; top:0; left:0; right:0;
  height:2px; background: linear-gradient(90deg, var(--teal), var(--blue));
}
.price-badge {
  position: absolute; top: 16px; right: 16px;
  font-size: 11px; padding: 3px 10px; border-radius: 20px;
  background: rgba(0,210,175,0.15); color: var(--teal);
  font-family: var(--font-mono);
}
.price-plan { font-size: 13px; color: var(--text-muted); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 8px; }
.price-amount {
  font-family: var(--font-mono); font-size: 48px; font-weight: 700;
  color: var(--text-primary); line-height: 1;
}
.price-amount span { font-size: 18px; color: var(--text-muted); }
.price-period { font-size: 13px; color: var(--text-muted); margin-bottom: 28px; }
.price-features { list-style: none; text-align: right; margin-bottom: 28px; }
.price-features li {
  font-size: 14px; color: var(--text-secondary);
  padding: 7px 0; border-bottom: 1px solid rgba(255,255,255,0.04);
  display: flex; align-items: center; gap: 10px;
}
.price-features li::before { content: '✓'; color: var(--teal); font-size: 12px; flex-shrink: 0; }
.price-features li.no::before { content: '—'; color: var(--text-muted); }
.price-features li.no { color: var(--text-muted); }
.btn-price {
  width: 100%; padding: 13px;
  border-radius: 30px; font-family: var(--font-arabic);
  font-size: 15px; font-weight: 700; cursor: pointer; transition: all 0.3s;
}
.btn-price-outline {
  background: transparent; border: 1px solid var(--border); color: var(--text-secondary);
}
.btn-price-outline:hover { border-color: rgba(0,210,175,0.4); color: var(--teal); }
.btn-price-fill {
  background: linear-gradient(135deg, var(--teal), var(--blue));
  border: none; color: white;
  box-shadow: 0 8px 24px rgba(0,210,175,0.25);
}
.btn-price-fill:hover { box-shadow: 0 12px 36px rgba(0,210,175,0.4); transform: translateY(-2px); }

/* ═══════════════════════════════════════════
   SCIENCE SECTION
═══════════════════════════════════════════ */
#science {
  position: relative; z-index: 1;
  padding: 120px 5%;
  background: var(--deep);
}
.science-grid {
  display: grid; grid-template-columns: 1fr 1fr 1fr;
  gap: 16px; max-width: 1000px; margin: 0 auto;
}
.science-card {
  padding: 28px; border-radius: 16px;
  border: 1px solid var(--border);
  background: var(--card); transition: all 0.4s;
}
.science-card:hover { border-color: rgba(0,210,175,0.25); transform: translateY(-4px); }
.sci-icon { font-size: 28px; margin-bottom: 12px; }
.sci-stat { font-family: var(--font-mono); font-size: 28px; font-weight: 700; color: var(--teal); margin-bottom: 6px; }
.sci-title { font-size: 14px; font-weight: 700; margin-bottom: 8px; }
.sci-source { font-size: 11px; color: var(--text-muted); font-style: italic; }

/* ═══════════════════════════════════════════
   CTA SECTION
═══════════════════════════════════════════ */
#cta {
  position: relative; z-index: 1;
  padding: 140px 5%;
  text-align: center; overflow: hidden;
  background: var(--void);
}
.cta-glow {
  position: absolute; inset: 0;
  background: radial-gradient(ellipse at 50% 50%, rgba(0,210,175,0.07), transparent 70%);
  pointer-events: none;
}
.cta-h2 {
  font-family: var(--font-display);
  font-size: clamp(40px,6vw,80px);
  font-weight: 900; line-height: 1.1;
  margin-bottom: 20px;
}
.cta-h2 em { font-style: italic; color: var(--teal); }
.cta-sub { font-size: 18px; color: var(--text-secondary); margin-bottom: 48px; font-weight: 300; }

.email-form {
  display: flex; gap: 12px; justify-content: center; flex-wrap: wrap;
}
.email-input {
  padding: 15px 24px; border-radius: 50px;
  background: var(--card); border: 1px solid var(--border);
  color: var(--text-primary); font-family: var(--font-arabic); font-size: 15px;
  min-width: 280px; outline: none; direction: rtl;
  transition: border-color 0.3s;
}
.email-input:focus { border-color: rgba(0,210,175,0.4); }
.email-input::placeholder { color: var(--text-muted); }

.cta-note { font-size: 13px; color: var(--text-muted); margin-top: 16px; }

/* ═══════════════════════════════════════════
   FOOTER
═══════════════════════════════════════════ */
footer {
  position: relative; z-index: 1;
  padding: 60px 5% 40px;
  background: var(--deep);
  border-top: 1px solid var(--border);
}
.footer-top {
  display: flex; justify-content: space-between; align-items: flex-start;
  flex-wrap: wrap; gap: 40px; margin-bottom: 48px;
}
.footer-brand .nav-logo { font-size: 20px; margin-bottom: 12px; display: inline-flex; }
.footer-brand p { font-size: 14px; color: var(--text-muted); max-width: 240px; line-height: 1.7; }
.footer-links h4 { font-size: 13px; color: var(--text-secondary); font-weight: 700; margin-bottom: 16px; letter-spacing: 1px; }
.footer-links ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
.footer-links a { font-size: 14px; color: var(--text-muted); text-decoration: none; transition: color 0.3s; }
.footer-links a:hover { color: var(--teal); }
.footer-bottom {
  display: flex; justify-content: space-between; align-items: center;
  flex-wrap: wrap; gap: 12px;
  padding-top: 24px; border-top: 1px solid var(--border);
  font-size: 13px; color: var(--text-muted);
}
.footer-bottom .teal { color: var(--teal); }

/* ═══════════════════════════════════════════
   SCROLL ANIMATIONS
═══════════════════════════════════════════ */
.reveal {
  opacity: 0; transform: translateY(30px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.reveal.visible { opacity:1; transform:translateY(0); }
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }
.reveal-delay-5 { transition-delay: 0.5s; }

/* ── Misc ── */
section { position: relative; }
.text-center { text-align: center; }
.mx-auto { margin-left: auto; margin-right: auto; }
.mb-80 { margin-bottom: 80px; }

/* ── Scroll Progress Bar ── */
#scroll-progress {
  position: fixed; top: 0; left: 0; right: 0;
  height: 2px; z-index: 9999;
  background: linear-gradient(90deg, var(--teal), var(--blue), var(--violet));
  transform-origin: left;
  transform: scaleX(0);
  transition: transform 0.05s linear;
  box-shadow: 0 0 8px rgba(0,210,175,0.6);
}

/* ── Mouse Trail ── */
.trail-dot {
  position: fixed; pointer-events: none; z-index: 9997;
  width: 5px; height: 5px; border-radius: 50%;
  background: var(--teal); mix-blend-mode: screen;
  transition: opacity 0.5s ease;
}

/* ── Silence Score Widget ── */
#silence-score {
  position: fixed; bottom: 32px; left: 32px;
  z-index: 500;
  background: rgba(10,16,32,0.85);
  backdrop-filter: blur(16px);
  border: 1px solid rgba(0,210,175,0.25);
  border-radius: 20px;
  padding: 16px 20px;
  display: flex; flex-direction: column; align-items: center;
  gap: 6px;
  opacity: 0; transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
  min-width: 120px;
  cursor: default;
}
#silence-score.visible { opacity: 1; transform: translateY(0); }
.score-label {
  font-family: var(--font-mono); font-size: 10px;
  color: var(--text-muted); letter-spacing: 3px; text-transform: uppercase;
}
.score-ring {
  position: relative; width: 64px; height: 64px;
}
.score-ring svg { transform: rotate(-90deg); }
.score-ring-bg { fill: none; stroke: rgba(0,210,175,0.1); stroke-width: 4; }
.score-ring-fg { fill: none; stroke: url(#scoreGrad); stroke-width: 4; stroke-linecap: round; transition: stroke-dashoffset 0.6s ease; }
.score-number {
  position: absolute; inset: 0;
  display: flex; align-items: center; justify-content: center;
  font-family: var(--font-mono); font-size: 18px; font-weight: 700;
  color: var(--teal);
}
.score-status {
  font-size: 11px; color: var(--text-secondary);
  text-align: center; line-height: 1.4; max-width: 100px;
}

/* ── Ripple Effect ── */
.ripple {
  position: absolute; border-radius: 50%;
  background: rgba(255,255,255,0.25);
  transform: scale(0);
  animation: rippleAnim 0.6s linear;
  pointer-events: none;
}
@keyframes rippleAnim {
  to { transform: scale(4); opacity: 0; }
}
.btn-primary, .btn-secondary, .btn-price { position: relative; overflow: hidden; }

/* ── Noise overlay ── */
body::after {
  content:''; position:fixed; inset:0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events:none; z-index:200; opacity:0.4;
}

/* Responsive */
@media(max-width:768px){
  .problem-grid, .preview-layout { flex-direction: column; gap: 40px; }
  .features-grid { grid-template-columns: 1fr; }
  .science-grid { grid-template-columns: 1fr 1fr; }
  .preview-phones { width: 260px; height: 380px; }
  .preview-phone { width: 180px; height: 360px; }
  nav .nav-links { display: none; }
  .pricing-grid { flex-direction: column; align-items: center; }
  .price-card.featured { transform: scale(1); }
}
</style>
</head>
<body>

<!-- Scroll progress bar -->
<div id="scroll-progress"></div>

<!-- Silence Score Widget -->
<div id="silence-score">
  <div class="score-label">درجة صمتك</div>
  <div class="score-ring">
    <svg width="64" height="64" viewBox="0 0 64 64">
      <defs>
        <linearGradient id="scoreGrad" x1="0%" y1="0%" x2="100%" y2="0%">
          <stop offset="0%" stop-color="#00D2AF"/>
          <stop offset="100%" stop-color="#3D8EFF"/>
        </linearGradient>
      </defs>
      <circle class="score-ring-bg" cx="32" cy="32" r="28"/>
      <circle class="score-ring-fg" id="scoreArc" cx="32" cy="32" r="28"
        stroke-dasharray="175.9" stroke-dashoffset="175.9"/>
    </svg>
    <div class="score-number" id="scoreNum">0</div>
  </div>
  <div class="score-status" id="scoreStatus">ابدأ الاستكشاف</div>
</div>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Starfield -->
<canvas id="starCanvas"></canvas>

<!-- ══ NAV ══ -->
<nav>
  <a class="nav-logo" href="#">
    <div class="nav-logo-icon">🔇</div>
    MUTE
  </a>
  <ul class="nav-links">
    <li><a href="#problem">المشكلة</a></li>
    <li><a href="#solution">الميزات</a></li>
    <li><a href="#how">كيف يعمل؟</a></li>
    <li><a href="#pricing">الأسعار</a></li>
    <li><a href="#cta" class="nav-cta">جرّبه مجاناً</a></li>
  </ul>
</nav>

<!-- ══ HERO ══ -->
<section id="hero">
  <div class="hero-ambient">
    <div class="ambient-ring"></div>
    <div class="ambient-ring"></div>
    <div class="ambient-ring"></div>
    <div class="ambient-ring"></div>
  </div>
  <div class="hero-glow"></div>

  <div class="hero-badge">
    <div class="badge-pulse"></div>
    <span id="typewriter-text"></span><span class="typewriter-cursor" style="color:var(--teal);animation:badgePulse 1s infinite">|</span>
  </div>

  <div class="hero-eyebrow">SILENCE IS A SUPERPOWER</div>

  <h1 class="hero-h1">
    Can you sit in<br><em>silence</em>?
  </h1>

  <div class="hero-h1-ar">
    معظم الشباب <strong>لا يستطيعون</strong> — وميوت يُغيّر ذلك
  </div>

  <p class="hero-desc">
    منصة علمية متكاملة تساعدك على التحرر من إدمان المحتوى الصوتي تدريجياً،
    واستعادة تركيزك وإبداعك وصحتك الذهنية.
  </p>

  <div class="hero-actions">
    <button class="btn-primary" onclick="document.getElementById('cta').scrollIntoView({behavior:'smooth'})">
      ابدأ رحلة التعافي — مجاناً
    </button>
    <button class="btn-secondary" onclick="document.getElementById('preview').scrollIntoView({behavior:'smooth'})">
      شاهد التطبيق ←
    </button>
  </div>

  <div class="hero-social-proof">
    <div class="proof-avatars">
      <div class="proof-avatar">😊</div>
      <div class="proof-avatar">🌟</div>
      <div class="proof-avatar">💪</div>
      <div class="proof-avatar">🎯</div>
    </div>
    <div class="proof-text">انضم إلى <strong>+1,200</strong> مشترك في قائمة الانتظار</div>
  </div>

  <div class="hero-scroll">
    <div class="scroll-label">SCROLL</div>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ══ STATS STRIP ══ -->
<div class="stats-strip reveal">
  <div class="stat-item">
    <div class="stat-num" id="stat1">0</div>
    <div class="stat-label">متوسط ساعات الاستماع اليومية</div>
  </div>
  <div class="stat-item">
    <div class="stat-num" id="stat2">0</div>
    <div class="stat-label">من الشباب ينامون مع سماعاتهم</div>
  </div>
  <div class="stat-item">
    <div class="stat-num" id="stat3">0</div>
    <div class="stat-label">حاولوا الإقلاع وفشلوا</div>
  </div>
  <div class="stat-item">
    <div class="stat-num" id="stat4">0</div>
    <div class="stat-label">نمو سوق البودكاست العربي سنوياً</div>
  </div>
</div>

<!-- ══ PROBLEM SECTION ══ -->
<section id="problem">
  <div class="problem-bg-text">SILENCE</div>
  <div class="problem-grid">
    <div>
      <div class="section-label reveal">المشكلة</div>
      <h2 class="section-h2 reveal reveal-delay-1">
        الصمت أصبح<br><span class="accent">مصدر قلق</span><br>لا راحة
      </h2>
      <p class="section-body reveal reveal-delay-2">
        في عالم يصخب بالبودكاست والكتب الصوتية وقوائم التشغيل التي لا تنتهي،
        فقد الجيل الجديد القدرة على البقاء في الصمت. وهذا ليس مجرد عادة —
        إنه إدمان سلوكي حقيقي يضعف الذاكرة والإبداع والصحة النفسية.
      </p>
    </div>
    <div class="problem-cards">
      <div class="problem-card reveal reveal-delay-1">
        <div class="pc-icon" style="background:rgba(255,107,138,0.1)">😴</div>
        <div>
          <div class="pc-num" style="color:#FF6B8A">58%</div>
          <div class="pc-label">ينامون مع سماعاتهم في آذانهم كل ليلة</div>
        </div>
      </div>
      <div class="problem-card reveal reveal-delay-2">
        <div class="pc-icon" style="background:rgba(245,166,35,0.1)">⏱</div>
        <div>
          <div class="pc-num" style="color:#F5A623">6.8h</div>
          <div class="pc-label">متوسط الاستماع اليومي — 3 أضعاف الموصى به</div>
        </div>
      </div>
      <div class="problem-card reveal reveal-delay-3">
        <div class="pc-icon" style="background:rgba(155,110,255,0.1)">🧠</div>
        <div>
          <div class="pc-num" style="color:#9B6EFF">71%</div>
          <div class="pc-label">لا يستطيعون الدراسة أو التركيز بدون صوت خلفي</div>
        </div>
      </div>
      <div class="problem-card reveal reveal-delay-4">
        <div class="pc-icon" style="background:rgba(0,210,175,0.1)">🌍</div>
        <div>
          <div class="pc-num" style="color:var(--teal)">صفر</div>
          <div class="pc-label">تطبيقات متخصصة في هذه المشكلة في السوق العربي</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══ SOLUTION / FEATURES ══ -->
<section id="solution">
  <div class="features-intro reveal">
    <div class="section-label">الحل</div>
    <h2 class="section-h2">ستة أسلحة<br><span class="accent">لاستعادة صمتك</span></h2>
  </div>

  <div class="features-grid reveal">
    <div class="feature-card" style="--gradient:linear-gradient(90deg,var(--teal),var(--blue))">
      <div class="fc-icon" style="background:rgba(0,210,175,0.1)">🎯</div>
      <div class="fc-title">برنامج التخفيض التدريجي</div>
      <div class="fc-desc">30 يوماً من الخطوات العلمية المدروسة تخفّض ساعات استماعك بنسبة 15% أسبوعياً دون ألم.</div>
      <div class="fc-tag" style="background:rgba(0,210,175,0.08);color:var(--teal)">CBT-Based</div>
    </div>
    <div class="feature-card" style="--gradient:linear-gradient(90deg,#9B6EFF,#3D8EFF)">
      <div class="fc-icon" style="background:rgba(155,110,255,0.1)">🧘</div>
      <div class="fc-title">تأمل موجّه بالعربية</div>
      <div class="fc-desc">جلسات تأمل صوتية بالعربية مع رسوم تنفس متحركة تحوّل الصمت من مصدر قلق إلى تجربة ممتعة.</div>
      <div class="fc-tag" style="background:rgba(155,110,255,0.08);color:#9B6EFF">Mindfulness</div>
    </div>
    <div class="feature-card" style="--gradient:linear-gradient(90deg,var(--amber),var(--rose))">
      <div class="fc-icon" style="background:rgba(245,166,35,0.1)">💰</div>
      <div class="fc-title">حاسبة الوقت والمال</div>
      <div class="fc-desc">اكتشف كم أنفقت على الاشتراكات وكم من الوقت أهدرت — ثم اعرف ماذا يمكنك أن تفعل بهذا المال.</div>
      <div class="fc-tag" style="background:rgba(245,166,35,0.08);color:var(--amber)">Reality Check</div>
    </div>
    <div class="feature-card" style="--gradient:linear-gradient(90deg,#3D8EFF,#9B6EFF)">
      <div class="fc-icon" style="background:rgba(61,142,255,0.1)">🧠</div>
      <div class="fc-title">محتوى علمي — 60 ثانية</div>
      <div class="fc-desc">مقالات موجزة من أرقى الجامعات تشرح لماذا يحتاج دماغك الصمت للإبداع والذاكرة والصحة النفسية.</div>
      <div class="fc-tag" style="background:rgba(61,142,255,0.08);color:var(--blue)">Neuroscience</div>
    </div>
    <div class="feature-card" style="--gradient:linear-gradient(90deg,#10B981,var(--teal))">
      <div class="fc-icon" style="background:rgba(16,185,129,0.1)">👥</div>
      <div class="fc-title">مجتمع التحديات</div>
      <div class="fc-desc">تحديات أسبوعية جماعية مع لوحة متصدرين تُعزز دافعيتك وتمنع الانتكاسة بدعم مجتمعي حقيقي.</div>
      <div class="fc-tag" style="background:rgba(16,185,129,0.08);color:#10B981">Social Support</div>
    </div>
    <div class="feature-card" style="--gradient:linear-gradient(90deg,var(--amber),#9B6EFF)">
      <div class="fc-icon" style="background:rgba(245,166,35,0.1)">🏆</div>
      <div class="fc-title">نظام الإنجازات والـ XP</div>
      <div class="fc-desc">نقاط وشارات وتقدم مرئي يحوّل التعافي من واجب ثقيل إلى تجربة مجزية لا تستطيع إيقافها.</div>
      <div class="fc-tag" style="background:rgba(245,166,35,0.08);color:var(--amber)">Gamification</div>
    </div>
  </div>
</section>

<!-- ══ APP PREVIEW ══ -->
<section id="preview">
  <div class="preview-glow"></div>
  <div class="preview-layout">
    <div class="preview-phones reveal">
      <!-- Phone 1 — main -->
      <div class="preview-phone">
        <div class="pp-header">
          <div class="pp-status"><span>9:41</span><span>5G ◉</span></div>
          <div class="pp-title">أهلاً، خالد 👋</div>
          <div class="pp-sub">اليوم 12 من برنامج التعافي</div>
        </div>
        <div class="pp-ring-area">
          <svg class="pp-ring-svg" width="80" height="80" viewBox="0 0 80 80">
            <circle class="ring-bg-pp" cx="40" cy="40" r="30" stroke-width="6"/>
            <circle class="ring-fg-pp" cx="40" cy="40" r="30" stroke-width="6"/>
          </svg>
        </div>
        <div class="pp-stats">
          <div class="pp-stat"><div class="pp-stat-v" style="color:var(--teal)">3.2h</div><div class="pp-stat-l">اليوم</div></div>
          <div class="pp-stat"><div class="pp-stat-v" style="color:var(--amber)">245د</div><div class="pp-stat-l">وُفِّر</div></div>
          <div class="pp-stat"><div class="pp-stat-v" style="color:var(--violet)">7</div><div class="pp-stat-l">إنجاز</div></div>
        </div>
        <div style="margin:12px 14px;padding:12px;background:rgba(0,210,175,0.08);border-radius:10px;border:1px solid rgba(0,210,175,0.2)">
          <div style="font-size:9px;color:var(--teal);font-weight:700;margin-bottom:4px">تحدي اليوم 🎯</div>
          <div style="font-size:11px;color:#EDF2FC">10 دق بدون سماعات بعد الغداء</div>
        </div>
        <div class="pp-nav">
          <div class="pp-nav-i active">🏠</div>
          <div class="pp-nav-i">📊</div>
          <div class="pp-nav-i">🧘</div>
          <div class="pp-nav-i">👥</div>
          <div class="pp-nav-i">⚙️</div>
        </div>
      </div>
      <!-- Phone 2 -->
      <div class="preview-phone">
        <div class="pp-header">
          <div class="pp-status"><span>9:41</span><span>5G</span></div>
          <div class="pp-title">تأمل الصمت 🌙</div>
          <div class="pp-sub" style="color:#9B6EFF">جلسة تنفس — 5 دقائق</div>
        </div>
        <div style="flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:16px">
          <div style="width:90px;height:90px;border-radius:50%;border:1.5px solid rgba(155,110,255,0.3);display:flex;align-items:center;justify-content:center">
            <div style="width:65px;height:65px;border-radius:50%;border:1.5px solid rgba(155,110,255,0.5);display:flex;align-items:center;justify-content:center">
              <div style="width:44px;height:44px;border-radius:50%;background:rgba(155,110,255,0.2);display:flex;flex-direction:column;align-items:center;justify-content:center">
                <div style="font-size:8px;color:#9B6EFF;font-weight:700">تنفّس</div>
              </div>
            </div>
          </div>
          <div style="font-family:var(--font-mono);font-size:24px;font-weight:700;color:white;margin-top:14px">04:12</div>
          <div style="font-size:10px;color:var(--text-muted);margin-top:4px">من 5:00 دقائق</div>
        </div>
        <div class="pp-nav">
          <div class="pp-nav-i">🏠</div>
          <div class="pp-nav-i">📊</div>
          <div class="pp-nav-i active">🧘</div>
          <div class="pp-nav-i">👥</div>
          <div class="pp-nav-i">⚙️</div>
        </div>
      </div>
      <!-- Phone 3 -->
      <div class="preview-phone" style="background:#F0F4FF">
        <div class="pp-header" style="background:linear-gradient(180deg,#E0EBFF,transparent)">
          <div class="pp-status" style="color:#4A6FA5"><span>9:41</span><span>5G</span></div>
          <div class="pp-title" style="color:#0A1628">💸 حاسبة التكلفة</div>
        </div>
        <div style="padding:12px 14px;flex:1">
          <div style="background:linear-gradient(135deg,#0A1628,#1B3A6B);border-radius:14px;padding:16px;text-align:center;margin-bottom:10px">
            <div style="font-size:10px;color:rgba(255,255,255,0.5)">إنفاقك السنوي</div>
            <div style="font-family:var(--font-mono);font-size:28px;font-weight:700;color:var(--teal)">1,740د</div>
          </div>
          <div style="display:flex;flex-direction:column;gap:6px">
            <div style="display:flex;justify-content:space-between;background:white;padding:8px 10px;border-radius:8px;border:1px solid #C5D8F0">
              <div style="font-size:10px;color:#0A1628">وقت مهدر/أسبوع</div>
              <div style="font-size:10px;font-weight:700;color:#FF6B8A">47.6 ساعة</div>
            </div>
            <div style="display:flex;justify-content:space-between;background:white;padding:8px 10px;border-radius:8px;border:1px solid #C5D8F0">
              <div style="font-size:10px;color:#0A1628">وفّرته حتى الآن</div>
              <div style="font-size:10px;font-weight:700;color:#10B981">245 درهم ✓</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="preview-text">
      <div class="section-label reveal">التطبيق</div>
      <h2 class="section-h2 reveal reveal-delay-1">واجهة مصمّمة<br>لعقلك <span class="accent">العربي</span></h2>
      <p class="section-body reveal reveal-delay-2">
        تصميم RTL أصيل، وتجربة مستخدم سلسة تعرف كيف تتحدث مع الشاب الخليجي بلغته وثقافته.
        Dark Mode للليل، وDay Mode للنهار.
      </p>
      <div class="preview-features">
        <div class="pf-item reveal reveal-delay-1"><div class="pf-icon">📱</div><div class="pf-text">iOS & Android — متاح قريباً</div><div class="pf-dot"></div></div>
        <div class="pf-item reveal reveal-delay-2"><div class="pf-icon">🌙</div><div class="pf-text">Dark Mode + Day Mode مزيج مثالي</div><div class="pf-dot"></div></div>
        <div class="pf-item reveal reveal-delay-3"><div class="pf-icon">🌐</div><div class="pf-text">عربي بالكامل — RTL أصيل وسلس</div><div class="pf-dot"></div></div>
        <div class="pf-item reveal reveal-delay-4"><div class="pf-icon">🔒</div><div class="pf-text">بياناتك خاصة — لا اشتراكات مخفية</div><div class="pf-dot"></div></div>
      </div>
    </div>
  </div>
</section>

<!-- ══ HOW IT WORKS ══ -->
<section id="how">
  <div style="max-width:700px;margin-bottom:80px" class="reveal">
    <div class="section-label">آلية العمل</div>
    <h2 class="section-h2">من الإدمان إلى<br><span class="accent">الحرية</span> في 5 خطوات</h2>
  </div>
  <div class="steps-container">
    <div class="step-row reveal">
      <div class="step-num">01</div>
      <div class="step-content">
        <div class="step-icon">🔍</div>
        <div class="step-title">التشخيص الذكي</div>
        <div class="step-desc">5 أسئلة تحلّل عاداتك الصوتية وتحدّد مستوى الإدمان بدقة، ثم تولّد لك خطة شخصية مُخصَّصة تماماً لوضعك.</div>
        <div class="step-tag">Personalized AI Plan</div>
      </div>
    </div>
    <div class="step-row reveal">
      <div class="step-num">02</div>
      <div class="step-content">
        <div class="step-icon">📉</div>
        <div class="step-title">التخفيض التدريجي</div>
        <div class="step-desc">بدلاً من الإقلاع المفاجئ الذي يفشل دائماً، نخفّض ساعاتك 15% أسبوعياً بأسلوب مبني على نظرية العلاج السلوكي المعرفي (CBT).</div>
        <div class="step-tag">CBT + Neuroscience</div>
      </div>
    </div>
    <div class="step-row reveal">
      <div class="step-num">03</div>
      <div class="step-content">
        <div class="step-icon">🧘</div>
        <div class="step-title">بناء عادة الصمت</div>
        <div class="step-desc">جلسات تأمل يومية قصيرة تُعيد برمجة تعاملك مع الصمت. من 2 دقيقة يومياً إلى 20 دقيقة بنهاية البرنامج.</div>
        <div class="step-tag">Habit Formation</div>
      </div>
    </div>
    <div class="step-row reveal">
      <div class="step-num">04</div>
      <div class="step-content">
        <div class="step-icon">📊</div>
        <div class="step-title">تتبع التحسّن</div>
        <div class="step-desc">رسوم بيانية تُظهر انخفاض ساعات الاستماع والتكلفة المالية المُوفَّرة، مع إنجازات تُحفّزك على الاستمرار يومياً.</div>
        <div class="step-tag">Real-time Analytics</div>
      </div>
    </div>
    <div class="step-row reveal">
      <div class="step-num">05</div>
      <div class="step-content">
        <div class="step-icon">🏆</div>
        <div class="step-title">الحرية الذهنية</div>
        <div class="step-desc">بعد 30 يوماً، تملك القدرة على الجلوس في الصمت 20 دقيقة بدون قلق — وتعود إليك قدرات التفكير الإبداعي والتركيز العميق.</div>
        <div class="step-tag">Mental Freedom</div>
      </div>
    </div>
  </div>
</section>

<!-- ══ SCIENCE ══ -->
<section id="science">
  <div class="text-center mb-80 reveal">
    <div class="section-label mx-auto" style="justify-content:center">العلم وراء ميوت</div>
    <h2 class="section-h2">الصمت ليس <span class="accent">فراغاً</span><br>— إنه وقود الدماغ</h2>
  </div>
  <div class="science-grid">
    <div class="science-card reveal reveal-delay-1">
      <div class="sci-icon">🧠</div>
      <div class="sci-stat">+23%</div>
      <div class="sci-title">تحسّن الذاكرة قصيرة المدى</div>
      <div class="sci-source">University of Sussex, 2023</div>
    </div>
    <div class="science-card reveal reveal-delay-2">
      <div class="sci-icon">💡</div>
      <div class="sci-stat">+41%</div>
      <div class="sci-title">ارتفاع الإبداع وتوليد الأفكار</div>
      <div class="sci-source">Journal of Neuroscience, 2024</div>
    </div>
    <div class="science-card reveal reveal-delay-3">
      <div class="sci-icon">😴</div>
      <div class="sci-stat">+31%</div>
      <div class="sci-title">تحسّن جودة النوم العميق</div>
      <div class="sci-source">NIH Sleep Research, 2023</div>
    </div>
    <div class="science-card reveal reveal-delay-1">
      <div class="sci-icon">😌</div>
      <div class="sci-stat">-37%</div>
      <div class="sci-title">انخفاض مستويات القلق اليومي</div>
      <div class="sci-source">Harvard Medical School, 2024</div>
    </div>
    <div class="science-card reveal reveal-delay-2">
      <div class="sci-icon">🎯</div>
      <div class="sci-stat">×2.4</div>
      <div class="sci-title">تضاعف التركيز لفترات طويلة</div>
      <div class="sci-source">MIT Cognitive Science, 2023</div>
    </div>
    <div class="science-card reveal reveal-delay-3">
      <div class="sci-icon">🔋</div>
      <div class="sci-stat">+58%</div>
      <div class="sci-title">ارتفاع طاقة الدماغ وصفاء الذهن</div>
      <div class="sci-source">Max Planck Institute, 2024</div>
    </div>
  </div>
</section>

<!-- ══ TESTIMONIALS ══ -->
<section id="testimonials" style="position:relative;z-index:1;padding:120px 5%;background:var(--void)">
  <div class="mb-80 reveal">
    <div class="section-label">شهادات</div>
    <h2 class="section-h2">قالوا عن ميوت</h2>
  </div>
  <div class="test-track reveal">
    <div class="test-card">
      <div class="test-stars">★★★★★</div>
      <div class="test-quote">"أول مرة أعرف إنه في اسم لمشكلتي. كنت أعتقد إني مجرد 'أحب التعلم' — لكن ميوت أثبت لي إن في فرق بين التعلم والهروب."</div>
      <div class="test-author">
        <div class="test-avatar" style="background:rgba(0,210,175,0.1)">😊</div>
        <div><div class="test-name">خالد ع.</div><div class="test-role">طالب هندسة — الشارقة</div><div class="test-result">وصل لـ 2.1 ساعة في 14 يوم</div></div>
      </div>
    </div>
    <div class="test-card">
      <div class="test-stars">★★★★★</div>
      <div class="test-quote">"حاسبة الاشتراكات غيّرت حياتي حرفياً. لما شفت إني أدفع 2,160 درهم في السنة — قررت أغيّر فوراً. الآن أنام بهدوء للمرة الأولى منذ سنتين."</div>
      <div class="test-author">
        <div class="test-avatar" style="background:rgba(155,110,255,0.1)">🌟</div>
        <div><div class="test-name">سارة م.</div><div class="test-role">طالبة أعمال — دبي</div><div class="test-result">وفّرت 543 درهم في 30 يوم</div></div>
      </div>
    </div>
    <div class="test-card">
      <div class="test-stars">★★★★★</div>
      <div class="test-quote">"كطالب طب أعلم نظرياً بأضرار الإدمان الصوتي — لكن ميوت أعطاني الخطة العلمية التي احتجتها للتطبيق الفعلي. الفرق كبير جداً."</div>
      <div class="test-author">
        <div class="test-avatar" style="background:rgba(61,142,255,0.1)">💪</div>
        <div><div class="test-name">محمد ر.</div><div class="test-role">طالب طب — أبوظبي</div><div class="test-result">يوم 28 في البرنامج</div></div>
      </div>
    </div>
    <div class="test-card">
      <div class="test-stars">★★★★☆</div>
      <div class="test-quote">"جلسات التأمل بالعربية شيء مختلف كلياً — كنت دائماً أعاني مع التطبيقات الإنجليزية. ميوت يتكلم لغتي ويفهم ثقافتي."</div>
      <div class="test-author">
        <div class="test-avatar" style="background:rgba(245,166,35,0.1)">🎯</div>
        <div><div class="test-name">نور ك.</div><div class="test-role">موظفة — الكويت</div><div class="test-result">أنجزت 21 جلسة تأمل</div></div>
      </div>
    </div>
    <div class="test-card">
      <div class="test-stars">★★★★★</div>
      <div class="test-quote">"المجتمع والتحديات الأسبوعية هي السر. كنت أفشل وحدي — لكن مع 247 شخص يكافحون نفس الكفاح أصبح ممكناً."</div>
      <div class="test-author">
        <div class="test-avatar" style="background:rgba(16,185,129,0.1)">🔥</div>
        <div><div class="test-name">أحمد خ.</div><div class="test-role">مهندس — الشارقة</div><div class="test-result">42 يوم متواصل 🔥</div></div>
      </div>
    </div>
  </div>
</section>

<!-- ══ PRICING ══ -->
<section id="pricing">
  <div class="text-center mb-80 reveal">
    <div class="section-label mx-auto" style="justify-content:center">الأسعار</div>
    <h2 class="section-h2">ابدأ <span class="accent">مجاناً</span><br>وطوّر حين تجهز</h2>
  </div>
  <div class="pricing-grid">
    <div class="price-card reveal reveal-delay-1">
      <div class="price-plan">مجاني</div>
      <div class="price-amount">0 <span>د</span></div>
      <div class="price-period">للأبد — لا بطاقة مطلوبة</div>
      <ul class="price-features">
        <li>أسبوع التجربة (7 أيام)</li>
        <li>3 جلسات تأمل أسبوعياً</li>
        <li>حاسبة الاشتراكات</li>
        <li>الانضمام للمجتمع</li>
        <li class="no">البرنامج الكامل 30 يوم</li>
        <li class="no">المحتوى العلمي</li>
        <li class="no">تحليلات متقدمة</li>
      </ul>
      <button class="btn-price btn-price-outline">ابدأ مجاناً</button>
    </div>

    <div class="price-card featured reveal reveal-delay-2">
      <div class="price-badge">الأشهر</div>
      <div class="price-plan">بريميوم</div>
      <div class="price-amount">29 <span>د</span></div>
      <div class="price-period">شهرياً — أو 249 د سنوياً</div>
      <ul class="price-features">
        <li>البرنامج الكامل 30 يوم</li>
        <li>تأمل غير محدود بالعربية</li>
        <li>حاسبة متقدمة + توصيات</li>
        <li>محتوى علمي كامل</li>
        <li>تحليلات وتقارير أسبوعية</li>
        <li>أولوية في الدعم الفني</li>
        <li>شارة "عضو مميز"</li>
      </ul>
      <button class="btn-price btn-price-fill">ابدأ الآن — جرّب 7 أيام مجاناً</button>
    </div>

    <div class="price-card reveal reveal-delay-3">
      <div class="price-plan">مؤسسات</div>
      <div class="price-amount">999 <span>د</span></div>
      <div class="price-period">شهرياً / لكل مؤسسة</div>
      <ul class="price-features">
        <li>حسابات غير محدودة</li>
        <li>لوحة تحكم للمدراء</li>
        <li>تقارير مُخصَّصة</li>
        <li>دعم مدير حساب مخصص</li>
        <li>ورش عمل توعوية</li>
        <li>شهادة مؤسسة صحية رقمياً</li>
        <li>API للتكامل مع أنظمتكم</li>
      </ul>
      <button class="btn-price btn-price-outline">تواصل معنا</button>
    </div>
  </div>
</section>

<!-- ══ CTA ══ -->
<section id="cta">
  <div class="cta-glow"></div>
  <h2 class="cta-h2 reveal">
    هل أنت مستعد<br>لاسترداد <em>صمتك</em>؟
  </h2>
  <p class="cta-sub reveal reveal-delay-1">
    سجّل الآن وكن من أوائل 500 مستخدم — وصول مبكر مجاني لمدة شهر
  </p>
  <div class="email-form reveal reveal-delay-2">
    <input class="email-input" type="email" placeholder="بريدك الإلكتروني..." />
    <button class="btn-primary">احجز مكانك</button>
  </div>
  <p class="cta-note reveal reveal-delay-3">لا إزعاج، لا رسائل مزعجة — فقط إشعار واحد عند الإطلاق</p>
</section>

<!-- ══ FOOTER ══ -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <a class="nav-logo" href="#"><div class="nav-logo-icon">🔇</div>MUTE</a>
      <p>منصة علمية لمعالجة إدمان المحتوى الصوتي — أول حل خليجي متخصص.</p>
    </div>
    <div class="footer-links">
      <h4>التطبيق</h4>
      <ul>
        <li><a href="#solution">الميزات</a></li>
        <li><a href="#how">كيف يعمل؟</a></li>
        <li><a href="#pricing">الأسعار</a></li>
        <li><a href="#">تحميل التطبيق</a></li>
      </ul>
    </div>
    <div class="footer-links">
      <h4>العلم</h4>
      <ul>
        <li><a href="#">مكتبة المقالات</a></li>
        <li><a href="#">الدراسات والمراجع</a></li>
        <li><a href="#">مدونة ميوت</a></li>
        <li><a href="#">اختبر مستواك</a></li>
      </ul>
    </div>
    <div class="footer-links">
      <h4>الشركة</h4>
      <ul>
        <li><a href="#">من نحن</a></li>
        <li><a href="#">تواصل معنا</a></li>
        <li><a href="#">سياسة الخصوصية</a></li>
        <li><a href="#">شركاء</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <div>© 2026 <span class="teal">MUTE</span> — جميع الحقوق محفوظة</div>
    <div>صُنع بـ 🔇 وعلم الأعصاب في <span class="teal">الإمارات</span></div>
    <div style="display:flex;gap:14px">
      <a href="#" style="color:var(--text-muted);text-decoration:none;font-family:var(--font-mono);font-size:12px">Twitter</a>
      <a href="#" style="color:var(--text-muted);text-decoration:none;font-family:var(--font-mono);font-size:12px">Instagram</a>
      <a href="#" style="color:var(--text-muted);text-decoration:none;font-family:var(--font-mono);font-size:12px">TikTok</a>
    </div>
  </div>
</footer>

<script>
/* ══════════════════════════════════
   CURSOR
══════════════════════════════════ */
const cursor = document.getElementById('cursor');
const cursorRing = document.getElementById('cursorRing');
let mx = 0, my = 0, rx = 0, ry = 0;

document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.left = mx + 'px';
  cursor.style.top = my + 'px';
});

function animateRing() {
  rx += (mx - rx) * 0.12;
  ry += (my - ry) * 0.12;
  cursorRing.style.left = rx + 'px';
  cursorRing.style.top = ry + 'px';
  requestAnimationFrame(animateRing);
}
animateRing();

/* ══════════════════════════════════
   STARFIELD
══════════════════════════════════ */
const canvas = document.getElementById('starCanvas');
const ctx = canvas.getContext('2d');
let stars = [];

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}

function initStars() {
  stars = [];
  for (let i = 0; i < 180; i++) {
    stars.push({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      r: Math.random() * 1.2 + 0.2,
      alpha: Math.random() * 0.6 + 0.1,
      speed: Math.random() * 0.3 + 0.05,
      pulse: Math.random() * Math.PI * 2,
    });
  }
}

function drawStars() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  stars.forEach(s => {
    s.pulse += 0.008;
    const a = s.alpha * (0.6 + 0.4 * Math.sin(s.pulse));
    ctx.beginPath();
    ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(180, 220, 255, ${a})`;
    ctx.fill();
    s.y -= s.speed;
    if (s.y < -5) { s.y = canvas.height + 5; s.x = Math.random() * canvas.width; }
  });
  requestAnimationFrame(drawStars);
}

resizeCanvas();
initStars();
drawStars();
window.addEventListener('resize', () => { resizeCanvas(); initStars(); });

/* ══════════════════════════════════
   STATS COUNTER
══════════════════════════════════ */
function countUp(el, target, suffix='', duration=2000) {
  const start = performance.now();
  const isFloat = target % 1 !== 0;
  function update(now) {
    const elapsed = now - start;
    const progress = Math.min(elapsed / duration, 1);
    const ease = 1 - Math.pow(1 - progress, 3);
    const val = target * ease;
    el.textContent = (isFloat ? val.toFixed(1) : Math.floor(val)) + suffix;
    if (progress < 1) requestAnimationFrame(update);
  }
  requestAnimationFrame(update);
}

/* ══════════════════════════════════
   INTERSECTION OBSERVER
══════════════════════════════════ */
const revealObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) { e.target.classList.add('visible'); }
  });
}, { threshold: 0.12 });

document.querySelectorAll('.reveal').forEach(el => revealObs.observe(el));

// Stats counter trigger
const statsObs = new IntersectionObserver((entries) => {
  if (entries[0].isIntersecting) {
    countUp(document.getElementById('stat1'), 6.8, 'h');
    countUp(document.getElementById('stat2'), 58, '%');
    countUp(document.getElementById('stat3'), 63, '%');
    countUp(document.getElementById('stat4'), 28, '%');
    statsObs.disconnect();
  }
}, { threshold: 0.5 });
statsObs.observe(document.querySelector('.stats-strip'));

/* ══════════════════════════════════
   SMOOTH NAV
══════════════════════════════════ */
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const target = document.querySelector(a.getAttribute('href'));
    if (target) { e.preventDefault(); target.scrollIntoView({ behavior: 'smooth' }); }
  });
});

/* ══════════════════════════════════
   PARALLAX HERO AMBIENT
══════════════════════════════════ */
window.addEventListener('scroll', () => {
  const y = window.scrollY;
  document.querySelector('.hero-ambient').style.transform = `translateY(${y * 0.3}px)`;
  document.querySelector('.hero-glow').style.transform = `translate(-50%, calc(-50% + ${y * 0.2}px))`;
});

/* ══════════════════════════════════
   SCROLL PROGRESS BAR
══════════════════════════════════ */
const progressBar = document.getElementById('scroll-progress');
window.addEventListener('scroll', () => {
  const doc = document.documentElement;
  const scrolled = doc.scrollTop / (doc.scrollHeight - doc.clientHeight);
  progressBar.style.transform = `scaleX(${scrolled})`;
}, { passive: true });

/* ══════════════════════════════════
   MOUSE TRAIL PARTICLES
══════════════════════════════════ */
const trailColors = ['rgba(0,210,175,', 'rgba(61,142,255,', 'rgba(155,110,255,'];
let lastTrail = 0;
document.addEventListener('mousemove', e => {
  const now = Date.now();
  if (now - lastTrail < 40) return;
  lastTrail = now;
  const dot = document.createElement('div');
  dot.className = 'trail-dot';
  const color = trailColors[Math.floor(Math.random() * trailColors.length)];
  const size = Math.random() * 4 + 2;
  dot.style.cssText = `
    left:${e.clientX}px; top:${e.clientY}px;
    width:${size}px; height:${size}px;
    background:${color}0.8);
    transform:translate(-50%,-50%);
  `;
  document.body.appendChild(dot);
  requestAnimationFrame(() => { dot.style.opacity = '0'; dot.style.transform = 'translate(-50%,-50%) scale(0)'; dot.style.transition = 'all 0.5s ease'; });
  setTimeout(() => dot.remove(), 550);
});

/* ══════════════════════════════════
   MAGNETIC BUTTONS
══════════════════════════════════ */
document.querySelectorAll('.btn-primary, .nav-cta').forEach(btn => {
  btn.addEventListener('mousemove', e => {
    const rect = btn.getBoundingClientRect();
    const cx = rect.left + rect.width / 2;
    const cy = rect.top + rect.height / 2;
    const dx = (e.clientX - cx) * 0.25;
    const dy = (e.clientY - cy) * 0.25;
    btn.style.transform = `translate(${dx}px, ${dy}px)`;
  });
  btn.addEventListener('mouseleave', () => {
    btn.style.transform = '';
    btn.style.transition = 'transform 0.4s ease';
    setTimeout(() => btn.style.transition = '', 400);
  });
});

/* ══════════════════════════════════
   RIPPLE CLICK EFFECT
══════════════════════════════════ */
document.querySelectorAll('.btn-primary, .btn-secondary, .btn-price, .nav-cta').forEach(btn => {
  btn.addEventListener('click', e => {
    const rect = btn.getBoundingClientRect();
    const ripple = document.createElement('span');
    ripple.className = 'ripple';
    const size = Math.max(rect.width, rect.height);
    ripple.style.cssText = `
      width:${size}px; height:${size}px;
      left:${e.clientX - rect.left - size/2}px;
      top:${e.clientY - rect.top - size/2}px;
    `;
    btn.appendChild(ripple);
    setTimeout(() => ripple.remove(), 700);
  });
});

/* ══════════════════════════════════
   TYPEWRITER EFFECT
══════════════════════════════════ */
const typeText = 'قادم قريباً — سجّل الآن للوصول المبكر';
const typeEl = document.getElementById('typewriter-text');
let typeIdx = 0;
function typeNext() {
  if (typeIdx <= typeText.length) {
    typeEl.textContent = typeText.slice(0, typeIdx);
    typeIdx++;
    setTimeout(typeNext, typeIdx < 5 ? 80 : 45);
  }
}
setTimeout(typeNext, 1200);

/* ══════════════════════════════════
   SILENCE SCORE WIDGET
══════════════════════════════════ */
const scoreWidget = document.getElementById('silence-score');
const scoreArc = document.getElementById('scoreArc');
const scoreNum = document.getElementById('scoreNum');
const scoreStatus = document.getElementById('scoreStatus');
const circumference = 175.9;

const scoreMessages = [
  { min: 0,  label: 'ابدأ الاستكشاف' },
  { min: 10, label: 'تحرّكت! 🌱' },
  { min: 25, label: 'تقدّم جيد ✨' },
  { min: 50, label: 'نصف الطريق 🎯' },
  { min: 70, label: 'قريب من الصمت 🧘' },
  { min: 90, label: 'وصلت! 🏆 أنت مستعد' },
];

let scoreShown = false;
let currentScore = 0;

window.addEventListener('scroll', () => {
  const doc = document.documentElement;
  const scrollPct = doc.scrollTop / (doc.scrollHeight - doc.clientHeight);
  const target = Math.round(scrollPct * 100);

  if (!scoreShown && doc.scrollTop > 200) {
    scoreShown = true;
    scoreWidget.classList.add('visible');
  }

  if (target !== currentScore) {
    currentScore = target;
    scoreNum.textContent = target;
    const offset = circumference * (1 - target / 100);
    scoreArc.style.strokeDashoffset = offset;
    const msg = scoreMessages.filter(m => target >= m.min).pop();
    if (msg) scoreStatus.textContent = msg.label;
  }
}, { passive: true });

const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a');
window.addEventListener('scroll', () => {
  let current = '';
  sections.forEach(s => {
    if (window.scrollY >= s.offsetTop - 100) current = s.id;
  });
  navLinks.forEach(a => {
    a.style.color = a.getAttribute('href') === '#' + current ? 'var(--teal)' : '';
  });
});
</script>
</body>
</html>
